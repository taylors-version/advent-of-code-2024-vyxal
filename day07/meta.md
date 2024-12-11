Part 1 (65 bytes)
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSn24s-lRT5fVsdkPdyw-t9uoxsfQNjq3JM82ojYjt8Qu2iCi1ujIBqu8AMPMcwvKC9JyS1QqVEC8Rx0TodxHHStqj0yrTTs87-HuLpB4hpKOUlp-fgnMqrScxPRiJavoWB2lzLyC0hIQO1rJvSi_tEDBUEknWkkpNjZWR6kstag4Mz9PyUrJWM9Ez9BAqRYAFBCRQ70AAAA) Note: Need to turn off timeouts
```
eṂ⌊:ƛḣλ2|L1=[mtn=X}hmt>[0X}2İ:nP1iΠwpfmt$x$nP1i∑wpfmt$x∨}Ė}fÞỊi∑h
eṂ⌊:                                                              :Split input by lines, spaces, convert to numbers and duplicate on the stack
    ƛ                                                     }       :Map each line to boolean result of whether you can reach the goal
     ḣ                                                            :Push the head onto the stack, then push the rest of the list
      λ2|                                               }Ė        :Execute a function which takes 2 inputs
         L1=[     }                                               :If length of numbers = 1 then
             mtn=X                                                :Compare the goal with the list element and return
                   hmt>[  }                                       :If first element of the list > goal then
                        0X                                        :Return 0 (falsey)
                           2İ:                                    :List without first 2 elements, duplicate on the stack
                              nP1i                                :Get 2nd prefix of list (first 2 elements, shortest byte of doing this - but inefficient)
                                  Π                               :Multiply together
                                   wpf                            :Wrap in a list, prepend to shortened list and flatten
                                      mt$                         :Get the goal and place under the new list on the stack
                                         x                        :Recursive call this function
                                          $nP1i∑wpfmt$x           :Do the same thing as above but this time Add instead of multiply
                                                       ∨          :OR the result
                                                           f      :Flatten the result
                                                            ÞỊ    :Get the indices of truthy elements
                                                              i   :Get the lines which are truthy
                                                               ∑h :Sum down the columns and return the first value (goal sum)
```
Part 2 (81 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSn24s-lRT5fVsdkPdyw-t9uoxsfQNjq3JM82ojYjt8Qu2iCi1ujIBqu8AMPMcwvKC9JyS1QqVMDcRx0TYXwQV98LynvUseJRx4raI9Nq0w7Pe7i7C6QwQ0lHKS0_vwRmeVpOYnqxklV0rI5SZl5BaQmIHa3kXpRfWqBgqKQTraQUGxuro1SWWlScmZ-nZKVkrGeiZ2igVAsAFNK9I88AAAA) Note: Need to turn off timeouts
```
eṂ⌊:ƛḣλ2|L1=[mtn=X}hmt>[0X}2İ:nP1iΠwpfmt$x$:nP1i∑wpfmt$x$nP1i/Jwpfmt$x∨∨}Ė}fÞỊi∑h
eṂ⌊:ƛḣλ2|L1=[mtn=X}hmt>[0X}2İ:nP1iΠwpfmt$x$:nP1i∑wpfmt$x               ∨}Ė}fÞỊi∑h :Same as part 1
                                                        $nP1i/Jwpfmt$x            :Combine the 2 numbers together instead of Add or Multiply
                                                                      v           :OR this with other 2 results

```