The sequential program is a kind of prefix sum, except that each value in the array is first (expensively) encoded before it is added into the sum and the prefix sums are then (expensively) decoded before putting them back in the original array as the result. The idea is that we are simulating a more complex encoding and decoding function.

You should be able to substantially speed up the program (can you get a factor of 2?) by using two threads running at the same time.

Here's a hint: First encode all the values in the data array with two threads, then do the accumulation in the main thread, and then use two threads again to decode everything.
