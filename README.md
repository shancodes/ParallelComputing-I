HW 1 - Sum Convert
The sequential program is a kind of prefix sum, except that each value in the array is first (expensively) encoded before it is added into the sum and the prefix sums are then (expensively) decoded before putting them back in the original array as the result. The idea is that we are simulating a more complex encoding and decoding function.

Also,  substantially speed up the program by using two threads running at the same time.

First encode all the values in the data array with two threads, then do the accumulation in the main thread, and then use two threads again to decode everything.




HW 2 - Tree Prefix Sum
This is a Ladner-Fischer† parallel prefix sum algorithm using the C++ thread libraryLinks to an external site.. The interior nodes of the tree in the algorithm will be implemented using an array (like a heap). The data array will be in a std::vector<int> typedef'd to be called Data.

Here, The recursive adder pass is parallelized for the top four levels of the tree by forking a thread, using std::async, at each of those levels but done within the same thread for levels below that (total of 16 threads). Similarly, the prefix summation pass is also done in parallel in the same fashion.

The prefix sum algorithm is a two-pass algorithm.

The pair-wise sum pass. This is done during the construction of the SumHeap object and must be done in parallel (using 16 threads as noted above).
SumHeap heap(&data);
The prefix sum pass. This is done within the prefixSums method and must also be done in parallel. The base case of this recursion writes the prefix sum values into the output array.
heap.prefixSums(&prefix);
