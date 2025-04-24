# product2

//ساخت کلاس 

/* 
import java.util.Scanner;

public class Product {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    public Product(String name) {
        this.name = name;
        this.price = 0.0;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("please enter name:");
        String name = scanner.nextLine();

        System.out.println("please enter price:");
        double price = scanner.nextDouble();

        System.out.println("name:" + name);
        System.out.println("price:" + price);

        Product product;
    }
}
*/

//افزودن متدها و فیلدهای استاتیک 
/*
import java.util.Scanner;

public class Product {
    private String name;
    private double price;
    private static int counter = 0; 

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
        counter++; 
    }

    public Product(String name) {
        this.name = name;
        this.price = 0.0;
        counter++; 
    }

    public void displayInfo() {
        System.out.println("Product Name: " + name);
        System.out.println("Product Price: " + price);
    }

    public static void printProductCount() {
        System.out.println("Total products created: " + counter);
    }

    public void applyDiscount(double discountPercentage) {
        if (discountPercentage < 0 || discountPercentage > 100) {
            System.out.println("Invalid discount! Please enter a value between 0 and 100.");
            return;
        }

        price -= price * (discountPercentage / 100);
        System.out.println("Discount applied! New Price: " + price);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter product name: ");
        String name = scanner.nextLine();

        System.out.print("Enter product price (press enter to skip): ");
        String priceInput = scanner.nextLine();

        Product product;
        if (priceInput.isEmpty()) {
            product = new Product(name);
        } else {
            product = new Product(name, Double.parseDouble(priceInput));
        }

        product.displayInfo();

        System.out.print("Enter discount percentage (or press enter to skip): ");
        String discountInput = scanner.nextLine();
        if (!discountInput.isEmpty()) {
            double discountPercentage = Double.parseDouble(discountInput);
            product.applyDiscount(discountPercentage);
        }

        Product.printProductCount();

        scanner.close();
    }
}
*/



//کار با کالس و ارث بری
/*
public class DigitalProduct extends Product {
    private double fileSize; 

    public DigitalProduct(String name, double price, double fileSize) {
        super(name, price); 
        this.fileSize = fileSize;
    }

    public void displayInfo() {
        super.displayInfo(); 
        System.out.println("File Size: " + fileSize + " MB");
    }
}
*/



//Polymorphism کردن متد و استفاده از Override
/*
public class Product {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public void displayInfo() {
        System.out.println("Product Name: " + name);
        System.out.println("Product Price: " + price);
    }
}

public class DigitalProduct extends Product {
    private double fileSize;

    public DigitalProduct(String name, double price, double fileSize) {
        super(name, price);
        this.fileSize = fileSize;
    }

    @Override
    public void displayInfo() {
        super.displayInfo(); 
        System.out.println("File Size: " + fileSize + " MB");
    }

    public static void main(String[] args) {
        Product digitalProduct = new DigitalProduct("E-Book", 15.99, 2.5);
        
        digitalProduct.displayInfo();
    }
} 
*/



//Abstract Class و Interface 
/*
public interface IDiscountable {
    void applyDiscount(double discountPercentage);
}

public class Product implements IDiscountable {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public void displayInfo() {
        System.out.println("Product Name: " + name);
        System.out.println("Product Price: " + price);
    }

    @Override
    public void applyDiscount(double discountPercentage) {
        if (discountPercentage < 0 || discountPercentage > 100) {
            System.out.println("Invalid discount! Please enter a value between 0 and 100.");
            return;
        }
        price -= price * (discountPercentage / 100);
        System.out.println("Discount applied! New Price: " + price);
    }
}

public class PhysicalProduct extends Product {
    private double weight; 

    public PhysicalProduct(String name, double price, double weight) {
        super(name, price); 
        this.weight = weight;
    }

    @Override
    public void displayInfo() {
        super.displayInfo(); 
        System.out.println("Product Weight: " + weight + " kg");
    }
}

public class Main {
    public static void main(String[] args) {
        Product physicalProduct = new PhysicalProduct("Laptop", 1000.0, 2.5);

        physicalProduct.displayInfo();

        physicalProduct.applyDiscount(10);
    }
}
*/



// Abstract استفاده از کلاس 
/*
public abstract class Product {
    protected String name;
    protected double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public abstract void displayInfo();
}

public class PhysicalProduct extends Product {
    private double weight;

    public PhysicalProduct(String name, double price, double weight) {
        super(name, price);
        this.weight = weight;
    }

    @Override
    public void displayInfo() {
        System.out.println("Product Name: " + name);
        System.out.println("Product Price: " + price);
        System.out.println("Product Weight: " + weight + " kg");
    }
}

public class DigitalProduct extends Product {
    private double fileSize;

    public DigitalProduct(String name, double price, double fileSize) {
        super(name, price);
        this.fileSize = fileSize;
    }

    @Override
    public void displayInfo() {
        System.out.println("Product Name: " + name);
        System.out.println("Product Price: " + price);
        System.out.println("File Size: " + fileSize + " MB");
    }
}

public class Main {
    public static void main(String[] args) {
        Product physicalProduct = new PhysicalProduct("Laptop", 1000.0, 2.5);
        physicalProduct.displayInfo();

        System.out.println("------------------");

        Product digitalProduct = new DigitalProduct("E-Book", 15.99, 2.5);
        digitalProduct.displayInfo();
    }
}
*/





//Downcasting و Upcasting
/*
import java.util.ArrayList;

public abstract class Product {
    protected String name;
    protected double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public abstract void displayInfo();
}

interface IDiscountable {
    void applyDiscount(double discountPercentage);
}

class PhysicalProduct extends Product implements IDiscountable {
    private double weight;

    public PhysicalProduct(String name, double price, double weight) {
        super(name, price);
        this.weight = weight;
    }

    @Override
    public void displayInfo() {
        System.out.println("Physical Product:");
        System.out.println("Name: " + name);
        System.out.println("Price: " + price);
        System.out.println("Weight: " + weight + " kg");
    }

    @Override
    public void applyDiscount(double discountPercentage) {
        if (discountPercentage > 0 && discountPercentage <= 100) {
            price -= price * (discountPercentage / 100);
            System.out.println("Discount applied! New Price: " + price);
        } else {
            System.out.println("Invalid discount percentage!");
        }
    }

    public double getWeight() {
        return weight;
    }
}

class DigitalProduct extends Product {
    private double fileSize;

    public DigitalProduct(String name, double price, double fileSize) {
        super(name, price);
        this.fileSize = fileSize;
    }

    @Override
    public void displayInfo() {
        System.out.println("Digital Product:");
        System.out.println("Name: " + name);
        System.out.println("Price: " + price);
        System.out.println("File Size: " + fileSize + " MB");
    }
}

public class Main {
    public static void main(String[] args) {
        Product product = new PhysicalProduct("Laptop", 1000, 2.5);

        if (product instanceof PhysicalProduct) {
            PhysicalProduct physicalProduct = (PhysicalProduct) product;
            System.out.println("The weight of the product is: " + physicalProduct.getWeight() + " kg");
        }

        System.out.println("---------------------");

        ArrayList<Product> products = new ArrayList<>();
        products.add(new PhysicalProduct("Phone", 500, 0.3));
        products.add(new DigitalProduct("E-Book", 15.99, 2.5));
        products.add(new PhysicalProduct("Tablet", 750, 0.8));
        products.add(new DigitalProduct("Music Album", 9.99, 1.2));

        for (Product p : products) {
            p.displayInfo();
            if (p instanceof IDiscountable) {
                ((IDiscountable) p).applyDiscount(10); 
            }
            System.out.println("---------------------");
        }
    }
} 
*/
