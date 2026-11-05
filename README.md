### Hi, I'm Ethan Verduzco 👋

I build the data systems that turn messy operations into numbers a business can act on: from the business question and its KPIs to a cloud pipeline running for real, with its cost and its evidence.
Data Science & Mathematics Engineer · M.S. Financial Management (Boston University).

This profile is a growing portfolio of **end-to-end data projects on AWS**. Each one:
- starts from a real business question;
- defines 3–5 KPIs;
- builds the pipeline that answers it: ingestion, processing, alerts, analytics, infrastructure as code and CI;
- is **deployed for real**, documented with screenshots and logs from the run, torn down, and its actual cloud cost reported.

The method is industry-agnostic. So far: manufacturing and finance. Next: supply chain, banking, tech and sports.

#### Projects

| Project | Business question | KPIs | Stack | Proof |
|---|---|---|---|---|
| [**ap-duplicate-payment-detection**](https://github.com/ethanverper/ap-duplicate-payment-detection) · *Finance* | Are we paying any supplier invoice twice? Are we paying on time, or losing early-payment discounts? | $ at risk from duplicates (HIGH/MEDIUM confidence) · on-time % · DPO · discounts lost | S3 events · Lambda · Glue (PySpark) + **Data Quality** · Athena · SNS · Terraform | [evidence](https://github.com/ethanverper/ap-duplicate-payment-detection/blob/main/docs/evidence/README.md) |
| [**manufacturing-scrap-and-stockout-alerts**](https://github.com/ethanverper/manufacturing-scrap-and-stockout-alerts) · *Manufacturing* | Catch scrap and stock-outs on the factory floor in seconds, and know which supplier pays for them | Reject rate (SPC control limits) · stock coverage · throughput vs plan · scrap cost | Kinesis · Lambda · DynamoDB · SNS · Firehose · Glue (PySpark) · Athena · Terraform | [evidence](https://github.com/ethanverper/manufacturing-scrap-and-stockout-alerts/blob/main/docs/evidence/README.md) |

#### Latest: accounts-payable duplicate payment detection
An ERP drops one payment file per entity per day (Mexico and US). Deployed with 30 AWS resources for 29 minutes, then destroyed and verified clean.
- **Every file is checked in seconds as it lands** (S3 event → Lambda): a control trailer, the header contract, and re-sent files ignored. A hand-edited file was rejected live, with the exact $1,000 that had been added.
- **A PySpark job on Glue finds duplicate payments**: invoice numbers retyped (`FAC-0457` vs `fac 457`), advances paid twice, invoices resubmitted under new numbers. Graded against an answer key it never sees: **27 of 27 found, 0 false alarms, $195K at risk**.
- **Glue Data Quality** ran a versioned DQDL ruleset: 11 of 11 rules passed.
- **What the real run taught:**
  - the account allowed only 10 concurrent Lambdas, and the asynchronous trigger absorbed 259 throttles without losing a file;
  - one alert email never arrived, so email is a notification and not a record.

  Both are [lessons learned](https://github.com/ethanverper/ap-duplicate-payment-detection/blob/main/docs/lessons-learned.md).

Before it: [manufacturing scrap and stock-out alerts](https://github.com/ethanverper/manufacturing-scrap-and-stockout-alerts). Streaming and batch, 41 AWS resources, 8 real-time alerts with 0 false alarms, **$0.12** of actual cloud cost.

#### Toolbox
- **Languages:** SQL · Python · PySpark · R
- **AWS:** S3 · Glue · Athena · Kinesis · Firehose · Lambda · DynamoDB · SNS · SQS · EMR · EventBridge · Redshift _(grows with each project)_
- **Practices:** Terraform · CI with GitHub Actions · data quality and reconciliation · statistical process control · least-privilege IAM · cost tracking
- **BI:** Power BI · Tableau

#### Currently studying
AWS Certified Data Engineer – Associate · AWS Certified AI Practitioner
