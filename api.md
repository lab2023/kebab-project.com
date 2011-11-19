---
title: Kebab Revolution Api
layout: default
---

<h3>· {{ page.title }} ·</h3>

## Check Client

When Kebab run first time, server should check the tenant (subdomain) and create a authenticity_token.

    GET /tenants/register
    
### Response Success

<%= headers 200 %>
<%= json ["success" => true, "tenant" => ["id" => 1, "name" => "Tenant Name"]] %]

### Response Failed

<%= headers 404 %>
<%= json ["success" => false]


