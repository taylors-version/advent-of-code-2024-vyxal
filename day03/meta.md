Part 1 (25 bytes)
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAEzXLOwrCQBRG4a3I36h4CYZYzQZcxNwpBjOjgSQ3zEMQSS9iY23jaixdRFYiKWwOX3Ou8BI6m6AqwsnZ2gUogHCQ2kGB0eWWecVcb2gO85px-byWFKfH_fsep9sTBC-S_qtv7TFCaUNo-iGn2Rr7IHlYlCANGGMIZxdiIz0UqmJXlFuMP_RvDZeNAAAA)
```
"mul\(\d+,\d+\)"yƛ',s⌊Π}∑
"mul\(\d+,\d+\)"          :RegEx string
                y         :Find all matches in input
                 ƛ     }  :Map via a lamda
                  ',      :Single character string ","
                    s     :Split my preceding sting e.g. "mul(2","14)"
                     ⌊    :Extract numbers
                      Π   :Product
                        ∑ :Sum the results

```
Part 2 (58 bytes)  
[Vyxal It Online!](https://vyxal.github.io/latest.html#H4sIAAAAAAAAE6tWSssvyk0sUbIy1lHKSE1MSS1SslJS0lFKzk9JVbJSilF61NTm4_6oqUHt4bZVj5p6zu1-tGPBo6bW4IdbthQ_atz1qKkl_NWcuaWPmjoebtn_qHFfllGdy5FpD7ctedSw6OHWaY8a5j5q6ny4a0GMUm5pTkyMRkxMirYOiIiJ0YxRqjw2W12n-FFP17kFtY86JirpKKXl55fAHJGWk5herGQVHaujlJlXUFoCYkcruRfllxYoGCrpRCspxcbG6iiVpRYVZ-bnKVkpGeuZ6BkaKNUCAOBYFaXXAAAA)
```
"₆LG₀&ᶪ₌λ⸠₅Sᴴs⁺₄Wꜝu₈ᴿ⁾j2~DĖᶤ•ᵖ”₉Ạ"mul\(\d+,\d+\)"yƛ',s⌊Π}∑
"₆LG₀&ᶪ₌λ⸠₅Sᴴs⁺₄Wꜝu₈ᴿ⁾j2~DĖᶤ•ᵖ”                            :The regex string "(don't\(\))(.|\n)+?((do\(\))|$)" Compressed
                               ₉                           :The empty string
                                Ạ                          :Replace all regex matches with the empty string
                                 "mul\(\d+,\d+\)"yƛ',s⌊Π}∑ :Part 1 on the resultant string
                                                               
```