

Faculty of Computers and Artificial Intelligence  
Cairo University

CS352 Advanced Software Engineering

| ID | Name | Email |
| ----- | :---: | :---: |
| 20240009 | Ahmed Ahmed | 20240009@stud.fci-cu.edu.eg |
| 20240607 | Moataz Mohamed | 20240607@stud.fci-cu.edu.eg |
| 20240197 | Rawan Mohammed | 20240197@stud.fci-cu.edu.eg |
| 20240489 | Mohamed Hossam  | 20240489@stud.fci-cu.edu.eg |

      

### **Problem Summary**

PayLink is an Egyptian digital payment company that allows customers to pay utility bills, including electricity, water, mobile, and internet bills, using digital wallets.

The company needs a reliable backend system to manage customer accounts, wallet balances, bill inquiries, and payment processing.

The main challenge is ensuring that payments are processed accurately and securely while preventing duplicate charges, insufficient-balance transactions, and incorrect wallet balances.

PayLink aims to develop a modular and reliable backend system that supports multiple billers, manages financial transactions using a ledger, handles payment failures, and provides customers with a convenient and secure payment experience.

## **2\. Stakeholders**

| Stakeholders | Responsibility |
| ----- | ----- |
| Customer | Registers, manages wallet, checks bills, and makes payments |
| Agent | Accepts payments on behalf of customers and receives commissions. |
| System Administrator | Manages billers, services, and system configurations. |
| Support Employee | Investigates payments and helps resolve customer issues. |
| Billers | Provide bill information and process payments |
| PayLink Management | Oversees operations, revenue, reliability, and business performance. |
| Engineering Team | Develops, tests, maintains, and integrates the backend system. |

**US-01 — Customer Registration**

Priority: Must  
Source: FR-1As a customer, I want to register an account so that I can access PayLink services with a basic verification level.

Acceptance Criteria

AC-1

**Given** a new customer provides valid registration information, **When** the customer submits the registration request, **Then** the system creates an account with a basic verification level.

AC-2

**Given** the registration information is invalid or the account already exists, **When** the customer submits the registration request, **Then** the system rejects the registration and displays an appropriate error.

**US-02 — Account Verification Upgrade**

Priority: Should  
Source: FR-2As a customer, I want to upgrade my account to verified so that I can access higher daily payment limits.

Acceptance Criteria

AC-1

**Given** a customer has a basic account and meets the verification requirements, **When** the verification upgrade is approved, **Then** the system changes the account level to verified and applies the 30,000 EGP daily limit.

AC-2

**Given** a customer has a basic account, **When** the verification upgrade is not approved, **Then** the system keeps the basic level and its 5,000 EGP daily limit.

**US-03 — View Wallet Balance and History**

Priority: Must  
Source: FR-3As a customer, I want to view my available balance, held balance, and transaction history so that I can track my money.

Acceptance Criteria

AC-1

**Given** the customer has a wallet, **When** the customer requests wallet details, **Then** the system displays the available balance, held balance, and transaction history.

AC-2

**Given** the customer has no previous transactions, **When** the customer views the transaction history, **Then** the system displays an empty history without an error.

**US-04 — Top Up Wallet**

Priority: Must  
Source: FR-4As a customer, I want to top up my wallet using a simulated card or agent cash so that I can have sufficient funds for payments.

Acceptance Criteria

AC-1

**Given** the customer provides a valid positive amount and selects a supported top-up method, **When** the top-up succeeds, **Then** the system records the top-up and increases the available wallet balance.

AC-2

**Given** the top-up fails, **When** the system processes the failed top-up result, **Then** the wallet balance remains unchanged.

**US-05 — Record Wallet Ledger Entries**

Priority: Must  
Source: FR-5As a PayLink financial operations stakeholder, I want every wallet balance change recorded in the ledger so that all money movements are traceable and balances are accurate.

Acceptance Criteria

AC-1

**Given** a wallet transaction changes the available or held balance, **When** the transaction is successfully processed, **Then** the system creates the corresponding ledger entries.

AC-2

**Given** a wallet balance is requested, **When** the system calculates the balance, **Then** the result is derived from ledger entries rather than directly overwriting a stored balance.

**US-06 — Manage Billers and Services**

Priority: Must  
Source: FR-6As a system administrator, I want to add, edit, and disable billers and services so that PayLink can maintain its supported payment services.

Acceptance Criteria

AC-1

**Given** an administrator provides valid details for a new biller or service, **When** the administrator saves the details, **Then** the system creates the biller or service.

AC-2

**Given** an existing biller or service is selected, **When** the administrator updates its valid details, **Then** the system saves the changes.

AC-3

**Given** an active biller or service is selected, **When** the administrator disables it, **Then** the system marks it as disabled and prevents new payments through it.

**US-07 — View Billers and Required Fields**

Priority: Must  
Source: FR-7As a customer, I want to view available billers and their required input fields so that I can provide the correct information for bill payment.

Acceptance Criteria

AC-1

**Given** the biller catalog contains active services, **When** the customer requests the biller list, **Then** the system displays the available billers and services.

AC-2

**Given** the customer selects a biller service, **When** the system loads the service details, **Then** the required input fields, such as meter or phone number, are displayed.

