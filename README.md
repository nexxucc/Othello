# Othello

A browser Othello (Reversi) game in plain JavaScript, with a computer opponent.

**Play it:** https://othello.vansh.runs-on.dev

Built at the **Scribble Pad Hackathon**, where it won **third prize**. It was a team
project; the original team repository is
[maria-2806/Heckers](https://github.com/maria-2806/Heckers).

## How to play

- You play **Black** and move first. The computer plays **White**.
- Darker squares mark your legal moves. Click one to place a disc; every line of
  White discs you enclose flips to Black.
- If a player has no legal move, their turn is skipped.
- The game ends when neither side can move, and the player with more discs wins.

## How it works

Everything is in [`index.html`](./index.html): a single script that builds the page,
with no dependencies or build step.

- **Board:** an 8×8 array, starting from the standard four-disc position.
- **Move rules:** a move is legal if, in at least one of the 8 directions, it encloses
  a run of opponent discs against one of your own. Placing a disc flips every
  enclosed run.
- **Computer opponent:** for each legal move, White runs a depth-3 **minimax** search
  and picks the move with the best score. A position is scored as White's disc count
  minus Black's.

## Known limitations

- During its look-ahead, the computer places discs without flipping the captured
  ones, so it underestimates how much a move gains. Its play is weaker than a depth-3
  search would normally be.
- The evaluation counts discs only. It doesn't value corners, edges or mobility,
  which matter most in real Othello strategy.
- There is no restart button or score display during play; reload the page to start
  a new game.

## Run locally

Open `index.html` in any modern browser. No server is needed.

The page was exported from a [Scribbler](https://app.scribbler.live) JavaScript
notebook, which is why it loads Scribbler's stylesheets.
