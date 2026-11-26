---
name: explain-code
description: >
  Explain code in short, plain words so it is easy to follow.
  Use when the user asks what code does, says the code is hard to understand,
  wants a simple explanation, or runs /explain-code.
---

# Explain Code

Explain code. Do not change it.

What to explain, in this order:

1. The file, function, or pasted code the user names.
2. Code you just wrote or changed in this chat.
3. The current diff (`git diff HEAD`).
4. If none of these exist, ask which file.

## Words

- Short sentences. Everyday words.
- Write like you are talking to a friend who codes a little.
- One idea per line.
- Do not use these words: leverage, utilize, orchestrate, facilitate, robust, seamless, abstraction, instantiate, paradigm, boilerplate.
- If a hard word is in the code and you must keep it, add it to Hard words.

## Output

Use only this shape. Count the words. Rewrite any line that is over the limit.

### What
One sentence. 15 words or fewer. Say what this code is for.

### Read it this way
The code, in the order it runs. One line per step. 12 words or fewer.

- Start each line with the function or block name.
- Add the file line numbers when you have them.
- For an if, write each path as its own line.
- Skip imports, blank lines, and renames that do not change the result.
- 8 lines or fewer. If the code is longer, group it and still keep 8 lines.

### Pieces
Only when there is more than one function or block.

| Name | Job |
| --- | --- |
| | |

- Job: 8 words or fewer.
- 8 rows or fewer. Fold a tiny helper into the piece that calls it.

### Hard words
Only words from this code that are not everyday words.

| Word | Means |
| --- | --- |
| | |

5 rows or fewer. If none, write "No hard words."

### Watch
Up to 3 lines. Each line is one way this can go wrong. 12 words or fewer.
If nothing important, write "Nothing tricky."

Stop. Do not paste the code again. Do not add tips.

## Example

### What
Save an order when the cart has items, then tell the warehouse.

### Read it this way
- `saveOrder` lines 10–12: stop when the cart is empty
- `saveOrder` lines 14–16: write the order into the database
- `saveOrder` line 18: tell the warehouse the order id

### Hard words

| Word | Means |
| --- | --- |
| database | the place the app stores data |

### Watch
- Empty cart: nothing is saved
