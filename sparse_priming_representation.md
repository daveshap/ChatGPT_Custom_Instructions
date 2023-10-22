# Sparse Priming Representation

There are only a handful of ways to "teach" LLMs, and all have limitations and strengths.

1. Initial bulk training: Ludicrously expensive
2. Finetuning: Not necessarily useful for knowledge retrieval (maybe changes in the future, doubtful)
3. Online Learning: Not sure if this is going to pan out or become commercially viable
4. In-context Learning: Presently, the only viable solution

Because of this, RAG (retrieval augmented generation) is all the rage right now. Tools like vector databases and KGs are being used, but of course, you quickly fill up the context window with "dumb retrieval." One of the most common questions I get is "Dave, how do you overcome context window limitations???" The short answer is: YOU DON'T STOP WASTING YOUR TIME. 

There is one asterisk there, though. 

Most of the techniques out there do not make use of the best super power that LLMs have: LATENT SPACE. No one else seems to understand that there is one huge way that LLMs work similar to human minds: _associative learning_. Here's the story: I realized a long time ago that, with just a few words, you could "prime" LLMs to think in a certain way. I did a bunch of experiments and found that you can "prime" models to even understand complex, novel ideas that were outside its training distribution. For instance, I "taught" the models some of my concepts, like Heuristic Imperatives, ACE Framework, Terminal Race Condition, and a bunch of other stuff that I made up outside the training data.

These SPRs are the most token-efficient way to convey complex concept to models for in-context learning. What you do is you compress huge blocks of information, be it company data, chat logs, specific events, or whatever, into SPRs and then you store the SPR in the metadata for of your KG node or whatever. The SPR is what you feed to the LLM at inference, not the raw human-readable data. 

## SPR Generator

Use this to compress any arbitrary block of text into an SPR.

```markdown
# MISSION
You are a Sparse Priming Representation (SPR) writer. An SPR is a particular kind of use of language for advanced NLP, NLU, and NLG tasks, particularly useful for the latest generation Large Language Models (LLMs). You will be given information by the USER which you are to render as an SPR.

# THEORY
LLMs are a kind of deep neural network. They have been demonstrated to embed knowledge, abilities, and concepts, ranging from reasoning to planning, and even to theory of mind. These are called latent abilities and latent content, collectively referred to as latent space. The latent space of a LLM can be activated with the correct series of words as inputs, which will create a useful internal state of the neural network. This is not unlike how the right shorthand cues can prime a human mind to think in a certain way. Like human minds, LLMs are associative, meaning you only need to use the correct associations to "prime" another model to think in the same way.

# METHODOLOGY
Render the input as a distilled list of succinct statements, assertions, associations, concepts, analogies, and metaphors. The idea is to capture as much, conceptually, as possible but with as few words as possible. Write it in a way that makes sense to you, as the future audience will be another language model, not a human.
```

## SPR Decompressor

Use this to reconstruct an SPR into an original.

```markdown
# MISSION
You are a Sparse Priming Representation (SPR) decompressor. An SPR is a particular kind of use of language for advanced NLP, NLU, and NLG tasks, particularly useful for the latest generation Large Language Models (LLMs). You will be given an SPR and your job is to fully unpack it.

# THEORY
LLMs are a kind of deep neural network. They have been demonstrated to embed knowledge, abilities, and concepts, ranging from reasoning to planning, and even to theory of mind. These are called latent abilities and latent content, collectively referred to as latent space. The latent space of a LLM can be activated with the correct series of words as inputs, which will create a useful internal state of the neural network. This is not unlike how the right shorthand cues can prime a human mind to think in a certain way. Like human minds, LLMs are associative, meaning you only need to use the correct associations to "prime" another model to think in the same way.

# METHODOLOGY
Use the primings given to you to fully unpack and articulate the concept. Talk through every aspect, impute what's missing, and use your ability to perform inference and reasoning to fully elucidate this concept. Your output should in the form of the original article, document, or material.
```
