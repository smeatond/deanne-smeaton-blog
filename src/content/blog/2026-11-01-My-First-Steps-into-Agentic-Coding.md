---
title: 'My First Steps into Agentic Coding'
description: 'Exploring agentic coding, its productivity benefits, limitations, and why engineering judgement and code quality still matter.'
pubDate: 'Nov 01 2026'
heroImage: '../../assets/agentic-coding.png'
tags:
  - Agentic Coding
  - Software Engineering
  - Productivity
  - Code Quality
 
---
For the longest time I have been keeping AI Coding agents away from my projects, not because I didn’t think they would work but because I was worried I would have less control and understanding of my team's codebase. I have been using chat for a while. As a small team, chat has given me the ability to rubber duck, explore architectural options, and provide code snippets for methods or small parts of the application.  I have found chat a good aggregator of information and it allowed me to have control of what I have been developing.  This month I have gained access to Claude Code, have been to some talks on how AI has helped local companies and started to be curious on where an AI agent could help me in my normal day workflow. 

## First Use-cases 

My first use cases were reviewing the codebase and as a secondary reviewer to pull requests coming through. 

### Reviewing the Codebase 

I was asked to extract some information that our end users could understand and have as a FAQ for expected behaviour of the system I have been developing. I still approached this the same way I have been with chat. I didn’t bombard AI with a long list of requirements; I just prompted one question at a time and manually copied the extracted data to a user-friendly document. This allowed me to review and verify the actual data the agent was giving me. During this process, it also raised bugs and potential issues in the codebase. Around 80% of what the agent raised were legitimate issues that should be addressed. Mostly edge cases that the system had yet to experience. The other issues were either already raised, would not happen in the real world, or the agent had a misunderstanding of the context of the system. Through this, I did notice it was overly agreeable and wanted to give me answers even if there was nothing new to add. But having access to the codebase, rather than me pasting parts that I thought it would need, meant I got a better review, and I also saw how it could be useful for testing in the future. 

### Secondary Pull Request Reviewer 

The other use case was having the agent help me perform pull request reviews. I still like to have a human look first. But after that having the agent view the pull request has helped pick up things that I hadn’t noticed.  

### Preparation 

Over the past year I had noticed more and more agentic code coming into the codebase. I wasn’t against others using the tools, but I was noticing a pattern of code continuing to come through that went against our codebase preset rules. New files created rather than using the existing codebase, not sticking to DRY principles, and even files not following the file naming standards. So, to protect the codebase and make sure it stayed human-readable, maintainable and followed existing coding practices I decided to make a shared instructions file so everyone in the team, no matter which agent they were using, would have the same instructions. This was through `AGENTS.md` which other agent files included i.e. `CLAUDE.md` and `GEMINI.md`. In this file I included the following: 
- Project context, so it knew what the system is about 
- How developers work, including needing acceptance criteria, plan before coding, staying in scope and asking when unsure 
- Let it know safety critical areas so agents must check with the developer before making changes 
- Shared coding standards and the team’s principles for each part of the project i.e. C#, TypeScript, SASS and scripts 
- Security concerns to follow i.e. what is allowed in logs 
- Testing requirements, how are unit tests created, what are we testing for i.e. business logic vs code coverage 
- Commits, pull request and reviews, the process, what should be covered when reviewing other code and how to go about it. 
- What requires a human i.e deploying on a live existing deployment. 

These instructions were decided so pull requests coming through would not have fundamental issues of not matching our coding standards, give humans the opportunity to direct the agent and making it clear what it should and shouldn’t do. 

The idea is that as the team learns, we can update this and become more precise and even loosen up rules once we have become sure that the agents follow as we expect. In addition to this, I also included some guideline documentation for the development team as this is a new tool available for us to use. 

### Actual Code 

As a Tech Lead I am finding I have less and less time to focus on coding tasks while I work with other developers and other non-code related priorities. To keep the project moving forward I decided to use AI to finish writing a feature I had been working on and off for weeks. It was a new API endpoint for a lambda function I was creating. It was close to completion, but I hadn’t quite finished everything needed. 
 
