# Interactions between AI decision support systems and human JDM

Matthew Radovan

## Decision support systems

Decision support systems are defined as the inclusion of computerized
algorithms in the human decision making process for more optimal
decision outcomes. Research
on this class of software has existed since the 70s, with one such
example being ONCOCIN, a system designed in the late 1970s and early
1980s to provide advice on patient treatment post cancer diagnosis
(Shortliffe, 1986). Typical
of traditional decision support systems, ONCOCIN was based on a set of
encoded rules that interacted with its manually designed knowledge
base. Although these rules
were explicit, they were hidden from the end user and integrated into
the user’s existing workflow to not create any additional overhead in
the workflow - ONCOCIN had the appearance of a digitized paper
management tool that just happened to provide filled-in suggestions (as
opposed to commands).

## The Rise of Deep Learning AI

However, the decision support system paradigm has undergone major shifts
within the past decade, in part due to the rise of deep neural networks
for AI. Traditional
approaches to AI have been around for decades; however, the rise of deep
neural networks has made modern AI nearly synonymous with deep neural
networks (and, for convenience, deep neural networks will be what the
term “AI” refers to going forward in this chapter). Rather than having manually
designed rules and knowledge bases, neural networks are typically
trained on a large set of examples to achieve the highest accuracy
relative to the ground truth (as in supervised learning) or greatest
“reward” (as in reinforcement learning). These neural networks have
significantly more predictive power than previous approaches - in fact,
some models have proven to outperform humans.< Despite their power, the impact
of AI suggestions on the human decision-making process has only been
studied recently due to the relatively recent rise of AI in
general. Integration-wise,
it’s fully possible for AI-based decision support systems to fit into
workflows the same way traditional decision support systems have.

Unlike traditional decision support systems with their explicitly
encoded rules and knowledge bases, AI is typically a black box unless
explicitly designed otherwise. That is, AI models are often not interpretable: they take an
input and produce an output, but it is often very difficult to
understand exactly why the system makes the suggestion that it does,
even if the model’s parameters are presented to the user. Although difficult, explainable
AI is not impossible, and the ways to provide interpretability to AI
models can be characterized into two axes: global versus local and
model-specific versus model-agnostic (Wang and Yin, 2021). Global explanations try to
explain the overall model’s behavior, such as the intermediate features
a neural network may find and how the network learns those
features. Local
explanations, on the other hand, take a given model prediction and
explain why the model returned that specific prediction, such as
specific features that the model used to determine its output. Orthogonally to local and global
explanations, model-specific explanations focus on explaining the model
itself, while model-agnostic explanations focus on specific features and
examples to explain why models behave the way they do.

Despite AI being less explainable than previous decision support
systems, AI models have significantly stronger predictive power than
traditional systems. As a
result, AI models have been applied across a wide variety of situations
to great success, which can be characterized by the user type (expert
vs. non-expert) and implementation type (suggestion vs. control). One such AI system is WRDensity,
an FDA-approved system that supports (i.e. suggests) radiologists
(expert users) when analyzing mammogram density. Another, more common example is
Tesla’s autopilot, which takes full control of the car regardless of the
(non-expert) human’s driving experience. In these cases of full AI
control, the human is relegated to a monitor, making decisions about
whether the AI is performing correctly rather than making each decision
jointly with the AI. Although this does seem to remove autonomy from the human, the AI
systems that have full control have significant advantages - AI can
ingest significantly more data, and process it significantly faster than
humans can, making the control paradigm a reasonable solution for real
time situations such as driving. In fact, as AI support systems continue to gain traction, Panch,
Szolovits, and Atun (2018) have proposed that humans will switch from
decision-maker into an “information specialist”, in which the human
will, in most cases, monitor and act on the suggestions given by the AI
rather than make the decision itself.

## Impact of AI

As previously mentioned, the processes and outcomes of decisions made by
the combination of AI and human - joint decisions - have only been
studied relatively recently due to the relative newness of AI. Although AI-only decisions often
have higher accuracy than human-only decisions, joint decisions can
increase the accuracy of outcomes over both human-only and AI-only
decisions when humans use the suggestions of AI to augment their own
decision-making processes. As such, humans may use the AI prediction as evidence for their
own final decision. For
instance, pathologists making a decision jointly with AI, by considering
the AI suggestion as part of their decision, have been shown to have
higher accuracy than either the pathologists or the AI alone (Wang et
al., 2016).

