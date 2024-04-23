[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/OlW38W4k)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.


## Analysis

if statement -> constant... + 1

else statement ->

-for loops $n * n * n * n * n = n^5$

-recursion $3T(n/3)$ -> 3 recursion calls with n/3 each time

=> $3T(n/3)+n^5$

plug it into itself

=> $3(3T(n/3/3)+(n/3)^5) + n^5$     =>     $9T(n/9)+3(n/3)^5 + n^5$

one more time

=> $27T(n/27) + 9(n/9)^5 + 3(n/3)^5 + n^5$ 

=> $3^iT(n/3^i) + \sum_{j=0}^{i-1} 3^j (n/3^j)^5$ 

because constants can be ignored, we can write $\sum_{j=0}^{i-1} 3^j(n/3^j)^5$ as just $n^5$

let $i = \log_3(n)$

=> $nT(1) + n^5$

=> $n + n^5$

drop the n because it is a lower order

=> $T(n) = O(n^5)$

### sources used
class video on insertion sort

https://www.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/big-o-notation

checked my work against nolan berg's repo to make sure that I was on the right track










