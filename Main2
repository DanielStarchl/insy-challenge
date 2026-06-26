import java.awt.*;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.*;
import java.util.Locale;
import java.util.Scanner;

public class Main2 {
    public static void main(String args[]) {
        System.out.println("---LOGIN TERMINAL---");
        System.out.println("Tipp-Query: Select * from users where username = 'admin' and passwort=**** \n");
        System.out.println("Passwort: ");
        Scanner sc = new Scanner(System.in);
        String pw = sc.nextLine();

        String filter = pw.toLowerCase();
        if(filter.contains("or") || filter.contains("1=1") || filter.contains("--")){
        System.out.println("Das wäre zu einfach gewesen");
        System.exit(0);
        }

        try(Connection conn = DriverManager.getConnection("jdbc:sqlite::memory:")) {
            Statement stmt = conn.createStatement();
            stmt.execute("Create table if not exists users(username Text , password Text) ");
            stmt.execute("Insert into users values('admin','stritzi')");

            String input = "Select * from users where username = 'admin' and password='" + pw + "'";
            System.out.println("Query: " + input);
            ResultSet rs = stmt.executeQuery(input);

            if (rs.next()){
                System.out.println("Login success!");
                File file = new File("proof.txt");
                if (file.exists()){
                    Desktop.getDesktop().open(file);
                }
            }else{
                System.out.println("Login Failed");
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }

}
