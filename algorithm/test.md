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
t(n) = 1 + 2 + 3 + ... + (n - 1) + n <br/>

$$ t(n) = \sum_{i=1}^{n} i = \frac{n(n+1)}{2} \Rightarrow O(n^2) $$

</div>