**US-08 — Bill Inquiry**

Priority: Must  
Source: FR-8As a customer, I want to inquire about a bill and view the amount, service fee, and total so that I can review the cost before paying.

Acceptance Criteria

AC-1

**Given** the customer selects a supported live-inquiry biller and provides valid details, **When** the customer requests a bill inquiry, **Then** the system retrieves and displays the bill amount, fee, and total.

AC-2

**Given** ElectroCo returns a bill amount of 350.00 EGP, **When** the system calculates the standard electricity fee, **Then** the system displays a 2.50 EGP fee and a 352.50 EGP total.

AC-3

**Given** the biller inquiry fails, **When** the customer requests the bill information, **Then** the system reports the inquiry failure without charging the wallet.

**US-09 — Pay a Bill**

Priority: Must  
Source: FR-9As a customer, I want to pay a bill using my wallet so that I can settle my utility bills conveniently.

Acceptance Criteria

AC-1

**Given** the customer has sufficient funds and passes the required payment checks, **When** the customer confirms a valid bill payment, **Then** the system holds the required amount and sends the payment to the biller.

AC-2

**Given** the biller confirms the payment, **When** the system processes the confirmation, **Then** the system finalizes the charge and marks the payment Completed.

AC-3

**Given** the customer has insufficient available funds, **When** the customer attempts to pay, **Then** the system rejects the payment without charging the wallet.

**US-10 — Prevent Duplicate Payments**

Priority: Must  
Source: FR-10As a customer, I want repeated payment requests to be handled safely so that I am not charged twice for the same payment.

Acceptance Criteria

AC-1

**Given** a payment request has already been processed with an idempotency key, **When** the same request is submitted again with that key, **Then** the system returns the original payment result.

AC-2

**Given** a repeated request uses an existing idempotency key, **When** the system handles the repeated request, **Then** no additional payment or wallet charge is created.

**US-11 — Manage Payment Life Cycle**

Priority: Must  
Source: FR-11As a payment operations stakeholder, I want payments to follow defined states and transitions so that payment processing remains consistent and traceable.

Acceptance Criteria

AC-1

**Given** a payment is Initiated and passes fraud and balance checks, **When** the system reserves the funds, **Then** the payment moves to FundsHeld.

AC-2

**Given** a payment is SentToBiller, **When** the biller confirms, refuses, or times out, **Then** the payment moves to Completed, Failed, or Unknown respectively.

AC-3

**Given** a payment is in a particular state, **When** an event requests a transition not permitted by the defined life cycle, **Then** the system rejects the invalid transition.

**US-12 — Hold and Release Funds**

Priority: Must  
Source: FR-12As a customer, I want my funds to be held during payment processing and released when payment fails so that my wallet balance remains accurate.

Acceptance Criteria

AC-1

**Given** a payment passes validation and sufficient funds are available, **When** the system prepares to contact the biller, **Then** the required amount is moved from available to held balance before the biller call.

AC-2

**Given** the biller confirms that the payment failed, **When** the system handles the failure and releases the hold, **Then** the reserved amount returns to the available wallet balance and the payment reaches Refunded.

**US-13 — Handle Payment Timeouts and Retries**

Priority: Must  
Source: FR-13As a customer, I want timed-out payments to be tracked and checked again so that my money is not lost or refunded incorrectly.

Acceptance Criteria

AC-1

**Given** a live biller does not respond within 10 seconds, **When** the payment request times out, **Then** the system marks the payment Unknown and keeps the money held.

AC-2

**Given** a payment remains Unknown, **When** the scheduled retry times are reached, **Then** the system re-queries the payment after 1, 5, and 15 minutes, up to three retries.

AC-3

**Given** the payment remains Unknown after all retries, **When** the retry process finishes without a confirmed outcome, **Then** the system waits for reconciliation and does not automatically refund the money.

# **1\. Remaining User Stories and Acceptance Criteria**

## **US-14 — Handle TopUpNet Mobile Top-up Callbacks**

**Priority:** Must    **Source:** FR-14

As the PayLink system, I want to receive asynchronous callbacks from TopUpNet and ignore duplicate callbacks so that a mobile top-up payment is completed only once.

**Acceptance Criteria**

· **AC-1:** Given a payment has been sent to TopUpNet and is awaiting its asynchronous outcome, When TopUpNet first replies “accepted”, Then the payment remains in SentToBiller while awaiting the callback.

· **AC-2:** Given a payment is awaiting a callback, When TopUpNet sends a valid success callback, Then the payment moves to Completed and its held funds are finalized exactly once.

· **AC-3:** Given a payment is awaiting a callback, When TopUpNet sends a valid failed callback, Then the payment moves to Failed and the hold is released so the payment becomes Refunded.

· **AC-4:** Given the payment has already reached Completed or Failed through a callback, retry, or settlement reconciliation, When a late or repeated callback arrives, Then it cannot change the final state or create another ledger movement, and the callback is logged.

· **AC-5:** Given TopUpNet sends the same success callback twice, When the second callback is received, Then the system ignores and logs the duplicate.

## **US-15 — Support Multiple Biller Integrations**

**Priority:** Must    **Source:** FR-15

As a PayLink customer, I want PayLink to support different billers through their required integration formats so that I can pay supported utility and mobile services.

