# Tutorial 
1. a)
```java
PrintWriter out = new PrintWriter(new FileOutputStream("integer.txt"));
Random r = new Random();
for (int i = 0; i < 10; i++) {
    out.println(r.nextInt(1001));
}
out.close;
```

  b)
```java
Scanner in = new Scanner(new FileInputStream("integer.txt"));
int max = Integer.MIN_VALUE;
while (in.hasNextInt()) {
    int val = in.nextInt();
    System.out.println(val);
    if (val > max) max = val;
}
System.out.println("Largest: " + max);
in.close;
```

  c)
```java
ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("integer.dat"));
Random r = new Random();
for (int i = 0; i < 10; i++) {
    out.writeInt(r.nextInt(1001));
}
out.close;
```

  d)
```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("integer.dat"));
int sum = 0, count = 0;
try {
    while (true) {
        int val = in.readInt();
        System.out.println(val);
        sum += val;
        count++;
    }
} catch (EOFException e) {
}
System.out.println("Average: " + (double)sum/count);
in.close;
```
2. a)
```java
PrintWriter out = new PrintWriter(new FileOutputStream("d:\\data\\matrix.txt"));
```

  b)
```java
try {
    PrintWriter out = new PrintWriter(new FileOutputStream("data.txt"));
    out.close();
} catch (IOException e) {
    System.out.println("Problem with file output: " + e.getMessage());
}
```

  c)
```java
int num;
try {
    DataInputStream a = new DataInputStream(new FileInputStream("data.dat"));
    num = a.readInt();
    a.close;
} catch (IOException e) {
    System.out.println("Error reading binary file");
}
```

  d)
```java
try {
    ObjectOutputStream o = new ObjectOutputStream(new FileOutputStream("data.dat"));
    o.writeChar('A');
    o.close;
} catch (IOException e) {
    System.out.println("Error writing binary file");
}
```

3.
```java
import java.io.*;
import java.util.Scanner;

public class BinaryConverter {
    public static void main(String[] args) {
        String sentence = "Hello World";
        String fileName = "data.txt";

        try {
            PrintWriter writer = new PrintWriter(new FileOutputStream(fileName));
            for (char c : sentence.toCharArray()) {
                String binary = String.format("%8s", Integer.toBinaryString(c)).replace(' ', '0');
                writer.print(binary + " "); 
            }
            writer.close();
            System.out.println("Sentence stored in binary format.");
        } catch (IOException e) {
            System.out.println("Error writing to file.");
        }

        try {
            Scanner reader = new Scanner(new FileInputStream(fileName));
            StringBuilder result = new StringBuilder();
            System.out.print("Read from file: ");
            
            while (reader.hasNext()) {
                String binaryString = reader.next();
                int charCode = Integer.parseInt(binaryString, 2);
                result.append((char) charCode);
            }
            
            System.out.println(result.toString());
            reader.close();
        } catch (IOException e) {
            System.out.println("Error reading from file.");
        }
    }
}
```
