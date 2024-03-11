# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-

//NAME: RIDHI   CLASS: BCA-4-C/2  ROLL NUMBER:2210997192
import java.util.Scanner;

class EMPLOYEE {
    String NameOfEmp;
    int EmpId;
    double BasicSalary;
    double GrossSalary;

    EMPLOYEE(String NameOfEmp, int EmpId, double BasicSalary) {
        this.NameOfEmp = NameOfEmp;
        this.EmpId = EmpId;
        this.BasicSalary = BasicSalary;
        calculateSalary();
    }

    void calculateSalary() {
        double HRA = 0.25 * BasicSalary;
        double DA = 0.40 * BasicSalary;
        GrossSalary = BasicSalary + HRA + DA;
    }

    void displayConsonantEmployees() {
        if (!NameOfEmp.toLowerCase().startsWith("a") && !NameOfEmp.toLowerCase().startsWith("e")
                && !NameOfEmp.toLowerCase().startsWith("i") && !NameOfEmp.toLowerCase().startsWith("o")
                && !NameOfEmp.toLowerCase().startsWith("u")) {
            System.out.println("Name: " + NameOfEmp + ", Gross Salary: " + GrossSalary);
        }
    }

    void displayEmpIdRange() {
        if (EmpId >= 101 && EmpId <= 150) {
            System.out.println("Emp ID: " + EmpId + ", Gross Salary: " + GrossSalary);
        }
    }

    static int countLowSalaryEmployees(EMPLOYEE[] employees) {
        int count = 0;
        for (EMPLOYEE emp : employees) {
            if (emp.GrossSalary < 35000) {
                count++;
            }
        }
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of employees: ");
        int numEmployees = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        EMPLOYEE[] employees = new EMPLOYEE[numEmployees];

        for (int i = 0; i < numEmployees; i++) {
            System.out.print("Enter name of employee " + (i + 1) + ": ");
            String NameOfEmp = scanner.nextLine();
            System.out.print("Enter Emp ID of employee " + (i + 1) + ": ");
            int EmpId = scanner.nextInt();
            System.out.print("Enter Basic Salary of employee " + (i + 1) + ": ");
            double BasicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline
            employees[i] = new EMPLOYEE(NameOfEmp, EmpId, BasicSalary);
        }

        //(a)Display employees whose name starts with a consonant
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (EMPLOYEE emp : employees) {
            emp.displayConsonantEmployees();
        }

        // (b) Display employees with EmpId between 101 and 150
        System.out.println("\nEmployees with Emp ID between 101 and 150:");
        for (EMPLOYEE emp : employees) {
            emp.displayEmpIdRange();
        }

        // (c) Count employees with GrossSalary less than 35000
        int count = EMPLOYEE.countLowSalaryEmployees(employees);
        System.out.println("\nTotal number of employees with GrossSalary less than 35000: " + count);

        scanner.close();
    }
}
