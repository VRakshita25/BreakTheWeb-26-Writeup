# Small Basket - Har din mehnga

## Description: 
Today is Moochi's birthday, and she wants to buy chocolates to give to her friends.

Unfortunately, Small Basket is very expensive, and Moochi has only **₹20**.

Can you help Moochi get a **Ferrero Rocher**?

## Flag: BTWCTF{sm4ll_b4sk3t_1s_n0t_t00_3xp3ns1v3}

## Solution: 
1. Add Munch chocolate to cart.

2. Visit cart and capture the request for payment page.

3. Copy the order id and payment id.

4. Go back to shopping page without paying, and add ferrero rocher to cart.

5. Visit cart and capture the request for payment page. 

6. Intercept and click the pay button. 

7. Modify the request by replacing the current transaction's payment id with the previous.

8. You get the flag