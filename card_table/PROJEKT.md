# Project – Card Table

**Individual Project Brief – Week 6 · u01**

Start: Monday, 16 November 2026. Show the working program on Monday, 23 November 2026.

## The Idea

You build a card table that does what a real dealer does, and then does it two hundred times without getting bored. The program builds a deck of fifty-two cards, shuffles it, deals five cards to each player at the table, and names the best combination in every hand. Then it repeats the same deal in a loop, writes every hand to `deals.csv`, counts how often each combination appeared on your own table, and draws that count as a PBM picture.

The deck is a list. A card is two values that belong together. A hand is a slice of the deck. A deal is a loop. The picture at the end is a grid of zeros and ones with a header, which you already wrote by hand last week. Nothing here needs a new language feature — one new module, `random`, is the only tool you have to look up.

## Why This Project Is Yours

You wrote HTML and CSS, and you play cards and guitar. Both are pattern work: a chord progression is a sequence you repeat with small changes, and a shuffle is a sequence you reorder with rules. You said you want to learn programming as a by-product of building something real — this is that something. The last milestone is the interesting one: once the program plays the game, it can also answer questions about the game, and that is the same move a data program makes.

## What You Already Have

- Lists, tuples, indices and slices — the whole deck fits in a list.
- `for` and `while` loops, `if`/`elif`/`else`, comparison and logical operators.
- `%s`, `%d` and `%.1f` formatting, and `len()` for counting elements.
- `open()` inside `with`, writing and reading text files, and the `csv` module.
- The PBM format from last week: a `P1` header followed by a grid of `0` and `1`.

## The New Thing

`random` is a module, not a function you can call without importing it. Find out how to:

1. Build a shuffled list, and which function shuffles a list in place.
2. What `random.shuffle()` returns, and what happens when you assign that return value to a variable.
3. How to make a shuffle repeatable, so that a test can run twice with the same order.
4. The difference between `random.choice()`, `random.sample()` and `random.randint()`.
5. Why a program that uses random numbers cannot be tested by running it once.

**Write it down:** Start `notes.md` with `## The New Thing – random`. Write two or three sentences about the function you chose for the shuffle, one example with real card values, and the one detail that surprised you. Finish with one sentence that explains how you will run the same deal twice when you test the program.

## The Plan

### Milestone 1 – A deck of fifty-two

Create `deck_lab.py`.

1. Store the ranks in one list and the suits in another.
2. Build all fifty-two cards with two nested loops, as strings such as `AS` and `10H`.
3. Print the number of cards, then the first five and the last five.
4. Prove there are no duplicates: compare every card with every other card in a nested loop and print the number of repeated pairs.

At the end of this step the program prints `52` and `0 duplicate pairs`.

### Milestone 2 – A shuffle you can trust

1. Import `random` and shuffle the deck.
2. Print the first five cards before and after the shuffle.
3. Store the result of the shuffle in a variable and print it.
4. Set a seed, shuffle, print five cards, set the same seed again, shuffle, print five cards.

At the end of this step you can explain, without looking at the documentation, why the last two prints are identical.

### Milestone 3 – Deal to a table

1. Ask how many players sit at the table; accept only `2`, `3` or `4`.
2. Give each player five cards, one card per turn, the way a dealer does it.
3. Print each hand as one line, with the card values separated by spaces.
4. Keep the rest of the deck in a variable named `stock` and print its size.

At the end of this step a table of four players holds twenty cards in four hands and thirty-two cards in the stock.

### Milestone 4 – Name the hand

Give every hand one of these names: `flush` (all five cards in one suit), `three of a kind`, `two pair`, `pair`, `high card`.

1. Count how many cards share each rank, using nested loops. Do not use a dictionary and do not use `count()`.
2. Decide the name from those counts, not from the card values.
3. Print the hand together with its name, in one formatted line.

At the end of this step a hand `AS KH 9D 2C 2S` prints as `pair of 2` and not as `pair`.

