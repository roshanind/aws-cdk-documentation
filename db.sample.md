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

## Database Structure

### **Application Table**

Structure of `Application` table.

```mermaid
erDiagram
Application {
    String id PK "Partition key"
    String applicationId
    String applicationStatus
    Map documentStatus
    String idempotencyKey
    String tenantId FK "GSI for application"
    String createdAt
    String updatedAt
}

```

Access pattern `Applicaiton`

| Table Name | Access Pattern |
| ---------- | -------------- |
| Application |  GetApplicationByTenantId | 

### **otterz-generalInfo Table**

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

### **Authentication Table**

Structure of `Authentication` table

```mermaid
erDiagram
Authentication {
    String id PK "Partition key"
    Boolean active
    String email
    String roleName
    String tenantId FK "GSI for Authentication"
    String createdAt
    String updatedAt
}
```
Access pattern `Authentication`

| Table Name | Access Pattern |
| ---------- | -------------- |
| Authentication |  GetChildUsersByTenantId | 