**Acceptance Criteria**

· **AC-1:** Given ElectroCo is selected, When PayLink sends an inquiry or payment, Then it uses the ElectroCo REST/JSON contract.

· **AC-2:** Given AquaCo is selected, When PayLink sends a request, Then it uses AquaCo's SOAP-style XML over HTTP contract and maps its field names and error codes.

· **AC-3:** Given AquaCo rejects a payment because the requested payment is above the bill amount, When PayLink receives that response, Then the payment moves to Failed, the hold is released, and the customer receives a failure notification with a clear reason.

· **AC-4:** Given TopUpNet is selected, When PayLink submits a mobile top-up payment, Then it handles the initial accepted response and the later asynchronous callback.

· **AC-5:** Given a new biller is added, When the integration is implemented and configured, Then only the Biller Integration module and configuration need to change; existing modules remain unchanged.

## **US-16 — Calculate Service Fees and Promotions**

**Priority:** Must    **Source:** FR-16

As a customer, I want the service fee to be calculated according to the selected service's fee rules so that I can see the correct total before confirming payment.

**Acceptance Criteria**

· **AC-1:** Given the selected service is electricity or water and no applicable promotion is active, When the fee is calculated, Then the fee is 2.50 EGP.

· **AC-2:** Given the selected service is mobile top-up and no applicable promotion is active, When the fee is calculated, Then the fee is 1.5% of the amount with a minimum of 1 EGP.

· **AC-3:** Given the selected service is internet and no applicable promotion is active, When the fee is calculated, Then the fee is 2 EGP for amounts up to and including 200 EGP and 4 EGP for amounts above 200 EGP.

· **AC-4:** Given a promotion is active for the selected biller and the current date is within its configured start and end dates, When the fee is calculated, Then the fee is 0 EGP for that biller during the promotion period.

· **AC-5:** Given the fee is calculated, When the amount requires fractional precision, Then the system uses an exact decimal type and does not use floating-point arithmetic; the final rounding convention must be confirmed by the team.

## **US-17 — Pay Through an Agent**

**Priority:** Should    **Source:** FR-17

As an agent, I want to make a bill payment on behalf of a customer so that the customer can pay through an agent terminal and the agent can earn the applicable commission.

**Acceptance Criteria**

· **AC-1:** Given an agent is authorized and supplies the required customer and bill details, When the agent submits a payment request, Then PayLink processes it subject to the normal payment checks.

· **AC-2:** Given an agent-assisted payment reaches Completed, When commission is calculated, Then the agent receives 40% of the service fee in the agent wallet.

· **AC-3:** Given the payment is Initiated, FundsHeld, SentToBiller, or Unknown, When the system evaluates commission, Then it does not credit commission until the payment reaches Completed.

· **AC-4:** Given the service fee is 0 EGP during a promotion, When the payment completes, Then the commission calculated as 40% of the fee is 0 EGP.

· **AC-5:** Given an agent-assisted payment is submitted, When the system determines the debit wallet and applicable limits/velocity identity, Then it follows the policy confirmed by the team; these policies are currently open questions.

## **US-18 — Enforce Payment Amount and Daily Limits**

**Priority:** Must    **Source:** FR-18

As a customer, I want payments that exceed the allowed single-payment or daily limit to be rejected with a clear reason so that payment limits are consistently enforced.

**Acceptance Criteria**

· **AC-1:** Given a payment amount is below 5 EGP or above 10,000 EGP, When the system validates it, Then the payment moves to Rejected, no funds are held, and a clear reason is returned.

· **AC-2:** Given a basic account would exceed its 5,000 EGP daily limit, When it submits a payment, Then the payment moves to Rejected, no funds are held, and the customer receives a clear reason.

· **AC-3:** Given a verified account would exceed its 30,000 EGP daily limit, When it submits a payment, Then the payment moves to Rejected, no funds are held, and the customer receives a clear reason.

· **AC-4:** Given the payment amount and applicable daily total are within limits, When the remaining checks pass, Then payment processing may continue.

· **AC-5:** Given a payment is rejected by a limit check, When the result is recorded, Then no amount is moved to the held balance.

## **US-19 — Block Excessive Payment Activity**

**Priority:** Should    **Source:** FR-19

As PayLink, I want to block an account for 10 minutes when it makes more than 5 payments in 60 seconds so that excessive payment activity is controlled.

**Acceptance Criteria**

· **AC-1:** Given an account exceeds 5 payments within 60 seconds, When the velocity rule is evaluated, Then the account is blocked for 10 minutes.

· **AC-2:** Given an account is blocked by the velocity rule, When it attempts a payment during the block period, Then the payment moves to Rejected, no funds are held, and a clear reason is returned.

· **AC-3:** Given the 10-minute block period has ended, When the account submits a payment and no other rule rejects it, Then normal payment checks continue.

· **AC-4:** Given the Brief defines the rule in terms of “payments”, When the team decides whether rejected attempts count and whether the window is sliding or fixed, Then that decision is recorded; until then these details remain unresolved.

## **US-20 — Search Payment History by Reference**

**Priority:** Must    **Source:** FR-20

As a support employee, I want to search for a payment using its reference and view its full history so that I can investigate customer payment issues.

