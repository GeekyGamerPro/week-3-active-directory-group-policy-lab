# Week 3 - Day 5: OU-Based Group Policy Targeting & Validation

## Objective
The goal of this lab was to understand and validate how Group Policy Objects (GPOs) apply through Organizational Units (OUs), and to verify policy enforcement behavior on a client machine.

---

## Environment
- Domain Controller: DC01
- Client Machine: CLIENT01
- Domain: corp.geekytech.local
- User Account: CORP\jcarter
- OU Structure: Lab-Workstations

---

## What Was Implemented

### 1. OU-Based Group Policy Targeting
- A single GPO (Desktop-Restrictions-GPO) was linked to the **Lab-Workstations OU**
- Confirmed that OU-level linking is the primary method for scoped policy application
- Verified that no conflicting active GPO links existed at the domain level

---

### 2. Security Filtering
- Default configuration used:
  - Authenticated Users
- No custom security filtering applied
- Policies applied broadly within OU scope

---

### 3. Control Panel Restriction Policy
- Configured using:
  - “Prohibit access to Control Panel and PC settings” (Enabled)
- Intended to restrict user access to Control Panel through user-based policy enforcement

---

## Validation Results (CLIENT01 - CORP\jcarter)

- Win + R: Functional
- Command Prompt: Functional
- Desktop access: Normal
- Control Panel: Accessible (policy did not visibly enforce restriction in this session)

---

## Key Learnings

- OU-based linking determines where GPOs are applied
- GPO visibility does not guarantee active enforcement on the client
- User Configuration policies depend on correct scope and processing context
- Policy application must always be validated from the client side
- “Enabled” status in GPO does not equal immediate or guaranteed enforcement

---

## Conclusion

This lab reinforced the importance of Organizational Unit (OU) targeting in Active Directory Group Policy management. It demonstrated that correct GPO configuration must always be paired with client-side validation to confirm actual enforcement behavior.

The exercise highlighted real-world differences between policy configuration and policy application, strengthening understanding of Active Directory scope and troubleshooting fundamentals.