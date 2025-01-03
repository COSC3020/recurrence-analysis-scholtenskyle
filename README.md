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

When n > 1, $$3T(n/3) + n^5$$ is true.

$$3T(n/3) + n^5$$

$$=3 * 3T(n/(3*3)) + 3(n/3)^5 + n^5$$

$$=3 * 3 * 3T(n/(3 * 3 * 3)) + 3 * 3 * (n/(3 * 3))^5 + 3(n/3)^5 + n^5$$

$$=3 * 3 * 3T(n/(3 * 3 * 3)) + (3 * 3n^5)/((3 * 3)^5) + (3n^5)/(3^5) + n^5$$

$$=3 * 3 * 3T(n/(3 * 3 * 3)) + ((3 * 3)/((3 * 3)^5) + 3/(3^5) + 1) * n^5$$

$$3^i * T(n/(3^i)) + (\sum_{k=0}^{i-1} ((3^k)/(3^{5k})))*n^5$$

Plugging in 1 for i, we get $$3T(n/3) + n^5$$

Next we substitute i with logn

$$3^{logn} * T(n/(3^{logn})) + (\sum_{k=0}^{logn-1} ((3^k)/(3^{5k})))*n^5$$

And knowing that $$\sum_{k=0}^{logn} 1 = logn$$, we can actually remove the summation and it becomes the following:

$$nT(1) + n^5 * ((3^{logn - 1}/(3^{5(logn-1)}) + 1)$$

$$nT(1) + n^5 * ((3^{logn - 1}/(3^{5(logn-1)})) + n^5$$

$$((3^{logn - 1}/(3^{5(logn-1)})) * n^5$$, except it will always be smaller than $$n^5$$, so the final answer is $$n^5 ∈ O(n^5)$$

https://www.geeksforgeeks.org/how-to-analyse-complexity-of-recurrence-relation/ - This helped me to understand things like the master method for the final analysis.

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