**Acceptance Criteria**

· **AC-1:** Given a support employee is authorized, When they search using a valid PayLink payment reference, Then the matching payment is displayed.

· **AC-2:** Given a payment is found, When the support employee opens its details, Then the system displays its current state and recorded history, including relevant state changes and processing events.

· **AC-3:** Given no payment matches the entered reference, When the support employee searches, Then the system displays a clear no-result message.

· **AC-4:** Given the meaning and format of “payment reference” have not yet been agreed, When the team confirms whether it means PayLink payment ID, biller reference, or idempotency key, Then the agreed definition is documented.

## **US-21 — Block and Unblock Customer Accounts**

**Priority:** Should    **Source:** FR-21

As a support employee, I want to block or unblock a customer account so that support can respond to account issues and prevent new unauthorized payment activity.

**Acceptance Criteria**

· **AC-1:** Given a support employee is authorized and selects an Active account, When they block it, Then the account status becomes Blocked and new payment attempts are rejected with no funds held.

· **AC-2:** Given an account is Blocked, When an authorized support employee unblocks it, Then the account status becomes Active.

· **AC-3:** Given an account is blocked or unblocked, When the action is saved, Then the system records the administrative action in the audit log.

· **AC-4:** Given a payment is already in progress when an account is blocked, When the system evaluates the block, Then the handling of that in-flight payment follows the policy confirmed by the team; the block must not silently create an invalid payment-state transition.

## **US-22 — Notify Customers About Payment Outcomes**

**Priority:** Must    **Source:** FR-22

As a customer, I want to receive an SMS and a push notification when my payment completes or fails so that I know its outcome.

**Acceptance Criteria**

· **AC-1:** Given a payment reaches Completed, When the final outcome is processed, Then the system sends an SMS and push notification confirming completion.

· **AC-2:** Given a payment reaches Failed, When the final outcome is processed, Then the system sends an SMS and push notification stating that the payment failed and giving a clear reason.

· **AC-3:** Given a payment becomes Unknown, When its outcome is not yet confirmed, Then the customer is told that the payment is being processed and the money remains held.

· **AC-4:** Given a payment is Rejected before funds are held, When the system handles the rejection, Then notification behavior follows the team-confirmed policy; FR-22 explicitly requires notifications on completion and failure.

· **AC-5:** Given the notification provider is unavailable, When a payment completes or fails, Then notification failure does not reverse or prevent the payment outcome.

## **US-23 — Retry Failed Notifications**

**Priority:** Should    **Source:** FR-23

As PayLink, I want failed SMS or email notifications to be retried and then marked undelivered so that temporary notification failures are handled and tracked.

**Acceptance Criteria**

· **AC-1:** Given an SMS or email notification fails, When the retry process runs, Then the system retries delivery 3 times.

· **AC-2:** Given a retry succeeds, When the provider confirms delivery, Then the notification is marked delivered and no further retry is attempted.

· **AC-3:** Given all 3 retries fail, When the final retry fails, Then the notification is marked undelivered.

· **AC-4:** Given the SMS provider is down when a payment completes, When notification delivery fails, Then the payment remains Completed independently of notification delivery and the SMS retry process continues.

· **AC-5:** Given push notifications are required by FR-22 but FR-23's retry rule names SMS/email, When push retry behavior is needed, Then it follows a separately confirmed policy rather than assuming the SMS/email rule applies.

## **US-24 — Update Fees and Limits Without Redeployment**

**Priority:** Should    **Source:** FR-24

As an admin, I want to edit configurable fee and limit values without redeploying the application so that business rules can be updated efficiently.

**Acceptance Criteria**

· **AC-1:** Given an authorized admin enters valid configurable fee or limit values, When the admin saves them, Then the system stores the updated configuration.

· **AC-2:** Given updated values have been saved, When a new payment is evaluated, Then the system uses the current configured values.

· **AC-3:** Given invalid configuration values are submitted, When the admin attempts to save them, Then the system rejects the changes and displays a validation error.

· **AC-4:** Given the Brief says the section 2.6 business rules belong in configuration, When the team defines which values may be edited through the admin function, Then that list is documented; the current FR-24 wording specifically names fees and limits.

## **US-25 — Maintain an Audit Log**

**Priority:** Must    **Source:** FR-25

As an admin, I want every money movement and administrative action recorded in an audit log so that important actions are traceable and reviewable.

**Acceptance Criteria**

· **AC-1:** Given a money movement occurs, When it is recorded, Then the system creates an audit record containing who, when, and why.

· **AC-2:** Given an administrative action is performed, When it is completed, Then the system creates an audit record containing the actor, timestamp, and action details.

· **AC-3:** Given an authorized reviewer retrieves audit records, When the records are displayed, Then the original audit entries are not altered by viewing them.

## **US-26 — Reconcile Payments Against Settlement Files**

**Priority:** Should    **Source:** FR-26

As a support employee, I want PayLink to compare its payment records with the biller's daily settlement file so that differences and unresolved payments can be identified.

**Acceptance Criteria**

· **AC-1:** Given a biller settlement file is received, When reconciliation runs, Then the system compares settlement entries with PayLink payment records and produces a daily report.

