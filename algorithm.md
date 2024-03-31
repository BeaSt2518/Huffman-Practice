 # The Algorithm for Huffman Encoding

## We need a tree structure

% The Algorithm for Huffman Encoding

function Huffman(code)
    n = length(code);

    % Sort the code symbols based on their frequencies
    for i = 1:n-1
        for j = 1:n-i
            if code{j}.frequency > code{j+1}.frequency
                % Swap the code symbols
                temp = code{j};
                code{j} = code{j+1};
                code{j+1} = temp;
            end
        end
    end

    % Build the Huffman tree
    while n > 1
        % Create a new node
        newNode = struct('left', [], 'right', [], 'frequency', 0);

        % Take the two nodes with the lowest frequencies
        newNode.left = code{1};
        newNode.right = code{2};

        % Update the frequency of the new node
        newNode.frequency = newNode.left.frequency + newNode.right.frequency;

        % Remove the two nodes with the lowest frequencies from the code cell array
        code(1:2) = [];

        % Insert the new node into the code cell array
        code{end+1} = newNode;

        % Sort the code cell array based on the frequencies
        for i = 1:n-1
            for j = 1:n-i
                if code{j}.frequency > code{j+1}.frequency
                    % Swap the code symbols
                    temp = code{j};
                    code{j} = code{j+1};
                    code{j+1} = temp;
                end
            end
        end

        % Decrease the size of the code cell array
        n = n - 1;
    end

    % The root of the Huffman tree is the only node left in the code cell array
    root = code{1};
end

//Write the above code as matlab code
