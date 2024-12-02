Part 1 (48 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSn24s-lRT9e5ledXBj9q6jkyLe9ib_DDnbPA7EcdK_LOryyFspfnndvtY2gbbRhRm5FnmHliubFdtEFE7cMdiypqwfK1Pko6Smn5-SUwO9JyEtOLlayiY3WUMvMKSkug7LLUouLM_DwlKyVjPRM9QwOlWgDzpRxipgAAAA)
```
eṂ⌊ΩϩS₌ĖnэSṚ₌Ė∨nϩu₌Ė∧nλL1=[1X}hn1iȧ3>[0X}Ḣx}Ė∧}L  
eṂ                                               :Split input on new lines and then white space 
  ⌊                                              :Convert strings to numbers (white space converts to 0)
   Ω                                          }L :Apply a filter lambda and count the size of the output
    ϩ  Ė                                         :Create a lambda from the next 2 elements and execute
     S₌                                          :Sort the input and compare to the input
        n                                        :Push the initial filter input onto the stack
         э   Ė                                   :Create a lambda from the next 3 elements and execute
          SṚ₌                                    :Sort the input, reverse it and compare to the input
               nϩ  Ė                             :Push initial filter input onto the stack and execute a 2 element lambda
                 u₌                              :Remove duplicate elements and compare to the input
                     nλ                    }Ė    :Push initial filter input onto the stack and execute a lambda
                       L1=[1X}                   :Compare length of input to 1, if equal return 1 (truthy)
                              h                  :Pop the first element of the input onto the stack
                               1i                :Pop the second element of the input onto the stack
                                 ȧ               :Take the absolute difference
                                  3>             :Compare if greater than 3
                                    [0X}         :If previous statement is true, return 0 (falsey)
                                        Ḣx       :Remove the head from the input and recursive call
              ∨     ∧                        ∧   :Logical OR, AND, AND of the lambda functions
```
Part 2 (62 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSn24s-lRT9ex2YcWn9t5bPahpXmBtedWnl8Z_Kip58i0vIu9wQ93zgKzH3WsyDu_shTKXp53brePoW20YURtRp5h5onlxnbRBhG1D3csqqgFy9f61J5bafCoc0Gtj5KOUlp-fgnM5rScxPRiJavoWB2lzLyC0hIouyy1qDgzP0_JSslYz0TP0ECpFgBQFUGZvAAAAA)
```
eṂ⌊ƛ£ιƛ¥nQ}ΩϩS₌ĖnэSṚ₌Ė∨nϩu₌Ė∧nλL1=[1X}hn1iȧ3>[0X}Ḣx}Ė∧}L}Ω0≠}L
eṂ⌊                                                            :Input to lists of numbers
   ƛ                                                    }      :Map input with a lambda
    £                                                          :Set the Register to the input value
     ι                                                         :Create a Range from 0 to length of input-1
      ƛ   }                                                    :Map the range via a lambda
       ¥nQ                                                     :Read from the register, and remove the ith (from range mapping) element
           Ω                                          }L       :Send each (sub)list to same filter as in Part 1 and count how many pass
                                                         Ω0≠}L :Filter only inputs with non-zero passes and count remaning
                                                               
```