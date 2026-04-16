# Week 3 – Day 1: Group Policy Introduction and Setup

## Objective
Create, link, and configure a Group Policy Object (GPO) to control user behavior in an Active Directory environment.

---

## Environment
- DC01 (Domain Controller)
- CLIENT01 (Domain-joined machine)
- Domain: corp.geekytech.local

---

## Steps Completed

### 1. Opened Group Policy Management
- Accessed Group Policy Management Console (GPMC)

---

### 2. Reviewed Default Domain Policies
- Identified:
  - Default Domain Policy
  - Default Domain Controllers Policy

---

### 3. Created New GPO
- Created GPO:
  Disable-Control-Panel-GPO

---

### 4. Linked GPO to Domain
- Linked GPO to:
  corp.geekytech.local

---

### 5. Configured Policy Setting
- Navigated to:
  User Configuration → Administrative Templates → Control Panel
- Enabled:
  Prohibit access to Control Panel and PC settings

---

### 6. Forced Policy Update
- Ran:
  gpupdate /force on CLIENT01

---

### 7. Validation Test
- Attempted to open Control Panel
- Access was successfully blocked

---

## Key Concepts Learned
- Group Policy Object (GPO) creation and management
- Linking GPOs to domains
- User-based policy enforcement
- Centralized system control
- Policy update and validation using gpupdate

---

## Outcome
Successfully implemented and enforced a Group Policy that restricts user access to the Control Panel across the domain environment.