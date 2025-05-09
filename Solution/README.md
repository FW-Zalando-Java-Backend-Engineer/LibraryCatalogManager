# ✅ Complete Solution: `LibraryCatalogManager`

---

## 📦 File Structure

```
LibraryCatalogManager/
├── LibraryCatalogManager.java
├── Main.java
└── (Optional) LibraryCatalogManagerTest.java
```

---

## 📄 `LibraryCatalogManager.java`

```java
package com.library;

import java.util.*;

/**
 * A class that manages a library catalog using:
 * - A Binary Tree to store genres
 * - A TreeMap to sort authors and store their books in each genre
 */
public class LibraryCatalogManager {

    /**
     * A node representing a Genre in the Binary Tree.
     */
    static class GenreNode {
        String genreName;
        GenreNode left;
        GenreNode right;

        // TreeMap keeps authors sorted; value is list of books for each author
        TreeMap<String, List<String>> booksByAuthor;

        public GenreNode(String genreName) {
            this.genreName = genreName;
            this.booksByAuthor = new TreeMap<>();
        }

        /**
         * Adds a book under a specific author in this genre.
         *
         * @param author the author's name
         * @param bookTitle the title of the book
         */
        public void addBook(String author, String bookTitle) {
            booksByAuthor.putIfAbsent(author, new ArrayList<>());
            booksByAuthor.get(author).add(bookTitle);
        }

        /**
         * Lists all books grouped by author (TreeMap keeps authors sorted).
         */
        public void listBooks() {
            System.out.println("\n📚 Genre: " + genreName);
            if (booksByAuthor.isEmpty()) {
                System.out.println("  (No books yet)");
            }
            for (Map.Entry<String, List<String>> entry : booksByAuthor.entrySet()) {
                System.out.println("  Author: " + entry.getKey());
                for (String book : entry.getValue()) {
                    System.out.println("    - " + book);
                }
            }
        }
    }

    private GenreNode root;

    /**
     * Adds a genre to the catalog (Binary Tree insert).
     */
    public void addGenre(String genreName) {
        root = insertGenre(root, genreName);
    }

    /**
     * Standard binary search tree insertion (alphabetical order).
     */
    private GenreNode insertGenre(GenreNode node, String genreName) {
        if (node == null) return new GenreNode(genreName);

        if (genreName.compareToIgnoreCase(node.genreName) < 0) {
            node.left = insertGenre(node.left, genreName);
        } else if (genreName.compareToIgnoreCase(node.genreName) > 0) {
            node.right = insertGenre(node.right, genreName);
        }
        // If it's equal, do nothing — genres must be unique
        return node;
    }

    /**
     * Adds a book to a specific genre.
     *
     * @param genre     the genre to add to
     * @param author    the author of the book
     * @param bookTitle the book title
     */
    public void addBook(String genre, String author, String bookTitle) {
        GenreNode genreNode = findGenre(root, genre);
        if (genreNode != null) {
            genreNode.addBook(author, bookTitle);
        } else {
            System.out.println("❌ Genre not found: " + genre);
        }
    }

    /**
     * Searches the Binary Tree for a given genre.
     */
    private GenreNode findGenre(GenreNode node, String genreName) {
        if (node == null) return null;
        if (node.genreName.equalsIgnoreCase(genreName)) return node;

        if (genreName.compareToIgnoreCase(node.genreName) < 0) {
            return findGenre(node.left, genreName);
        } else {
            return findGenre(node.right, genreName);
        }
    }

    /**
     * Lists all books in all genres, sorted by genre (in-order traversal),
     * and sorted by author (TreeMap).
     */
    public void listAllBooks() {
        System.out.println("📖 Library Catalog:");
        inOrderTraversal(root);
    }

    private void inOrderTraversal(GenreNode node) {
        if (node != null) {
            inOrderTraversal(node.left);
            node.listBooks();
            inOrderTraversal(node.right);
        }
    }
}
```

---

## 📄 `Main.java` – Live Demo

```java
package com.library;

/**
 * Demonstrates usage of LibraryCatalogManager with sample genres and books.
 */
public class Main {
    public static void main(String[] args) {
        LibraryCatalogManager catalog = new LibraryCatalogManager();

        // Step 1: Add genres
        catalog.addGenre("Science");
        catalog.addGenre("Fiction");
        catalog.addGenre("History");

        // Step 2: Add books to genres
        catalog.addBook("Fiction", "George Orwell", "1984");
        catalog.addBook("Fiction", "J.K. Rowling", "Harry Potter");
        catalog.addBook("History", "Yuval Harari", "Sapiens");
        catalog.addBook("Science", "Stephen Hawking", "A Brief History of Time");
        catalog.addBook("Science", "Carl Sagan", "Cosmos");

        // Step 3: List all books grouped by genre and author
        catalog.listAllBooks();
    }
}
```

---

## ✅ Sample Output

```text
📖 Library Catalog:

📚 Genre: Fiction
  Author: George Orwell
    - 1984
  Author: J.K. Rowling
    - Harry Potter

📚 Genre: History
  Author: Yuval Harari
    - Sapiens

📚 Genre: Science
  Author: Carl Sagan
    - Cosmos
  Author: Stephen Hawking
    - A Brief History of Time
```

---

## ❓ Why This Structure?

| Component             | Structure          | Why It's Used                                   |
| --------------------- | ------------------ | ----------------------------------------------- |
| Genres                | Binary Tree        | Sorted, fast insert & search (O(log n))         |
| Authors in each genre | TreeMap            | Auto-sorted author names                        |
| Books per author      | List               | Allows duplicates and preserves insertion order |
| Overall Print Order   | In-order + TreeMap | Sorted by genre → sorted by author              |


