COS10005 - Assignment 2
Cinefi: Movie Discovery and Ticket Booking Website

Student name: [Ragan]
Student ID:   [106900779]
Mercury URL:  [http://mercury.swin.edu.au/cos10005/s106900779/Assignment02/index.html]


FILES

index.html      Home page
movies.html     Movie listing (8 movies)
recommend.html  Recommendation form
register.html   Registration form (JavaScript validation)
booking.html    Ticket booking form (JavaScript validation)
css/style.css   Stylesheet linked from every page
js/script.js    All JavaScript (only techniques taught in Weeks 7 to 9)
images/         logo.png, hero.png, movie1.jpg to movie8.jpg


HOW THE SELECTED MOVIE IS CARRIED TO THE BOOKING PAGE

Approach: URL query string, read with a regular expression on window.location.href.

1. Every movie has an ID (1 to 8), used by getTitle() and getPrice() in script.js.
2. On movies.html the "Book this movie" link is, for example,
   booking.html?movie=3
3. On recommend.html, JavaScript builds the same kind of link for each
   recommended movie.
4. On booking.html, script.js looks at the page address with
   window.location.href.match(/movie=([0-9]+)/). If it finds "movie=" and
   digits, found[1] holds the movie ID. The script checks that it is a real
   movie ID, then sets the Movie dropdown to it with movieBox.value = found[1].
   The price boxes are then updated.

Why: it needs no server, works from both pages with the same code, survives
a page refresh, and the user can still change the dropdown afterwards.
If the page is opened directly, there is no "movie" value, so the dropdown
stays on "-- Select a movie --".


RECOMMENDATION RULES (recommend.html)

recommend() in script.js uses a switch on the genre, then if/else rules on
the age group and viewing preference to pick one movie:
- Animation: Child -> Starlight Rescue, otherwise The Tiny Orchestra.
- Comedy: Adult watching with a Date Night or Friends -> Bad Wedding
  Planner, otherwise Laugh Track.
- Action: Child or Family viewing -> Skyline Runners (PG), otherwise
  Iron Meridian (M).
- Drama: Adult watching Solo -> The Last Ledger (MA15+), otherwise
  Paper Lanterns.
The result has a "Book this movie" link carrying the movie ID.


VALIDATION

Register: all fields required; username 5+ characters (letters, numbers,
underscores); valid email; phone 8-15 digits; password 10+ characters with
uppercase, lowercase, number and special character; passwords match; gender
selected; at least one genre; country selected.

Booking: required fields; valid email; phone 10+ digits; screening date and
time not in the past; tickets greater than 0; ticket type selected.
Voucher = 12 digits (shown only for Voucher). Online payment = card type
and digits-only card number (Visa/Mastercard 16, Amex 15) plus a billing
email (shown only for Online payment).
All error messages are collected in one message and shown in an alert box.
The form cannot be submitted until all errors are fixed.


REFERENCES AND NOTES

- Hero image (images/hero.png), logo (images/logo.png) and movie posters
  (images/movie1.jpg to movie8.jpg) are original artwork created for this
  assignment. All movie titles, descriptions and prices are fictional.
- Form action for booking.html and register.html:
  http://mercury.swin.edu.au/it000000/cos10005/regtest.php
- Test card numbers: use fake numbers only (for example 16 digits for Visa).
