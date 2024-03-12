# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-
//RIDHI 2210997192


package ridhiii;
import java.util.Scanner;

class Employee {
    String nameOfEmp;
    int empId;
    double basicSalary;
    double grossSalary;

    // Constructor to initialize data members
    Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate GrossSalary
    void calculateGrossSalary() {
        double hra = 0.25 * basicSalary;
        double da = 0.40 * basicSalary;
        grossSalary = basicSalary + hra + da;
    }

    // Method to display employee information
    void displayInfo() {
        System.out.println("Name: " + nameOfEmp + ", Gross Salary: " + grossSalary);
    }

    // Method to check if the name starts with a consonant
    boolean startsWithConsonant() {
        char firstChar = Character.toLowerCase(nameOfEmp.charAt(0));
        return !(firstChar == 'a' || firstChar == 'e' || firstChar == 'i' || firstChar == 'o' || firstChar == 'u');
    }

    // Method to check if the EmpId is between 101 and 150
    boolean isEmpIdInRange() {
        return empId >= 101 && empId <= 150;
    }

    // Method to check if the GrossSalary is less than 35000
    boolean isGrossSalaryLessThan35000() {
        return grossSalary < 35000;
    }
}


public class Main {
	public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Taking input for number of employees
        System.out.print("Enter the number of employees: ");
        int numOfEmployees = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        Employee[] employees = new Employee[numOfEmployees];

        // Inputting employee details
        for (int i = 0; i < numOfEmployees; i++) {
            System.out.println("Enter details for Employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Emp Id: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline

            employees[i] = new Employee(name, empId, basicSalary);
        }

        // Displaying employees whose name starts with a consonant
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (Employee employee : employees) {
            if (employee.startsWithConsonant()) {
                employee.displayInfo();
            }
        }

        // Displaying employees whose EmpId is between 101 and 150
        System.out.println("\nEmployees whose EmpId is between 101 and 150:");
        for (Employee employee : employees) {
            if (employee.isEmpIdInRange()) {
                System.out.println("Emp Id: " + employee.empId + ", Gross Salary: " + employee.grossSalary);
            }
        }

        // Counting employees whose GrossSalary is less than 35000
        int count = 0;
        for (Employee employee : employees) {
            if (employee.isGrossSalaryLessThan35000()) {
                count++;
            }
        }
        System.out.println("\nTotal number of employees whose GrossSalary is less than 35000: " + count);

        scanner.close();
    }
}
