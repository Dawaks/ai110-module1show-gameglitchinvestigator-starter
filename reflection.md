# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
  The first time I ran the game, it looked like a normal number guessing game with a difficulty setting, score, number of attempts, and a section called Developer Debug Info. 
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
  I noticed that some of the game logic was incorrect. When the secret number was 8, I entered 7 and the game told me to go lower instead of higher. I also noticed that the game accepted an invalid guess such as -1, and after I correctly guessed the number and clicked New Game, the game still said that I had already won.

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Entered `7` when the secret number was `8` | The game should tell me to go higher | The game told me to go lower | No console error |
| Entered `-1` | The game should reject the input because it is outside the valid range | The game accepted `-1` and continued giving a hint | No console error |
| Correctly guessed `8`, then clicked **New Game** | The game should reset and allow me to start a new round | The game continued saying that I had already won | No console error |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  I used ChatGPT and Claude as AI teammates during this project. ChatGPT helped me understand the assignment, and identify the bugs I observed. Claude helped me inspect the code, make targeted fixes, refactor the logic into logic_utils.py, and review the changes.
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  One correct suggestion was to reset st.session_state.status to "playing" when the New Game button is clicked. The AI explained that the game remained in the "won" state because the status variable was not being reset. I verified the fix by winning the game, clicking New Game, and confirming that I could start a new round instead of seeing the message that I had already won.
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.
  At one point, the AI identified and fixed an additional bug involving the secret number being converted from an integer to a string on some attempts. Although this was a valid issue, it was not the second bug I originally wanted to focus on at that stage, which was the New Game problem. I therefore kept the additional finding in mind but redirected the AI to fix only the New Game session-state issue so that I could stay within the scope of the assignment. I then manually tested the New Game behavior to verify that the targeted fix worked.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  I decided a bug was fixed only after I could repeat the same action that originally caused the problem and get the expected result. 
- Describe at least one test you ran (manual or using pytest) and what it showed you about your code.
  I manually tested the hint logic when the correct number was 25. I entered 24 and confirmed that the game told me to go higher, then I entered 26 and confirmed that the game told me to go lower. This showed me that the higher/lower hint logic was working correctly after the fix. And selecting new game worked effectively
- Did AI help you design or understand any tests? How?
  Yes. I used AI to review my testing approach and suggest additional cases I could use to verify the fix more thoroughly. For example, it reinforced the idea of testing values just below, just above, and equal to the secret number so I could confirm that each possible outcome behaved correctly.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
