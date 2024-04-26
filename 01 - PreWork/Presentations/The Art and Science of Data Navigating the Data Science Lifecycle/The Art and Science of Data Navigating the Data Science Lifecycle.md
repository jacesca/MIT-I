# The Art and Science of Data: Navigating the Data Science Lifecycle

Learning Outcomes:
* Develop an idea of the DS and ML lifecycle.
* Understand how the solution lifecycle is implemented to solve business problems.
* Gain insights on the underlying architecture that powers a solution for business problems.
* Comprehend how different job roles come together to deliver these impactful solutions.

## How data driven-solutions are typically built?
1. Define: 
    - What you really want to solve.
    - Define the problem really well. 
    - Scope of the problem.
    - \>> Scope >> Data

2. Execution:
    - What is the current stage.
    - What is the information I have.
    - What is the ideal stage.
    - What algortithms are applicable.
    - \>> Deploy >> Build

3.  Consume:
    - Assumption that the solution will be used by the final users.
    - Is my problem solved?
    - Is there any piece not solved yet? -> yes, return to 1 and define what it is not solved yet. Continue the cycle.
    - \>> Action >> Measure


## Business Context: Ecommerce
    - Customers are not reached directly, there is a lot of layers of technology in touch with the potential customers.
    - Customar can have a lot of problems: how to do the things, who can be contacted if there is any problema, where can be found information.
    - Components to be considered in a chat bot:
        - Track orders
        - 24*7 support
        - Product analytics
        - Search for products
        - Assist with FAQs
        - Nudge to complete sales
    - Considerations:
        - Product selection struggle
        - Difficult navigation of web page
        - Inadequate support
        - Poor shoping experience
        - Poor customer satisfaction
        - High cart abandonment rate

## Strategy for building the chatbot
    - If you were owning this business, what teams would have to come together to build this solution?
    - You will need someone to:
        - UI/UX developer: Create the UI of the chatbot and integrate it into your website/app
        - Data Scientist: Create a language based model to answer your customers' questions
        - Data Engineer: Create/gather and manage the data that is needed to train your model.
        - ML Engineer: Deploy that model, monitor it and manage it's performance.
        - Product Manager: Manage and drive the development and consumption of this product.
    * In some cases the data scientist, the data engineer and the ml engineer roles are executed by the same person. It depends on the business, problem scope, etc.

## A typical solution lifecycle
* Scoping / Problem definition --> Leadership
    - Define the problem, the business value, and how to measure.
    - E.g. Define a model to prodict the support that will require the top 10% of the customers, so we can prioritize resources on those services to provide a better expeerience.

* Gather Data --> Product Manager, Data Scientist
    - Formulate the data requirement and acquire them from source.

* Prepare Data --> Data Scientist, Data Engineer
    - Transform, clean, business integrity checks and create an analytical dataset.
* EDA --> Data Scientist, Data Engineer
    - Mine for instights, explore the data, identify patterns and trends.
* ML --> ML Engineer, Data Scientist
    - Statistical modeling to extract insights, predict, classify, and recommend.
* Measure Impact --> Product Manager
    - Dashboarding, tracking of business KPIs and health past solutions.

## (1) Scoping / Problem Definition
- What should this chatbot be able to do how would it work?
- Considerations:
    - On what platform should we built this chatbot? What is the tech infraestructure needed to support this solution at scale?
    - What language model should we use to build this solution? What should it be trained on and how?
    - How do we monitor the performance of this chatbot? How we will be deployed to be made available to the user?
    - What kind of questions related to orders do we want the chatbot to answer?
    - How should this chatbot behave for different kind of requests / what actions should it takes based on inputs?
    - How would we measures the impact? What are the business KPIs and who are the stakeholders?

## (2) Gather Data
- What data do I need to build this chatbot?
- Considerations:
    - Product data 
        - Product brand
        - Product type
        - Model type
    - FAQ
        - Payment method
        - Product Availability
        - Refund return
    - Shipping
        - Pending orders
        - Dispatched orders
        - Returned orders
    - Feedback
        - Product quality
        - Service rating
        - Delivery rating
    - Orders data
        - Order id
        - Payment type
        - Order quantity
    - User data
        - Customer details
        - Browsing
        - Purchase history

## (3) Prepare Data
- How do I create the data I need for my data solution/product?
- Various databases within a datawharehouse like MySQL
- Considerations
    - Source of Data:
        - Customer Interacts with support Agent
        - Customer actions on the web site
        - Purchases, refund, requests
        - Personal customer information (PII)
    - Data Ingestion
        - TicketId, Duration, Status, Query
        - Clicks, Favourites, Duration, Bounce
        - Amount, Payment method, items
        - Location, Income, Profession, Wallet
    - ETL (Extract, Transform, Load)
        - Clean
        - Integrate --> Analytical Dataset
    - Consumption ready for
        - EDA
        - AI/ML
        - Data Product / Service

