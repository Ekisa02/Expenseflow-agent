# AutoExpenseFlow — Expenseflow-agent

AutoExpenseFlow is an IBM watsonx-powered AI agent that automates corporate expense processing using document intelligence, policy enforcement, and ERP integration. It combines Watsonx Orchestrate, AI assistants, and cloud services to reduce manual work by 80% while ensuring compliance.

## Project summary
AutoExpenseFlow replaces manual expense processing with an intelligent AI agent built on IBM watsonx. It extracts data from receipts and invoices, validates them against company policy, integrates validated transactions with ERP systems, and generates auditable reports — reducing processing time from ~15 minutes to ~30 seconds per invoice while maintaining 99%+ accuracy.

Submission (Agentic AI Hackathon with IBM watsonx Orchestrate)
- Submission Title: AutoExpenseFlow: Enterprise AI Agent for Automated Expense Processing
- Short description: "AutoExpenseFlow is an IBM watsonx-powered AI agent that automates corporate expense processing using document intelligence, policy enforcement, and ERP integration. It combines Watsonx Orchestrate, AI assistants, and cloud services to reduce manual work by 80% while ensuring compliance."
- Long description: See "Core technologies & components" below.

## Core technologies & components

- AI & Orchestration
  - IBM watsonx Orchestrate — central workflow controller
  - IBM watsonx.ai Foundation Models (LLAMA-3) — document understanding and extraction
  - AI assistants — specialized agents for validation, parsing, and compliance checking

- Document processing
  - extract_document_text — OCR (image/pdf -> text)
  - parse_invoice_data — structured data extraction from unstructured text
  - validate_expense_policy — enforces company rules & policy
  - check_vendor_approval — validates vendor against master data

- Integration & actions
  - erp_integrator — connectors for ServiceNow / SAP / QuickBooks
  - notification_dispatcher — Email / Slack approvals and notifications
  - audit_logger — compliance tracking and immutable audit trail
  - report_generator — automated PDF / Excel reports

- IBM Cloud infrastructure (example components)
  - IBM Cloud Object Storage — secure document repository
  - IBM Db2 on Cloud — transaction records & audit trails
  - IBM API Connect — secure APIs
  - IBM Cloud IAM — identity & access controls

- Specialized agents
  - ExpenseFlow Orchestrator (main controller)
  - Invoice Reader Agent (document processing)
  - Policy Validator Agent (compliance checking)
  - ERP Integrator Agent (system integration)
  - Audit Logger Agent (compliance tracking)

## Features
- Automatic OCR and data extraction from receipts/invoices
- Policy-based validation (spend limits, approvals, duplicate detection)
- Vendor validation and fraud detection hooks
- Seamless ERP update and approval orchestration
- Full audit trail and report generation

## Project structure (based on the demo video)
A recommended layout that reflects the demo organization, with clear separation of orchestrator, agents, connectors, services, infra, and docs.

```text
/ (root)
├─ README.md
├─ .env.example
├─ docker-compose.yml
├─ terraform/
│  ├─ main.tf
│  └─ variables.tf
├─ docs/
│  ├─ architecture.md
│  ├─ deployment.md
│  └─ user_guide.md
├─ orchestrator/
│  ├─ orchestrator.yaml
│  └─ workflows/
│     ├─ ingest-workflow.yaml
│     └─ approval-workflow.yaml
├─ agents/
│  ├─ invoice_reader/
│  │  ├─ main.py
│  │  ├─ model/
│  │  │  └─ prompts.md
│  │  └─ tests/
│  ├─ policy_validator/
│  │  ├─ validator.py
│  │  └─ rules/
│  ├─ erp_integrator/
│  │  ├─ connector.py
│  │  └─ adapters/
│  │     ├─ servicenow_adapter.py
│  │     └─ sap_adapter.py
│  └─ audit_logger/
│     ├─ logger.py
│     └─ schemas/
├─ connectors/
│  ├─ servicenow/
│  ├─ sap/
│  └─ quickbooks/
├─ services/
│  ├─ ocr_service/
│  │  ├─ server.py
│  │  └─ Dockerfile
│  ├─ parser_service/
│  └─ notification_service/
├─ cloud/
│  └─ ibm_cloud_setup.md
├─ examples/
│  ├─ sample_invoices/
│  └─ integration_demo/
├─ scripts/
│  ├─ build.sh
│  └─ deploy.sh
├─ tests/
│  ├─ unit/
│  └─ integration/
└─ LICENSE
```

Notes on key directories:
- orchestrator/: Contains the Watsonx Orchestrate configuration and workflow definitions used to route tasks between agents and services.
- agents/: Self-contained agents (invoice_reader, policy_validator, erp_integrator, audit_logger). Each agent has an entrypoint, models/prompts (where applicable), and tests.
- connectors/: Adapter implementations for different ERP systems and vendor/master-data checks.
- services/: Microservices for OCR, parsing, and notifications. Can be deployed separately or as containers.
- docs/: Architecture diagrams, deployment steps for IBM Cloud, and user/testing guides.
- terraform/: IaC for provisioning IBM Cloud resources used in the demo (storage, Db2, IAM, API Gateway).

## Quickstart (example)
1. Clone the repo
   ```bash
   git clone https://github.com/Ekisa02/Expenseflow-agent.git
   cd Expenseflow-agent
   ```
2. Configure environment
   ```bash
   cp .env.example .env
   # populate .env with Watsonx credentials, ERP keys, and cloud credentials
   ```
3. Local run (example)
   ```bash
   docker-compose up --build
   ```
4. Submit a sample invoice to the ingestion endpoint or run the integration demo in examples/integration_demo/.

## Team (Agentic AI Hackathon)
- Ekisa Joseph Opurongo — Team lead / Software & AI Engineer (https://github.com/Ekisa02)
- Roselie Atieno
- Marion Jebet
- Daniel Juma

## How to contribute
- Open an issue for bugs or feature requests.
- For code contributions, fork the repo, create a feature branch, and submit a PR with tests and a clear description.

## License
- Add your license here (e.g., MIT). If none specified, please add a LICENSE file.

## Contact
- Project owner: Ekisa (https://github.com/Ekisa02)
- For questions about the hackathon submission or demo, open an issue or contact the maintainer via the GitHub profile.
