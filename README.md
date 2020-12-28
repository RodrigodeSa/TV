# TV
Primeiros Exercícios de POO
package entities;
public class Products {
	private String name;
	private double price; // ATRIBUTOS DO OBJETO
	private int quantity;
	
	public Products() {	
	}
	public Products (String name, double price, int quantity) {
		this.name = name;  // PARAMETRO DO OBJETO
		this.price = price;
		this.quantity = quantity;
	}
	public Products (String name, double price) {
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
	public int getQuantity() {
		return quantity;
	}
	
	public double totalValueInStock() {
		return price*quantity;
	}
	
	public void addProducts (int quantity) {
		this.quantity += quantity;
	}
	
	public void removeProducts (int quantity) {
		this.quantity -= quantity;
	}
	
	public String toString() {
		return name
				+", $ "
				+String.format("%.2f",price)
				+", "
				+quantity
				+" units, Total: $ "
				+String.format("%.2f",totalValueInStock());
				
	}
}


package application;

import java.util.Locale;
import java.util.Scanner;

import entities.Products;


public class Program {

	public static void main(String[] args) {

		Locale.setDefault(Locale.US);
		Scanner sc = new Scanner(System.in);		

		System.out.println("Enter product data: ");
		System.out.print("Name: ");
		String name = sc.nextLine();
		System.out.print("Price: ");
		double price = sc.nextDouble();
		
		Products product = new Products(name, price);//aula Construtores (instanciação mudou de lugar)(com sobrecarga)
		
		product.setName("Computer");
		System.out.println("Updated name: " + product.getName());
		product.setPrice(1200.00);
		System.out.println("Updated price: " + product.getPrice());
		int quantity;
		System.out.println();
		System.out.print("Product data: " + product);
		System.out.println();
		
		System.out.print("Enter the number of produts to be added in stock: ");
		quantity = sc.nextInt();
		product.addProducts(quantity);

		System.out.println();
		System.out.print("Updated data: " + product);

		System.out.println();
		System.out.print("Enter the number of produts to be removed in stock: ");
		quantity = sc.nextInt();
		product.removeProducts(quantity);

		System.out.println();
		System.out.print("Updated data: " + product);

		sc.close();

	}

}
