Part 1 (101 bytes)
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSlXXObzh4dbZRQ93Nj3q6To2O88o81FT6-HpeRnahgaGqnnGUK5hprahgbGqda3VuZV5GaYGNjV5JaaGNrU-KigCdggBO7gAMt-m1ufwdBBU0lFKy88vgbknLScxvVjJKjpWRykzr6C0BMSOVnIvyi8tUDBU0olWUoqNjdVRKkstKs7Mz1OyUjLWM9EzNFCqBQCFEPHE4gAAAA)
I'm sure this could be done shorter, perhaps with Group By
```
e',ðᵛrṂ⌊ƛn2i₅×nh+101%n3i₅×n1i+103%;}:Ωnh50<|nt51<}L$:Ωnh50<|nt51>}L$:Ωnh50>|nt51>}L$Ωnh50>|nt51<}L×××
e                                                                                                     :Split input by lines
 ',ð                                                                                                  :Push a comma and then space onto the stack
    ᵛr                                                                                                :vectorise (run over each line), replace "," with " "
      Ṃ                                                                                               :Split each line by spaces
       ⌊                                                                                              :Convert to numbers (non-numbers are ignored)
        ƛ                          }                                                                  :Map each line
         n2i                                                                                          :Third number on the line
            ₅                                                                                         :Number 100
             ×                                                                                        :Multiply together
              nh+                                                                                     :Add the first number
                 101%                                                                                 :Module 101
                     n3i₅×n1i+103%                                                                    :Do the same with 3rd and second numbers and mod 103
                                  ;                                                                   :Pair the two results
                                    :                                                                 :Duplicate this on the stack
                                     Ω           }L                                                   :Filter and count results
                                      nh50<|nt51<                                                     :First value < 50 and 2nd <51
                                                   $:Ωnh50<|nt51>}L$:Ωnh50>|nt51>}L$Ωnh50>|nt51<}L    :Stack manipulation, but do the same with each quadrant
                                                                                                  ××× :Multiply all 4 together
```
Part 2 (66 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSMji02D5VXefwhodbZxc93Nn0qKer2urY7LyMPMNM69pSH_tUn0edC2oebtn_as7cY7OVo_My8owytQ0NDFVr8gwz80q0DQ2MVWvyjDJr8kqUY2trDy1V0lFKy88vgVmUlpOYXqxkFR2ro5SZV1BaAmWXpRYVZ-bnKVkpGeuZ6BkaKNUCAGX-khKrAAAA): Note turn off timeouts
```
0£?e',ðᵛrṂ⌊{:ƛnhn1i;}uL?eL≠|ᴿꜝƛ#[nhn2i+101%|n1int+103%|n2i|nt#]}}¥
0£                                                                 :Store 0 to the register
  ?e',ðᵛrṂ⌊                                                        :Turn each line into 4 numbers as per above
           {               |                                    }  :While{is_true|do}
            :ƛ      }                                              :Duplicate top of stack and map over it
              nhn1i;                                               :Put first two numbers into a pair
                     u                                             :Remove duplicates from list of pairs
                      L                                            :Get length
                       ?eL                                         :Get number of lines of input
                          ≠                                        :Check if not equal
                            ᴿꜝ                                     :Increment the register
                              ƛ                                }   :Map over top of stack
                               #[          |          |   |  #]    :List of 4 elements
                                 nhn2i+101%                        :Add 1st and 3rd numbers, modulo 101
                                            n1int+103%             :Add 2nd and 4th number, modulo 103
                                                       n2i         :3rd number
                                                           nt      :4th number
                                                                 ¥ :Print the register
```