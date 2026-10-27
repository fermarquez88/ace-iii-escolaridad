# Education-adjusted ACE-III calculator

A single-file web calculator that shows the expected total score on the Addenbrooke's Cognitive Examination III (ACE-III) [1] for a given number of years of education and age, with a reference table and a cohort simulator. It reads the same score in two ways side by side. The first is the two-step rule used in everyday practice in Argentina (a cut-off of 86 points from 12 years of education and 68 below). The second is a continuous model that places each person against the 5th percentile of people with the same education and age.

The page is published at https://fermarquez88.github.io/ace-iii-escolaridad/. It opens in English and has a button to switch to Spanish.

## Status

This is a research prototype and a methodological demonstration. The values are illustrative, not population norms, and the tool is not a medical device. It does not diagnose, it does not replace clinical assessment, and it must not be used to make decisions about an individual patient. The full analysis behind it is being prepared for peer review. The coefficients shown here are provisional and will be superseded by the published normative study.

## Where the reference values come from

The model was fitted to 342 community-dwelling adults assessed by Neuromentia, the community screening program led by Dr. Martín Bruno, CONICET researcher and director of the Instituto de Ciencias Biomédicas (ICBM) of the Universidad Católica de Cuyo, with the Instituto de Investigaciones en Psicología Básica y Aplicada (IIPBA) and Fundación Alzheimer San Juan. The program holds the data, and nothing leaves it.

Participants were classified as controls by a criterion independent of the ACE-III. They had a word-list recognition score of 10 or more, no history of stroke or head trauma, and independence in basic activities of daily living. The criterion shows no educational gradient (chi-square p = 0.504). Even so, the control group may include people with undetected mild impairment, which would make the 5th percentile a lenient threshold. Most controls are between 50 and 80 years old, and data are sparse below 3 years of education. Education is displayed from 0 to 20 years; the six controls with more than 20 years are counted in the 18 to 20 band.

## What the repository contains, and what it does not

- `index.html` is the whole application. There is no server, no build step and no external resource, so the page works offline. Nothing typed into it is sent or stored anywhere; the browser only remembers the chosen language and theme.
- The page embeds aggregate model coefficients (one regression for the expected score and one for its dispersion) and banded counts of controls by years of education, which the simulator uses to draw a cohort.
- It contains no participant-level data. Counts are grouped so that no band has fewer than five controls, and observed age extremes are not published.
- It contains no ACE-III items, forms or scoring materials. The ACE-III is distributed by its authors [1]. The Spanish-language version used in Argentina was validated by Bruno and colleagues [2].

## How the model was estimated

The expected score is an ordinary least squares regression of the ACE-III total on years of education, its square, age and sex. Dispersion is modelled separately, as a regression of the log squared residuals on education and age, so that variability can change with education; that second step carries Harvey's correction for its downward bias [3]. Within the sample, 5.8% of controls fall below the model's nominal 5th percentile. A beta-binomial model, used as a robustness check, places 5.6% below it under cross-validation. On load, the page runs a small self-test against reference values computed independently in Python.

## About the two-step rule

The two-step rule shown on the page is the way the ACE-III is read in practice. It combines cut-offs from different validation studies, neither of which proposed the combined rule. The page does not judge those studies. It only shows where each cut-off falls relative to what is expected for a given education and age.

## Authorship and credit

Developed by Fernando Márquez, neurologist, Memory and Brain Health Unit, Hospital Dr. Guillermo Rawson, San Juan, Argentina. Published with the agreement of Dr. Diana Bruno, who led the Argentine-Chilean validation of the ACE-III [2]. The reference data belong to the Neuromentia program of Dr. Martín Bruno's team, as described above. The analysis of cut-offs that motivated the tool is the work of a team from the hospital and the university, and it will be reported with its authors once it has been peer reviewed.

## Ethics and data governance

This repository publishes only aggregate quantities derived from the program's data, with small-cell suppression. No new data were collected for the tool, and no participant can be identified from what is published here. Ethical oversight of the screening program rests with the institutions that run it.

## Running it locally

Download `index.html` and open it in any modern browser. No installation is needed.

## How to cite

Márquez F. Education-adjusted ACE-III calculator: a research prototype [software]. San Juan, Argentina; 2026. Available from: https://fermarquez88.github.io/ace-iii-escolaridad/

A `CITATION.cff` file is included so that GitHub offers the citation from the repository page.

## License

The code is released under the MIT License. Text, figures and tables are released under the Creative Commons Attribution 4.0 International license (CC BY 4.0).

## References

1. Hsieh S, Schubert S, Hoon C, Mioshi E, Hodges JR. Validation of the Addenbrooke's Cognitive Examination III in frontotemporal dementia and Alzheimer's disease. Dement Geriatr Cogn Disord. 2013;36(3-4):242-50. doi: [10.1159/000351671](https://doi.org/10.1159/000351671)
2. Bruno D, Slachevsky A, Fiorentino N, Rueda DS, Bruno G, Tagle AR, et al. Validación argentino-chilena de la versión en español del test Addenbrooke's Cognitive Examination III para el diagnóstico de demencia. Neurología. 2020;35(2):82-8. doi: [10.1016/j.nrl.2017.06.004](https://doi.org/10.1016/j.nrl.2017.06.004)
3. Harvey AC. Estimating regression models with multiplicative heteroscedasticity. Econometrica. 1976;44(3):461-5. doi: [10.2307/1913974](https://doi.org/10.2307/1913974)

---

Calculadora del ACE-III ajustada por escolaridad. Prototipo de investigación con valores ilustrativos, no normas poblacionales; no debe usarse para decidir sobre un paciente. La página tiene un botón para pasar al español.
