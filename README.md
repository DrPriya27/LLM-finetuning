# LLM-finetuning

https://www.linkedin.com/feed/update/urn:li:activity:7338460224455925760/?updateEntityUrn=urn%3Ali%3Afs_updateV2%3A%28urn%3Ali%3Aactivity%3A7338460224455925760%2CFEED_DETAIL%2CEMPTY%2CDEFAULT%2Cfalse%29

https://www.linkedin.com/feed/update/urn:li:activity:7308536567277490179/?updateEntityUrn=urn%3Ali%3Afs_updateV2%3A%28urn%3Ali%3Aactivity%3A7308536567277490179%2CFEED_DETAIL%2CEMPTY%2CDEFAULT%2Cfalse%29

https://www.linkedin.com/posts/youssef-hosni-b2960b135_if-you-would-like-to-get-your-hands-on-llm-activity-7295459477489672192-49Mu/?utm_source=share&utm_medium=member_android&rcm=ACoAAAe8D0cBW3NxXQaB93SNhHswReYjboBh_2k

https://www.linkedin.com/feed/update/urn:li:activity:7355228285615656960/

I've watched many videos on fine-tuning LLMs this week, but these three stood out the most. If you have time for just one, watch the first one—it covers everything you need to know about fine-tuning and merging models.

► Video 1: Everything You Need to Know About Fine-tuning and Merging LLMs – A deep dive into fine-tuning techniques like LoRA, QLoRA, PPO, and DPO, presented by Maxime Labonne. Link: https://www.youtube.com/watch?v=uLrOI65XbDw

► Video 2: LoRA & QLoRA Fine-tuning Explained In-Depth – A detailed breakdown of LoRA vs. full-parameter fine-tuning and key hyperparameters.
Link: https://www.youtube.com/watch?v=t1caDsMzWBk

► Video 3: Fine-tuning Large Language Models (LLMs) | w/ Example Code – A hands-on walkthrough with Python code examples.
Link: https://www.youtube.com/watch?v=eC6Hd1hFvos&t=1190s

https://www.linkedin.com/posts/sigalshaked_slm-rlhf-grpo-activity-7299128135852212224-nq_N/?utm_source=share&utm_medium=member_android&rcm=ACoAAAe8D0cBW3NxXQaB93SNhHswReYjboBh_2k

Here are the top 5 LLM fine-tuning techniques, explained with visuals:

First of all, what's so different about LLM finetuning?

Traditional fine‑tuning is impractical for LLMs (billions of params; 100s GB).

Since this kind of compute isn't accessible to everyone, parameter-efficient finetuning (PEFT) came into existence.

Before we go into details of each technique, here's some background that will help you better understand these techniques:

LLM weights are matrices of numbers adjusted during finetuning.

Most PEFT techniques involve finding a lower-rank adaptation of these matrices—a smaller-dimensional matrix that can still represent the information stored in the original.

Now with a basic understanding of rank of a matrix, we're in a good position to understand the different finetuning techniques.

Let's go! 🚀

(refer the image below for visual explanation of each technique)

1) LoRA

- Add two low-rank trainable matrices, A and B, alongside weight matrices.
- Instead of fine-tuning W, adjust the updates in these low-rank matrices.

Even for the largest of LLMs, LoRA matrices take up a few MBs of memory.1111111

2) LoRA-FA

While LoRA significantly decreases the total trainable parameters, it requires substantial activation memory to update the low-rank weights.

LoRA-FA (FA stands for Frozen-A) freezes matrix A and only updates matrix B.

3) VeRA

- In LoRA, low-rank matrices A and B are unique for each layer.
- In VeRA, A and B are frozen, random, and shared across all layers.
- Instead, it learns layer-specific scaling VECTORS (b and d) instead.

4) Delta-LoRA

- It tunes the matrix W as well, but not in the traditional way.
- Here, the difference (or delta) between the product of matrices A and B in two consecutive training steps is added to W.

5) LoRA+

- In LoRA, both matrices A and B are updated with the same learning rate.
- Authors of LoRA+ found that setting a higher learning rate for matrix B results in better convergence.
