import java.util.ArrayList;
import java.util.Scanner;

class Book {
    String title;
    double price;

    public Book(String title, double price) {
        this.title = title;
        this.price = price;
    }

    @Override
    public String toString() {
        return title + " - $" + price;
    }
}

public class BookStore {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Book> books = new ArrayList<>();
        books.add(new Book("Java Programming", 30.99));
        books.add(new Book("Python Basics", 25.50));
        books.add(new Book("Web Development", 40.75));

        ArrayList<Book> cart = new ArrayList<>();
        int choice;

        do {
            System.out.println("Welcome to the Bookstore! Choose a book to add to cart:");
            for (int i = 0; i < books.size(); i++) {
                System.out.println((i + 1) + ". " + books.get(i));
            }
            System.out.println("4. Checkout");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            if (choice >= 1 && choice <= books.size()) {
                cart.add(books.get(choice - 1));
                System.out.println("Book added to cart!");
            }
        } while (choice != 4);

        double total = 0;
        System.out.println("\nYour Cart:");
        for (Book book : cart) {
            System.out.println(book);
            total += book.price;
        }
        System.out.println("Total Price: $" + total);
        System.out.println("Thank you for shopping with us!");
    }
}