### Milestone 5 – Two hundred deals

1. Wrap the deal in a loop that runs two hundred times.
2. Write every hand to `deals.csv` with the `csv` module: one header row, then one row per hand, with the deal number, the player, five separate card columns and the name.
3. Read the file back and count each name with a loop over the rows.
4. Write `odds.txt` with one line per name and the percentage formatted with `%.1f`.
5. Check that the percentages add up to about `100.0` and write down what your program does with the rounding difference.

### Milestone 6 – The chart

1. Create `hands.pbm` with a `P1` header, one horizontal bar per hand name, eight rows per bar.
2. Make each bar as wide as the count allows, with the longest bar at most three hundred pixels.
3. Print the same picture to the terminal with `#` for black and `.` for white.
4. Compare the terminal picture with `odds.txt` — the two must tell the same story.

## Example

Your numbers will differ, because your shuffle is random. The shape must be the same.

```text
Players (2-4): 3

Deal 1
  rafik   AS KH 9D 2C 2S   pair of 2
  kuba    QD 10C 7H 4S 3D  high card
  marta   5H 5C 5S JD 8C   three of a kind

Saved 600 rows to deals.csv

odds.txt
high card       41.5%
pair            33.0%
two pair        17.5%
three of a kind  8.0%
flush            0.0%

Saved hands.pbm (300x40)
```

## Requirements

- One program, `card_table.py`, started from the terminal with `python3 card_table.py`.
- The deck is built by loops, not typed out by hand.
- Hands are judged from rank counts computed with nested loops; no dictionary and no `count()`.
- `deals.csv` has a header row and is written and read with the `csv` module.
- `odds.txt` uses `%s` for the name and `%.1f` for the percentage.
- `hands.pbm` has a correct header, one row per line, and the categories that never appeared are still drawn, with a bar of width zero.
- A test run uses `random.seed()` and the seed value is written in `notes.md`.

## Files

```text
card_table/
├── deck_lab.py
├── card_table.py
├── deals.csv
├── odds.txt
├── hands.pbm
├── notes.md
└── check.py
```

Commit the whole directory to your repository and push it before the Monday session. A directory that exists only on your laptop cannot be checked.

Run `python3 check.py` in the project directory before you commit. It reads the files your program produced, not your code, and prints one line per requirement.


## How It Will Be Checked

- The deck test prints fifty-two cards and zero duplicates.
- Two hundred deals produce exactly six hundred rows in `deals.csv` for three players.
- Every row in `deals.csv` has five cards and one name, and no row is empty.
- The bar widths in `hands.pbm` agree with the percentages in `odds.txt`.
- You can explain how one hand was classified, line by line, without running the program.

**Hint:** Decide the name from the counts, not from the cards. First compute how many ranks appear once, twice and three times, then compare those three numbers with the categories in Milestone 4. A `flush` is a separate question about suits, and it is asked before the counts.

**Additional challenge:** Add a bankroll simulation. Every player starts with one hundred chips, pays five before each deal, and the best hand takes the pot. Run fifty deals, write the bankroll of every player after each deal to `bankroll.csv`, and draw the four bankrolls as lines in a PGM picture, one line per player, with a different gray value for each player.

## Suggested Learning Resources

- [The `random` module – generate pseudo-random numbers](https://docs.python.org/3/library/random.html)
- [The `csv` module – reading and writing tabular data](https://docs.python.org/3/library/csv.html)
- [More on lists – `append`, `pop`, `sort` and slicing](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
- [Netpbm – description of the PBM format](https://netpbm.sourceforge.net/doc/pbm.html)

**Final goal:** By the end of this project, you should have a program that builds, shuffles, deals and judges cards, logs a few hundred deals to a CSV file, and turns its own statistics into a PBM picture — combining lists, tuples, loops, conditions, `%` formatting and file handling from the first five weeks.
