# Word Ladder Building Game & Shortest-Ladder Solver  
**UIC – CS211 Programming Practicum**  
**Author: Shenxing Zhang**

## Overview
This project implements a fully interactive **Word Ladder Game** and a **shortest-path Word Ladder Solver** in C.  
A word ladder connects one word to another by changing one letter at a time, and each intermediate step must be a valid English word.

The program includes:
- A dictionary loading system (dynamic memory)
- A word ladder building game (user-driven)
- A BFS-based solver to find the shortest ladder
- Linked list structures for both ladders and lists of ladders
- Full memory management (no leaks)

---

## How It Works (Step-by-Step Explanation)

### **1. Build the Dictionary**
- User chooses the word length and dictionary file.
- Program scans the dictionary twice:
  1. **Count** all valid-length words  
  2. **Allocate memory** and **load** those words into an array  
- All words are stored as dynamic C-strings in alphabetical order.
- Binary search is used to efficiently locate words.

---

### **2. Gameplay: Building a Word Ladder**
- A ladder starts with the given `startWord`.
- Users enter the next word manually.
- A word is considered **valid** only if:
  1. It has the correct length  
  2. It exists in the dictionary  
  3. It differs by exactly **one** character from the previous word  
- If “DONE” is entered, the user stops the game.
- The ladder is displayed with proper formatting (required spacing).

---

### **3. Displaying Ladders**
#### **Incomplete ladders**
Displayed with three lines of `"...“` on top.

#### **Complete ladders**
Displayed with:
- Words stacked vertically  
- `^` markers showing where letters differ  
- Exact whitespace formatting

---

### **4. Shortest-Ladder Solver (Breadth-First Search)**
This is the core algorithm:

1. Start with a ladder containing only `startWord`.
2. Generate all “neighbor words” by:
   - Modifying each character position A–Z  
   - Checking if the result is a valid dictionary word  
3. Use a **linked list of ladders** to represent BFS levels.
4. Maintain a `usedWord[]` array to avoid cycles and reduce searches.
5. If a ladder reaches `finalWord`:
   - Return the complete ladder  
6. If all possibilities are exhausted:
   - No ladder exists  

This algorithm guarantees the shortest ladder.

---

### **5. Memory Management**
The project handles:
- Dynamic array of C-strings
- Allocations for every WordNode and LadderNode
- Proper freeing of:
  - Ladders no longer needed  
  - Dictionary arrays  
  - Temporary structures used by the solver

Valgrind confirms **no leaks**.

---

## Project Structure
word-ladder/
│
├── main.c
├── makefile
├── README.md
├── demo.mp4 (or YouTube link)
└── dictionary.txt (optional to upload)

