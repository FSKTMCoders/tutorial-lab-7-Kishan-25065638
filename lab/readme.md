```java
//Q1.
import java.util.Scanner;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class Main{
    public static void main(String[] args){
        try{
            ObjectOutputStream oos= new ObjectOutputStream(new FileOutputStream("coursename.dat"));
            String[] CourseCode={"Course Code","WXES1116","WXES1115","WXES1110","WXES1112"};
            String[] CourseName={"Course Name","Programming I","Data Structure","Operating System","Computing Mathematics I"};
            for(int i=0;i<CourseCode.length;i++){
                oos.writeUTF(CourseCode[i]+" is "+CourseName[i]);
            }
            oos.close();
        }
        catch(IOException e){
            System.out.println("ERROR");
        }
        try{
            ObjectInputStream ois=new ObjectInputStream(new FileInputStream("coursename.dat")); 
            Scanner keyboard= new Scanner(System.in);
            System.out.print("Enter Course Code: ");
            String Code=keyboard.nextLine();
            String line= ois.readUTF();

            for(int i=0;i<5;i++){
                if(line.contains(Code)){
                    System.out.println("Course Name for "+line);
                }
                line=ois.readUTF();
            }  
            ois.close();
        }
        catch(IOException e){
            System.out.println("");
        }
    }
}
```

```java
//Q2.
import java.util.Scanner;
import java.net.URL;
import java.io.InputStream;
import java.net.URLConnection;
import java.io.IOException;
import java.io.PrintWriter;
import java.io.FileOutputStream;
import java.io.FileInputStream;
import java.io.FileNotFoundException;


public class Main{
    public static void main(String[] args){
        try {
            URL u = new URL("http://fsktm.um.edu.my");
            URLConnection cnn = u.openConnection();
            InputStream stream = cnn.getInputStream();
            Scanner in = new Scanner(stream);
            PrintWriter pw = new PrintWriter(new FileOutputStream("index.htm"));
            while(in.hasNextLine()){ //while the webiste has next line
                String line = in.nextLine(); //line is line read from the website. starting from first line to last line.
                pw.println(line); //writes the current line into the text file
            }
            in.close();
            pw.close();
        }
        catch (IOException e) {
            System.out.println("IO Error:" + e.getMessage());
        }
        try{
            Scanner inp=new Scanner(new FileInputStream("index.htm"));
            while(inp.hasNextLine()){
                String line=inp.nextLine();
                System.out.println(line);
            }
            inp.close();
        }
        catch(FileNotFoundException e){
            System.out.println("File not found: " + e.getMessage());
        }
        catch(IOException e){
            System.out.println("IO Error: " + e.getMessage());
        }   

    }
}
```
```java
//Q3.
import java.io.PrintWriter;
import java.io.FileOutputStream;    
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        try{
            Scanner sc= new Scanner(new FileInputStream("text file.txt"));
            PrintWriter pw= new PrintWriter(new FileOutputStream("reverse.txt"));
            while(sc.hasNextLine()){
                String line=sc.nextLine(); // read a line say : "Hello"
                for (int i=line.length()-1;i>=0;i--){ //i=4,3,2,1,0
                    pw.print(line.charAt(i)); //o,l,l,e,H
                }
                pw.print("\n");
            }
            pw.close();
            sc.close();
        }
        catch(FileNotFoundException e){
            System.out.println("File not found: "+ e);
        }
        catch(IOException e){
            System.out.println("An error occurred: "+ e);
        }
    }
}
```

```java
//Q4.
import java.util.Scanner;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
public class Main{
    public static void main(String[] args){
        try{
            Scanner sc= new Scanner(new FileInputStream("text file.txt"));
            int charCount=0;
            int wordCount=0;
            int lineCount=0;
            while(sc.hasNextLine()){
                String line=sc.nextLine();
                System.out.println(line);

                lineCount++;
                charCount += line.length(); 
                String[] words = line.split(" ");
                wordCount += words.length;
            }
            System.out.println("\n"+"Number of characters: " + charCount);
            System.out.println("Number of words: " + wordCount);
            System.out.println("Number of lines: " + lineCount);
            sc.close();
        }
        catch(FileNotFoundException e){
            System.out.println("An error occurred: "+ e);
        }
    }
}
```

```java
//Q5.
import java.io.ObjectInputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        try{
            ObjectInputStream ois=new ObjectInputStream(new FileInputStream("person.dat"));
            int totalRecords=ois.readInt();
            for(int i=0;i<totalRecords;i++){
                String name=ois.readUTF();
                int age=ois.readInt();
                char gender=ois.readChar();
                System.out.println("Name: "+name+", Age: "+age+", Gender: "+gender);
            }
        }
        catch(FileNotFoundException e){
            System.out.println("File not found: "+e);
        }
        catch(IOException e){
            System.out.println("An error occurred: "+e);   
        }
    }
}
```
