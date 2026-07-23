# 🛠️ HomeCareContacts (HCC)

> **A mobile-first, event-driven ecosystem engineering seamless matches between household service requesters and independent contractors—powered by Multimodal AI diagnosis, real-time spatial indexing, and a gamified tiering engine.**

---

## 📌 Executive Summary

**HomeCareContacts** bridges the gap in on-demand residential maintenance and specialized trade booking. Property owners or tenants initiate a request by submitting text, selecting categorized parameters, or capturing imagery/video of the issue. 

The platform’s underlying intelligence ingests the media via Vision Language Models (VLMs) to classify the defect and scope the repair. It then computes a real-time spatial match, orchestrating dispatch notifications across **Push Services and WhatsApp APIs**. 

To drive retention and maintain rigorous service standards, service providers progress through a **Gamified Tiering System** (Bronze through Diamond), unlocking operational incentives such as reduced platform commission rates and preferential dispatch latency.

---

## 🚀 Key Value Drivers

* **AI-Driven Visual Diagnostics:** Zero-friction intake powered by Vision APIs to automate domain classification, material identification, and job complexity estimation.
* **Proximity & Performance Match Engine:** A multi-factored ranking algorithm weighing geo-distance, historic feedback scores, response latency, and gamification standings.
* **Conversational-First Onboarding:** Deep integration with WhatsApp webhooks for friction-free transactional updates, identity verification, and instantaneous job alerts.
* **Incentivized Provider Progression:** Event-driven XP architecture enforcing service-level agreements (SLAs) through a structured tier system (*Bronze ➔ Silver ➔ Gold ➔ Platinum ➔ Diamond*).

---

## 🏗️ System Architecture

```text
[ Mobile Application (React Native/Expo) ] ◄──(WhatsApp Webhook)──► [ WhatsApp API Provider ]
                  │                                                      │
                  ├────────────────────────────────────────┐             │
                  ▼                                        ▼             ▼
        [ Edge Gateway / CDN ]                  [ S3 / R2 Bucket ]   [ Webhook Ingestion ]
                  │                                        │             │
                  ▼                                        ▼             │
        [ Core API Node (NestJS) ] ◄─── [ Multimodal Vision API ] ───────┘
                  │
         ┌────────┴────────┬───────────────────┬──────────────────┐
         ▼                 ▼                   ▼                  ▼
   [ PostgreSQL/PostGIS ] [ Redis Sorted Sets ] [ Message Queue ]  [ Push Dispatcher ]
