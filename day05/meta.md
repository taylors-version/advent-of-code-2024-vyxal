Both parts (72 bytes)
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAEzXOMQrCMBhA4bv8lEohaKVO6RW8QXEompiCJtJGHdRBQVDp4mpABHF3UexQhyi9R3ISEXR7wze8GVCRDmMJOEDASNwjKWAABF3RI4BBF6SGzE1lNt9VSp_t8kp0afOdfZzY-1Qpxqbc3JR0F5Vi-tKNuNQXu3xyNnXndrX1Gm3zuJvi8EUU89fRFGuXYm5XuYPbukycyA_nvhN6drMHBFQI-Z-gg7ifAY46CBI-GstfT0iaJYIDhqDeqjd9WHwAFEOWJccAAAA)
```
¹e',ᵛs⌊ƛ£⁰e½⌊⸠hĠƛhhwnᵛt&}ƛh¥c[nt¥⁾nhw&|₉)/LḶṚᵛtf:nÞṅ&f:n₌$:L½i$[0;|0$;)∑
¹e                                                                       :Split 2nd input (page lists) by lines
  ',ᵛs⌊                                                                  :Split each line by commas and convert to numbers
       ƛ                                                              )  :for each line which calculate middle value of sorted and unsorted lines
        £                                                                :Store the line to the register
         ⁰e                                                              :Split the first input by lines
           ½⌊                                                            :Split in half and convert to numbers (the |s are dropped)
             ⸠h                                                          :Create a function which takes the 1st element of a list
               Ġ                                                         :Group rules by the LHS (previous function)
                ƛ       }                                                :Map over each group of rules to produce [LHS,[RHS0,RHS1,...]] - ruleset
                 hhw                                                     :Get LHS (via head) and wrap in a list
                    nᵛt&                                                 :Get all RHS (via tail) and append to LHS
                         ƛ              )                                :For each ruleset take only the RHSs that are in the current page list
                          h¥c[        | )                                :If LHS is in the page list get RHSs in page list else an empty string
                          h                                              :LHS of ruleset
                           ¥                                             :Read from the register
                            c                                            :Check if contains
                             [        | )                                :if else block <condition>[<if true>|else}
                              nt                                         :All RHSs of ruleset
                                ¥                                        :Current page list
                                 ⁾                                       :Intersection of two lists
                                  nhw&                                   :Get LHS, wrap it and append ([[RHS0,RHS2,RHS5],LHS])
                                       ₉                                 :Empty string
                                         /L                              :Filter out the empty strings (via length)
                                           ḶṚ                            :Sort lists by length and reverse (so most RHSs first)
                                             ᵛtf                         :Extract the LHS and flatten list
                                                :                        :Duplicate this on the stack
                                                 n                       :Push the page list back on the stack
                                                  Þṅ                     :Calculate the multiset difference between the two (find page numbers with now RHS)
                                                    &f:                  :Concatenate this, flatten the list (this is now the sorted page list) and duplicate
                                                       n₌                :Compare this with the original list
                                                         $:              :Swap to have sorted list on top of the stack and duplicate it
                                                           L½            :Get the length of the sorted list and half it
                                                             i           :Get element at the 1/2 position
                                                              $          :Swap so boolean from list compare is at top of the stack
                                                               [  |   )  :If [true|else}
                                                                0;       :[<middle>,0]
                                                                   0$;   :[0,<middle]
                                                                       ∑ :Sum up the pairs
```