<h1 align="center">Zhenhuan Wang</h1>

<p align="center"><a href="mailto:zhenhuanwang@link.cuhk.edu.cn">Email</a> · <a href="https://www.linkedin.com/in/zhenhuan-wang/">LinkedIn</a> · <a href="https://orcid.org/0009-0001-2400-1839">ORCID</a></p>

<p>I’m a data science undergraduate at The Chinese University of Hong Kong, Shenzhen. I study how to steer diffusion models at inference time and how to evaluate agent actions against safety policies. I also build developer tools and contribute to open-source machine learning libraries.</p>

## Research

<p><strong>Step-PI</strong> · First author · 2026<br>I designed an inpainting controller for frozen Stable Diffusion 1.5. It carries feedback from the mask boundary and interior across denoising steps. The same settings worked on images of faces, animals, and scenes. Across 3,500 paired cases, retaining feedback improved all five metrics on all three datasets. Adjusting when to apply that feedback improved all five again on each dataset. <a href="https://arxiv.org/abs/2609.00862">Preprint</a></p>

<p><strong>Jev-Guard</strong> · Co-author · 2026<br>Jev-Guard selects the policy that applies to a proposed agent action, then checks the action against it. I studied routing errors and measured accuracy and latency in Qwen LoRA experiments. I also helped design a benchmark for how well the auditor handles rules that have been added, split, or revised. <a href="https://arxiv.org/abs/2610.18326">Preprint</a> · <a href="https://hkust-knowcomp.github.io/jev-guardrail/">Project</a></p>

## Open Source Contributions

<p>By November 2026, eight community projects had merged <strong>20 of my pull requests</strong>.</p>

<ul><li><strong>Kornia</strong> · I added a mask that tells callers which reconstructed 3D points are numerically valid. For lazy transforms, I changed how Kornia rebuilds a matrix. Keeping just the shape, dtype, and device lets it release the image batch. In one CPU flip module, that cut the serialized size from 6.29 MB to 1.6 KB. <a href="https://github.com/kornia/kornia/pull/4484">PR #4484</a> · <a href="https://github.com/kornia/kornia/pull/4701">PR #4701</a></li>
<li><strong>Gymnasium</strong> · The determinism check now compares the active random generators after reset. My regression test uses two seeded runs that return identical observations but consume randomness differently, a case the old check missed. <a href="https://github.com/Farama-Foundation/Gymnasium/pull/1705">PR #1705</a></li>
<li><strong>Microsoft Agent Lightning</strong> · I changed how the trainer aggregates a rollout’s token log probabilities. It now copies the source list before appending to it, so a second conversion retains those probabilities. My tests check that tokens stay aligned and both conversions produce identical tensors. <a href="https://github.com/microsoft/agent-lightning/pull/613">PR #613</a></li></ul>

<details><summary>Three more contributions · GEAR, Archify, PaperLens</summary>

<ul><li><strong>GEAR</strong> · I preserved the selected parent’s scope and scores when the optimizer passes it to the proposal stage. Regression tests cover saving and reloading that state in both GEPA and random search. <a href="https://github.com/rsi-gear/gear/pull/84">PR #84</a></li>
<li><strong>Archify</strong> · Applications can import the diagram compiler and keep their own error handlers. I moved global handler setup to diagram loading, so an unrelated exception no longer causes the compiler to terminate its host. All five CLI entry points retain their diagnostics. <a href="https://github.com/tt-a1i/archify/pull/418">PR #418</a></li>
<li><strong>PaperLens</strong> · Each Office-to-PDF conversion runs with its own LibreOffice profile. I made sure the child process exits if a request times out, the client disconnects, or the service shuts down. I tested all four supported Word and PowerPoint formats end to end on Windows. <a href="https://github.com/Peter-cuhk/PaperLens/pull/8">PR #8</a></li></ul>

</details>

## Experience

### MODE IO · AI R&D Engineering Intern

<em>Jul 2026–present · Shenzhen</em>

