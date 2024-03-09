# Lead-Conversion-Supervized-Learning (Python)

The [_Applied Data Science Program: Leveraging AI for Effective Decision-Making_](https://professional.mit.edu/course-catalog/applied-data-science-program-leveraging-ai-effective-decision-making)  is an intensive program covering courses of supervised and unsupervised learning, neural networks, graphs, decision trees, generative AI and recommendation systems focusing on theory, Python coding and application to different industries. It is taught by MIT professors, Munther Dahleh, Caroline Uhler, John N. Tsitsiklis, Stefanie Jegelka and Devavrat Shah. This GitHub repository consolidates my final Python script and main conclusions presented below that I submitted in the final step of the 5-month program, the _Elective project_.  

[Click here to check the Python script](https://github.com/pacifiq-hub/Lead-Conversion-Supervized-Learning-Python/blob/main/Elective_Project_ExtraaLearn_Practical_DS.ipynb) 

## ![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) Problem Statement 

The online education sector has witnessed rapid growth and is attracting a lot of new customers. Due to this rapid growth, many new companies have emerged in this industry. With the availability and ease of use of digital marketing resources, companies can reach out to a wider audience with their offerings. The customers who show interest in these offerings are termed as leads. There are various sources of obtaining leads for Edtech companies, like:

- The customer interacts with the marketing front on social media or other online platforms.
- The customer browses the website/app and downloads the brochure.
- The customer connects through emails for more information.

The company then nurtures these leads and tries to convert them to paid customers. For this, the representative from the organization connects with the lead on call or through email to share further details. With a large number of leads being generated on a regular basis, one of the issues faced by ExtraaLearn is to identify which of the leads are more likely to convert so that they can allocate the resources accordingly.

## ![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) Objective

- Analyze and build an ML model to help identify which leads are more likely to convert to paid customers.
- Find the factors driving the lead conversion process.
- Create a profile of the leads who are likely to convert.

## ![#1589F0](https://placehold.co/15x15/1589F0/1589F0.png) Proposed final solution

**_Final Decision Tree model:_** 
<br/><br/>

![image](https://github.com/pacifiq-hub/Lead-Conversion-Prediction-Supervized-Learning/assets/46910395/c4a7798a-7533-40c5-8fd3-d81962f89e15)

<br/><br/>


**_And its features of importance:_** 
<br/><br/>

 ![image](https://github.com/pacifiq-hub/Lead-Conversion-Prediction-Supervized-Learning/assets/46910395/70662709-b73f-4f3c-bb95-f96093436b83)

<br/><br/>

- This decision tree is very understandable and easy to interpret. The first node separates leads who basically first interacted with the website vs. others that interacted with the phone. We saw in the EDA that this variable seemed to impact the outcome of our leads converting or not, this is confirmed here.
- We also see that the left part of the tree which are basically leads that first interacted on the phone shows many more churners nodes (red color) than the right part (blue color).
- The initial sample is 3228 which corresponds to our train dataset, and is equally represented with 682 leads that will churn, and 668.5 that will convert. Note this is a result of the weighting that increased the weight of our converted leads that are under-represented in this dataset (if we were to show the non-weighted tree, we would have a much bigger proportion of churners in that first node, and also no decimals)
W- e then go to the next node seeing the next range of features chosen, and so on. The colors tell us about the categories, and how we end up getting to purer subsets of population. purer standing for homogeneous.

<br/><br/>
#

**_Comments on alternative Random Forest model tried:_** 

<br/><br/>

- The random forest model yielded a good overall performance in its tuned version. We yielded 77% f-1 score on the converted class, and a balanced recall and precision score at respectively 77% and 76%.
- Overall the tuned random forest model improved the f-1 score by 1 pts, but we consistently reduced our recall and improved our precision. The tuned random forest is more balanced between miss-classifying false negatives and false positives.
- For equivalent f-1 scores at just 1 pt difference, I would rather have a model that predicts my converted leads in a version that reduces the number of false negatives. That is our first single decision tree model. Random forest models are also more heavy computationally as they require calculating multiple models which weights on my decision too. Our tuned random forest took significantly more time to run vs. the tuned decision tree.
- Only concerns we can have with a single decision tree is that it could have overfitted our training dataset and we could have been lucky applying it to the current relativelly small test dataset and yielding good performance results, so it will be worth monitoring the consistency of this performance as we grow our population of leads.

## ![#1589F0](https://placehold.co/15x15/1589F0/1589F0.png) Refined insights

1. we built a **classifier model that can help ExtraaLearn predict if our customers will be churners or converted customers with an f-1 score of 77% and a recall of 87%**.

> This means that out of all leads that will convert into paying customers, which will bring revenue to our company, our model will have detected close to 9 out of ten correctly. The downside of our choice to focus on recall and f-1 score is that we may classify wrongly some leads as future converters when they will actually churn. At least we're not missing on revenue opportunities. As we grow our database of leads, we hope we can improve the overall f-1 score and precision at above 80%.

2. we saw that the **time spent on the website is the most important factor in getting our leads to convert.** This is not surprising, when the customer takes the time to read the content on our website, it does show a higher interest on our programs and therefore increases chance of conversion.

3. The **website channel is also our strong channel that helps converting our leads**.

> The organization should keep working on their website, improving its content, adding more videos and comments from previous alumni. As a result we also saw that the mobile experience is very bad, and absolutely needs to be improved as it accounts for half the traffic.

4. **Our program mostly appeals to older people (not retired though), that are either working professionals or unemployed**.

> This should really help shape ExtraaLearn's strategy in the future. Either by solely targeting these individuals and become more of a niche education product, or by deciding to expand our attractiveness to students by adding more programs.

5. **Profile completion matters, when we get a fully completed profile vs. medium we do increase our chances of converting our leads**.

> ExtraaLearn should put a strategy in place to ensure we get all our customers to fully complete their profile.

6. **The channel of interaction of our customer service team is also a factor of conversion but at a lesser degree than the previously mentioned features**. The written channels such as email and chat do contribute to a higher conversion rate. The phone is not as good of a factor for conversion rate.

> I would do a follow-up analysis with the customer service team to understand how we can improve the phone channel experience to ultimately improve conversion rate.

7. **Our media strategy so far has not been successful.** The amount of leads targeted is too small at below 10%, and when targeted we couldn't see a real improvement in the conversion rate vs. non targeted leads. In the model, media variables convey the same results, they're not important factors in the conversion prediction.

> We saw a potential quick win idea, that would consist in combining these media campaigns. Improving the media strategy is key here as a way to continue improving our conversion rate.

8. **Our EDA showed potential data quality issues that I would absolutely question with the data team** in charge of collecting this dataset. If the data is not accurate, our model won't be either.

9. **Referral doesn't seem to be an important factor in our model,** we wonder if that's due to the very low amount of leads referred to us, at 2% of our whole dataset. We saw some positive numbers in the EDA, showing an improvement in the conversion rate when leads were referred.

> We could definitely work with ExtraaLearn on a plan to increase the referral volumes, maybe by incentivizing the referrees.

10. **Our typical future ExtraaLearn customer profile type is a person that is out of college, so older in age, might be unemployed, has shown some interest on our website, by spending time on it**, likely reading content and downloading the brochure, checking different pages on our website. That person also provided a completed profile, with learning interests and personal information. The follow-up interaction with the customer service in a lower measure has played a role too, mostly depending on the channel.

#
