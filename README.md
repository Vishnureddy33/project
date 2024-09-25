# Suitable selection for petshop manangement
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Pet {
    private String type;
    private String breed;
    private int age;
    private double price;

    public Pet(String type, String breed, int age, double price) {
        this.type = type;
        this.breed = breed;
        this.age = age;
        this.price = price;
    }

    public String getType() {
        return type;
    }

    public String getBreed() {
        return breed;
    }

    public int getAge() {
        return age;
    }

    public double getPrice() {
        return price;
    }

    @Override
    public String toString() {
        return String.format("%s\t%s\t%d\t%.2f", type, breed, age, price);
    }
}

public class PetShopManager {
    private List<Pet> pets = new ArrayList<>();

    public void addPet(String type, String breed, int age, double price) {
        Pet pet = new Pet(type, breed, age, price);
        pets.add(pet);
        System.out.println("Pet added successfully!");
    }

    public void displayPets() {
        if (pets.isEmpty()) {
            System.out.println("No pets available.");
        } else {
            System.out.println("Type\tBreed\tAge\tPrice");
            System.out.println("-------------------------------------");
            for (Pet pet : pets) {
                System.out.println(pet);
            }
        }
    }

    public static void main(String[] args) {
        PetShopManager manager = new PetShopManager();
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\nPet Shop Management System");
            System.out.println("1. Add Pet");
            System.out.println("2. View Pets");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter pet type (e.g., Dog, Cat, Fish): ");
                    String type = scanner.nextLine();
                    System.out.print("Enter pet breed: ");
                    String breed = scanner.nextLine();
                    System.out.print("Enter pet age: ");
                    int age = scanner.nextInt();
                    System.out.print("Enter pet price: ");
                    double price = scanner.nextDouble();
                    scanner.nextLine();  // Consume newline

                    manager.addPet(type, breed, age, price);
                    break;

                case 2:
                    manager.displayPets();
                    break;

                case 3:
                    System.out.println("Exiting the system. Goodbye!");
                    break;

                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 3);

        scanner.close();
    }
}
# Input format
