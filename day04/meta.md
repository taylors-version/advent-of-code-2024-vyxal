Part 1 (62 bytes)
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSsk-1OrT42OzcIxtqQx41zPE6tPTY7Ny8czMe7pyFEHi4cxaagoc7Z6GoAVPHZscoRfg6BscoPdza7qzycOesPBVn7dpHHROVdJTS8vNLYHan5SSmFytZRcfqKGXmFZSWgNjRSu5F-aUFCoZKOtFKSrGxsTpKZalFxZn5eUpWSsZ6JnqGBkq1AKDCIMXOAAAA)
```
?e:£ƛmİ}T“J¥ƛmnΘṚ}T“J¥ƛṚmİ}T“J¥ƛmnṚΘṚ}T“J¥T“Jƛ"XMAS"ᵇC$Ṛn$C+}∑
?e:                                                            :Split input by lines and duplicate on stack
   £                                                           :Store this to the register
    ƛ   }                                                      :Map each line
     m                                                         :Get index of line
      İ                                                        :Drop first "m" characters
        T“                                                     :Transpose the collection of strings and stringyfy
           ¥ƛ    }                                             :Read from register and map
             mnΘṚ                                              :Keep the first "m" characters and reverse
                  T“                                           :Transpose the collection of strings and stringyfy
                     ¥ƛṚmİ}T“                                  :Reverse each line on register and drop first "m" characters, transpose and stringyfy
                              ¥ƛmnṚΘṚ}T“                       :Reverse each line on register and drop first "m" characters, transpose and stringyfy
                                         ¥T“                   :Transpose the register and stringyfy
          J         J        J          J   J                  :Join all sets of Strings together
                                             ƛ              }∑ :Map over each string and sum the result
                                              "XMAS"ᵇC         :Count how many times "XMAS" appears and keep it on the stack
                                                      $Ṛ       :Swap top 2 values on the stack (get the "XMAS") and reverse
                                                        n$C    :Count how many times "SAMX" appears
                                                           +   :Add the 2 counts together                                     
```
Part 2 (65 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSSrV6uHPVwx2Ljs1-tGOBuqPtwx3zauN8jHRP7ovSzzg22z718LwT6_NKMvMyMh81zHm4o7n22OyH27b4Bqc83NrurPJw56w8Z-28GKVgX9_gGCUw0zc42BfErH3UMVFJRyktP78EZmlaTmJ6sZJVdKyOUmZeQWkJiB2t5F6UX1qgYKikE62kFBsbq6NUllpUnJmfp2SlZKxnomdooFQLAPWvXsnHAAAA) Note: Need to turn off timeouts
```
e:ṪḢƛ⸠'A=Ḟ}^L2-ɾZ/hƛ?eÞȯntinhi“ḃ}ƛᶴMSdᵇC$ṚnC+n"SMMS"C+n"MSSM"C+}∑
e:                                                                :Split input by lines and duplicate on stack
  ṪḢ                                                              :Remove the first and last line
    ƛ     }                                                       :Map over each remaining line
     ⸠'A=                                                         :Create a lambda function comparing to "A"
         Ḟ                                                        :Return each index where previous lambda is true
           ^                                                      :Retrieve the duplicate input split by lines
            L2-                                                   :Count number of lines and subtract 2
               ɾ                                                  :Range from 1-previous (inclusive)
                Z                                                 :Zip these with the results from the mapping function
                 /h                                               :Remove rows with no "A"s (front element is empty)
                   ƛ            }                                 :Mapping function to get diagonals (in order of BR,TL,BL,TR)
                    ?e                                            :Read input split on lines
                      Þȯ                                          :Create list of list of the neighbours of each element
                        ntinhi                                    :Extract neighbours of our element
                              “ḃ                                  :Get 2nd half (diagonal neighbours)
                                 ƛ                             } :Lambda function to count the cross MAS for each line with "A"
                                  ᶴMS                             :2 character String "MS"
                                     d                            :Double the string (e.g. "MSMS")
                                      ᵇC                          :Count occurances and keep "MSMS" on stack
                                        $Ṛ                        :Get the "MSMS" and reverse it
                                          nC+                     :Count occurances and add to previous count
                                             n"SMMS"C+n"MSSM"C+   :Add on occurances of "SMMS" and "MSSM"
                                                                ∑ :Sum results
```