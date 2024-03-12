 # The Algorithm for Huffman Encoding

## We need a tree structure

Huffman (code) {
    n = size(code)

// Sort the code symbols based on their frequencies
for (int i = 0; i < n - 1; i++) {
    for (int j = 0; j < n - i - 1; j++) {
        if (code[j].frequency > code[j + 1].frequency) {
            // Swap the code symbols
            swap(code[j], code[j + 1]);
        }
    }
}

// Build the Huffman tree
while (n > 1) {
    // Create a new node
    Node* newNode = new Node();

    // Take the two nodes with the lowest frequencies
    newNode->left = code[0];
    newNode->right = code[1];

    // Update the frequency of the new node
    newNode->frequency = newNode->left->frequency + newNode->right->frequency;

    // Remove the two nodes with the lowest frequencies from the code array
    code.erase(code.begin(), code.begin() + 2);

    // Insert the new node into the code array
    code.push_back(newNode);

    // Sort the code array based on the frequencies
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (code[j]->frequency > code[j + 1]->frequency) {
                // Swap the code symbols
                swap(code[j], code[j + 1]);
            }
        }
    }

    // Decrease the size of the code array
    n--;
}

// The root of the Huffman tree is the only node left in the code array
Node* root = code[0];
}