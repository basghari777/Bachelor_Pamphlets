### مرتبه زمانی:
در طراحی الگوریتم هدف استفاده از روش‌هایی برای کاهش مرتبه زمانی و کاهش تعداد گام‌های یک برنامه می‌باشد. مرتبه زمانی یا Order مدت زمان اجرا یا همان تعداد گام‌های اجرای یک برنامه را نشان می‌دهد. مرتبه زمانی الگوریتم‌ها در دسته‌های زیر قرار می‌گیرند.

<p style="direction: ltr; text-align: center">$$ O(1) < O(\log_{2} n) < O(n) < O(n\log_{2} n) < O(n^2) < O(2^n) < O(n!) < O(n^n) $$ </p>

**مثال:**

<p style="direction:ltr; text-align:left">$$ O(1) $$:</p>
```
for(int i = 0; i < 5; i++)
    cout << i;
```
<br/>

<p style="direction:ltr; text-align:left">$$ O(n) $$:</p>
```
for(int i = 0; i < n; i++)
    cout << i;
```
<br/>

<p style="direction:ltr; text-align:left">$$ O(\log_{2} n) $$:</p>
```
int i = n;
while(i >= 1)
{
    i /= 2;
    cout << i;
}
```
<br/>

<p style="direction:ltr; text-align:left">$$ O(n\log_{2} n) $$:</p>
```
for(int i = 0; i < n; i++)
{
    int j = n;
    while(j >= 1)
    {
        j /= 2;
        cout << j;
    }
}
```
<br/>

<p style="direction:ltr; text-align:left">$$ O(n^2) $$:</p>
```
for(int i = 0; i < n; i++)      // O(n)
    for(int j = 2; j < n; j++)  // O(n)
        cout << i * j;          // O(n) * O(n) = O(n^2)
```
#### تابع بازگشتی
**مثال:** مقدار <span style="direction:ltr"> f(5) </span> را بدست آورید.
```
int f(int n)
{
    if(n <= 1)
        return n;
    return f(n - 1) + f(n - 1);
}
```
<div style="text-align:left">
$$ f(5) = f(4) + f(4) $$ <br/>
$$ f(4) = f(3) + f(3) $$ <br/>
$$ f(3) = f(2) + f(2) $$ <br/>
$$ f(2) = f(1) + f(1) = 1 + 1 = 2 $$ <br/>
$$ f(3) = 2 + 2 = 4 $$ <br/>
$$ f(4) = 4 + 4 = 8 $$ <br/>
$$ f(5) = 8 + 8 = 16 $$ <br/>
</div>

**نکته:** معمولاً مسائلی که به صورت درختی حل شوند دارای مرتبه زمانی نمایی هستند.

#### شمارگام‌های یک برنامه:
برای محاسبه‌ی مرتبه‌ی زمانی باید شمار گام‌های یک برنامه محاسبه شود، یعنی هر سطر از برنامه چند بار اجرا می‌شود. در ادامه با چند مثال شمار گام‌ها را محاسبه می‌کنیم.
```
int y = 0;                  // (1)
int x;                      // (0)
for(int i = 0; i < n; i++){ // (n + 1)
    y++;                    // (n)
    x = y;                  // (n)
}                           // ________
                            // (3n + 2)
```
<p style="direction:ltr; text-align:left">$$ (3n + 2) \in O(n) $$</p>
<br/>

```
for(int i = 2; i < n; i++)  // (n - 1)
    cout << i;              // (n - 2)
                            // ________
                            // (2n - 3)
```
<p style="direction:ltr; text-align:left">$$ (2n - 3) \in O(n) $$</p>
<br/>

```
for(int i = 0; i < n; i++)      // (n+1)
    for(int j = 1; j < n; j++)  // ( n ) * n
        cout << i * j;          // ( n ) * (n-1)
                                // _____________
                                // 2(n^2) + 1
```
<p style="direction:ltr; text-align:left">$$ 2n^{2} + 1 \in O(n^2) $$</p>
<br/>

```
for(int i = 0; i < n; i++){     // (n+1)
    for(int j = 1; j <= n; j++) // ( n ) * (n+1)
        cout << i * j;          // (n^2)
    for(int k = 0; k < n; k++)  // ( n ) * (n+1)
        cout << k;              // (n^2)
}                               // _______________
                                // 4(n^2) + 3n + 1
```
<p style="direction:ltr; text-align:left">$$ 4n^{2} + 3n + 1 \in O(n^2) $$</p>
<br/>

#### حل معادلات بازگشتی به روش جایگزینی
با استفاده از رابطه‌ی بازگشتی (با جایگذاری) از $$ n $$ شروع کرده و به عقب بر می‌گردیم تا به شرط خروجی یا مقدار اولیه رابطه بازگشتی برسیم.

**مثال:**

<p style="direction:ltr; text-align:left">
t(n) = t(n - 1) + n , n > 1 <br/>
t(n) = 1 , n = 1
</p>

حل:

<div style="text-align:left">
t(n) = t(n - 1) + n <br/>
t(n) = t(n - 2) + (n - 1) + n <br/>
t(n) = t(n - 3) + (n - 2) + (n - 1) + n <br/>
...<br/>
<br/>
t(2) = t(1) + 2 <br/>
t(1) = 1 <br/>
<br/>
t(n) = 1 + 2 + 3 + $$ \cdots $$ + (n - 1) + n <br/>
t(n) = $$ \sum_{i = 1}^{n} i = \frac{n(n + 1)}{2} \Rightarrow O(n^2) $$ <br/>
</div>

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