· **AC-2:** Given the settlement file lists a payment that PayLink records as Failed, When reconciliation detects the mismatch, Then it flags the difference for support review and does not silently overwrite the state.

· **AC-3:** Given a payment is Unknown and the settlement file confirms that the biller received it, When reconciliation processes the record, Then the payment moves to Completed.

· **AC-4:** Given a payment is Unknown and the settlement file confirms no such payment was received, When reconciliation processes the record, Then the payment moves to Failed and the hold is released so the payment becomes Refunded.

· **AC-5:** Given a settlement entry has no matching PayLink payment, When reconciliation runs, Then the unmatched settlement entry is flagged in the report.

· **AC-6:** Given a PayLink payment has no matching settlement entry, When reconciliation runs, Then the discrepancy is flagged for review; an Unknown payment may move to Failed only when the reconciliation outcome establishes that the biller did not receive it.

## **US-27 — Request a Refund for a Completed Payment**

**Priority:** Could    **Source:** FR-27

As a customer, I want to request a refund for a completed payment so that support can review the request and approve or reject it.

**Acceptance Criteria**

· **AC-1:** Given a customer has a Completed payment, When they submit a refund request, Then the system creates a separate refund request record linked to the payment.

· **AC-2:** Given a refund request is pending, When authorized support approves it, Then the system records the decision and initiates the refund workflow using separate refund/ledger entries according to the confirmed refund policy.

· **AC-3:** Given a refund request is pending, When authorized support rejects it, Then the system records the rejection and does not issue a refund.

· **AC-4:** Given a refund request is resolved, When another decision is submitted for the same request, Then the system prevents duplicate processing.

· **AC-5:** Given Completed is a final payment state in the life cycle, When a refund is approved, Then the original payment remains Completed; the refund is represented separately and does not transition the payment from Completed to Refunded.

## **US-28 — View Daily Operational Totals**

**Priority:** Could    **Source:** FR-28

As an admin, I want to view daily operational totals so that I can monitor PayLink's payment activity and revenue.

**Acceptance Criteria**

· **AC-1:** Given payment activity exists for a selected day, When the admin requests the daily summary, Then the system displays the total number of payments.

· **AC-2:** Given completed payments have generated service fees and agent commissions, When the admin requests the daily summary, Then it displays total fees earned and total commissions paid.

· **AC-3:** Given payment attempts have failed for one or more billers, When the admin requests the daily summary, Then it displays failures per biller.

· **AC-4:** Given the business-day boundary and inclusion rules for Failed, Rejected, Unknown, and Completed payments are not specified, When the team confirms the reporting definition, Then the selected timezone and counting rules are documented.

# **2\. Non-Functional Requirements**

The six expected quality attributes and base targets come from Student Brief §3.3. Measurement methods are added below. NFR-03's numeric threshold is explicitly a proposal, not a Brief-mandated value.

| ID / Priority | Requirement and target | Measurement method | Verification source | Status |
| :---- | :---- | :---- | :---- | :---- |
| NFR-01 — Correctness / Must | Zero double charges and zero negative wallet balances in duplicate-request and concurrent-payment tests. | Run the duplicate idempotency test and simultaneous-wallet-payment integration test; assert zero duplicate ledger charges and non-negative available balance. | Automated integration tests; CI test report. | NFR-03 target proposed; other targets from Brief |
| NFR-02 — Performance / Must | Sustain 100 payments per second for 1 minute against mock billers. | Run a 60-second load test against mock billers; report achieved throughput and error count. Test environment/hardware and acceptable latency/error threshold must be recorded by the team. | Load-test report attached to Phase 1/CI. | NFR-03 target proposed; other targets from Brief |
| NFR-03 — Resilience / Should | A biller outage must not stop payments to other billers. Proposed measurable target: at least 99% of requests to healthy mock billers complete their normal processing during a simulated outage of a different biller. | Run a fault-injection integration test: disable one mock biller and send requests to the remaining healthy mock billers; report success percentage. The 99% target is a team proposal and needs approval. | Fault-injection test report; team approval of proposed numeric threshold. | NFR-03 target proposed; other targets from Brief |
| NFR-04 — Modifiability / Should | Adding a biller touches only the Biller Integration module and configuration; existing modules remain unchanged. | Perform a change-impact review for a test biller and compare changed-file list; verify no changes outside Biller Integration/configuration. | Pull-request changed-file list and reviewer checklist. | NFR-03 target proposed; other targets from Brief |
| NFR-05 — Auditability / Must | 100% of money movements have an audit record containing who, when, and why. | Run tests covering every money-movement operation and compare ledger/money-movement records with audit records; report percentage with all three fields. | Automated audit completeness test and CI report. | NFR-03 target proposed; other targets from Brief |
| NFR-06 — Testability / Should | At least 70% line coverage on domain logic, measured in CI. | Run the configured coverage tool in GitHub Actions; report line coverage for the agreed domain-logic packages and fail the quality gate below 70%. | CI coverage artifact/report; domain package scope documented. | NFR-03 target proposed; other targets from Brief |

# **3\. Ambiguities and Open Questions**

These are questions, not confirmed requirements. For each one, the proposed direction (where useful) is clearly labelled and must be accepted or changed by the team/instructor.

