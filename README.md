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

$$ = 3^2 *(T(n/9) + 3 * (n^5/(3^5)) +n^5$$

We can plug in n/9 for when the size becomes that.

$$ T(n) = 3^3(T(n/27)+ 3^2 * (n^5 / 3^5) +3(n^5 / 3^5) + n^5 $$

$$= T(n/n) + n^5$$

$$= T(1) + n^5$$

And since T(1) = 1:

$$n^5$$

$$O(n^5)$$

So the final answer would be:

$$n+n^5∈O(n^5)$$

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
