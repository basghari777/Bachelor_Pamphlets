**مثال:**

<p style="direction:ltr; text-align:left">
t(n) = t(n - 1) + n | n > 1 <br/>
t(n) = 1 | n = 1
</p>

حل:

<p style="direction:ltr; text-align:left">
t(n) = t(n - 1) + n <br/>
t(n) = t(n - 2) + (n - 1) + n <br/>
t(n) = t(n - 3) + (n - 2) + (n - 1) + n <br/>
$ \vdots $ <br/>
<br/>
t(2) = t(1) + 2 <br/>
t(1) = 1 <br/>
<br/>
t(n) = 1 + 2 + 3 + $$ \cdots $$ + (n - 1) + n <br/>
t(n) = $$ \sum_{i = 1}^{n} i = \frac{n(n + 1)}{2} \Rightarrow O(n^2) $$ <br/>
</p>

#### تمرین:
##### 1. مرتبه زمانی و مقدار $$ f(5) $$ را بدست آورید.

```
int f(int n){
    if(n <= 0)
        return 2;
    return f(n - 1) + n * f(n - 2);
}
```
<br/>

##### 2. مرتبه زمانی و شمارگام‌های قطعه کد زیر را بدست آورید.

```
for(int i = 0; i < n - 1; i++)
    for(int j = 1; j < m; j++)
        for(int k = 0; k <= n; k++)
            cout << i * j * k;
```
