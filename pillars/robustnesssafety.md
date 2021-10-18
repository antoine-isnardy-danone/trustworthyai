# Technical robustness and security

## Security

Artificial Intelligence is no exception when it comes to security: AI systems are exposed to a wide range of attacks. Consequently, AI contributors must be sensitised to Machine Learning security and enforce security audits, especially when humans are impacted by an AI system decision. Attacks lie among:

| Attack | Description | Defense |
| ------ | ------ | ------|
| Data poisoning | Malicious individuals access data they're not authorized to and alter them before an AI system training (in the case of a credit score e.g., change the target from "deny" to "accept" for a certain subset of the population) | <ul><li><b>Disparate impact analysis</b> to study positive or negative discriminations (see the non discrimination section)</li><li><b>RONI</b>: reject on negative impact. Remove any individual from the training set that would make the accuracy abnormally decrease</li><li><b>Self reflection</b>: look for abnormal beneficial predictions</li></ul> |
| Backdoors and watermarks| Code of an AI system is compromised by malicious individuals so that water-marked data can lead the faulty AI system to produce desired outcome (if the AI system is a decision tree e.g., add a faulty leaf that would output a compromised decision) |<ul><li><b>Version control</b>: AI system code must be versioned through a version control tool, most likely Git</li><li><b>Data integrity constraints</b> not to allow unrealistic combinations of data</li></ul>|
| Surrogate model inversion | If an AI system is served through an API, malicious individuals can simulate data, query the API and receive predictions from the AI system, and in turn build a surrogate model that could: <ul><li>Expose the business logic</li><li>Reveal sensitive information regarding the data that were used to train the AI system</li><li>Facilitate a membership inference attack</li><li>Facilitate production of adversarial examples</li></ul> | <ul><li><b>Authentication</b>: authenticate API users, or more generally any endpoint that would give access to the AI system predictions</li><li><b>Throttling</b>: decrease response time of the API so that malicious individuals can only access a limited number of predictions</li><li><b>White-hat surrogate</b>: act as a hacker and train a surrogate model to collect learnings about what malicious individuals could have access to</li></ul> |
| Membership inference | If an AI system is served through an API, malicious individuals could know if an individual / a row was present in the training dataset, and in turn violate individual or group privacy, by:<ul><li>Training a surrogate model (see above)</li><li>Simulating new data points and scoring them with the surrogate model</li><li>Training a new model that discriminates between data points present in the training set or not</li></ul>|<ul><li>Above defense</li><li><b>Prediction monitoring</b>: monitor data used to query the API and check similarity with training data</li></ul>|
| Adversarial example | If an AI system is served through an API, malicious individuals can simulate data, query the API, get predictions and in turn learn how to trick the AI system to receive a desired outcome | <ul><li>Above defense</li><li><b>White-hat sensitivity analysis</b>: try to trick the AI system with different input values</li></ul> |

Source: [H20AI](https://github.com/h2oai/ml-security-audits)

## Development robustness

AI contributors must comply with development standards to ease reliability, readability of procedures and handovers.

Practically, enforce development best practices, that lie among:

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
    :width: 60%
    :align: center

.. image:: ./_static/robustnesssafety_2.png
    :width: 60%
    :align: center

.. image:: ./_static/robustnesssafety_3.png
    :width: 60%
    :align: center

-