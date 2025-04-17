# **User Story: Use Renamed Variable Names in JSON Payload for LLM**

**As** an Engineer supporting the LLM integration,

**I want** the JSON payload delivered to the LLM to use only the business-approved **Renamed Variable Names** instead of the original  **iHub Account/Variable Names** ,

**So that** the payload is human-readable, consistent, and aligned with approved business terminology.

**This includes removing internal suffixes like “FR” and preserving symbols like “%” only when explicitly defined.**

---

## **Acceptance Criteria**

### **Scenario 1: Replace iHub Account/Variable Names with Renamed Variable Names**

**Given** a mapping document that defines a Renamed Variable Name for each iHub Account/Variable Name,

**And** a JSON payload that currently uses iHub Account/Variable Names as keys,

**When** preparing the final JSON for delivery to the LLM,

**Then** each key in the JSON must be replaced with its corresponding Renamed Variable Name from the mapping document.

---

### **Scenario 2: Preserve metric values during key replacement**

**Given** metric values associated with the original iHub Account/Variable Names,

**When** the Renamed Variable Names are substituted as JSON keys,

**Then** the metric values must remain unchanged in the final JSON payload.

---

### **Scenario 3: Remove internal system suffixes like “FR”, “UCA”, or “PP”**

**Given** iHub Account/Variable Names that contain suffixes used for system tagging (e.g., “FR”),

**And** a Renamed Variable Name in the mapping that excludes these suffixes,

**When** the JSON is prepared,

**Then** the suffix must not appear in the JSON key or any narrative generated using that field name.

---

### **Scenario 4: Preserve symbols like (%) only when explicitly included**

**Given** that some Renamed Variable Names in the mapping include semantic indicators such as the percent sign (%),

**When** the key is added to the final JSON,

**Then** the symbol must be included exactly as defined in the mapping,

**And** no additional symbols should be inferred or carried over from the iHub name.

---

### **Scenario 5: Do not display iHub Account/Variable Names in narratives**

**Given** that a metric has a Renamed Variable Name defined in the mapping,

**When** the metric is used in narrative sections (e.g., LLM-generated summaries),

**Then** the original iHub Account/Variable Name (e.g., from column D in the mapping file) must not be shown anywhere in the output.
