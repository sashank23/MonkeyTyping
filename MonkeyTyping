import java.util.Random;
import java.util.Scanner;

public class MonkeyTyping {

    // Array of meaningful words to generate the random text from
    private static final String[] WORDS = {
        "apple", "banana", "cherry", "date", "elderberry", "fig", "grape", "honeydew",
        "kiwi", "lemon", "mango", "nectarine", "orange", "papaya", "quince", "raspberry",
        "strawberry", "tangerine", "ugli", "vanilla", "watermelon", "xigua", "yam", "zucchini"
    };

    // Method to generate a random sentence of given word count
    public static String generateRandomText(int wordCount) {
        Random random = new Random();
        StringBuilder text = new StringBuilder();

        for (int i = 0; i < wordCount; i++) {
            int index = random.nextInt(WORDS.length);
            text.append(WORDS[index]);
            if (i < wordCount - 1) {
                text.append(" ");
            }
        }

        return text.toString();
    }

    // Method to calculate accuracy
    public static int calculateAccuracy(String original, String typed) {
        int matches = 0;
        int length = Math.min(original.length(), typed.length());

        for (int i = 0; i < length; i++) {
            if (original.charAt(i) == typed.charAt(i)) {
                matches++;
            }
        }

        return (int) ((double) matches / original.length() * 100);
    }

    // Method to start a countdown
    public static void startCountdown(int seconds) {
        try {
            for (int i = seconds; i > 0; i--) {
                System.out.println(i + "...");
                Thread.sleep(1000);
            }
            System.out.println("Start typing now!");
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
            System.out.println("Countdown was interrupted.");
        }
    }

    // Method to highlight the text
    public static void highlightText(String text) {
        int length = text.length();
        String border = "*".repeat(length + 4);
        
        System.out.println(border);
        System.out.println("* " + text + " *");
        System.out.println(border);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.print("Enter the number of words to generate (or '0' to exit): ");
            int wordCount = scanner.nextInt();
            scanner.nextLine(); // Consume newline left-over

            if (wordCount == 0) {
                break;
            }

            String randomText = generateRandomText(wordCount);
            System.out.println("Random text:");
            highlightText(randomText);

            System.out.println("Get ready to type the text. Countdown starting...");
            startCountdown(5);

            long startTime = System.nanoTime();
            System.out.print("Type the above text: ");
            String userTypedText = scanner.nextLine();
            long endTime = System.nanoTime();

            int accuracy = calculateAccuracy(randomText, userTypedText);
            long timeTaken = (endTime - startTime) / 1_000_000; // Convert to milliseconds

            System.out.println("Your accuracy: " + accuracy + "%");
            System.out.println("Time taken: " + timeTaken + " ms");
        }

        scanner.close();
    }
}
