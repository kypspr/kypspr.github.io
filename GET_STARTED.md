# 🚀 Getting Started with Kypspr Visit Navigator

Welcome to the Kypspr Developer Commons. This guide will walk you through your first **Clinical Fidelity Simulation**—transforming "Semantic Sludge" into a "Golden Record."

## 1. Prerequisites
- Access to the [Kypspr Cockpit](https://app.kypspr.ai)
- A terminal with `curl` or a tool like Postman
- A basic understanding of [FHIR R4](https://hl7.org/fhir/R4/)

## 2. The Architecture of Truth
Kypspr sits as an intelligence layer between messy source data (L0) and the EHR (Health Bank).



## 3. Step 1: Trigger an Inbound Simulation
To see the refinery in action, push a raw clinical packet to our **Inbound Receptor**. Replace `YOUR_SESSION_ID` with a unique string.

```bash
curl -X POST [https://app.kypspr.ai/api/ingest](https://app.kypspr.ai/api/ingest) \
  -H "Authorization: Bearer kypspr-test-token" \
  -H "Content-Type: application/json" \
  -d '{
    "metadata": {
      "source_system": "UNIVERSAL_GATEWAY",
      "transaction_id": "YOUR_SESSION_ID",
      "timestamp": "'$(date -u +%Y-%m-%dT%H:%M:%SZ)'"
    },
    "payload": {
      "data_type": "UNSTRUCTURED_NOTE",
      "content": {
        "text": "Patient John Doe presents with persistent cough. History of hypertension. Currently on Metformin 500mg."
      }
    }
  }'
  ```
## 4. Step 2: Observe the L2 Refinery
- Open the Kypspr Cockpit.

- Look at the L2_SEMANTIC_ENGINE (Center Pane).

- You will see the log stream processing the unstructured text, identifying clinical concepts, and calculating the KFI (Kypspr Fidelity Index).

## 5. Step 3: The "Golden Record" Checkout
Once the refinery finishes, the FHIR_DATA_FABRIC (Right Pane) will update.

- Toggle to the Summary view to see the human-readable "Golden Record."

- Click [ EHR_PREVIEW ] to launch the Sidecar Simulator.

- Click [ COMMIT TO CHART ] to simulate the final write-back to the EHR Bank.

## 6. Next Steps
- Review the Inbound Spec for advanced data mapping.

- Learn how to embed the SMART on FHIR Sidecar in your own EHR.

- Join the conversation in our GitHub Discussions.