And how did it go? I let it know what I was trying to achieve and asked it to make a plan for what I had left to do. It was pretty accurate, although the agent went beyond the scope of the task. I narrowed down to the specifics of the task and asked it to finish it off, including the missing unit tests. During the time it did this, I was busy with an urgent task that required my full attention and would otherwise mean this feature would continue to be delayed. The agent was in the background working on the task that kept the project’s momentum. And overall, I am happy for what it did. It asked questions a few times, it didn’t make things up and it followed the project’s instructions. More importantly it was able to pick up on a task that I had been constantly context-switching from and finished it off for me.  One part had a big implication if the agent got it wrong, I had chosen to make the changes manually based on its suggestions when I had a free moment.  Before pushing it back to the branch, I reviewed the changes and confirmed the task was completed (and nothing more) and ran the code locally to confirm that it was working as expected.  
 
Obviously this is only one case of using it to code. I am also an experienced engineer, so the way I instruct it may differ to someone without my experience, which may affect the outcome of the code. There is still plenty to learn, but I can see how it can be a useful tool to keep moving momentum forward when other tasks need to be completed. 

## Big Picture 

### Benefits 

Personally, what did I gain? Tasks, like reviewing the codebase to create FAQ, that would take me weeks were done in days and the coding task, that required my full attention, I was able to complete in one afternoon while focusing on an urgent issue elsewhere. Which is always good from a business point of view. As a Tech Lead, it is almost like delegating work to another developer, the difference being you must retain your own judgement and have much more care when setting up the task. 

For younger developers or when using a new technology, and even from what I have seen in chat, it can be a great learning tool as it can aggregate data from many resources, although this is only if you know the limitations. 

### Limitations 

While working on some of the non-coding tasks with the agent I did find it difficult focusing on so many moving parts. In truth, this is real multi-tasking, and the cognitive load of keeping track of what the agents were doing, and what they needed to do next was difficult to manage. Learning how to properly instruct tasks so the agent is less disruptive to my other workflow would help overcome this. Although the cognitive load of reviewing a larger amount of data would not have been useful for this task either. 

If you use the tool for a new technology or as a junior developer by telling it the requirements and letting it do the work for you this could lead to some serious implications. Junior developers do not have the experience of what makes a good piece of code and overall how that code fits into the system. Normally they are working on one task at a time and the senior(s) around them are thinking of the bigger picture. They also haven’t got the battle scars to lean on when instructing the agent to write the code. As they say garbage in, garbage out. 

It is also eager to please the person on the other end. So, when using the tool, you must be prepared to analyse the output and be clear with your instructions to make sure it hasn’t overlooked any issues or raise concerns just to produce output. 

At the end of the day agentic coding is a tool that software developers can use to help speed up their development and tasks. It still requires human judgement, and reviewing as it does make assumptions and even with the whole codebase available to it, it can make its best guess based on what it knows elsewhere. 

### Longer Term Considerations 

Agents produce code faster than a human can. That is undeniable. And at the moment it is helping productivity for businesses. But I do believe we have to be careful about backing ourselves into a corner of only relying on agentic coding. The codebase needs to still remain maintainable, readable for humans. In the future we don’t know if there will be cost increases, or changes on who provides agents, so we don’t want to solely rely on them. 

That doesn’t mean we shouldn’t use the tool; we just must correctly instruct them so code is kept to the high standard and can be supported by the software team using the agents. 
 
This is an ever-changing field and there is so much more for me to learn. Undoubtedly my opinions and how I use this tool will continue to change. I will continue experimenting and learning how best to use this for my daily workflow.  

## What is next? 

I want to see if I give agents more coding tasks and see if that will improve project momentum. With that I am expecting some risks, will we be able to keep up with the reviewing the output or will it cause more cognitive load and context-switching not reduce it. I would like to explore having an agent to help with the QA process. I am also experimenting for a future blog on “slop” vs software-engineered code produced by an agent. 

 