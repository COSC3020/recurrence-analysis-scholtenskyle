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

First of all, this is recursively called 3 times, where n/3 is always the input. We can calculate the amount of loops run as $$n^5$$ (where fisrt loop is $$n^2$$, second loop is n, and the third loop is $$n^2$$ $$(n^2 * n * n^2))$$. This can be simplified into:

$$T(n) = 3T(n/3) + n^5$$

This then can be solved:

$$ = 3(3T(n/9) + (n/3)^5)+ n^5$$

$$ = 9T(n/9) + 3(n/3)^5 + n^5$$

$$ = 3^i *T(n/(3^i)) + \sum_{k=0}^{i-1} * 3^i * (n/(3^i))^5$$
