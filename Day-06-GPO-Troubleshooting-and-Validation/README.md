# Week 3 - Day 6: GPO Troubleshooting, Scope Conflicts & Policy Validation

## Objective
The objective of this lab was to troubleshoot Group Policy behavior in an Active Directory environment, identify conflicting policy application, and restore normal user functionality through structured debugging and validation techniques.

---

## Environment
- Domain Controller: DC01  
- Client Machine: CLIENT01  
- Domain: corp.geekytech.local  
- User: CORP\jcarter  
- Primary OU: IT OU  
- Secondary OU (initial test): Lab-Workstations OU  

---

## Initial Lab Goal
The original goal was to validate OU-based Group Policy targeting and confirm proper application of user restrictions.

---

## Issues Encountered

During the lab, multiple unexpected restrictions appeared on the client system:

- Command Prompt became inaccessible  
- Win + R (Run dialog) was disabled  
- Control Panel access was restricted  

At first, these behaviors appeared inconsistent and suggested a potential policy failure or misconfiguration.

---

## Troubleshooting Process Used

The following structured troubleshooting methods were applied:

### 1. Policy Verification (Scope Analysis)
- Checked GPO linking across multiple OUs
- Identified that Desktop-Restrictions-GPO was linked to:
  - IT OU
  - Lab-Workstations OU (duplicate link issue)

This created overlapping policy application and confusion in enforcement scope.

---

### 2. Client-Side Validation
- Used `gpresult` equivalent via GUI tools due to client restrictions
- Observed that the GPO was being applied but also showing filtered/denied behavior at different stages

This indicated **scope conflict rather than missing policy application**

---

### 3. GPO Inspection (Settings Review)
Inside Desktop-Restrictions-GPO, the following settings were identified as enabled:

- Prevent access to Command Prompt  
- Remove Run menu from Start Menu  
- Prohibit access to Control Panel and PC settings  

These settings collectively explained all observed restrictions.

---

### 4. Conflict Isolation
- Removed duplicate GPO link from Lab-Workstations OU
- Reduced policy application path to a single OU (IT OU)

This eliminated conflicting enforcement paths.

---

### 5. Controlled Reset Approach
Instead of immediately deleting the GPO, a staged rollback was performed:
- Disabled all restrictive settings inside the GPO
- Preserved GPO structure for future reuse

---

### 6. Policy Refresh & Validation
- Performed logoff/logon cycle on client machine
- Verified restoration of system access

---

## Root Cause Analysis

The issue was caused by:

1. **Overlapping GPO Links**
   - Same GPO applied to multiple OUs simultaneously

2. **Multiple Active Restrictions**
   - CMD, Run menu, and Control Panel restrictions all enabled together

3. **Scope Misinterpretation During Testing**
   - Initial assumption of broken policy instead of layered enforcement behavior

---

## Resolution

- Removed duplicate OU link to prevent overlapping enforcement
- Disabled all restrictive settings inside the GPO
- Reapplied policy through user session refresh
- Verified restoration of system functionality

---

## Final Validation Results

After remediation:
- Command Prompt: Functional  
- Win + R: Functional  
- Control Panel: Functional  

All previous restrictions were successfully removed.

---

## Troubleshooting Techniques Applied

This lab utilized real-world IT troubleshooting approaches:

- Scope validation (OU vs domain vs inheritance)
- Policy inspection (inside GPO settings)
- Client-side validation testing
- Incremental rollback strategy
- Controlled isolation of variables
- Service behavior verification through user session testing

---

## Key Learnings

- GPOs can apply cumulatively and create unexpected compound effects
- OU structure is critical in preventing overlapping policy enforcement
- “Enabled” does not always indicate correct or intended behavior
- Troubleshooting must isolate:
  - scope
  - settings
  - application behavior
- Systematic rollback is safer than immediate deletion or aggressive changes

---

## Conclusion

This lab demonstrated advanced Group Policy troubleshooting techniques in an Active Directory environment. It highlighted the importance of structured debugging, scope awareness, and controlled remediation. The exercise reinforced real-world IT skills including isolation of policy conflicts, validation of enforcement behavior, and safe rollback strategies.