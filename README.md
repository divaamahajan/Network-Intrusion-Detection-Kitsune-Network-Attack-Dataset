
# **Network Intrusion Detection using Machine Learning**

Team members: Darshil Modi, Divya Mahajan, Sudhanva Suresh Aithal, Yu Ji

Date: 03/15/2023

### **Problem Statement:**

In today's digital age, cyber attacks on businesses have become an increasingly regular concern. Malware infections, phishing schemes, denial-of-service assaults, ransomware attacks, and other types of attacks are all possible. A successful cyber assault can have serious implications, including the loss of crucial data, financial losses, reputational damage, and legal liability. 

According to a recent report, 47% of businesses in the US have experienced some type of cyber attack. In 2022, each cyber assault will cost businesses an average of $18,000 USD. In 2022, the average total cost of data breaches was $4.35 million. It costs them not only money, but also their reputation and sensitive client data. Customers' credit card information is sometimes stolen and sold on the dark web by hackers.

As a result, organizations must take proactive measures to protect themselves from cyber threats.

### **Objective:**

Based on data features of a network packet, the goal is to predict whether an incoming network data packet is malicious or benign.  By analyzing nine labeled attacks with extracted features and the original network capture, we will detect anomalies in the incoming packet to detect network intrusion.  This prediction will help us identify a potential cyber-attack.

### **Methodology:**

1) SAMPLING:

Sampling in Machine Learning  refers to the process of selecting a subset of data from a larger dataset to use for training or testing a model. The purpose of sampling is to create a representative subset that can be used to generalize to the entire dataset. Sampling is an important step in machine learning as it can impact the accuracy and performance of the model. 
After performing Sampling, we retrieved 1000 rows of benign and 1000 rows of malicious data points from each csv file. We then added a column called attack and did one hot encoding to classify attacks for all the given datasets( 1 for MitM, 2 for Active wiretap, 3 for Fuzzing.. so on)


2) STACKED MODEL APPROACH:

In machine learning, a stacked model technique involves integrating multiple models to improve overall predictive performance. This method is frequently utilized when individual models do not perform well enough on their own, or when a more precise and robust prediction is desired.
Several models are trained on the same data set in a stacked model technique. This method has the advantage of reducing bias and volatility in the final forecast. Individual models may have various strengths and limitations, and integrating their forecasts can improve overall predictive performance. Furthermore, because the aggregator model is trained on predictions rather than raw data, the stacked model technique can help to reduce overfitting.
Overall, stacked models are a powerful method, particularly beneficial in complex prediction problems where numerous models may be required to represent different features of the data.

![SM](https://user-images.githubusercontent.com/125092446/226152823-1494cd31-6664-415f-a04b-a99659b37139.png)

### **Feature Selection:**

We used a correlation heatmap to analyze features in order to choose the best features, enhance algorithm performance, and reduce feature dimension.
On that basis, we developed the selectKBest module from sklearn and chose the top 50 features.
Here is the Corelation Heatmap.

![Corelation](https://user-images.githubusercontent.com/125092446/226152845-894a965c-0adf-438d-8647-8d699ae1a45e.png)


### **Models Used:**

#### Intrusion Detection Model:

* This model takes a network packet of length 115 features as an input.
* This model is trained on two classes - Malicious / Benign.
* The training data including 9000 rows of Malicious and 9000 rows of Benign (1000 per attack).
* So training data shape : 18000 x 115.
* Output:

![IDM output](https://user-images.githubusercontent.com/125092446/226152885-6e1ce13d-1e2e-4763-876f-dbcc6e2f9999.png)


#### Attack Analyser Model:

* This model takes only malicious network packets of length 115 features as an input.
* This model is trained on nine attack classes - ARP Man-in-the-Middle, Active Wiretap, Fuzzing, OS Scan, SSDP Flood, Mirai Botnet, SSL Renegotiation, SYN DoS and Video Injection.
* The training data includes 9000 rows of data (1000 per attack)
* As a result, training data shape : 9000 x 115
* Output:

![AAM output](https://user-images.githubusercontent.com/125092446/226152901-a4988cc8-903b-4d70-8530-d68d1ec97674.png)


Some of the Observations:
![observations](https://user-images.githubusercontent.com/125092446/226152918-1c9418b3-c0cf-4c4b-8315-77c634a71fe9.png)

#### Observation: 

* The graph shows the feature importances in our model. Each bar represents the importance of a specific feature, with the height of the bar indicating how much the feature contributes to the accuracy of the model.

* The features are sorted in descending order of importance, so the most important feature is on the left-hand side of the graph. We can see that some features have very low importances, while others are quite important.

### **Future scope & latest trends:**
* Industry leaders such as Sophos are employing NLP techniques to detect malware, malicious code scripts, and even phishing emails using AI and ML models.
* Since network packets are similar to time-series data, complicated models such as GRU or LSTM can be used to better analyze network traffic and minimize network intrusions.
* Nevertheless, with the increased usage of AI and Generative models such as ChatGPT, it is now easier than ever to construct customized phishing assaults that are more likely to succeed.
* Who wins this age-old rivalry is a big question which only time can answer !

#### The link to our Database on Kaggle:
[Kitsune Network Attack Dataset](https://www.kaggle.com/datasets/ymirsky/network-attack-dataset-kitsune)

#### Citations:
* @inproceedings{mirsky2018kitsune, title={Kitsune: An Ensemble of Autoencoders for Online Network Intrusion Detection}, author={Mirsky, Yisroel and Doitshman, Tomer and Elovici, Yuval and Shabtai, Asaf}, booktitle={The Network and Distributed System Security Symposium (NDSS) 2018}, year={2018} }



