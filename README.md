# Implementation-of-the-Huffman-Coding-algorithm
## NAME: SHARVESHWARAN M
## REG.NO: 212224240150
# Aim 
To write and execute a Python program to implement the Huffman Coding algorithm for data compression and display the generated binary codes for each character in an input string.
# Algorithm
1. Calculate Frequencies: Traversal of the input string to count the occurrence frequency of each unique character.

2. Initialize Leaf Nodes: Create a list of nodes where each node contains a character and its corresponding frequency.

3. Build Huffman Tree:
* Sort the list of nodes in ascending order based on frequency.

* Extract the two nodes with the lowest frequencies (left and right children).

* Combine them into a new internal node with a frequency equal to the sum of the two nodes.

* Append the new node back into the list.

* Repeat the process until only one node (the root of the Huffman tree) remains.

4. Generate Huffman Codes: Recursively traverse the Huffman tree starting from the root. Assign '0' for left branches and '1' for right branches until reaching leaf nodes, recording the binary sequence for each character.

5. Display Output: Print each unique character alongside its computed Huffman code.
# Program
```
# Implementation of the Huffman Coding algorithm

# Step 1: Input string
input_string = "Sharveshwaran M"

# Step 2: Calculate frequency of each character
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create initial leaf nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Step 4: Build the Huffman Tree
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])
    
    # Pick two nodes with the smallest frequencies
    left = nodes.pop(0)
    right = nodes.pop(0)
    
    # Create a new internal node combining the two smallest nodes
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final remaining node is the root of the Huffman tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman codes by traversing the tree
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # Leaf node reached
        huffman_codes[tree[0]] = code
    else:  # Internal node recursion
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Step 6: Print characters and their generated Huffman codes
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

# Output
<img width="1017" height="1070" alt="image" src="https://github.com/user-attachments/assets/73a3a256-adcc-44f5-bc01-c7e8ff3cb0a7" />

# Result
Thus the huffman coding was implemented to compress the data using python programming.