As in typical decision-making, a number of cognitive biases exist within
the joint decision processes. One such example is Rastogi et al. (2020), who specifically
discuss anchoring bias in joint decisions. This bias occurs when the AI
model’s prediction is presented and becomes the “anchor” for the human’s
decision-making process, causing the human to make a final decision too
close to the AI’s initial anchor. However, although they exist in joint decisions, these cognitive
biases are not unique to joint decisions.

On the other hand, the differing strengths and weaknesses of humans and
AI models are unique to joint decisions. Because of these differences,
it’s generally optimal for the human to rely on the AI when the AI is
likely to be correct, while having the human rely on their own judgment
when the AI is likely to be incorrect. Therefore, in joint decisions,
humans make an additional decision: beyond the decision that the human
comes to independently, the human must then decide whether to use their
own decision or the AI’s decision based on whether they think the AI is
correct. And, if the human
believes the AI to be incorrect, the human then uses their own knowledge
to make the final decision, similarly to the idea of humans acting as a
“monitor” for the AI’s decisions. The creation of a function to determine when to use the AI’s
decision, whether in the form of a heuristic or otherwise, is known as
trust calibration.

These functions, also known as mental models of the AI, are learned over
time as the human interacts with the AI and receives feedback after
executing the chosen decision (Bansal et al., 2019). However, they’re generally based
on heuristics rather than “fully rational” decisions (Buçinca et al.,
2021), and can become flawed in a number of ways. In some cases, developing a
mental model of features that are not the same set of those used by the
AI (i.e. a “representation mismatch”) can cause humans to misjudge when
the AI is correct or incorrect. Additionally, the more consistently the AI makes erroneous
suggestions, the more accurate the human’s mental model can be;
inversely, unpredictable AI errors cause the human mental models to
become less accurate.

Beyond these characteristics of trust calibration models, the effects of
improper trust calibrations can be characterized in two overall ways:
overreliance and underreliance (Zhang et al., 2020). Overreliance is a common problem
in joint decisions where the human puts too much trust in the AI’s
suggestion, such as directly using the AI’s suggestion without
considering the possibility that the AI’s suggestion is incorrect. On the other hand, underreliance
is the case in which the human pays too little attention to the AI’s
suggestion (e.g. a radiologist not using an AI that highlights areas of
concern in a scan), often after the human observes the AI make mistakes.

## Designing AI

One method to improve humans’ trust calibration is to expose the
confidence levels of AI’s predictions to the human. However, unlike confidence scores for 
models such as simple linear regression, confidence levels in deep
learning must be explicitly built in, especially when considering the
variety of outputs AI may produce (e.g. single values, probability
distributions over categories, heatmaps). Displaying these levels has been
shown to improve humans’ trust calibration (Zhang et al., 2020), but
confidence levels alone may not be sufficient to correct for the AI’s
errors when the human judges that the AI has made an incorrect
prediction. In this case,
the authors suggest that the human must have some distinct set of
knowledge from the AI in order to correct for the AI’s error.

Explainable models have also been shown to increase trust
calibration. Recalling the
two axes of explainability discussed previously, Wang and Yin (2021)
have shown that explainable models tend to improve trust calibration
when the human is knowledgeable (i.e. an “expert”) in the problem
domain, but have little to no effect when the human is a
non-expert. In the case
where the human is an expert, providing contrasting examples (e.g. “if
we had a slightly different input X, then the model would have made this
other prediction Y”) does not help, which may be counterintuitive given
that humans often use this approach to explain their decisions to each
other (Miller, 2019). On the
other hand, quantifying how much each input feature contributed to the
final model prediction did improve trust calibration for expert humans
in Wang and Yin’s study.

Besides improper trust calibration, the other major issue with AI
support systems discussed is overreliance on AI (although this may be
considered an extreme form of improper trust calibration). Because humans tend to use
heuristics for their decisions on whether to trust an AI prediction
(Buçinca et al., 2021), one approach that has been shown to mitigate
overreliance is cognitive forcing, through two approaches: the AI
suggestion is visible to the human only after the human makes an initial
decision, or the human is not allowed to make a final decision until a
certain time after. In both
cases, the heuristic used to determine whether the AI should be relied
on is disrupted, forcing further cognition in the decision making
process. The latter approach
also was shown to disrupt anchoring bias (Rastogi et al., 2020). These cognitive forcing
techniques reduced overreliance even more so than the explanations used
in the study, despite not eliminating the issue. Additionally, the joint decision
outcomes did not improve despite overreliance decreasing, likely due to
the fact that the AI alone had a higher accuracy than the joint decision
outcomes.

  
## Conclusions

