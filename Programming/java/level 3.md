## Email Privacy
```java
public class EmailPrivacy {
    public static void main(String[] args) {
        String email = "user@gmail.com";

        // Get the position of '@'
        int atIndex = email.indexOf('@');

        // Calculate the number of characters to hide
        int hiddenLength = atIndex - 2;

        // Create a dynamic mask based on hiddenLength
        String mask = "*".repeat(hiddenLength);

        // Construct the hidden email
        String hidden = email.charAt(0) + mask + email.charAt(atIndex - 1) + email.substring(atIndex);

        System.out.println(hidden);
    }
}

```
## Camel case to Snake Case
```java
public class CamelToSnake {
    public static void main(String[] args) {
        String camel = "thisIsCamelCase";
        System.out.println(convertToSnakeCase(camel));
    }

    public static String convertToSnakeCase(String camel) {
        StringBuilder snake = new StringBuilder();

        for (char c : camel.toCharArray()) {
            // If the character is uppercase, add an underscore before it (except at the beginning)
            if (Character.isUpperCase(c)) {
                if (snake.length() > 0) {
                    snake.append('_');
                }
                snake.append(Character.toLowerCase(c));
            } else {
                snake.append(c);
            }
        }

        return snake.toString();
    }
}

// or useing regix
public class CamelToSnake {
    public static void main(String[] args) {
        String camel = "thisIsCamelCase";
        System.out.println(camel.replaceAll("([a-z])([A-Z])",         "$1_$2").toLowerCase());   
     }
}


```

## Input : 3       "the movie" was good.     Output; "The movie" was good.          Explanation : first get a no of words as input. then get the words. change the 1st word 1st letter to capital. then print all words in single line. 
```java
import java.util.Scanner;

public class CapitalizeFirstWord {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read number of words (not used, but required as per the problem statement)
        int numWords = scanner.nextInt();
        scanner.nextLine();  // Consume the newline character

        // Read the entire sentence
        String sentence = scanner.nextLine().trim();

        // Split sentence into words
        String[] words = sentence.split(" ", numWords);

        // Capitalize the first letter of the first word
        if (words.length > 0) {
            words[0] = Character.toUpperCase(words[0].charAt(0)) + words[0].substring(1);
        }

        // Print the modified sentence
        System.out.println(String.join(" ", words));

        scanner.close();
    }
}

```
## Freq count
```java
public class Main{
    public static void main(String[] args) {
        String str = "aaaabbb";
        StringBuilder encoded = new StringBuilder();
        int count = 1;
        for (int i = 1; i < str.length(); i++) {
            if (str.charAt(i) == str.charAt(i - 1)) {
                count++;
            } else {
                encoded.append(str.charAt(i - 1)).append(count);
                count = 1;
            }
        }
        encoded.append(str.charAt(str.length() - 1)).append(count);
        System.out.println(encoded);
    }
}

```