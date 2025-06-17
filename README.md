# File-Zipper
# Huffman File Compressor

A C++ project that implements **Huffman Coding**, a lossless data compression algorithm. This tool can **compress** and **decompress** any text file using efficient binary encoding based on character frequency.

## Features

- Compress any `.txt` file using Huffman coding.
- Decompress `.huf` files back to original text.
- Lossless and efficient compression.
- Custom implementation using min-heap and binary trees.

---

## About Huffman Coding

Huffman Coding is a greedy algorithm used for lossless data compression. It assigns **shorter binary codes to more frequent characters** and **longer codes to less frequent ones**, resulting in efficient file size reduction.




## Compression Workflow (`compress()`)

1. **`createMinHeap()`**
   - Reads input file and counts frequency of all ASCII characters.
   - Builds a min-heap using a priority queue.

2. **`createTree()`**
   - Constructs the Huffman tree by combining nodes with the lowest frequencies iteratively.

3. **`createCodes()`**
   - Assigns Huffman binary codes to characters via tree traversal.

4. **`saveEncodedFile()`**
   - Writes a `.huf` file containing:
     - The Huffman tree (metadata).
     - Encoded binary data (as 8-bit chunks).
     - Padding info (to align last byte).


## Decompression Workflow (`decompress()`)

1. **`getTree()`**
   - Reads and rebuilds the Huffman tree from the `.huf` file metadata.

2. **`saveDecodedFile()`**
   - Converts the binary-encoded data back into text using the reconstructed tree.
   - Ignores padding bits added during compression.


## How to Compile & Run

### Compile:
g++ -std=c++11 -o huffman huffman.cpp

# To compress a file
./huffman encode inputFile.txt output.huf

# To decompress a file
./huffman decode output.huf recovered.txt


