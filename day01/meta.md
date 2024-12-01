Part 1 (17 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSn24s-lRT9ex2Rm1wfZwTklt8InljzomKukopeXnl8D0pOUkphcrWUXH6ihl5hWUloDY0UruRfmlBQqGSjrRSkqxsbE6SmWpRcWZ-XlKVkrGeiZ6hgZKtQDBGNi2hgAAAA)  
```
eṂ⌊ƛh}S?eṂ⌊ƛt}Sȧ∑  
eṂ                 :Split input on new lines and then white space 
  ⌊                :Convert strings to numbers (white space converts to 0)
   ƛh}             :Mapping lambda function to get head of each line
      S            :Sort Ascending
       ?           :Re-read input to stack
        eṂ⌊ƛt}S    :Same as above but with the last number of each line
               ȧ   :Absolute difference (vectorised function - zips both lists and maps)
                ∑  :Sums
```
Part 2 (26 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSn24s-nY7JJHPV21yrZJ9hBuBoh7bLaySpKCc97h6bWPOiYq6Sil5eeXwHSn5SSmFytZRcfqKGXmFZSWgNjRSu5F-aUFCoZKOtFKSrGxsTpKZalFxZn5eUpWSsZ6JnqGBkq1APHnEsuQAAAA)  
```
eṂƛt⌊}#=b?eṂƛh⌊}ƛ#$b Cn×}∑
eṂƛt⌊}                      :List of last number on each line (see above)
      #=b                   :Assign to variable "b"
         ?eṂƛh⌊}            :List of first number on each line (see above) to stack
                ƛ#$b Cn×}   :Open a mapping function on top of stack
                 #$b C      :Count occurrences of the element in "b" and...
                      n×    :...Multiply by element value
                         ∑  :Sums
```