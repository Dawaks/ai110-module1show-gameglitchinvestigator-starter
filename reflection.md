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

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? Chatgpt
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). One correct suggestion was that the New Game problem was caused by the game resetting the secret number and attempts but not resetting st.session_state.status back to "playing". I verified this by reviewing the New Game section of the code and testing the game again after the change. 
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count. I did not accept every AI suggestion automatically; for example, when additional possible bugs were identified, I focused first on the bugs I had personally reproduced so that my changes stayed within the scope of the assignment.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed? I decided a bug was fixed only after I could repeat the same action that originally caused the problem and get the expected result. 
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
