# Diversity, non discrimination and fairness
AI systems must be built:
- Through an inclusive design process, so that stakeholders directly or indirectly affected by the AI system can understand and trust it. Practically: stakeholder’s feedback along the design process as well as during the run phase is necessary.
- Towards a non-discriminatory usage, namely, it must not be reserved to a subgroup of the society/entity/organisation.

AI contributors must think carefully:
- When defining class labels and target variable. Poorly defining them might have an unwanted adverse impact on specific groups.
- Not to use training data (labelling examples) with a bias
- Not to use training data (data collection) with a biased sampling procedure
- Not to select specific features that might introduce a bias against certain groups
- Not to use proxies that might strongly correlate with protected characteristics
- Not to discriminate on purpose (for example: pregnant woman)

AI contributors must foster the creation of bias-free AI systems and give themselves the means to reasonably arbitrage between performance and fairness, through the use of proper frameworks. Example:
<ul>
    <li><i>Anticipate bias and question the risk of discrimination:
        <ul>
            <li><i>In the data used to train AI systems (origin, gender, age, characteristics related to the brand image, …). Bias might come from history, incompleteness and/or bad governance data models. Any identifiable and discriminatory bias should be removed as much as possible in the data collection phase.</i></li>
            <li><i>In the AI systems (eg. algorithm programming). Bias might come from poorly defined constraints, bad decisions, wrong requirements. This can be counteracted by putting in place oversight processes. [PLACEHOLDER FOR DEEP DIVE AND MORE DOC]</i></li>
        </ul> </i></li>
    <li><i>Quantify the risk of breach of fairness on identified sensitive populations, through the use of metrics, including but not limited to: statistical parity difference, equal opportunity difference, average odds difference, disparate impact, theil index </i></li>
    <li><i>Correct bias, through the use of algorithms, including but not limited to: reweighting, optimized pre-processing, adversarial debiasing, reject option based classification</i></li>
</ul>
Practically: AI Fairness 360 by IBM, ethicalai,