### (4) Exploratory Data Analysis
- How should I approach exploring my data?
- Considering:
    - Data Cleaning
        - Removing / treating missing values
        - Treating outliers
        - Variable conversion
    - Formulate Questions
        - What is the user's intent?
        - What product/service is being referred to?
        - What are the data sources for this query?
    - Data Analysis
        - Univariate Analysis
        - BiMultivariate Analysis
    - Conclusions
        - Common pain points for customers
        - Feedback on chatbot performance
        - Key product/service features
    - Documenting insights
        - The most frequent services opted for in each category
        - Improvements to make based on the findings

## (5) Machine Learning LyfeCycle
- (a) Data preprocessing
    - get data into the right shape and form, encode, transform and scope.
    - For our business problem:
        - User Input to chatbot: 
            | Input | Input type |
            | ----- | ---------- |
            | I want to buy a new HP Laptop | Sales |
        - How does the chatbot understand us?:
            | Msg | Main Component | Recognition  |
            | --- | --- | --- |
            | I want to **[buy](#buy)** a new HP Laptop | Make purchase | Intent Recognition |
            | I want to buy a **[new](#new)** HP **[Laptop](#Laptop)** | Brand - HP | Named Entity Recognition |
            | I **[want to buy](#want)** a new HP Laptop | Sentiment - Positive | Sentiment Analysis |
        - Steps:
            Tokenization >> Lemmatization >> Stop Word Removal
- (b) Train
    - Train a model using the data to predict, classify or recommend.
    - Model training
            $$ LabeledDataset = InputQuery + DesiredResponseFromChatbot $$
    - Generally the training is on the 10% of the population. This data is labeled for the training purposes.
- (b) Tune (Train - Tune - Evaluate cycle)
    - Perform hyper parameter tunning on your model - enhance its performance.
    - Hyperparameters control the behavior of the model during the training
    - Hyperparameters to consider:
        - Learning rate
        - Hidden layers
        - Dropout rate
        - Batch size
    - Techniques:
        - Grid search
        - Random search
    - Hyperparameters tunning involves testing different combinations of hyperparameters and selecting the combination that offers the best performance
    - For Training and Tunning - On our bussiness cases:
        - Input Query: Desired Response from Chatbot
        - NLP model: Genralizes the patterns observed in input-output pairs.
            - Rule based chatbots
            - Generative chatbots
            - Retrieval chatbots
        - Output from chatbot.
- (b) Evaluate
    - Evaluate your model's performance, check benchmark, bias, viarance.
    - Model testing: Using validation/test dataset that is different from training data
    - On our business case:
        - Test data --> NLP model --> Output from chatbot
        - Evaluation:
            - Human: validate & label
            - Generalize: well on new examples
- (c) Deploy
    - Expose your model as an endpoint - which can be used by your stakeholders.
    - On our business case:
        - How am I able to get the real time response for my queries?
        - website: Response >> gateway >> server (language model)
- (d) Monitor
    - Monitor for anomalies, errors - alert and update model to improve performance.
    - On our business case:
        - Collect data of our chat behavior
        - Chatbot performance WoW: Poor response or Good response

## 6. Measuring impact
- Dashboards & reports
- On our business case:
    - Weekly Query Response Metric
    - Top 7 queries
    - % satisfaction WOW increase?
    - % Escalantions WOW increase?
    - Satisfaction vs support over weeks

# Summary
* Data science lifecycle is a cycle that needs collaboration across teams and stakeholders.
* ML lifecycle is contained within Data Science Lifecycle.
* Art is to define problems, get the right data and the right final recommendations for deployment and improvement.
* Science is to be abble to code the algorithms, extract insights and deploy the solutions.
* The problems that customers face commonly in ecommerce domain like inadequate cutomer support, difficult navigation, product selection issues and how a chatbot can help solve them
    - How a UI-UX developer, a data scientist, a data engineer, an ml engineer, and a product manager collaborate to build a chatbot
    - How the data science and machine learning lifecycle work in gathering data, building and monitoring the chatbot
    - How the data engineering pipeline, the machine learning pipeline and the operations pipeline assist in development and maintenance of the solution
    - How an input given to the chatbot is meaningfully interpreted by the chatbot to generate a suitable response
    
# Q&A
- There will be aspects of human behaviour which will be difficult to capture or "create a footprint"? Will there be anomalies therefore in how this captured data is interpreted?
    - These aspects difficult to capture, which we may not even know of, are often called hidden variables in research. It's a difficult topic, as they may influence our variables in a way that we don't understand

