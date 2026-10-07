# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

Game Purpose
The purpose of the game is for the player to guess a randomly generated secret number within the range for the selected difficulty level. The game provides hints after each guess to tell the player whether the guess is too high or too low, while also tracking attempts and score.

Bugs I Found
I found several issues while testing the game. The Higher and Lower hint messages were reversed, so a guess below the secret number incorrectly told the player to go lower. The game also accepted guesses outside the selected difficulty range, such as negative numbers or numbers above the maximum. In addition, after winning and clicking New Game, the game remained in the previous "won" state instead of starting a fresh round.

I also found that the secret number was converted into a string on some attempts, which could cause incorrect comparisons between guesses and the secret number.

Fixes I Applied
I corrected the Higher/Lower hint logic so that a guess below the secret tells the player to go higher and a guess above the secret tells the player to go lower. I reset the Streamlit session status to "playing" when a new game begins and updated the app to use the selected difficulty range consistently.

I also added validation for guesses outside the selected range, removed the unnecessary string conversion of the secret number, and refactored the core game functions from app.py into logic_utils.py. Finally, I updated the automated tests to verify both the outcome and the hint message returned by check_guess().

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. The game selects a secret number within the chosen difficulty range.
2. When the secret number is 25, the user enters 24.
3. The game returns "Too Low" and tells the user to "Go HIGHER!"
4. The user enters 26, and the game returns "Too High" and tells the user to "Go LOWER!"
5. The user enters 25, and the game displays "Correct!" and ends the round.
6. The user clicks New Game, and the game resets to a new playable round with a new secret number.

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results
(.venv) PS C:\Users\damil\ai110-module1show-gameglitchinvestigator-starter\ai110-module1show-gameglitchinvestigator-starter> python -m pytest tests -v                                                               
=========================================================================================================== test session starts ============================================================================================================
platform win32 -- Python 3.13.5, pytest-9.1.1, pluggy-1.6.0 -- C:\Users\damil\ai110-module1show-gameglitchinvestigator-starter\ai110-module1show-gameglitchinvestigator-starter\.venv\Scripts\python.exe
cachedir: .pytest_cache
rootdir: C:\Users\damil\ai110-module1show-gameglitchinvestigator-starter\ai110-module1show-gameglitchinvestigator-starter
plugins: anyio-4.15.1
collected 3 items                                                                                                                                                                                                                           

tests/test_game_logic.py::test_winning_guess PASSED                                                                                                                                                                                   [ 33%]
tests/test_game_logic.py::test_guess_too_high PASSED                                                                                                                                                                                  [ 66%]
tests/test_game_logic.py::test_guess_too_low PASSED                                                                                                                                                                                   [100%]

============================================================================================================ 3 passed in 0.25s =============================================================================================================
The automated tests verified the following:
A correct guess returns "Win" and "🎉 Correct!".
A guess above the secret returns "Too High" and "📉 Go LOWER!".
A guess below the secret returns "Too Low" and "📈 Go HIGHER!".

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
