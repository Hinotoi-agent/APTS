# Authority Delegation Matrix Template

Informative Appendix (non-normative)

This appendix provides an illustrative Authority Delegation Matrix (ADM) template for autonomous penetration testing operations. It is intended to help platform operators, customers, and reviewers implement and verify the requirements in the Human Oversight and Auditability domains. It does not prescribe one mandatory format for all platforms.

## Purpose

APTS requires organizations to maintain a documented Authority Delegation Matrix defining who can approve which actions and how escalation should occur. In practice, operators and reviewers benefit from a concrete starter template that makes those requirements easier to implement, review, and audit consistently.

This appendix shows:

- a simple starter matrix
- the minimum fields that should be documented
- supporting notes for escalation, backup authority, and dual approval
- review questions customers and reviewers can use during evaluation

## Design Principles

An Authority Delegation Matrix should:

- be role-based rather than person-based
- define authority limits clearly for each action category
- identify backup approvers for continuity and shift coverage
- require escalation when the current approver lacks authority
- identify actions that need dual approval
- link decisions to auditable approval records
- be reviewed after staffing, role, or operational changes

## Recommended Minimum Fields

Recommended columns:

- `action_category`
- `autonomy_level`
- `impact_or_risk_threshold`
- `primary_approver_role`
- `backup_approver_role`
- `dual_approval_required`
- `escalate_to`
- `evidence_record`
- `review_frequency`

## Example Starter Matrix

| Action category | Autonomy level | Impact or risk threshold | Primary approver role | Backup approver role | Dual approval required | Escalate to | Evidence record | Review frequency |
|---|---|---|---|---|---|---|---|---|
| Standard exploitation attempt | L2 | CVSS 7.0-8.9 | Engagement Lead | Security Operations Lead | No | Practice Director | Approval ticket or signed workflow record | Quarterly |
| Critical exploitation attempt | L2-L3 | CVSS 9.0+ | Engagement Lead | Security Operations Lead | Yes | Practice Director | Approval ticket plus second approver record | Quarterly |
| Lateral movement beyond initial compromise | L2-L3 | Any approved case | Security Operations Lead | Practice Director | Yes | Executive Sponsor | Approval record linked to engagement ID | Quarterly |
| Sensitive data access for validation | L2-L3 | Restricted or regulated data | Security Operations Lead | Privacy or Compliance Lead | Yes | Executive Sponsor | Approval record plus data-handling justification | Quarterly |
| Scope change or new target inclusion | L2-L4 | Any scope expansion | Asset Owner Delegate | Engagement Lead | Yes | Customer Approver | Scope-change approval and updated Rules of Engagement | Per engagement and quarterly |
| Kill switch activation | L1-L4 | Safety breach or legal trigger | On-Call Operator | Security Operations Lead | No | Practice Director | Kill switch event log and incident record | Quarterly |
| Engagement continuation after legal or compliance trigger | L1-L4 | Any legal or compliance escalation | Legal or Compliance Lead | Executive Sponsor | Yes | Customer Executive Contact | Escalation decision log and legal review record | Quarterly |

## Field Guidance

### Action category

Describe the action in a way that matches the platform's approval workflow and safety controls.

Examples:

- exploitation attempt
- lateral movement
- data access
- scope change
- irreversible action
- kill switch activation

### Autonomy level

Document the autonomy level where the approval rule applies.

Examples:

- `L1`
- `L2`
- `L3`
- `L4`
- `L2-L3`

### Impact or risk threshold

State the condition that determines whether this approval path applies.

Examples:

- `CVSS >= 7.0`
- `Any production target`
- `Any sensitive data access`
- `Any scope expansion`

### Primary approver role

Use a role name, not a person's name.

Examples:

- `Engagement Lead`
- `Security Operations Lead`
- `Legal or Compliance Lead`

### Backup approver role

Identify the authorized fallback when the primary approver is unavailable.

This supports continuity and shift handoff requirements.

### Dual approval required

Use a simple `Yes` or `No` value.

Dual approval is useful for:

- critical exploit attempts
- data access involving regulated information
- scope expansion
- continuation after legal or compliance escalation

### Escalate to

Identify the next authority level if the current approver lacks authority, does not respond in time, or the situation exceeds the defined threshold.

### Evidence record

State where the decision is recorded.

Examples:

- approval workflow ID
- ticket number
- signed change record
- incident case reference

### Review frequency

Document how often the matrix is reviewed.

Typical examples:

- quarterly
- after staffing changes
- before each new engagement model rollout

## Supporting Notes

### Role-based authority

Authority should be granted to defined roles, not attached informally to specific individuals. Personnel changes should trigger role reassignment and matrix review.

### No sub-delegation

Approvers should not be allowed to create ad hoc downstream approvers outside the documented matrix.

### Higher authority coverage

Organizations may allow higher-authority roles to approve actions assigned to lower-authority roles, but this should be explicit and documented.

### Link to audit trail

Every matrix row should map to an approval record, escalation record, or incident record so reviewers can verify that authority decisions were executed as documented.

## Review Questions

Customers and reviewers can use the following questions when evaluating an Authority Delegation Matrix:

- Is the matrix formally documented and current?
- Are approval authorities defined by role rather than by individual name alone?
- Does each high-risk action category have a clearly assigned approver?
- Are backup approvers identified for continuity and off-hours coverage?
- Are dual-approval conditions documented for high-risk actions?
- Is escalation defined when an approver lacks authority or misses the decision window?
- Can the operator show approval records that match the matrix?
- Is the matrix reviewed after staffing or operational changes?

## Related APTS Requirements

This appendix is especially relevant to:

- APTS-HO-004 Authority Delegation Matrix
- APTS-HO-005 Delegation Chain-of-Custody and Decision Audit Trail
- APTS-HO-019 24/7 Operational Continuity and Shift Handoff
- APTS-AR-001 Structured Event Logging with Schema Validation
- APTS-AR-011 Chain of Custody for Evidence
