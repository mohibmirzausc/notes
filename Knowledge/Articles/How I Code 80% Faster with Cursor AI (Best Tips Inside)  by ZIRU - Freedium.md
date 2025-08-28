---
title: "How I Code 80% Faster with Cursor AI (Best Tips Inside) | by ZIRU - Freedium"
source: "https://freedium.cfd/@jh.baek.sd/how-i-code-80-faster-with-cursor-ai-best-tips-inside-be5e500aa7d0"
author:
published:
created: 2025-08-27
description: "Stop writing code the hard way. Here's how senior developers are using AI to work smarter, not..."
tags:
  - "clippings"
---
[< Go to the original](https://medium.com/@jh.baek.sd/how-i-code-80-faster-with-cursor-ai-best-tips-inside-be5e500aa7d0#bypass)

![Preview image](https://miro.medium.com/v2/resize:fit:700/0*5vPbulIsXmADPaHq)

## How I Code 80% Faster with Cursor AI (Best Tips Inside)

## Stop writing code the hard way. Here's how senior developers are using AI to work smarter, not harder.

androidstudio · May 26, 2025 (Updated: May 26, 2025) · Free: No

I just had a chat with one of our senior engineers. He told me something that blew my mind: **"I barely write code by hand anymore. I just type what I want into Cursor's agent, and it does the work."**

I had to agree. About 80% of my work happens this way now.

If you know what you want to build, Cursor can handle complex tasks like a dream. Today, I'm sharing exactly how I use it — plus my best tips that most people miss.

### Turn On "Auto-Run Mode" (The Game Changer)

Here's a feature that most people overlook: Cursor doesn't just fix lint errors. It keeps working until your code actually runs properly. But you need to enable Auto-Run Mode first.

**Here's how:**

- Go to Settings
- Scroll down and turn on Auto-Run Mode (used to be called YOLO mode)
- Don't let the name scare you — I thought it was risky at first, but now I always keep it on

> When you enable Auto-Run Mode, you can set up custom prompts. Here's mine: Any kind of tests are always allowed like vitest, npm test, nr test, etc. Also basic build commands like build, tsc, etc. Creating files and making directories (like touch, mkdir, etc) is always ok too.

This lets the agent freely run mkdir, tsc, or lint checks whenever it wants. The coolest workflow? It runs tsc, finds build errors, fixes them, and repeats until everything passes. It's magic.

### Handle Complex Tasks Like a Pro

Let me show you how to tackle complex work with Cursor. I'll use this prompt as an example:

*"Create a function that converts a markdown string to an HTML string."*

I love this prompt because no AI gets it right on the first try. It needs several iterations.

Before AI, I'd write code, test it, go back, think "oh, that's not right," and repeat. It felt like being a QA tester sometimes. Not bad, but not always fun.

That's why people invented automated testing and TDD. I don't usually prefer TDD, but with AI? It's different. Add one line to your prompt and make it 1000x better:

**"Write tests first, then the code, then run the tests and update the code until tests pass."**

Now Cursor handles everything. I don't need to approve creating test directories or add example context files. Cursor looks at package.json and figures out what it needs for testing. Pretty smart.

### Watch the AI Work (But Stay Alert)

Here's what's interesting: When it creates test files, Cursor's code is more likely to work correctly than typical AI-generated code. If tests pass, it means the code actually does something right.

After writing implementation code, it runs tests. Six tests failed? No problem. Since I set up Auto-Run Mode to handle tests automatically, it keeps fixing code until tests pass. And I'm doing nothing.

**But you can't just walk away.** AI often goes down weird paths. When that happens, I hit the stop button and say: "Wait, hold on. You're implementing this really strangely. Reset, recalibrate, and get back on track."

Still, in my case, all tests eventually passed!

### Build on Existing Tests

Another cool Cursor feature: you can expand work based on existing tests. For example, I can say: "Add a few more test cases and make sure the code passes everything."

In another project, I work with multiple compilers and converters for a builder tool. One converter occasionally threw errors. What do I do? Every few days, I grab code from logs that won't convert, paste it into Cursor, and say:

*"Run this code, see what doesn't compile, write tests for those issues, then update the code until all tests pass."*

It's incredible. I keep adding new cases every few days. Great way to make code more robust.

### Fix TypeScript Errors Instantly

Here's another tip I absolutely love.

Say I've been coding for a while and realize I have TypeScript issues. I run the build and see errors everywhere. I go to Cursor and command:

*"I've got some build errors. Run nr build to see the errors, then fix them, and run build until it passes."*

That's how I finish most of my work. When coding in one go, you get lots of lint issues and type problems. I literally ask Cursor to fix all of them.

I always create a "pre-PR" command in every project. This includes the fastest scripts from the build stage. No E2E tests from CI (those rarely break anyway), but simple tools like tsc, Prettier, and ESLint that can tell if CI build will break.

Then I run Cursor and let it fix the PR until everything passes. Works pretty well even on large, complex projects.

### Debug with Logs (Super Effective)

When dealing with complex, tricky problems, having Cursor output logs and using those logs to solve issues is quite useful. Here's my approach:

1. **Add logs:** "Add logs to the code so I can better understand what's happening inside. I'll run the code and share the log results with you."
2. **Cursor adds log code** at key points
3. **I run the code** and collect logs
4. **Back to Cursor:** "Here are the log results. What problems do you see now? How should we fix them?"
5. **I paste the log results** for Cursor to analyze

This approach gives Cursor more specific information to work with. It's like providing a diagnostic report about what's happening inside your code.

This way, Cursor can make much more precise fix suggestions based on actual code behavior, not just static analysis.

This method is especially effective for solving tricky bugs that are hard to identify just by looking at code. It's like having a smart junior developer who adds logs, runs code, and interprets results.

### Master Command K and Command I

Let me show you some super useful Cursor shortcuts that you may or may not know about. These are really practical for daily work.

**Command K** is great for quick fixes. For example, maybe you want to keep the original content but make all fonts smaller. Select your code block, press Command K, and just tell Cursor what you want.

**Command I** opens the agent window. If you select some code and press Command I, the selected code automatically gets included in the agent's context. Super useful for modifying or discussing code snippets.

The main reason I use Command K instead of Command I is speed. Command K only works on selected code, so it's very fast. The inline UI is also pretty clean, making it simple and pleasant to use.

### Use Command K in Terminal

Command K in terminal is another favorite feature. I love using it to reduce typing. For example, I say "list the 5 most recently created branches" and the command runs automatically.

I don't memorize complex git commands anymore. Instead, I have more time and mental space to solve more important problems. Cursor does what I want, and that's why I love this tool.

### Balance AI Help with Coding Skills

People often ask: "Won't using AI tools like Cursor make me lose my coding skills?" It's a fair concern, but I think differently.

If we define "coding skills" as the ability to build great products through great code (which is what most companies actually want), I don't think you need to hand-code all day every day to maintain or improve this ability.

AI automates repetitive, basic tasks, saving time and mental energy so you can focus on harder problems. For example, I use Cursor's Composer feature to quickly build UI, then step in personally when I hit complex problems to refine them precisely.

I don't think there's a world where you can complete entire products with just vibe coding. I've never seen anyone do it, and I don't think it'll be possible in the future. While AI tools keep improving, some areas already feel like they're hitting growth limits.

We'll always face situations where we need to modify code and implement things directly. If you can't code at all and don't know how to debug, those are important skills you must learn. When coding, you'll definitely hit walls, and you need to solve them yourself.

**I think AI helps senior developers the most.** The best strategy for everyone is to build as much development capability as possible, then add AI help on top. But importantly, you need to properly understand and handle the code AI creates.

If you keep writing code, your coding skills naturally improve. More importantly, you can develop practical capabilities like productivity and efficiency. I prefer developers who use tools like Cursor well over those who try to hand-code everything.

I want developers who know how to work as lightly and quickly as possible. You can't spend 8 hours a day only on difficult problems. But I believe spending 4 hours quickly implementing UI by feel, then 2 hours focusing intensely on complex problems by hand produces much better results.

### The Bottom Line

Overall, Cursor is a fantastic tool. If you're only using auto-complete features, you might be missing this tool's real value. Make sure to try advanced features like the agent functionality too. It's important to learn by experience which workflows fit well, what tasks work great with agents, and what methods are useful for testing.

The core goal is delivering better products to customers and contributing to business profits. AI tools are auxiliary means to help achieve this goal more efficiently. But don't forget the importance of your own coding skills and problem-solving abilities.

These are my best Cursor tips. Try them yourself and feel how much your workflow improves.