<ol><li><strong>vllm-jev · Multi-backend inference and validation.</strong> I added native Windows x64 CPU inference for <strong>24 decision-model checkpoints</strong> through a common CLI and HTTP API. The checkpoints need different loaders, precisions, and dependency versions. I grouped them into four isolated environments and matched each to its PyTorch or llama.cpp runtime. To check model behavior, I built a regression runner and compared outputs from real model weights with reference implementations. Upstream merged both the implementation and the validation tools. <a href="https://github.com/mode-io/vllm-jev/commit/3bdb350ea58838a388cbb6615509e417c4fab03d">My contribution</a> · <a href="https://github.com/mode-io/vllm-jev/blob/487ff7765a47e48b20fc2d48c14314fb28feaa51/docs/guide.md#windows-cpu-experimental">Windows guide</a></li>
<li><strong>modeio-integration-platform · Document redaction.</strong> I made asynchronous redaction jobs safe to retry. When users switch documents, a late preview can no longer overwrite the current one. Operators can trace each request through the account, API key, and job records I linked.</li>
<li><strong>modeio-hardware · Device reporting and Linux updates.</strong> Each usage figure in the reports I built comes from its scan snapshot. For Linux updates, I separated downloads from privileged installation and implemented atomic version switches that can roll back both the application and its data.</li>
<li><strong>skill-manager · Windows support.</strong> I led the native Windows x64 port so users could manage skills and run the service from a standard account. My changes handle locked files during updates and check the process identity before stopping the background service. <a href="https://github.com/mode-io/skill-manager/pull/54">Merged PR #54</a></li></ol>

### LEELEN · Test Engineering Intern

<em>May–Aug 2025 · Xiamen</em>

<p>I designed tests for remote device control and visitor registration, covering edge cases and failures across devices and network conditions. When results differed, I compared what the app showed with the API response and the device bindings stored in MySQL for that user. I automated recurring API checks with pytest and wrote Python tools to summarize regression logs.</p>

### COSCO Shipping Technology · University–industry project

<em>Jun–Aug 2026</em>

<p>I defined ten shipping metrics and built a prototype that answers questions about them. The language model interprets the question, and a validated query plan calculates the result. The prototype covered 171,958 historical port-efficiency records from 34 ports. Analysts comparing ports can see each aggregate’s definition, sample size, source, and cutoff date.</p>

## Selected Projects

<ul><li><strong>Skill Atlas</strong> · I built a local skill manager where users approve the exact files they reviewed. Before writing, it checks the source and destination again. It stages each update and restores the previous version if replacement fails. <a href="https://github.com/NaCr05/skill-atlas">Repository</a></li>
<li><strong>Project Preflight</strong> · I modeled project planning as a state machine that can resume between sessions. Before advancing, it checks the evidence and records the next action. A later session can pick up the decision and the reasoning behind it. <a href="https://github.com/NaCr05/project-preflight">Repository</a></li>
<li><strong>Mattermost AI Assignment Grader</strong> · My grading workflow keeps the model’s suggestion alongside the teacher’s edits and final decision. It checks feedback against a schema and uses version checks to prevent an older review from overwriting a newer one. <a href="https://github.com/NaCr05/mattermost-ai-assignment-grader">Repository</a></li>
<li><strong>Build Engineering Harness</strong> · I wrote this audit to trace conflicting repository instructions back to their sources. It identifies which rules CI can enforce and which need human review. I used it to prepare the grading platform for release. <a href="https://github.com/NaCr05/build-engineering-harness-skill">Repository</a></li></ul>

## Teaching

<p>At CUHK-Shenzhen, I lead weekly tutorials for <strong>Statistical Foundations for AI</strong> (Fall 2026). In Spring 2026, I taught weekly tutorials for <strong>Calculus II</strong>.</p>

## Tech Stack

<p><strong>Machine learning</strong> · Python, PyTorch, Diffusers, scikit-learn<br><strong>Applications and systems</strong> · TypeScript, React, Node.js, FastAPI, SQL, Docker</p>
