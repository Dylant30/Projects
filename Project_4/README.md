# West Nile Virus

Contributing members: Dylan, Ming Fang, Samuel, Alan from DSI 12

## Problem Statement

We are a team of data scientist and business analysts from DSI Vector Control. In this project, we will be investigating West Nile Virus(WNV) and predicting the presence of WNV in respective trap locations. In addition, we have also conducted a [cost benefit analysis](https://github.com/alantancr/project4/blob/master/documents/Cost%20Benefit%20Analysis%20of%20Aerial%20Spraying.pdf) proposal to demostrate the importance of mosquitoes control and its benefits in terms of cost.

## Executive Summary

We have performed modelling with ExtraTrees, Random Forest, Support Vector Machine and XGBoost classifier. Through this modelling process, we have scored the performance of the various models on Kaggle. Based on the highest ROC-AUC score, we have selected ExtraTrees Classifier as our model.



|                            | ExtraTrees | Random Forest | XGBoost |  SVM  |
| :------------------------: | :--------: | :-----------: | :-----: | :---: |
|       ROC-AUC Score        |   0.745    |     0.737     |  0.724  | 0.715 |
| Performance on Unseen Data |   0.687    |     0.669     |  0.683  | 0.642 |

## Process

1. Exploratory Data Analysis /Featuring Engineering (Train, Test)
2. Exploratory Data Analysis /Featuring Engineering (Weather)
3. Modelling
4. Model Evaluation
5. Conclusion
6. Cost-Benefit Analysis



## Limitation & Recommendation



Spray data provided were bounded to 2011 and 2013.  The evaluation of spray effectiveness are constraint due to limited dates.



## Conclusion

Based on our study, we had a reasonable prediction of WNV presence by trap. By performing cost-benefit analysis, we uncovered the estimated cost for spray versus medical cost and productivity loss in the public. Asides that, West Nile Virus is not the only disease which mosquitoes carries. We encourage that public needs to be aware of other diseases which mosquitoes carries and its health threats



## Data Dictionary



[Data dictionary](https://github.com/alantancr/project4/blob/master/documents/noaa_weather_qclcd_documentation.pdf)



