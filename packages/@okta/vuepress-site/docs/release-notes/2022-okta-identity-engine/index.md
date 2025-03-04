---
title: Okta Identity Engine API Products release notes 2022
---
<ApiLifecycle access="ie" />

## March

### Weekly release 2022.03.3

| Change | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Bug fixed in 2022.03.3](#bugs-fixed-in-2022-03-3) | March 23, 2022 |

#### Bug fixed in 2022.03.3

The `auth_time` [claim](/docs/reference/api/oidc/#reserved-claims-in-the-header-section) wasn't defined as a reserved system claim. (OKTA-478924)

### Weekly release 2022.03.2

| Change | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Bugs fixed in 2022.03.2](#bugs-fixed-in-2022-03-2) | March 16, 2022 |

#### Bugs fixed in 2022.03.2

* An error was returned when a valid [update request](/docs/reference/api/authorization-servers/#update-a-scope) was made for the `device_sso` or `online_access` system scopes. (OKTA-417477)

* Sending an [error object](/docs/reference/registration-hook/#error) in the response message of an Inline Registration Hook resulted in an error message that included domain details and didn’t target attributes. (OKTA-473152)

### Weekly release 2022.03.1

| Change | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Bugs fixed in 2022.03.1](#bugs-fixed-in-2022-03-1) | March 09, 2022 |

#### Bugs fixed in 2022.03.1

* Performing a GET request on the `/policies/` [endpoint](/docs/reference/api/policy/) sometimes returned a page with the wrong number of items. (OKTA-455164)
* When the [List email templates](/docs/reference/api/brands/#list-email-templates) or the [List email customizations](/docs/reference/api/brands/#list-email-customizations) operations were performed on the `/brands/` endpoint, the base address in the link response header contained the `-admin` string instead of the requested base address. (OKTA-465356)
* When modifying the [custom email activation template](/docs/guides/custom-email/main/#use-customizable-email-templates), an admin could save the template without either of the required `verificationLink` or `verificationToken` elements. (OKTA-472895)
* When modifying the [custom email challenge template](/docs/guides/custom-email/main/#use-customizable-email-templates), an admin could save the template without either of the required `emailAuthenticationLink` or `verificationToken` elements. (OKTA-472928)

### Monthly release 2022.03.0

| Change                                                                   | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Authentication timestamp is added as an access token claim](#authentication-timestamp-is-added-as-an-access-token-claim) | March 2, 2022 |
| [Custom Administrator Roles is GA in Production](#custom-administrator-roles-is-ga-in-production) | February 3, 2022 |
| [Email Address Bounces API is EA in Preview](#email-address-bounces-api-is-ea-in-preview) | March 2, 2022 |
| [Shareable Authentication Policies](#shareable-authentication-policies) | March 2, 2022 |
| [Signed request support for generic OIDC IdP is EA in Preview](#signed-request-support-for-generic-oidc-idp-is-ea-in-preview) | March 2, 2022 |
| [Bugs fixed in 2022.03.0](#bugs-fixed-in-2022-03-0)         | March 2, 2022           |

#### Authentication timestamp is added as an access token claim

The user-authenticated epoch timestamp is provided as the `auth_time` [claim in the access token](/docs/reference/api/oidc/#reserved-claims-in-the-payload-section).

#### Custom Administrator Roles is GA in Production

The Okta [Custom Administrator Roles](/docs/reference/api/roles/) API provides operations that you can use to create customized roles and assign them to a user or a group.

#### Email Address Bounces API is EA in Preview

Okta admins can now control the bounced email address list through the [Email Address Bounces API](/docs/reference/api/org/#email-address-bounces-operations). When Okta-sent email addresses are blocked from an email service (the bounced email list), admins can use this API to create a list of blocked email addresses to be removed from the email service.

#### Shareable Authentication Policies

Admins can now manage authentication policies using a centralized view. While authentication policies allowed admins the ability to make application access decisions using user, device, and other contextual information, managing these policies across hundreds of applications became challenging and error-prone.

On the new Authentication Policies page, admins can create new policies, apply those policies to multiple applications, and assess what application access decisions are impacted by each policy.

Two policy name changes are included in this release: app sign-on policy is renamed authentication policy, and Okta sign-on policy is renamed Global Session Policy. See [Configure a Global Session Policy and authentication policies](/docs/guides/configure-signon-policy/) and [Authentication policies](https://help.okta.com/okta_help.htm?type=oie&id=ext-about-asop).

#### Signed request support for generic OIDC IdP is EA in Preview

When customers [integrate Okta with an OpenID Connect-based Identity Provider](/docs/guides/add-an-external-idp/openidconnect/main/#create-an-identity-provider-in-okta), Okta asks the IdP to authenticate the user with request elements that are passed as query parameters in the URL. The new [signed request object](/docs/reference/api/idps/#oidc-algorithms-object) allows customers to send these parameters encoded in a JWT instead, improving security on the authorization request sent to the OpenID Connect provider or authorization server.

#### Bugs fixed in 2022.03.0

* When ThreatInsight evaluated sign-in attempts for unknown users, the threat level was incorrectly displayed as `threatLevel=UNKNOWN` in the System Log. (OKTA-471299)

* The OAuth 2.0 [`/token`](/docs/reference/api/oidc/#token) and [`/authorize`](/docs/reference/api/oidc/#authorize) endpoints accepted requests that included the `resource` parameter. (OKTA-476549)

## February

### Weekly release 2022.02.2

| Change                                                                   | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Okta Org2Org integration now supports Okta API access using an OAuth 2.0 client](#okta-org2org-integration-now-supports-okta-api-access-using-an-OAuth-2-0-client)                        | February 16, 2022         |

#### Okta Org2Org integration now supports Okta API access using an OAuth 2.0 client

The Okta Org2Org integration enables you to push and match both users and groups from one Okta org to another. Previously, this integration only supported token-based access to the Okta API. You can now [configure the Org2Org integration](/docs/guides/secure-oauth-between-orgs/) to access the Okta API as an [OAuth 2.0 client](/docs/reference/api/apps/#token-based-provisioning-connection-profile-properties). This increases security by limiting the scope of access and providing a better mechanism to rotate credentials. <!-- OKTA-468121 -->

### Weekly release 2022.02.1

| Change                                                                   | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [API token ID added to System Log event types](#api-token-id-added-to-system-log-event-types)                        | February 9, 2022         |
| [Bug fixed in 2022.02.1](#bug-fixed-in-2022-02-1)                        | February 9, 2022         |

#### API token ID added to System Log event types

API requests that include an API token and return a System Log event now include the API token in the event payload. The token identifier appears in the System Log API `transaction.details.requestApiTokenId` field and in the `Event > System > Transaction > Detail > RequestApiTokenId` node in the Admin Console System Log.

To view an example of this new event detail, [create a user by API](/docs/guides/quickstart/main/#create-a-user-by-api) and view the associated event (`user.lifecycle.create`).

#### Bug fixed in 2022.02.1

The [OAuth token endpoint](/docs/reference/api/oidc/#response-example-error-2) didn’t reject requests that included a `code_verifier` parameter if the [authorization call](/docs/reference/api/oidc/#authorize) was issued without the PKCE `code_challenge` parameter. (OKTA-461970)

### Monthly release 2022.02.0

| Change                                                                   | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Custom Administrator Roles is GA in Preview](#custom-administrator-roles-is-ga-in-preview) | February 3, 2022 |
| [Client secret rotation and key management is EA](#client-secret-rotation-and-key-management-is-ea) | February 3, 2022 |
| [Group role assignment improvement](#group-role-assignment-improvement) | February 3, 2022 |
| [Custom Domains with Okta-Managed Certificates is GA in Production](#custom-domains-with-okta-managed-certificates-is-ga-in-production) | February 3, 2022 |
| [Bug fixed in 2022.02.0](#bug-fixed-in-2022-02-0)         | February 3, 2022           |

#### Custom Administrator Roles is GA in Preview

The Okta [Custom Administrator Roles](/docs/reference/api/roles/) API provides operations that you can use to create customized roles and assign them to a user or a group. <!--OKTA-457514-->

#### Client secret rotation and key management is EA

Rotating client secrets without service or application downtime is a challenge. Additionally, JSON Web Key management can be cumbersome. To make [client secret rotation](/docs/guides/client-secret-rotation-key/) a seamless process and improve JWK management, you can now create overlapping client secrets and manage JWK key pairs in the Admin Console. You can also create JWK key pairs from the Admin Console without having to use an external tool. <!--OKTA-460699-->

#### Group role assignment improvement

[Assigning a role to a group](/docs/reference/api/roles/#assign-a-role-to-a-group) through the Administrator Roles API has been enhanced by retaining the existing role assignment ID where possible. <!--OKTA-457506-->

#### Custom Domains with Okta-Managed Certificates is GA in Production

When you customize an Okta URL domain, your Okta-hosted pages are branded with your own URL. [Okta-Managed Certificates](/docs/guides/custom-url-domain/main/#configure-a-custom-domain-through-okta-managed-certificates) auto renew through a Let's Encrypt integration, a free certificate authority. Since Okta handles certificate renewals, this reduces customer developer maintenance costs and the high risk of a site outage when certificates expire.  <!--OKTA-459338-->

#### Bug fixed in 2022.02.0

In the [Custom Administrator Roles](/docs/reference/api/roles/) API, some public DELETE requests returned a different response code than their contract. (OKTA-456896)

## January

### Weekly release 2022.01.2

| Change                                                                                              | Expected in Preview Orgs |
|-----------------------------------------------------------------------------------------------------|--------------------------|
| [Device information in the OAuth 2.0 Interaction Code flow](#device-information-in-the-oauth-2-0-interaction-code-flow) | January 26, 2022 |
| [Fewer digits revealed for shorter phone numbers](#fewer-digits-revealed-for-shorter-phone-numbers) | January 26, 2022 |
| [Bugs fixed in 2022.01.2](#bugs-fixed-in-2022-01-2)         | January 26, 2022           |

#### Device information in the OAuth 2.0 Interaction Code flow

Confidential clients can now specify device information using the `X-Device-Token` header during the OAuth 2.0 [Interaction Code flow](/docs/guides/implement-grant-type/interactioncode/main/). <!--OKTA-455553-->

#### Fewer digits revealed for shorter phone numbers

The masking algorithm now reveals fewer digits in API responses for shorter profile phone numbers. <!--OKTA-455393-->

#### Bugs fixed in 2022.01.2

* Administrators were able to access and modify internal policies. (OKTA-455506)

* When an invalid client assertion type was provided during a [Client Credentials grant type flow](/docs/guides/implement-grant-type/clientcreds/main/), the error response code was 401 instead of 400. (OKTA-456503)

* When the [Create a new Binding](/docs/reference/api/roles/#create-a-new-binding) or the [Add more Members to a Binding](/docs/reference/api/roles/#add-more-members-to-a-binding) operation was performed on the `/iam/resource-sets` endpoint, and included all users or all groups in the request, the request didn't fail as expected. (OKTA-459994)

* When the [Get all policies](/docs/reference/api/policy/#get-all-policies-by-type) operation was performed on the `/policies` endpoint, unused Radius policies were returned. (OKTA-460965)

### Weekly release 2022.01.1

| Change                                                                                              | Expected in Preview Orgs |
|-----------------------------------------------------------------------------------------------------|--------------------------|
| [Bugs fixed in 2022.01.1](#bugs-fixed-in-2022-01-1)         | January 13, 2022           |

#### Bugs fixed in 2022.01.1

* If the [Create a Scope](/docs/reference/api/authorization-servers/#create-a-scope) endpoint received multiple requests at or near the same time, duplicate Scopes could be created. (OKTA-442533)

* When the [Update resource set](/docs/reference/api/roles/#update-resource-set) endpoint was called, the `resourceSetId` parameter was required in the body of the request. (OKTA-445144)

* When the [Upload Theme background image](/docs/reference/api/brands/#upload-theme-background-image) endpoint was called, the image was converted to PNG format. (OKTA-458260)

* When the [List events](/docs/reference/api/system-log/#list-events) operation was performed on the `/logs` endpoint, some system logs showed the incorrect status for debug behaviors if there was missing data that prevented behavior evaluation. (OKTA-455372)

### Monthly release 2022.01.0

| Change                                                                   | Expected in Preview Orgs |
|--------------------------------------------------------------------------|--------------------------|
| [Dynamic Issuer Mode is GA in Production](#dynamic-issuer-mode-is-ga-in-production) | December 8, 2021 |
| [Custom domains with Okta-managed certificates is GA in Production](#custom-domains-with-okta-managed-certificates-is-ga-in-production) | December 8, 2021 |
| [New permissions for custom admin roles](#new-permissions-for-custom-admin-roles) | January 6, 2022|
| [Self-service password reset with User API](#self-service-password-reset-with-user-api) | January 6, 2022 |

#### Dynamic Issuer Mode is GA in Production

An authorization server's issuer URL can be used to validate whether tokens are issued by the correct authorization server. You can configure the issuer URL to be either the Okta subdomain (such as `company.okta.com`) or a custom domain (such as `sso.company.com`). See [Property details](/docs/reference/api/authorization-servers/#authorization-server-properties).

When there are applications that use Okta's subdomain and other applications that use the custom domain, the issuer validation breaks because the value is hard-coded to one domain or the other.

With Dynamic Issuer Mode, the issuer value in minted tokens is dynamically updated based on the URL that is used to initiate the original authorize request. See [Client application settings](/docs/reference/api/apps/#settings-10). <!--OKTA-452668-->

#### Custom domains with Okta-managed certificates is GA in Production

When you customize an Okta URL domain, your Okta-hosted pages are branded with your own URL. [Okta-managed certificates](/docs/guides/custom-url-domain/main/#configure-a-custom-domain-through-okta-managed-certificates) automatically renew through a Let’s Encrypt integration, a free certificate authority. Okta-managed certificate renewals lower customer developer maintenance costs and reduce the high risk of a site outage when certificates expire. <!--OKTA-437290-->

#### New permissions for custom admin roles

The Administrator Roles API includes new app [permissions](/docs/reference/api/roles/#permission-properties) for custom admin roles to run end-to-end imports. See [About role permissions](https://help.okta.com/okta_help.htm?id=csh-cstm-admin-role-app-permissions).<!--OKTA-433371-->

#### Self-service password reset with User API

Client applications that use the Users API `/users/{$userId}/credentials/forgot_password` to implement the [self-service account recovery](https://help.okta.com/okta_help.htm?type=oie&id=ext-config-sspr) flow can now use this API call with password policies configured with the **Any enrolled authenticator used for MFA/SSO** additional verification option. <!--OKTA-452933-->