Artificial intelligence-based decision support systems have largely been
the focus of decision support systems in the past few years. In contrast to traditional
decision support systems, AI systems have significantly more predictive
power (such as much higher accuracy) and can be applied across a much
wider range of problems. However, AI suggestions often become the “anchor” for anchoring
bias. Additionally, most AI
models are difficult to explain, and as such, it can be difficult for
human decision makers to determine when to trust their AI support
systems. Research into
avoiding cognitive biases and improving trust calibration in AI support
systems is in its infancy due to the relative newness of neural
network-based AI, and designing AI to be part of an effective decision
support system continues to be an open problem.

## References

Bansal, G., B. Nushi, E. Kamar, W. S. Lasecki, D. S. Weld, and E.
Horvitz. “Beyond Accuracy: The Role of Mental Models in Human-AI Team
Performance”. Proceedings of the AAAI Conference on Human Computation
and Crowdsourcing, vol. 7, no. 1, Oct. 2019, pp. 2-11, [<span
class="s1">https://ojs.aaai.org/index.php/HCOMP/article/view/5285</span>](https://ojs.aaai.org/index.php/HCOMP/article/view/5285).

“Breast Cancer AI Company Whiterabbit Receives FDA Clearance for
WRDensity.” Imaging Technology News, 11 May 2021, [<span
class="s1">https://www.itnonline.com/content/breast-cancer-ai-company-whiterabbit-receives-fda-clearance-wrdensity</span>](https://www.itnonline.com/content/breast-cancer-ai-company-whiterabbit-receives-fda-clearance-wrdensity).

Buçinca, Zana, et al. “To Trust or to Think: Cognitive Forcing Functions
Can Reduce Overreliance on AI in AI-Assisted Decision-Making.”
Proceedings of the ACM on Human-Computer Interaction, vol. 5, no. CSCW1,
Apr. 2021, p. 188:1-188:21. April 2021, doi:10.1145/3449287.

Panch, Trishan et al. “Artificial intelligence, machine learning and
health systems.” Journal of global health vol. 8,2 (2018): 020303.
doi:10.7189/jogh.08.020303

Rastogi, Charvi, et al. “Deciding Fast and Slow: The Role of Cognitive
Biases in AI-Assisted Decision-Making.” ArXiv:2010.07938 \[Cs\], Oct.
1.    arXiv.org, [<span
class="s1">http://arxiv.org/abs/2010.07938</span>](http://arxiv.org/abs/2010.07938).

Shortliffe, E H. “Medical expert systems--knowledge tools for
physicians.” The Western journal of medicine vol. 145,6 (1986): 830-9.

Tim Miller. “Explanation in artificial intelligence: Insights from the
social sciences.” Artificial Intelligence 267, p. 1–38. 2019.

Wang, Dayong, et al. “Deep Learning for Identifying Metastatic Breast
Cancer.” ArXiv:1606.05718 \[Cs, q-Bio\], June 2016. arXiv.org, [<span
class="s1">http://arxiv.org/abs/1606.05718</span>](http://arxiv.org/abs/1606.05718).

Wang, Xinru, and Ming Yin. “Are Explanations Helpful? A Comparative
Study of the Effects of Explanations in AI-Assisted Decision-Making.”
26th International Conference on Intelligent User Interfaces,
Association for Computing Machinery, 2021, pp. 318–28. ACM Digital
Library, doi:10.1145/3397481.3450650.

Zerilli, J., Knott, A., Maclaurin, J. et al. “Algorithmic
Decision-Making and the Control Problem.” Minds & Machines 29, 2019, pp.
555–578. [<span
class="s1">https://doi.org/10.1007/s11023-019-09513-7</span>](https://doi.org/10.1007/s11023-019-09513-7)

Zhang, Yunfeng, et al. “Effect of Confidence and Explanation on Accuracy
and Trust Calibration in AI-Assisted Decision Making.” Proceedings of
the 2020 Conference on Fairness, Accountability, and Transparency, Jan.
2020, pp. 295–305. arXiv.org, doi:10.1145/3351095.3372852.
