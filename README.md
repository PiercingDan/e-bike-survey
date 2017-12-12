# City of Toronto e-bike Survey

Machine learning on the [City of Toronto e-bike survey](https://www1.toronto.ca/wps/portal/contentonly?vgnextoid=b3fc9ba6aa360410VgnVCM10000071d60f89RCRD&vgnextchannel=7807e03bb8d1e310VgnVCM10000071d60f89RCRD).

### Questions to Consider

**Which models did we consider? Which Model did we choose and why? How good was it?**

We considered ensemble CART methods: Random Forest and XGBoost, for their ability to make decisions on categorical variables. Our dataset was nearly all categorical variables. The accuracy was not that much better than the baseline model, but it did allow us to gain predictive ability on 'No' classes.

**What was the pattern of missing values? Was it random? Could those be inferred from the context?**

It seems some people understandably declined to answer their household income and a few declined to answer their sex. To infer them from the context, you could build a simple predictor on the rest of the values to fill these missing values or fill them with the median/mode values. Or you may simply leave them as is (there are not many null values).

**Which features were significant in predicting the target response?**

From our feature importance graphs in our Random Forest modelling, the 3 most important features were:

* Which transportation option do you end up using most often?
* What is your household income?
* Timestamp

We saw these features again arise in the XGBoost OHE model. It makes sense that your most commonly used transportation option and your household income could indicate whether your household has access to private motorized vehicles.

Strangely, the timestamp also is a fairly important feature. This may be correlated to the waves of discovery of the survey by different groups of people, but it is not clear without further investigation.

**If we could re-design the survey for next year, what question(s) would we add or remove in order to improve the precision of the prediction?**

First, we should attempt to limit users giving unique answers, as they prove difficult to deal with. Many survey-takers answered with unique responses that were similar to each other, or an existing answer (e.g. 'car' vs 'Car').

Questions that prove important in predicting access to a private motorized vehicle include:

* *How concerned are you about the effects of global warming?* A question like this may indicate enviro-conscious responders.
* *How long have you stayed in Toronto?/How long you plan to stay in Toronto?* This question allows us to distinguish short-term vs. long-term residents, the latter being more likely to own a private vehicle.
