# Tutorial 
```
QUESTIONS:

1. Write statements for each of the following:
  a. Store ten random integers within 0 to 1000 to a text file name integer.txt.
  b. Read from the text file generated in a. Display all the integer and the largest integer.
  c. Store ten random integers within 0 to 1000 to a binary file name integer.dat.
  d. Read from the binary file generated in a c. Display the all the integer and the average.

2. Correct the error for the following statements.
  a. PrintWriter out = new PrintWriter(new FileOutputStream("d:\data\matrix.txt"));
  b.
  try {
    PrintWriter out = new PrintWriter(new FileOutputStream("data.txt"));
    out.close();
    }
   catch (FileNotFoundException e) {
    System.out.println("Problem with file output");
    }
  c.
  int num;
  Scanner a = new Scanner(new FileInputStream("data.dat"));
  num = a.readInt();
  a.close();

  d.
  ObjectOutputStream o = new ObjectOutputStream (new
  FileOutputStream("data.dat"));
  o.print('A');
  o.close();

3. Write a program that convert a sentence into binary number (ASCII code 8 bit) and store it in a text file named data.txt. Then, read from the text file and display the sentence.
```

```java
//Q1 (a):
import java.util.Random;
import java.io.PrintWriter;
import java.io.IOException;
import java.io.FileOutputStream;
public class Main {
    public static void main(String[] args) {
        try{
            PrintWriter pw= new PrintWriter(new FileOutputStream("integer.txt"));
            Random r= new Random();
            for(int i=0; i<10; i++){
                int num=r.nextInt(1001);
                pw.println(num);
            }
            pw.close();
        }
        catch(IOException e){
            System.out.println("An error occurred: "+e);
        }
    }
}
```

```java
//Q1 (b):
import java.util.Scanner;
import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class Main {
    public static void main(String[] args) {
        try{
            Scanner keyboard= new Scanner(new FileInputStream("integer.txt"));
            int num=keyboard.nextInt();
            int max=num;
            while(keyboard.hasNextInt()){
                System.out.println(num);
                if(num>max){
                    max=num;
                }
                num=keyboard.nextInt();
            }
            System.out.println(num);
            if(num>max){
                max=num;
            }
            System.out.println("The largest integer is: "+ max);
            keyboard.close();
        }
        catch(FileNotFoundException e){
            System.out.println("An error occurred: "+ e);
        }
    }
}
```

```java
//Q1 (c):
import java.util.Random;
import java.io.ObjectOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try{
            ObjectOutputStream oos= new ObjectOutputStream(new FileOutputStream("integer.dat"));
            Random r= new Random();
            for(int i=0; i<10; i++){
                int num=r.nextInt(1001);
                oos.writeInt(num);
            }
            oos.close();
        }
        catch(IOException e){
            System.out.println("An error occurred: "+e);
        }
    }
}
```

```java
//Q1 (d)
import java.io.ObjectInputStream;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try{
            ObjectInputStream ois=new ObjectInputStream(new FileInputStream("integer.dat"));
            int sum=0;
            for(int i=0;i<10;i++){
                int num=ois.readInt();
                System.out.println(num);
                sum+=num;
            }
            ois.close();
            double average=sum/10.0;
            System.out.println("Average: "+average);
            
        }
        catch(FileNotFoundException e){
            System.out.println("An error occurred: "+e);
        }
        catch(IOException e){
            System.out.println("An error occurred: "+e);
        }
    }
}
```
