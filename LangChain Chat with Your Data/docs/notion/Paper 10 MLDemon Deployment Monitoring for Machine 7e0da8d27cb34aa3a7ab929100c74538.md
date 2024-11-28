# Paper 10: MLDemon: Deployment Monitoring for Machine Learning Systems

---

Ginart, Antonio & Zhang, Martin & Zou, James. (2021). MLDemon: Deployment Monitoring for Machine Learning Systems.

---

# Abstract

- Post-deployment monitoring of ML systems is critical for ensuring reliability, especially as new user inputs can differ from the training distribution.
- Here we propose a novel approach, MLDemon, for ML Deployment monitoring […] to produce a real-time estimate of the ML model’s current performance on a given data stream.

# Introduction

- Deployment monitoring is a vast topic. In this work, we focus on a particular streaming setting where an automated deployment monitoring policy can query experts for labels during deployment. The goal of the policy is to estimate the model’s real-time accuracy throughout deployment while querying the fewest amount of expert labels.