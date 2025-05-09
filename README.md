# 📝 Exercise: `LibraryCatalogManager`

## 🎯 Problem Statement

You are building a **Library Catalog System** where:

* Each **genre** (e.g., Fiction, History, Science) is stored in a **Binary Tree**.
* Each genre node contains books sorted by **author name** using a **TreeMap**.
* You must support adding genres, adding books to a genre, and printing all books in alphabetical order by genre and then by author.

---

## 🧠 Skills Practiced

* Binary Tree insertion and traversal
* TreeMap usage for sorted key-value management
* Recursion for traversing hierarchical structures
* Combining custom structures with Java Collections

---

## 🚀 Your Task

Create a class called `LibraryCatalogManager` that can do the following:

1. Add a new genre to the catalog
2. Add a new book under a genre and author
3. List all books grouped by genre and sorted by author within each genre

---

## 🧩 Algorithm Design – Step-by-Step

You are NOT to write the code immediately. Instead, **follow this structured pseudocode plan with reasoning**.

---

### 1. 📂 Define `GenreNode`

#### Purpose:

To represent each **genre** (e.g., Fiction, History) as a **binary tree node**.

#### Fields:

* `String genreName`
* `GenreNode left`
* `GenreNode right`
* `TreeMap<String, List<String>> booksByAuthor`
  (*Key = Author name, Value = list of book titles*)

```java
/**
 * Each GenreNode represents a genre section in the library.
 * It holds books organized by authors using a TreeMap.
 */
```

---

### 2. 🏗️ Insert Genre in Binary Tree

#### Algorithm:

1. Start at the root.
2. If `genreName` is alphabetically before current node, go left.
3. If it's after, go right.
4. If node is null, insert it here.

```java
/**
 * This maintains the genres in alphabetical order.
 * We use standard Binary Search Tree insertion logic.
 */
```

#### ❓ Why a Binary Tree?

Because genre names are unique and ordered, BST is ideal for fast lookup and insertion — `O(log n)` on average if balanced.

---

### 3. 📚 Add Book to a Genre

#### Steps:

1. Search the tree for the genre node.
2. If found:

   * Use `booksByAuthor.putIfAbsent(author, new ArrayList<>())`
   * Add the book to the author's list

```java
/**
 * Adding a book involves:
 * - Finding the correct genre node (BST search)
 * - Adding the book to the author's list (TreeMap auto-sorts authors)
 */
```

#### ❓ Why TreeMap?

Because TreeMap automatically maintains keys (authors) in sorted order. This makes listing books under a genre easy and clean.

---

### 4. 📃 List All Books

#### Goal:

Print all books grouped by genre and author in order:

* Alphabetically by genre (in-order traversal)
* Within each genre, authors sorted (TreeMap)
* For each author, list all books

#### Traversal Algorithm:

```java
/**
 * Use in-order traversal for the genre binary tree:
 * 1. Traverse left subtree
 * 2. Print current genre and its books (from TreeMap)
 * 3. Traverse right subtree
 */
```

---

## ✍️ Sample Output (based on the algorithm)

If we inserted:

```text
Genres: Science, History, Fiction

Fiction:
  J.K. Rowling → Harry Potter
  George Orwell → 1984

History:
  Yuval Harari → Sapiens

Science:
  Stephen Hawking → A Brief History of Time
```

The output should be:

```text
📚 Fiction
  George Orwell: 1984
  J.K. Rowling: Harry Potter

📚 History
  Yuval Harari: Sapiens

📚 Science
  Stephen Hawking: A Brief History of Time
```

---

## 🧠 Summary

| Feature         | Structure    | Why?                                |
| --------------- | ------------ | ----------------------------------- |
| Genre Structure | Binary Tree  | Efficient insertion/search by genre |
| Books in Genre  | TreeMap      | Automatically sorted authors        |
| Book Titles     | List<String> | Allows multiple books per author    |

---

## ✅ Submission Checklist

| Requirement                   | Status |
| ----------------------------- | ------ |
| `GenreNode` class implemented | ☐      |
| Binary Tree insertion works   | ☐      |
| TreeMap for authors used      | ☐      |
| Recursive listing implemented | ☐      |
| JUnit tests (optional)        | ☐      |
| Code includes JavaDocs        | ☐      |


