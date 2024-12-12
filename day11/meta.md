Part 1 (32 bytes)
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSeriz6VFPl5GpxrHZytV5BrY1hhE1Pqk1D7dtOrT3UU9XRK2RgZHJ4em1abU-SjpKafn5JTAD0nIS04uVrKJjdZQy8wpKS6DsstSi4sz8PCUrJWM9Ez1DA6VaABCBI5GDAAAA) Note: Need to turn off timeouts
```
Ṃ⌊25(ƛ#{n0=|1X|Le|ᶲ½⌊X}2024×}f}L
Ṃ⌊                               :Split input by spaces and convert to numbers
  25(                         }  :Do 25 times
                               L :Get length of result
     ƛ                      }f   :Map over values in list
      #{   |  |  |    }          :{if|then|elseif|then}
        n0= 1X                   :value == 0 return 1
               Le                :If length is even
                  ᶲ½⌊X           :Split in half and return
                       2024x     :Multiply by 2024
```
Part 2 (95 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSUo5Wjj20-NzukkNrog0jag8tfdSwLO_hjnlWBo86l0YfWqqSGVGrXJ2XcWhNjWFeSZl1RU1ehk9qTV7Gw22bDu191NNllQEWVikBU9o1eRlGBkYmh6eDubVWh5YWHFpcq2z7cGfTo56uY7PNTa2VVY5Mq33UMVFJRyktP78E5qC0nMT0YiWr6Fgdpcy8gtISEDtayb0ov7RAwVBJJzo2NlZHqSy1qDgzP0_JSslYz0TP0ECpFgAtCm-S4QAAAA) Note: Need to run locally and will take hours to run!
```
#[#]£λt¬[1X}¥…nḞ:0≥[¥$iX}#{nh¬|1ntv;x|nhLe|nhᶲ½⌊:hntv;x$tntv;x+|nh2024×ntv;x}:¥p£}#=Ṃ⌊ƛ75;#$Ė}∑
#[#]£                                                                                           :Store an empty list to the register - This is our cache [[stone,steps],result]
     λ                                                                           }#=            :Recursive lambda with empty name
                                                                                    Ṃ⌊          :Split input by spaces and convert to numbers
                                                                                      ƛ      }∑ :Map over each input and sum the result
                                                                                       75;#$Ė   :Pair the input number with 75 and provide as input large lambda
      t¬[1X}                                                                                    :If second number(steps) = 0, return 1
            ¥…nḞ:                                                                               :Search for input in cache head, return index (-1 if not found) and duplicate on stack
                 0≥[    }                                                                       :If index ≥0 (found in cache) then
                    ¥$iX                                                                        :Return value in cache
                         #{   |      |    |                    |            }                   :{if|then|elseif|then|else}
                           nh¬                                                                  :Head is falsey (e.g. 0)
                               1ntv;x                                                           :Pair 1 with the steps value-- and recursively call
                                      nhLe                                                      :Length of stone value is even
                                           nhᶲ½⌊:                                               :stringyfy, split into halves and convert to numbers, duplicate this pair on the stack
                                                 hntv;x                                         :First of the 2, pair with steps-- and recursively call
                                                       $tntv;x                                  :Second of the 2, do the same as above
                                                              +                                 :Add result of the 2 calls
                                                                nh2024×                         :Multiply stone value by 2024
                                                                       ntv;x                    :Pair with steps-- and recursively call
                                                                             :¥p£               :duplicate result on stack, prepend to the register
```