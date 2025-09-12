import java.io.*;
import java.util.*;
 
public class VendingMachine {

    static class Drink {
        String name;
        int quantity;
        double price;

        Drink(String name, int quantity, double price) {
            this.name = name;
            this.quantity = quantity;
            this.price = price;
        }
    }

    static List<Drink> drinks = new ArrayList<>();
    static double totalInserted = 0.0;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

    
        readPrices("Prices.txt");


        listDrinks();

    
        insertCoins(scanner);


        selectDrink(scanner);

        
        scanner.close();
    }


    static void readPrices(String filename) {
        try (BufferedReader br = new BufferedReader(new FileReader(filename))) {
            String line;
            while ((line = br.readLine()) != null) {
                String[] parts = line.split(",");
                String name = parts[0];
                int quantity = Integer.parseInt(parts[1]);
                double price = Double.parseDouble(parts[2].replace("$", ""));
                drinks.add(new Drink(name, quantity, price));
            }
        } catch (IOException e) {
            System.out.println("Prices.txt dosyası okunamadı.");
        }

    static void listDrinks() {
        System.out.println("\n--- Mevcut İçecekler ---");
        for (Drink drink : drinks) {
            if (drink.quantity > 0) {
                System.out.printf("%s - %.2f$ (%d adet)\n", drink.name, drink.price, drink.quantity);
            }
        }
    }


    static void insertCoins(Scanner scanner) {
        System.out.println("Para atmaya başlayın ('tamam' yazınca durur):");
        while (true) {
            String coin = scanner.nextLine().trim();
            if (coin.equalsIgnoreCase("tamam")) break;

            if (coin.equals("1$")) totalInserted += 1.0;
            else if (coin.equals("50c")) totalInserted += 0.5;
            else if (coin.equals("25c")) totalInserted += 0.25;
            else if (coin.equals("10c")) totalInserted += 0.1;
            else if (coin.equals("5c")) totalInserted += 0.05;
            else if (coin.equals("1c")) totalInserted += 0.01;
            else System.out.println("Geçersiz para!");

            System.out.printf("Toplam para: %.2f$\n", totalInserted);
        }
    }

    
    static void selectDrink(Scanner scanner) {
        System.out.println("Bir içecek seçin:");
        String selection = scanner.nextLine().trim();

        for (Drink drink : drinks) {
            if (drink.name.equalsIgnoreCase(selection) && drink.quantity > 0) {
                if (drink.price <= totalInserted) {
                    drink.quantity--;
                    totalInserted -= drink.price;
                    System.out.printf("%s verildi. Kalan para: %.2f$\n", drink.name, totalInserted);
                    return;
                } else {
                    System.out.println("Yetersiz bakiye.");
                    return;
                }
            }
        }
        System.out.println("İçecek bulunamadı.");
    }
