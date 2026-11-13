# Prompt for writing the SaveYourAir technical specification

Act as a product analyst and software architect with experience in respiratory protection, occupational exposure assessment, and AI integrations. Write an implementation-ready technical specification in English for **SaveYourAir**, a web application that helps users select a respirator, a replacement filter or cartridge, or a compatible respirator-and-filter combination based on weather, working conditions, airborne contaminants, and activity.

Cover personal outdoor activities and occupational use. Define when the application can suggest a product, when it needs clarification, and when the case requires a qualified occupational assessment. Label assumptions and open decisions explicitly, including the target market and applicable regulations. Deliver the specification in Markdown, with numbered requirements and testable acceptance criteria.

## 1. Propose the menu and user flows

Use the following as a starting point for the information architecture. For each entry, define the user action, required and optional inputs, conditional fields, output states, and validation. Describe navigation and behavior at the requirements level. Leave visual layout and styling to the design phase.

| Proposed menu entry | Requirements to specify |
|---|---|
| **Find Protection** | Let users select a respirator, find a replacement filter for an existing facepiece, or find a compatible complete set. Capture manufacturer and model when the user already owns a facepiece. |
| **Activity & Work Conditions** | Include walking, running, cycling, and heavy physical work. Capture indoor or outdoor setting. For occupational use, request relevant details such as task, material, intensity, exposure duration, ventilation, local extraction, other PPE, and measured exposure where applicable. |
| **Weather & Air Quality** | Support manual temperature entry and a winter/summer selector. Consider humidity, wind, and precipitation where relevant to product limits or the task. Propose optional weather and ambient air quality feeds using a user-entered location or permission-based geolocation. Show source, observation or forecast time, units, and data freshness. Define manual fallback and a proposed five-level pollution selector with accessible text labels. |
| **Airborne Contaminants** | Support multiple selections. Include urban smog, road dust, paints and varnishes, pollen, microorganisms and viruses, wood dust, and cement dust. Add conditional fields for chemical composition, concentration, averaging period, material, and method of application when relevant. Offer optional safety data sheet (SDS) upload for chemical products and allow users to verify extracted fields. |
| **Recommendations** | Return eligible product types or specific models where supported. Show manufacturer, model, SKU, applicable marking, valve status where relevant, compatible filters and accessories, covered hazards, limits, fit guidance, and source documents. Define clear states for insufficient data, unsupported scenarios, and no compatible product found. |
| **Break Timer** | Define start, end, expiry, and session recovery after refresh. Allow a user-defined reminder for personal use or a break interval from an applicable, documented workplace plan. Treat break reminders and cartridge replacement as distinct functions. Explain expected browser behavior when the device locks or the tab runs in the background. |
| **Sources & Guidance** | Explain which data came from the user, external feeds, manufacturer documents, or local occupational guidance. Provide source links and show when the catalog or a rule was last reviewed. |

Define a restricted catalog administration area if ongoing maintenance requires it. Specify how reviewers can add, verify, publish, and withdraw products, compatibility records, and rule versions.

## 2. Define how the selection method will be developed

Specify a work package to develop and validate the selection method using verified manufacturer selection guides, instructions for use, technical data sheets, approved facepiece and filter combinations, and product-specific limitations. Use the substance SDS and applicable occupational rules as inputs where relevant. Describe the required evidence, responsible reviewers, deliverables, and acceptance tests. Leave formulas, thresholds, coefficients, and detailed decision rules for the evidence and validation work.

Require records to identify the exact product and market, document revision and section, supported hazards, operating and storage conditions, compatibility, and limitations. Define how reviewers resolve conflicting documents, retire outdated products, and handle missing evidence. Require validation by a qualified respiratory protection or occupational hygiene specialist before occupational rules are published.

