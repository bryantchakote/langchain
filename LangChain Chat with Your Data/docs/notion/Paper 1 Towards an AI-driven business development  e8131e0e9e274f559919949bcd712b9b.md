# Paper 1: Towards an AI-driven business development framework: A multi-case study

---

John MM, Olsson HH, Bosch J. Towards an AI-driven business development framework: A multi-case study. *J Softw Evol Proc*. 2023; 35(6):e2432. doi:[10.1002/smr.2432](https://doi.org/10.1002/smr.2432)

---

# Abstract

- Artificial intelligence (AI) and the use of machine learning (ML) and deep learning (DL) technologies are becoming increasingly popular in companies. These technologies enable companies to leverage big quantities of data to improve system performance and accelerate business development.
- However, despite the appeal of ML/DL, there is a lack of systematic and structured methods and processes to help data scientists and other company roles and functions to develop, deploy and evolve models.
- In this way, we provide practitioners with a blueprint for effectively integrating ML/DL model development into the business to achieve better results than other (algorithmic) approaches.

# Introduction

- Digitalization implies a transition from a hardware and product-based business to one that relies primarily on software, data, and artificial intelligence (AI) to improve products, offer purely software-based products, and provide new digital and data-driven services to customers (1).
- However, as companies advance from a hardware and product-based business to one that is increasingly focused on digital technologies such as software, data, and AI, they will need to evolve their current systems and complement them with new technologies. From this perspective, AI, machine learning (ML), and deep learning (DL) technologies offer excellent opportunities as they enable innovation and new ways of meeting customer needs (2).
- Companies across all domains are using AI/ML/DL technologies to improve, scale and optimize their business (3, 4).
- Furthermore, non-experts with little or no data science background run the risk of developing and deploying invalid ML/DL models for their daily needs if they view accuracy as the only evaluation metric of a model performance (5).
- Regardless of the level of expertise and/or access to data scientists, companies across the domains struggle to create high-performance models due to a lack of established and systematic design methods and processes. Software companies need to evolve their development practices and processes to build intelligence into their products as the ML/DL technology matures.
- In previous literature studies, existing processes and structures representing ML/DL development tend to focus on the data-intensive context or on a mixture of data and model requirements contexts and have little to no focus on business case generation, selection and validation (9-14).
- In our previous research, we identified the typical phases that data scientists go through when designing ML/DL models. The seven typical phases are (i) Business case Specification, (ii) Data Exploration, (iii) Feature Engineering, (iv) Experimentation, (v) Development, (vi) Deployment and (vii) Operational. For each phase, we identified the approaches as well as the major challenges experienced by the data scientists involved in our study. Finally, we outlined the iterations between the different development phases and the events that trigger these iterations to optimize the design process (15).
- Second, we present a conceptual framework in which we describe not only the activities involved in the development of ML/DL models but also the roles and company functions involved as well as the iterations that occur and the activities they trigger to optimize the process. […] With this framework, we provide a blueprint for how to effectively integrate AI/ML/DL into the business of companies in a systematic way.
- The ML/DL model achieves better results because it learns from data. Businesses benefit from AI technology by enabling better ways of working, automating complex processes, enriching customer experience, increasing productivity, improving operational efficiency and freeing up time for innovation. […] This can only happen if they are able to successfully integrate ML/DL development into the larger system development and business context.

# Background

In this section, we first review the contemporary literature on how digital technologies are changing current business practices in the embedded systems domain, especially through the adoption of DevOps, DataOps and MLOps practices. Second, we discuss previous studies on AI/ML/DL technologies and their applications in various companies.

## Digitalization: New technologies and ways of working

- Most companies have undergone significant changes in recent years as a result of increasing digitalization (16).
- According to Gartner, digitalization generates new revenue and value by using digital technologies to transform a business model (17).
- In recent years, and as reported in previous studies, CI and continuous deployment (CD) practices are leading to shorter development times and faster placement of release candidates into production environments. Recently, new ways of working have emerged that are becoming increasingly important for companies seeking to take advantage of these new technologies. Practices such as DevOps, (18-20), DataOps (21) and MLOps (22, 23) are being adopted with the intention of driving both product automation and quality in terms of development, data and ML operations.
- Penners and Dyck (24) propose DevOps as a collaboration of teams working in development and IT operations within a software-intensive company to deliver faster software changes (18). Key benefits of adopting DevOps in companies (25) include faster delivery of software changes, higher operational productivity, better quality and improved organizational culture and attitudes.
- On the other hand, companies face some difficulties in adopting DevOps. These include inadequacies in infrastructure automation, high skill and knowledge requirements, project and resource constraints and monitoring challenges.
- According to Munappy et al (21), DataOps can be defined as “an approach that accelerates the delivery of high-quality results by automation and orchestration of data life cycle stages. DataOps chooses the best practices, processes, tools and technologies from agile software engineering (SE) and DevOps to regulate analytics development, optimizing code verification, building and delivering new analytics, and thereby fostering a culture of collaboration and continuous improvement.”
- Challenges to adopting DataOps include lack of pipeline robustness, data silos, organizational and restructuring.
- MLOps adopts and applies DevOps principles to ML models instead of software and merges the development cycles followed by data scientists and ML engineers with those of operational teams to ensure consistent delivery of high-performance ML models (22).
- One of the biggest challenges is training for AI operations as most data scientists are not trained computer scientists by education and most data-intensive companies have little to no idea on how to manage their data (26).
- Digitalization is indeed much more than DevOps, DataOps and MLOps practices.
- The companies see it as critical to integrate DevOps, DataOps and MLOps practices into their workflows as data and software components add value to their business by opening up new opportunities.

## AI/ML/DL and its applications

- The main difference between ML/DL and non-ML/DL systems is that in ML/DL systems, data take the place of code and data patterns are recognized using an algorithm rather than hard coding.
- ML/DL has emerged as the preferred method in many fields such as robotics, speech and image recognition, natural language processing (NLP) (30) and computer vision (31, 32).
- In addition, ML/DL technologies are used in a variety of companies (37). ML/DL applications in retail include recommendation engines, market segmentation and inventory planning. In contrast, ML/DL is used in demand forecasting, condition monitoring and process optimization. Some of the use cases in healthcare are real-time alerts and diagnostics, disease and risk detection while in financial services, use cases include evaluation of credit scoring, risk analytics and regulation, and customer segmentation. ML/DL technologies are used in the energy and utilities sector where use cases are power use analytics, carbon emissions, trading, and customer-specific pricing. The use of ML/DL technologies is widespread and advanced in the online sector, for instance, King and Peltarion.

# Empirical findings

- We report empirical findings from each of the six case companies involved in our study.
- As a structure for presenting our empirical findings, we divide them into three viewpoints: Business, Data and Models. The introduction of ML/DL technology in companies is pointless if it does not bring benefits to customers. High-quality data are needed to train models that can identify hidden valuable patterns in the dataset. The value of a particular ML/DL business case can only be realized by operationalizing the ML/DL models.

## Challenges

- The challenges are grouped into three categories that relate to the development of ML/DL models: (a) Pre-Deployment, (b) Deployment and (c) Non-Technical challenges.

### Pre-Deployment

- Representative and valuable dataset: According to data scientists, the dataset collected for ML/DL needs to be a valuable and representative sample.
- Improper feature selection: Most data scientists consider feature selection as an important step and point out that a feature set with insignificant features has implications for model performance.
- Bias introduction: We find that data scientists introduce bias based on their experience in selecting algorithms for both ML/DL models and in selecting features for ML. I1: “They bring their own experiences and then introduce own biases into the whole working.”
- High complex DL models: Despite the popularity of DL models, most data scientists prefer ML models for training because they are less complex. Compared with ML, they believe that deep knowledge is required to implement DL models.

### Deployment

- Training-serving skew: Data scientists consider training-serving skew as the discrepancy between training and serving performance.
- Model drifts: Data scientists see model drifts as a potential threat to model performance. Therefore, it is necessary to properly identify model drifts and determine when they need to be retrained or updated.

### Non-technical

- High cost and high AI expectations: According to the study, the implementation of ML/DL models requires significant infrastructure costs compared with traditional software development. […] Experts with little or no experience in data science have high AI expectations. […]  I4: “To make good business value, we need input from stakeholders, and sometimes we need to play an educational role because they are not aware of the potential risks involved in the design of ML/DL systems.”
- Proper allocation of data scientists and domain experts: Most practitioners involved in our study confirm that data scientists and domain  experts need to be carefully allocated to the project.
- Need for an intelligible model: Most data scientists stress the importance of understanding the model developed by other data scientists.
- End-user communication: All data scientists report that there is a need to encourage communication with end-users as the model is difficult for them to understand.

### Conclusion

- The majority of the companies face challenges in deployment.
- Most companies believe that a dedicated team should be set up to monitor deployment
issues.
- Communication with end users is a challenge for all companies when they have to interact with clients, testers, developers, architects, and others who have little or no ML/DL knowledge.

# Discussion

- We present three parallel and concurrent high-level activities that take place in companies as part of the development, deployment and evolution of ML/DL models, that is, business case experimentation, data experimentation and model experimentation.

## AI-driven business development framework

- Companies are struggling with the introduction of ML/DL components, model development and related practices into the business context of the company […] this was expressed by several company practitioners when they reported challenges in applying new technologies, adopting new ways of working, and difficulties in introducing and training different company roles in relation to ML/DL model development.
- The end-to-end ML/DL process from business case generation to deployment as outlined in the framework can serve as a blueprint for those working to develop, deploy and evolve ML/DL models. AI companies will only benefit when their products are deployed in production.
- Business case experimentation refers to the generation and validation of business cases suitable for ML/DL.
- Data experimentation refers to the generation, collection, and exploration of data, as well as the monitoring of model performance based on inference data.
- Model experimentation refers to the selection of appropriate features, experimentation with algorithms, finalization of an appropriate algorithm and placing the model into production.

## Roles and company functions

- Our empirical results show that different profiles of practitioners are involved in the development, deployment, and evolution of ML/DL models. […] A typical large data science team consists of a product owner, data scientists, domain experts, a business owner, and back-end or front-end software developers. All roles in the company may be involved in different ML/DL projects simultaneously and in parallel.

## Correlation between framework and challenges

- Scheduling stand-up meetings, sprint meetings, participating in demos, internal workshops and so forth can ensure that all team members are aware of each step in the development, deployment and evolution of models for a particular business case in the companies.
- A proof-of-concept can reduce the time required for model development and give a realistic idea of what can be achieved with the business case.