### Hi, I'm Ethan Verduzco 👋

I turn messy operational data into the numbers a business runs on: **finance, supply chain, manufacturing and insurance**.
Data Science & Mathematics Engineer · M.S. Financial Management (Boston University).

This profile is a growing portfolio of **end-to-end data projects on AWS**. Each one:
- starts from a real business question;
- defines 3–5 KPIs;
- builds the pipeline that answers it: ingestion, processing, alerts, analytics, infrastructure as code and CI.

Every project is deployed for real, documented with evidence from the run, torn down, and its actual cloud cost reported.

#### Projects

| Industry | Project | Business question | KPIs | Stack |
|---|---|---|---|---|
| Manufacturing | [**manufacturing-scrap-and-stockout-alerts**](https://github.com/ethanverper/manufacturing-scrap-and-stockout-alerts) | Catch scrap and stock-outs on the factory floor in seconds, and know which supplier pays for them | Reject rate (SPC control limits) · stock coverage · throughput vs plan · scrap cost | Kinesis · Lambda · DynamoDB · SNS · Firehose · Glue (PySpark) · Athena · Terraform |
| Finance | _coming soon_ | | | |
| Supply chain | _coming soon_ | | | |
| Risk & controls | _coming soon_ | | | |
| GenAI | _coming soon_ | | | |

#### Latest: manufacturing scrap and stock-out alerts
A streaming and batch pipeline for two simulated assembly plants. It was deployed with 41 AWS resources for 42 minutes, then destroyed and verified clean.
- **Real time:** 1,011 live scans → **8 email alerts in seconds**, each routed to the right team, with 0 false alarms and 0 errors. Statistical process control replaced a fixed threshold that had 64% false alarms.
- **Batch:** a PySpark job proves that every raw record is counted, recognized as a retry, or quarantined before it publishes anything (54,137 = 53,541 + 537 + 59).
- **Findings:**
  - one supplier lot at **13.9% defects**;
  - a part at **0.89 days** of stock;
  - **$169k of scrap recoverable** from suppliers.
- **What the real run caught:** a missing IAM permission and a data gap read as "zero production". Both were fixed and are documented as [lessons learned](https://github.com/ethanverper/manufacturing-scrap-and-stockout-alerts/blob/main/docs/lessons-learned.md).

[How it was built, level by level, with screenshots →](https://github.com/ethanverper/manufacturing-scrap-and-stockout-alerts/blob/main/docs/project-story.md)

#### Toolbox
- **Languages:** SQL · Python · PySpark · R
- **AWS:** S3 · Glue · Athena · Kinesis · Firehose · Lambda · DynamoDB · SNS · SQS · EMR · EventBridge · Redshift _(grows with each project)_
- **Practices:** Terraform · CI with GitHub Actions · data quality and reconciliation · statistical process control · least-privilege IAM · cost tracking
- **BI:** Power BI · Tableau

#### Currently studying
AWS Certified Data Engineer – Associate · AWS Certified AI Practitioner