| ID / Area | Question | Proposed handling / what must be decided | Status |
| :---- | :---- | :---- | :---- |
| A-01 | TopUpNet accepted/waiting state | After TopUpNet replies “accepted” but before callback, is the payment SentToBiller? | Proposed: SentToBiller, because request has been sent and callback is pending. Confirm with team and align state diagram. |
| A-02 | Agent debit wallet | Does an agent payment debit the customer's wallet or the agent's wallet? | Must be explicitly decided; do not assume. Record the chosen wallet and ledger ownership. |
| A-03 | Agent limits and velocity | Whose daily limits and velocity counter apply to agent-assisted payments: customer, agent, or both? | Must be explicitly decided and applied consistently in FR-17/18/19. |
| A-04 | Daily-limit calculation | Does the daily limit count bill amount alone or bill amount plus fee? Which payment states count? | Confirm amount basis and inclusion of Completed/Failed/Unknown/Rejected payments. |
| A-05 | Velocity rule definition | Does “more than 5 payments in 60 seconds” count rejected attempts? Is the window sliding or fixed, and is the 6th payment rejected? | Keep Brief wording “payments”; confirm counting and window semantics before implementation. |
| A-06 | Payment reference | Does the support search reference mean PayLink payment ID, biller reference, or idempotency key? | Define one canonical searchable reference and whether alternative references are also searchable. |
| A-07 | Fee rounding | How should fractional fee results be rounded when exact decimal arithmetic produces fractions smaller than the currency precision? | Brief requires exact decimal types, not floating point; confirm rounding scale and mode. Do not invent a rounding rule. |
| A-08 | Duplicate callback identity/conflict | How is a callback identified as duplicate? What if a later callback conflicts with an earlier success/failure? | Agree callback unique identifier/idempotency rule and conflict handling; final states must not be completed twice. |
| A-09 | NetCo scope | NetCo is optional and batch-based, while FR-16 includes internet fees. Is internet/NetCo included in Phase 1 scope? | Confirm whether NetCo batch integration is implemented or internet fee rule is documented/configured only for optional scope. |
| A-10 | Configurable business rules | Which section 2.6 values must be editable by admin under FR-24, beyond fees and daily limits? | Separate values fixed by Brief from which values the admin UI/API can change; document approved configuration list. |
| A-11 | Blocked account and in-flight payments | What happens to payments already FundsHeld, SentToBiller, or Unknown when an account is blocked? | Define whether blocking affects only new requests or also in-flight processing; preserve valid payment-state transitions. |
| A-12 | Rejected notifications/email | Should customers be notified on Rejected? When is email used, given FR-22 specifies SMS and push? | FR-22 mandates SMS/push on completion and failure. Confirm whether Rejected is treated as failure for notifications and where email is used. |
| A-13 | Refund vs final payment state | How can a Completed payment be refunded if Completed is a final state and Refunded is reached only from Failed after hold release? | Recommended model: keep original payment Completed; create a separate refund request and separate refund ledger entries. Team must confirm refund accounting/policy. |
| A-14 | Promotion time zone/overlap | Which time zone governs promotion start/end, and what happens if promotions overlap? | Confirm time zone and conflict rule; brief only says one chosen biller and configurable start/end dates. |
| A-15 | Support permissions | Which support actions/permissions and approvals are required for searching, blocking, unblocking, and refunds? | Use existing stakeholder role “Support Employee”; agree permission boundaries and approval requirements. |
| A-16 | Notification retry scope | Does the 3-retry rule apply to push notifications, or only SMS/email as FR-23 says? | Apply three retries to failed SMS/email per FR-23; decide push retry separately. |
| A-17 | Daily report definition | What timezone defines a day, and which states count in daily payment totals and failures? | Agree timezone and counting definitions for Completed, Failed, Rejected, and Unknown. |
| A-18 | AquaCo overpayment response | How should AquaCo's specific “payment above bill amount” error code be mapped to the customer-facing reason? | Map the biller error to Failed and show a clear reason; exact message/code mapping follows AquaCo mock contract. |
| A-19 | Callback authentication | What callback authentication/signature mechanism does the TopUpNet mock contract provide? | Use only the mock contract/instructor guidance; do not invent a signature protocol. |
| A-20 | Callback/retry timing | What happens if TopUpNet callback is delayed beyond the retry/reconciliation schedule, or arrives after reconciliation? | Preserve final-state/idempotency rules; confirm timeout and late-callback handling details with team. |
| A-21 | Actor naming | Should “Financial Operations Employee” and “PayLink Operations Stakeholder” be added as stakeholders, or should stories use existing “Support Employee” and “Admin”? | Use existing stakeholder names in the current pack: Support Employee for reconciliation review and Admin for audit oversight, unless Person 1/team approves new roles. |
| A-22 | Concurrent wallet payments | Who owns the acceptance criteria/test for two simultaneous payments when the wallet covers only one? | Brief requires one success and one Rejected with no negative balance. Coordinate ownership with Person 1 and design/test teammates. |

# **4\. Fixed Rules from the Student Brief (not team decisions)**

These values are specified by the assignment and should not be recorded as decisions invented by the team.

· **F-01 —** Basic daily payment limit: 5,000 EGP; verified daily limit: 30,000 EGP. *\[Brief §2.6\]*

