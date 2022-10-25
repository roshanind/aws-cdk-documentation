## Otterz Dtabase Structure

> As a database otterz using [DynamoDB](https://aws.amazon.com/dynamodb/)

### List of all the database using Otterz

- application
- master-settings-table
- otterz-cards
- otterz-generalInfo
- Authentication
- ExternalNotifications
- Rbac
- Tenant
- pa-settings
- payment-acceptance-onbarad-admin
- payment-acceptance-onboard
- payment
- product
- rewardsTable
- Subscription
- SubscriptionPlan
- SubscriptionUser
- tax
- temp__disable_nitificaitons
- tenantInfoForUnitEvents

## Database Structure and Access Pattern

<details>

<summary><strong>Application Table</strong></summary>

Structure of `Application` table.

```mermaid
erDiagram
Application {
    String id PK "Partition key"
    String tenantId FK "GSI for application"
    String applicationId
    String applicationStatus
    Map documentStatus
    String idempotencyKey
    String createdAt
    String updatedAt
}

```

Access pattern `Applicaiton`

| Table Name | Access Pattern |
| ---------- | -------------- |
| Application |  GetApplicationByTenantId | 

</details>

<details>

<summary><strong>otterz-generalInfo Table</strong></summary>

Structure of `otterz-generalInfo` table.

```mermaid
erDiagram
otterz-generalInfo {
    String tenantId PK "Partition key"
    String id
    String status
    String createdAt
    String updatedAt
}

```
</details>

<details>
<summary><strong>Authentication Table</strong></summary>

Structure of `Authentication` table

```mermaid
erDiagram
Authentication {
    String id PK "Partition key"
    String tenantId FK "GSI for Authentication"
    Boolean active
    String email
    String roleName
    String username
    String createdAt
    String updatedAt
}
```

Access pattern `Authentication`

| Table Name | Access Pattern |
| ---------- | -------------- |
| Authentication |  GetChildUsersByTenantId | 
</details>

<details>
<summary><strong>ExternalNotifications Table</strong></summary>

Structure of `ExternalNotifications` table

```mermaid
erDiagram
ExternalNotifications {
    String id PK "Partition key"
    String tenantId FK "GSI for ExternalNotifications"
    Boolean addPayee
    Boolean cardTrx
    Boolean dailyAccountBalance
    Boolean disallowedTrx
    Boolean inComingPayment
    Boolean outGoingPayment
    Boolean periodicBankStatement
}
```

Access pattern `ExternalNotifications`

| Table Name | Access Pattern |
| ---------- | -------------- |
| ExternalNotifications |  NotificationSettingsByTenantId | 
</details>

<details>
<summary><strong>Rbac Table</strong></summary>

Structure of `Rbac` table

```mermaid
erDiagram
Rbac {
    String id PK "Partition key"
    String roleName PK "GSI for Rbac"
    String tenantId
    List roleScopes
    String createdAt
    String updatedAt
}
```

Access pattern `Rbac`

| Table Name | Access Pattern |
| ---------- | -------------- |
| Rbac |  listByRoleName | 
</details>

<details>
<summary><strong>Tenant Table</strong></summary>

Structure of `Tenant` table

```mermaid
erDiagram
Tenant {
    String id PK "Partition key"
    String icid FK "GSI for Tenant"
    String accountId
    String businessContactName
    String businessName
    String cardnoxKey
    String customerId
    String ifieldKey
    String merchantId
    String ownerId
    String subscriptionPlanId
    String tenantType
    Boolean active
    Boolean approved
    Boolean icidActive
    String createdAt
    String updatedAt
}

```

Access pattern `Tenant`

| Table Name | Access Pattern |
| ---------- | -------------- |
| Tenant |  GetIfieldKeyByCompanyId | 
</details>