Treat ambient air quality and workplace exposure as separate data sources. Define how the app handles pollutant mixtures, missing concentrations, unknown hazardous atmospheres, possible oxygen deficiency, conditions outside verified product limits, and tasks that require a different protection approach. Specify how the result communicates missing information, the role of fit testing and seal checks where applicable, and when the user needs a specialist assessment. Derive any future cartridge replacement schedule from validated product-specific evidence and applicable requirements.

## 3. Recommend the application architecture

Use a **React and TypeScript frontend, a Python FastAPI backend, and PostgreSQL** as the recommended baseline. Explain the tradeoffs and identify any assumption that would justify a different stack.

- **Frontend.** Use an accessible, responsive web client for guided input, recommendations, source references, and timer sessions. Define local persistence for active timers and behavior when inputs change mid-session.
- **Backend.** Start with one deployable service with modules for input validation, environmental data, product catalog, selection rules, document processing, and AI provider access. Specify typed API contracts, input provenance, errors, and response states.
- **Data.** Model products, facepieces, filters, compatibility records, evidence documents, versioned rules, conditions, recommendations, and sessions. Use object storage for uploaded documents when uploads are enabled. Preserve the catalog and rule versions used for each recommendation.
- **External data.** Place weather and air quality providers behind backend adapters. Compare coverage in the target market, refresh frequency, units, licensing, and outages. Specify how users override automatic inputs and how stale or missing readings are presented. Keep provider credentials server-side.
- **Operations.** Specify a deployment plan, reviewer access control, encrypted transport, secrets management, upload validation, retention and deletion, rate limits, audit events, and monitoring. Define what the application can do if weather, air quality, or AI services are unavailable.

## 4. Evaluate AI API integration options

Recommend a server-side provider adapter with a common schema. Compare providers on extraction accuracy, support for PDFs and scanned pages, structured output, data retention, regional availability, latency, and cost. Propose one provider to evaluate first and at least one alternative.

| Integration | Suggested use |
|---|---|
| **OpenAI Responses API** | Evaluate as the first option for structured extraction from SDS and manufacturer PDFs, normalization of free-text inputs, and source-grounded explanations. Use [Structured Outputs](https://developers.openai.com/api/docs/guides/structured-outputs) and [file inputs](https://developers.openai.com/api/docs/guides/file-inputs). |
| **Anthropic Claude API** | Evaluate as an alternative for document extraction using [PDF support](https://platform.claude.com/docs/en/build-with-claude/pdf-support) and [structured outputs](https://platform.claude.com/docs/en/build-with-claude/structured-outputs). |
| **Google Gemini API** | Evaluate as an alternative for document and table extraction using [document understanding](https://ai.google.dev/gemini-api/docs/document-processing) and [structured outputs](https://ai.google.dev/gemini-api/docs/structured-output). |

Define three AI uses: extract candidate SDS or manufacturer fields with page references, convert user descriptions into editable form fields, and explain a result using approved evidence. Require server-side schema and evidence checks, user confirmation of extracted work conditions, and reviewer approval of catalog changes. Treat uploaded documents as untrusted input. Specify safeguards for prompt injection, confidential SDS content, incomplete extraction, unsupported claims, and provider outages. The validated selection service owns product eligibility, compatibility, and safety-critical decisions. Manual entry and the selection service remain available when the AI service is offline.

## 5. Structure the specification

Include the following sections in the generated specification:

1. Product goals, target users, supported scenarios, assumptions, and open decisions.
2. Proposed menu, user flows, functional requirements, and result states.
3. Manufacturer evidence collection, catalog approval, and selection-method validation plan.
4. Architecture, data model, API contracts, and external service dependencies.
5. AI provider comparison, evaluation dataset, human review, and fallback behavior.
6. Accessibility, security, privacy, reliability, deployment, and maintenance.
7. Acceptance criteria covering manual and live weather inputs, stale data, mixed pollutants, unknown chemicals, missing exposure data, incompatible filters, evidence traceability, faulty AI extraction, external API outages, and timer recovery after a reload.
