# Employee
creates an employee class then extends it
and demonstrates how to handle exceptions


public class Employee {
    private String name;
    private String employeeNumber;
    private String hireDate;

    public Employee(String n, String num, String date) throws InvalidEmployeeNumber {
        this.name = n;
        this.setEmployeeNumber(num);
        this.hireDate = date;
    }

    public Employee() {
        this.name = "";
        this.employeeNumber = "";
        this.hireDate = "";
    }

    public void setName(String n) {
        this.name = n;
    }

    public void setEmployeeNumber(String e) throws InvalidEmployeeNumber {
        if(this.isValidEmpNum(e)) {
            this.employeeNumber = e;
        } else {
            throw new InvalidEmployeeNumber();
        }
    }

    public void setHireDate(String h) {
        this.hireDate = h;
    }

    public String getName() {
        return this.name;
    }

    public String getEmployeeNumber() {
        return this.employeeNumber;
    }

    public String getHireDate() {
        return this.hireDate;
    }

    private boolean isValidEmpNum(String e) {
        boolean status = true;
        if(e.length() != 5) {
            status = false;
        } else if(!Character.isDigit(e.charAt(0)) || !Character.isDigit(e.charAt(1)) || !Character.isDigit(e.charAt(2)) || e.charAt(3) != 45 || Character.toUpperCase(e.charAt(4)) < 65 || Character.toUpperCase(e.charAt(4)) > 77) {
            status = false;
        }

        return status;
    }

    public String toString() {
        String str = "Name: " + this.name + "\nEmployee Number: ";
        if(this.employeeNumber == "") {
            str = str + "INVALID EMPLOYEE NUMBER";
        } else {
            str = str + this.employeeNumber;
        }

        str = str + "\nHire Date: " + this.hireDate;
        return str;
    }
}
