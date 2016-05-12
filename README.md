# Rabota-3

package obfuskator;

import java.io.*;
import java.util.*;

public class Obfuskator {

    public static void main(String[] args) throws IOException {
        String komment = "/**/"; 
        Scanner sc = new Scanner(System.in);
        System.out.println("Введите путь к файлу:");
        String path = sc.nextLine();
        String path2 = path + "Obfus.java";
        File oldFile = new File(path); 
        File newFile = new File(path2);
        if (!newFile.createNewFile()) { 
            newFile.delete();
            newFile.createNewFile();
        }
        int i = 0;
        boolean sw = true;
        try (FileInputStream inputStr = new FileInputStream(oldFile);
                FileOutputStream outputStr = new FileOutputStream(newFile)) {
            while (true) { 
                i = inputStr.read();
                if (i == -1) {
                    break;
                }
                if (i == 32&&sw) {
                    while (i == 32) { 
                        i = inputStr.read();
                    }
                    outputStr.write(komment.getBytes());
                }
                if (i != 10&&i!=13) { 
                    if(i == 34) sw = !sw;
                    outputStr.write(i);
                }
            }
        } catch (IOException exc) {
            System.out.println("I/O Error: " + exc);
        }
    }

}
