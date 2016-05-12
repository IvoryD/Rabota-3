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

