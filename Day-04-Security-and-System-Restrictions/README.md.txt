# Week 3 - Day 4: Group Policy Troubleshooting, Scope Fixes & Validation

## Objective
The goal of this lab was to create, apply, and troubleshoot Group Policy Objects (GPOs) in an Active Directory environment while learning how scope (Domain vs OU) affects policy behavior.

---

## Environment
- Domain Controller: DC01
- Client Machine: CLIENT01
- User: CORP\jcarter
- OU: Lab-Workstations

---

## What Was Completed

### 1. Desktop Restrictions GPO
- Created to restrict user access to system tools
- Initially tested in multiple scopes (Domain + OU), which caused confusion
- Final configuration: linked to Lab-Workstations OU only
- Successfully restricted Control Panel access while maintaining system usability

---

### 2. Security / Execution Policy Testing
- Software Restriction Policies were introduced for application control testing
- Initial configuration caused confusion due to overly broad settings (Disallowed default behavior)
- Policy was reset to a safe baseline (“Unrestricted”) to restore system stability
- Result: normal application execution behavior restored

---

### 3. Active Directory Scope Troubleshooting
- Multiple GPOs were initially visible under both Domain and OU
- Investigation showed that only OU-linked GPOs were actively enforcing policies
- Domain-level entries were not actively linked (inactive listings, not applied policies)

---

### 4. Control Panel Restriction
- Successfully applied via GPO
- Confirmed working as intended in OU-based scope

---

## Issues Encountered

### Issue 1: GPO Scope Confusion (Domain vs OU)
- GPOs appeared under Domain and OU, leading to confusion about enforcement
- Some policies were not actually active at domain level

**Resolution:**
- Confirmed OU-based linking is the correct enforcement method
- Standardized lab configuration to Lab-Workstations OU

---

### Issue 2: Software Restriction Policy Misconfiguration
- Initial SRP configuration was too restrictive and caused unpredictable behavior
- Required reset to restore stable environment behavior

**Resolution:**
- Reset SRP to Unrestricted baseline
- Avoided global enforcement during testing phase

---

### Issue 3: Removable Storage Policy (Incomplete Validation)
- USB/removable device restriction policy was configured at a basic level
- Full validation and fine-tuning testing was not completed during this lab session

**Status:**
- Partially implemented
- Requires future testing for full enforcement verification

---

## Final Validation Results (CLIENT01 - CORP\jcarter)

- Win + R: Working
- CMD: Working
- Desktop access: Stable
- Control Panel: Restricted as expected
- System behavior: Stable after GPO cleanup
- USB behavior: Partially restricted / not fully validated

---

## Key Learnings

- GPO scope (Domain vs OU) directly impacts policy enforcement behavior
- Multiple linked GPOs can create conflicting or confusing results
- Software Restriction Policies must be carefully configured to avoid system lockouts
- OU-based design is best practice for controlled lab environments
- Not all policies require full completion in a single session; documentation of partial implementation is valid in real IT environments

---

## Conclusion

This lab demonstrated real-world Active Directory troubleshooting including GPO creation, misconfiguration, scope conflicts, recovery procedures, and system stabilization. The environment was successfully corrected and stabilized through proper OU targeting and removal of conflicting domain-level assumptions.