· **F-02 —** Single payment minimum 5 EGP and maximum 10,000 EGP. *\[Brief §2.6\]*

· **F-03 —** Electricity/water fee: fixed 2.50 EGP; mobile top-up fee: 1.5%, minimum 1 EGP; internet fee: 2 EGP up to and including 200 EGP, 4 EGP above 200 EGP. *\[Brief §2.6\]*

· **F-04 —** Promotion fee is 0 for one chosen biller during configured start/end dates. *\[Brief §2.6\]*

· **F-05 —** Agent commission is 40% of service fee and is credited to agent wallet when payment completes. *\[Brief §2.6\]*

· **F-06 —** More than 5 payments in 60 seconds from one account triggers a 10-minute block. *\[Brief §2.6\]*

· **F-07 —** Live biller timeout is 10 seconds; payment becomes Unknown. Unknown payments are re-queried after 1, 5, and 15 minutes, then wait for reconciliation. *\[Brief §§2.5–2.6\]*

· **F-08 —** Failed SMS or email is retried 3 times, then marked undelivered. *\[Brief §2.6\]*

· **F-09 —** All money uses exact decimal types, never floating point. *\[Brief §2.6\]*

· **F-10 —** Completed, Rejected, and Refunded are final payment states. Unknown is never automatically refunded; funds return only when the system is sure the biller did not receive the payment. *\[Brief §2.5\]*

# **5\. Team Decision Log — Complete with the Team**

| Ambiguity ID | Decision agreed by team | Decided by | Date | Status |
| :---- | :---- | :---- | :---- | :---- |
| A-01 | Treat the TopUpNet “accepted” response as `SentToBiller` while waiting for the callback. | Team | 25/11/2026 | Resolved |
| A-02 | Agent-assisted payments will debit the **customer wallet** | Team | 25/11/2026 | Resolved |
| A-03 | Customer limits and velocity rules apply to the customer for agent-assisted payments. | Team | 25/11/2026 | Resolved |
| A-04 | Daily payment limits are calculated based on the **bill/payment amount**, excluding the service fee. Only successful/completed payments count toward the daily limit. | Team | 25/11/2026 | Resolved |
| A-05 | The velocity rule counts payment attempts, uses a sliding 60-second window, and the payment exceeding the limit is rejected. | Team | 25/11/2026 | Resolved |
| A-06 | The canonical payment reference is the PayLink payment ID. | Team | 25/11/2026 | Resolved |
| A-07 | Fees are calculated using exact decimal arithmetic and rounded to 2 decimal places. | Team | 25/11/2026 | Resolved |
| A-08 | Duplicate callbacks are identified using the callback/payment identifier, and callbacks cannot change a final payment state. | Team | 25/11/2026 | Resolved |
| A-09 | NetCo is considered optional and is outside the mandatory Phase 1 implementation scope. | Team | 25/11/2026 | Resolved |
| A-10 | Only fees and payment limits are editable through the admin configuration. | Team | 25/11/2026 | Resolved |
| A-11 | Blocking an account prevents new payments but does not cancel payments already in progress. | Team | 25/11/2026 | Resolved |
| A-12 | Rejected payments are not required to send SMS/push notifications unless the team decides to treat them as failures. | Team | 25/11/2026 | Resolved |
| A-13 | A refund of a Completed payment is represented as a separate refund request and ledger transaction; the original payment remains Completed. | Team | 25/11/2026 | Resolved |
| A-14 | Promotion dates use the system timezone, and overlapping promotions are not allowed for the same biller. | Team | 25/11/2026 | Resolved |
| A-15 | Support Employees can search payments and block/unblock accounts; refund approval requires authorized support access. | Team | 25/11/2026 | Resolved |
| A-16 | The 3-retry rule applies to SMS/email notifications. Push notification retry behavior is handled separately. | Team | 25/11/2026 | Resolved |
| A-17 | Daily reports use the system timezone and count payments according to their final state. | Team | 25/11/2026 | Resolved |
| A-18 | AquaCo overpayment errors are mapped to `Failed` with a clear customer-facing reason. | Team | 25/11/2026 | Resolved |
| A-19 | TopUpNet callback authentication follows the authentication mechanism defined in the provided mock contract. | Team | 25/11/2026 | Resolved |
| A-20 | Late callbacks cannot change a final payment state after reconciliation. | Team | 25/11/2026 | Resolved |
| A-21 | Existing stakeholder names are used: Customer, Agent, Admin, Support Employee, Billers, Management, Engineering Team. | Team | 25/11/2026 | Resolved |
| A-22 | Concurrent payments are handled using wallet locking/concurrency control so that only one payment succeeds when the balance covers only one payment. | Team | 25/11/2026 | Resolved |

# **6\. Priority and Traceability Summary**

