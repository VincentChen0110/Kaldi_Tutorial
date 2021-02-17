# Speech Adapatation 

###### tags: `adaptaion`

> notes of paper and books which I sumarized.

## :memo: What is Speaker Adaptation?

### Introduction: 

:rocket: There exists many models to recognize speech. If the model is able to recognize multi-people speeches, then it is called a **Speaker Independent System**. If the model is able to recognize only specific people, then it is called a **Speaker Dependent System**. <br /> :rocket: It is preferable to build a system that is able to recognize speeches from all kinds of people. However, if we wish to achieve higher performance on specific people, this is where we need ==**Speaker Adaptation**==.


### Abstract of Speaker Adaptation:

:rocket: First, a trained **Speaker Independent System** is required. Then, based on data of the specific speaker, we tune the model to adjust it to the specfic conditions which we desire. These "data" can be speech or text, which the features can be extracted via the acoustic and language model of the recipe. <br />
:rocket: Normally, we focus on extracting the **acoustic features**. However, the speaker may possess different habits of speech in specific phrases or grammer. In which, is dependent on the domain that is generalized as **Domain Adaptation**.
## :memo:Feature Adaptation
### Vocal Tract Length Normalization(VTLN) 
:rocket: VTLN is a typical method for speaker adaptation. The features of the human voice correlates hugely with the vocal tract length. Hence, we can distingush different human voices by their vocal tract lenghts, which can be analyzed at frequency domain. <br />
Therefore, we can define a normal length, and the other lengths can be transformed through a factor $\alpha$.
$$ 
S^\alpha(\omega) = S(\alpha\omega) 
$$
While S($\omega$) is the spectrum of the original speaker. The $\alpha$ factor is being found by testing through various tries and being selected at maximum probability.
In the `wsj` recipe, the `run_vtln.sh` is implemented and located in the `local` directory.

## :memo: Acoustic Adaptaion : HMM-GMM Model


### Step 3: Invite your team to collaborate!

Click on the <i class="fa fa-share-alt"></i> **Sharing** menu :arrow_upper_right: and invite your team to collaborate on this note!

![permalink setting demo](https://i.imgur.com/PjUhQBB.gif)

- [ ] Register and sign-in to HackMD (to use advanced features :tada: ) 
- [ ] Set Permalink for this note
- [ ] Copy and share the link with your team

:::info
:pushpin: Want to learn more? ➜ [HackMD Tutorials](https://hackmd.io/c/tutorials) 
:::

---

## BONUS: More cool ways to HackMD!

- Table

| Features          | Tutorials               |
| ----------------- |:----------------------- |
| GitHub Sync       | [:link:][GitHub-Sync]   |
| Browser Extension | [:link:][HackMD-it]     |
| Book Mode         | [:link:][Book-mode]     |
| Slide Mode        | [:link:][Slide-mode]    | 
| Share & Publish   | [:link:][Share-Publish] |

[GitHub-Sync]: https://hackmd.io/c/tutorials/%2Fs%2Flink-with-github
[HackMD-it]: https://hackmd.io/c/tutorials/%2Fs%2Fhackmd-it
[Book-mode]: https://hackmd.io/c/tutorials/%2Fs%2Fhow-to-create-book
[Slide-mode]: https://hackmd.io/c/tutorials/%2Fs%2Fhow-to-create-slide-deck
[Share-Publish]: https://hackmd.io/c/tutorials/%2Fs%2Fhow-to-publish-note

- LaTeX for formulas

$$
x = {-b \pm \sqrt{b^2-4ac} \over 2a}
$$

- Code block with color and line numbers：
```javascript=16
var s = "JavaScript syntax highlighting";
alert(s);
```

- UML diagrams
```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
Note left of Alice: Alice responds
Alice->Bob: Where have you been?
```
- Auto-generated Table of Content
[ToC]

> Leave in-line comments! [color=#3b75c6]

- Embed YouTube Videos

{%youtube PJuNmlE74BQ %}

> Put your cursor right behind an empty bracket {} :arrow_left: and see all your choices.

- And MORE ➜ [HackMD Tutorials](https://hackmd.io/c/tutorials)
