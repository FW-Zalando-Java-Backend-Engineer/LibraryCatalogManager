## 🌳 Binary Tree Structure – Organizing Genres

In our `LibraryCatalogManager`, genres are organized using a **Binary Search Tree (BST)**. This structure allows efficient insertion, deletion, and lookup operations.

**Visual Representation:**

```
        Fiction
       /       \
   Fantasy     History
              /       \
        Biography    Science
```

*Each node represents a genre. The left child contains genres that are lexicographically less than the parent, and the right child contains genres that are greater.*

![image](https://github.com/user-attachments/assets/ab2d5d14-ede1-452a-b553-79384cb393e4)

Here is the visual representation of the Binary Search Tree for organizing genres:

📘 Fiction is the root

Left child: Fantasy

Right child: History, which branches into Biography and Science

---

## 🗂️ TreeMap Structure – Organizing Authors and Books

Within each genre node, we use a **TreeMap** to store authors and their corresponding books. TreeMap maintains the keys (authors) in sorted order, which facilitates quick retrieval and ordered traversal.

**Visual Representation:**

```
Genre: Science
----------------
| Author        | Books                 |
|---------------|-----------------------|
| Carl Sagan    | Cosmos                |
| Stephen Hawking | A Brief History of Time |
```

*The TreeMap ensures that authors are sorted alphabetically, and each author maps to a list of their books.*

![image](https://github.com/user-attachments/assets/c3ef789e-79fe-4fcb-b0c3-2283bd36600a)

Here is the TreeMap visualization for the Science genre:

The TreeMap stores authors as keys (automatically sorted alphabetically).

Each author maps to a list of books.

You can see how:

📘 Carl Sagan → Cosmos

📘 Stephen Hawking → A Brief History of Time

---

## 🔄 Combined Structure – Library Catalog Overview

Combining both structures, the library catalog can be visualized as follows:

```
Binary Search Tree of Genres:
        Fiction
       /       \
   Fantasy     History
              /       \
        Biography    Science

Each Genre Node Contains:
TreeMap of Authors -> List of Books
```

*This hierarchical structure allows efficient organization and retrieval of books by genre and author.*


![image](https://github.com/user-attachments/assets/70aa625d-950c-4a2e-a5b8-9fb8e65248be)

Here is the TreeMap structure for the 'Science' genre:

Science (Genre) is the root node.

Authors (Carl Sagan and Stephen Hawking) branch off, sorted alphabetically.

Each author points to their book(s).

This visual demonstrates how TreeMap maintains order and groups data logically for easy retrieval and display.


![image](https://github.com/user-attachments/assets/a1650a84-c0ea-46d7-934b-10225601b212)

Here is the combined visual diagram showing:

🌳 A Binary Search Tree (BST) of genres:

Fiction as the root

Fantasy, History, Biography, and Science as descendants

📂 Under Science, a TreeMap:

Sorted authors: Carl Sagan and Stephen Hawking

Each author linked to their books: Cosmos and A Brief History of Time

---

## 🧠 Why Use These Structures?

* **Binary Search Tree (BST):** Efficiently organizes genres, allowing for quick insertion and lookup operations based on genre names.

* **TreeMap:** Maintains a sorted order of authors within each genre, facilitating ordered traversal and efficient retrieval of books by author.

By combining BST and TreeMap, the `LibraryCatalogManager` provides an organized and efficient way to manage a library's catalog, ensuring quick access and maintainability.


