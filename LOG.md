# Debug log

Your notes. One entry per bug you fixed, using the template below.

This file is read as carefully as your code. A correct fix you cannot
explain counts for little; a bug you could not fix but investigated
honestly still counts for something.

Delete the example before you submit.



## Example — delete this

### CC-99 — "The cart total is wrong"

**Reproduced:** Added 2 dosas at Rs. 60 each. The cart showed
Rs. 119.99999 instead of Rs. 130. Happened every time, on any dish with
a price ending in .50.

**Cause:** The total was being added up with plain floating point and
never rounded, so 0.1 + 0.2 style errors showed up on screen. The
rounding helper existed but this one place was not using it.

**Fix:** Ran the total through the existing rounding helper instead of
adding a new one, so every price on screen goes through the same path.

**Checked:** Cart, checkout and the order screen all show Rs. 130 now.
Prices without decimals still show without a trailing .00.

**Time:** about 40 minutes, most of it working out that the cart and the
order screen round in different places.



## CC-0X — "<the complaint, in short>"

**Reproduced:**

**Cause:**

**Fix:**

**Checked:**

**Time:**



## Could not fix

For anything you investigated but did not solve. Say what you tried and
where you got to. This is worth marks — leaving it blank when you got
stuck is not.

### CC-0X — "<the complaint>"

**What I tried:**

**Where I got to:**

**What I would try next:**



## Extra credit

Anything not on the bug log: a problem you found yourself, a test you
wrote, or a fix you are unsure about. Same format, plus one line on how
you noticed it.





### CC-02 — Dark mode text readability

Bug: Dish names and prices were difficult to read in dark mode because the text appeared too dark against the dark background.

Reproduction steps:

1. Open the canteen menu.
2. Switch the theme to dark mode.
3. Observe the dish names and prices on the menu cards.

Fix: Added a dark-theme CSS rule in "frontend/style.css" targeting ".dish-name" and ".dish-price", setting their text color to "#ffffff !important".

Reason: The explicit text color improves contrast against the dark background.

Verification: Tested the menu in dark mode and light mode.


### CC-03 — Mobile menu extends beyond screen edges

Reproduction: Open the website at a mobile viewport width of approximately 375px and open the navigation menu.

Fix: Updated the mobile ".site-nav" CSS rules to constrain its width to the viewport and apply "box-sizing: border-box".

Verification: Reopened the mobile menu at the tested viewport width and confirmed that it stays within the screen edges.


### CC-05 — The category bar scrolls away on my phone

Reproduction: Open the menu on a small-screen/mobile viewport and scroll down through the dishes. The category bar scrolls out of view.

Root cause: The ".cat-tabs" element used "position: relative", so it scrolled with the page instead of staying visible.

Fix: Changed ".cat-tabs" to "position: sticky", set "top: 0", added a "z-index", and retained its horizontal scrolling behavior.

Verification: Tested on a mobile viewport and confirmed that the category bar stays visible while scrolling through the dishes.


### CC-10: Sorting by price is backwards

Reproduction: Select “Price: low to high” and observe that expensive dishes appear first. Select “Price: high to low” and observe that cheaper dishes appear first.

Root cause: The ascending and descending price comparators were reversed. The rating-descending comparator also sorted by price instead of rating.

Fix: Corrected the price comparators and changed the rating-descending comparator to compare ratings.

Verification: Tested both price sorting options and rating-descending sorting. All three worked correctly.


### CC-01 — Search suggestions appear behind other elements

Reproduction steps:

1. Open the Canteen Chaos website.
2. Enter a dish name in the search box.
3. Observe the search suggestions dropdown when it appears near the filter bar and dish cards.

Root cause:
The search suggestions dropdown was appearing behind nearby page elements because its positioning and stacking order were not sufficient.

Fix:
Updated the CSS in "frontend/style.css" to position the search container and increase the stacking order of the suggestions dropdown. Also adjusted nearby container overflow so suggestions can remain visible.

Verification:
Tested the search suggestions and confirmed that they appear above other elements and remain usable.



### CC-08: An old coupon still works

**Reproduction:** Apply the FRESHERS24 coupon, which has an expiry date in the past.

**Root cause:** The coupon validation did not reject coupons whose expiry date had passed.

Fix: Added an expiry-date check in `applyCoupon()` before calculating the discount. Expired coupons are rejected with an explanatory message.

Testing: Verified that an expired coupon is rejected and does not receive a discount.


### CC-04 — "The buttons dont work on my tablet"

What I tried:
I tested the reported behavior and tried to reproduce the issue using the website. I checked the relevant functionality and attempted to identify the cause.

Where I got to:
I could not consistently reproduce the issue or confirm its root cause, so I could not implement a reliable fix.

What I would try next:
I would investigate the related code further, test more edge cases, and use browser developer tools to identify the cause.

### CC-06 — "I ordered more than i had"

What I tried:
I tested the reported behavior and checked whether the issue occurred during normal use. I attempted to reproduce it and inspect the relevant functionality.

Where I got to:
I could not reproduce the reported issue during my testing, so I did not make unnecessary code changes.

What I would try next:
I would test additional scenarios and inspect the relevant code to determine whether the issue occurs under specific conditions.

### CC-07 — "Cancelling makes it worse"

What I tried:
I investigated the reported behavior and tested the related functionality to understand the problem.

Where I got to:
I could not establish a reliable fix for this issue.

What I would try next:
I would review the relevant code in more detail, reproduce the issue with different inputs, and test a targeted fix.

### CC-09 — "The menu shows more dishes than it should"

What I tried:
I tested the reported behavior and checked the relevant functionality to see whether I could reproduce the bug.

Where I got to:
I could not confirm a reliable solution during my testing.

What I would try next:
I would investigate additional edge cases, inspect browser console messages, and test a focused fix once the root cause is clear.