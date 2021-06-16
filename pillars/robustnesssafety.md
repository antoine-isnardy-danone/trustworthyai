# Technical robustness and security

## Risk & criticality

AI contributors must evaluate the risk and criticality of an AI system before starting to implement it, namely during ideation phases, among following risks:

- **Unacceptable Risk**: the AI system must be banned
- **High Risk**: the AI system must comply with regulation enforcements (see recommendations below)
- **Limited Risk**: the AI system must be transparent for the user
- **Minimal Risk**: the AI system is not subject to regulation

<details>
    <summary>Definitions (click to unfold)</summary>

Directly quoted from <a href="https://ec.europa.eu/commission/presscorner/detail/en/IP_21_1682">ec.europa.eu</a>

<ul>
  <li><b>Unacceptable risk</b>: <i>AI systems considered a clear threat to the safety, livelihoods and rights of people [...]. This includes AI systems or applications that manipulate human behaviour to circumvent users' free will (e.g. toys using voice assistance encouraging dangerous behaviour of minors) and systems that allow ‘social scoring' by governments.</i></li>
  <li><b>High-risk AI systems include</b>:
    <ul>
      <li><i>Critical infrastructures (e.g. transport), that could put the life and health of citizens at risk</i></li>
      <li><i>Educational or vocational training, that may determine the access to education and professional course of someone's life (e.g. scoring of exams); safety components of products (e.g. AI application in robot-assisted surgery)</i></li>
      <li><i>Employment, workers management and access to self-employment (e.g. CV-sorting software for recruitment procedures);</i></li>
      <li><i>Essential private and public services (e.g. credit scoring denying citizens opportunity to obtain a loan);</i></li>
      <li><i>Law enforcement that may interfere with people's fundamental rights (e.g. evaluation of the reliability of evidence)</i></li>
      <li><i>Migration, asylum and border control management (e.g. verification of authenticity of travel documents);</i></li>
      <li><i>Administration of justice and democratic processes (e.g. applying the law to a concrete set of facts)</i></li>
    </ul>
  <li><b>Limited risk</b><i> - AI system with transparency obligations: When using AI systems such as chatbots, users should be aware that they are interacting with a machine so they can take an informed decision to continue or step back.</i></li>
  <li><b>Minimal risk</b><i>: the legal proposal allows the free use of applications such as AI-enabled video games or spam filters. The vast majority of AI systems fall into this category. The draft Regulation does not intervene here, as these AI systems represent only minimal or no risk for citizens' rights or safety.</i></li>
</ul>
</details>

## Security

AI contributors must be sensitised to Machine Learning security, especially when working on sensitive applications.[PLACEHOLDER FOR DOCUMENTATION]

## Development robustness

AI contributors must comply with development standards to ease reliability, readability of procedures and handovers.

Practically, enforce [Danone's Data Science best practices](https://github.com/danone/daai.data-science-best-practices) that lie among:

- Code documentation

- Unit tests

- Data tests

- Pipeline tests

- Code reviews

- Use of linter

- Use of formatters

## Data project lifecycle safety

| Project phase  | Guideline  | Practical consequences  |
|---|---|---|
| Data collection & preprocessing  | AI contributors must account for potential biases and not introduce additional ones while preprocessing data and/or imputing missing values, leveraging data augmentation, …  |<ul><li>Deeply understand the business process behind the data generation process, thanks to extensive discussion with business partners:<ul><li><b>When</b> was the data collected? (One-shot vs long period, ...)</li><li><b>Who</b> collected the data? (General-purpose team vs task-specific team)</li><li><b>What</b> was targeted? (Precise subset vs random set, is the dataset representative of the the challenge that is being tackled?)</li><li><b>How</b> was the data collected? (Manually, sensors, ...)</li></ul><li>Conduct descriptive analysis (univariate analysis, multivariate analysis, statistical testing)</li><li>Document treatments</li><li>Prevent from adding unlawful or illegitimate features (example: sex for a granting score, …)</li> |
| AI system training  | While training AI models, AI contributors must carefully understand model’s underlying mechanisms, carefully calibrate them, and carefully analyze results  | <ul><li>Not only compute a single aggregated performance metrics (<a href="https://en.wikipedia.org/wiki/Coefficient_of_determination">R2</a>, <a href="https://en.wikipedia.org/wiki/Precision_and_recall">precision</a>, <a href="https://en.wikipedia.org/wiki/Precision_and_recall">recall</a>, <a href="https://en.wikipedia.org/wiki/Precision_and_recall">accuracy</a>, or any other <a href="https://scikit-learn.org/stable/modules/model_evaluation.html">model evaluation metrics</a>…), but also carefully analyze result’s dispersion, and focus on large errors. For instance, while doing forecast, not only quantitatively refer to <a href="https://en.wikipedia.org/wiki/Root-mean-square_deviation">RMSE</a> / <a href="https://en.wikipedia.org/wiki/Mean_absolute_percentage_error">MAPE</a> / <a href="https://en.wikipedia.org/wiki/Symmetric_mean_absolute_percentage_error">SMAPE</a> / …, but also to qualitative measurements or representations like predictions vs reality</li><li>Leverage uncertainty for predictions. Examples: <a href="https://facebook.github.io/prophet/docs/quick_start.html">Prophet</a>, <a href="https://github.com/simai-ml/MAPIE/tree/master/mapie">MAPIE</a>, <a href="https://docs.pymc.io/">pyMC3</a></li></ul> |
| AI system industrialisation |  While industrialising AI models, AI contributors must ensure AI system's sustainability | <ul><li>Question generalization: whether training data are a relevant proxy of what is likely to happen while predicting with the trained model on new data</li><li>Implement reproducibility so that tracing back the root cause of anomalies is feasible. One solution: <a href="https://mlflow.org/">MLFlow</a></li><li>Implement feedback loops to detect / anticipate / prevent drifts in the data, to prevent new bias in the data, model’s loss of performance, through the use of monitoring metrics</li><li>Implement fallback plans to prevent damages. Examples: alerting, switch from statistical to rule-based procedures</li></ul>|


## Appendix - Recommendations from the EU
Below are the recommendations directly reported from [EU](https://digital-strategy.ec.europa.eu/en/library/ethics-guidelines-trustworthy-ai).

.. image:: ./_static/robustnesssafety_1.png

.. image:: ./_static/robustnesssafety_2.png

.. image:: ./_static/robustnesssafety_3.png