# EXPERIMENT 11 – IMPLEMENTATION OF THE HUFFMAN CODING ALGORITHM
## Name : Raha Priya Dharshini M
## Reg No.: 212224240124


## Aim
To implement the Huffman Coding algorithm in Python to generate variable-length binary codes for characters based on their frequency of occurrence.

## Software Requirements
- Python
- Jupyter Notebook

## Procedure

1. Get the input string.
2. Calculate the frequency of occurrence of each character in the input string using a dictionary.
3. Create tree nodes containing each character and its corresponding frequency.
4. Sort the nodes based on their frequencies.
5. Select the two nodes with the smallest frequencies and combine them to create a new node.
6. Repeat the process until a single Huffman tree is formed.
7. Generate binary Huffman codes by traversing the tree recursively:
   - Assign `0` to the left branch.
   - Assign `1` to the right branch.
8. Display each character along with its generated Huffman code.

## Code
```

# Step 1: Get the input string
input_string = "Raha Priya Dharshini"

# Step 2: Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Step 4: Build the Huffman tree
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Step 6: Print characters and Huffman codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {repr(char)}    |    {code}")
```

## Input String
`Raha Priya Dharshini`

## Output

### Huffman Codes
The program displays each character and its corresponding Huffman binary code based on its frequency in the input string.

<img width="390" height="285" alt="image" src="https://github.com/user-attachments/assets/74fc0a23-4345-4adf-b94f-820a036d24e9" />


## Result
Thus, the Huffman Coding algorithm was successfully implemented in Python to generate variable-length binary codes based on character frequencies.