| Story | FR | Priority | Module | Hard case / rule | NFR |
| :---- | :---- | :---- | :---- | :---- | :---- |
| US-01 | FR-1 | Must |   Accounts and Wallet | Customer registration and basic verification | FR-05 |
| US-02 | FR-2 | Should | Accounts and Wallet | Basic vs. verified daily limits | NFR-01 |
| US-03 | FR-3 | Must | Accounts and Wallet | Available/held balance and transaction history | NFR-05 |
| US-04 | FR-4 | Must | Accounts and Wallet | ailed top-up must not change balance | NFR-01 |
| US-05 | FR-5 | Must | Accounts and Wallet / Ledger | Every wallet balance change creates ledger entries | NFR-01,NFR-05 |
| US-06 | FR-6 | Must | Admin / Biller Management | Disable biller/service prevents new payments | NFR-04 |
| US-07 | FR-7 | Must | Biller Catalog | Display required fields for each service | NFRN-04 |
| US-08 | FR-8 | Must | Bill Inquiry | Biller failure must not charge wallet | NFR-01 |
| US-09 | FR-9 | Must | Payment Processing | Insufficient balance and biller confirmation | NFR-01 |
| US-10 | FR-10 | Must | Payment Processing | Duplicate request must not create duplicate charge | NFR-01 |
| US-11 | FR-11 | Must | Payment Processing | Valid payment state transitions only | NFR-01,NFR-05 |
| US-12 | FR-12 | Must | Accounts and Wallet / Payment Processing | Hold before biller call and release on failure | NFR-05 |
| US-13 | FR-13 | Must | Payment Processing / Reconciliation | 10-second timeout; retry after 1, 5, 15 minutes | NFR-01,NFR-03 |
| US-14 | FR-14 | Must | Biller Integration / Payment Processing | Hard case 6; late callback after final outcome | NFR-01, NFR-05 |
| US-15 | FR-15 | Must | Biller Integration | Hard case 8; AquaCo over-bill response | NFR-03, NFR-04 |
| US-16 | FR-16 | Must | Fees and Commissions | Promotion rule | NFR-01 |
| US-17 | FR-17 | Should | Accounts and Wallet / Fees and Commissions | Agent payment and commission | NFR-01, NFR-05 |
| US-18 | FR-18 | Must | Fraud Checks / Payment Processing | No hold when rejected; limits | NFR-01 |
| US-19 | FR-19 | Should | Fraud Checks / Payment Processing | Velocity block; no hold when rejected | NFR-01 |
| US-20 | FR-20 | Must | Support / Payment Processing | Payment history lookup | NFR-05 |
| US-21 | FR-21 | Should | Accounts and Wallet / Support | Blocked account and in-flight payments | NFR-05 |
| US-22 | FR-22 | Must | Notifications | Hard cases 2 and 3; Unknown processing message | NFR-03 |
| US-23 | FR-23 | Should | Notifications | Hard case 5; payment succeeds despite SMS outage | NFR-03 |
| US-24 | FR-24 | Should | Admin / Configuration | Business rules configurable | NFR-04 |
| US-25 | FR-25 | Must | Audit | Every money movement/admin action logged | NFR-05 |
| US-26 | FR-26 | Should | Reconciliation | Hard case 7; Unknown resolved by settlement; unmatched rows | NFR-01, NFR-05 |
| US-27 | FR-27 | Could | Refunds / Accounts and Wallet | Separate refund request; original Completed remains final | NFR-01, NFR-05 |
| US-28 | FR-28 | Could | Admin / Reporting | Daily totals per agreed day/state definition | NFR-05 |

# **7\. Glossary and Terminology Alignment**

· **Mobile top-up payment:** A payment for mobile service made through TopUpNet (FR-14/FR-15). This is different from topping up a customer's PayLink wallet (FR-4).

· **Wallet top-up:** Adding funds to a customer's PayLink wallet; this is Person 1's FR-4 topic.

· **Payment state:** Use the exact lifecycle terms: Initiated, FundsHeld, SentToBiller, Completed, Failed, Unknown, Rejected, Refunded.

· **Hold release / refund:** When a Failed payment's held funds are released, the lifecycle moves to Refunded. Do not use “refund” to mean an arbitrary reversal of a Completed payment.

· **Completed-payment refund request:** A separate request/workflow with separate ledger entries; the original Completed payment remains in its final state, subject to team confirmation of the detailed policy.

· **Payment reference:** Not yet defined; see ambiguity A-06.

# **8\. Coordination Items**

· Align story layout with Person 1: Priority before Source, and use the same AC numbering/format when merging.

· Use stakeholder names already in Person 1's stakeholder list: Customer, Agent, Admin, Support Employee, Billers, Management, Engineering Team. The reconciliation reviewer is written as Support Employee; audit oversight is written as Admin unless the team approves another role.

· Coordinate ownership of hard case 2 (Unknown customer message), hard case 4 (concurrent wallet payments), and AquaCo over-bill handling with Person 1 and the design/test teammates.

· Tell Persons 3 and 4 that the Unknown-state definition, agent wallet/limit rules, and separate refund-request model affect their diagrams and design.

· Before submission, replace pending decision-log entries only with decisions the team actually made.

# **9\. Coverage Summary**

Person 2 covers 15 stories (US-14 to US-28), mapped one-to-one to FR-14 to FR-28. Combined with Person 1's US-01 to US-13, the pack contains 28 stories, exceeding the minimum of 25\. Priority counts for Person 2: 7 Must, 6 Should, 2 Could.

Source basis: PayLink Year Work Project — Student Brief, especially §§2.4–2.7, 3.2–3.3, and Phase 1 deliverables. Existing team document was used for numbering and stakeholder-name alignment.

