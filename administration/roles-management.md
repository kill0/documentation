##Overview

In order to restrict access for some users you need to use Roles. Administrator can manage roles in Administration panel. Each role defines an access to certain areas (scopes) which is applied to users who own that role.

One user can have multiple roles. Those roles can be selected for a specific user (‘Roles’ field in User entry) and/or be inherited from the teams that user belongs to.

If a user has multiple roles then they will be merged so that permissive rule will have a higher priority. That allows administrator to manage access level control easily and flexibly.

##Example

For example, user belongs to team ‘Sales’. That team has single role ‘Salesman’. So all users from this team will obtain ‘Salesman’ role.

‘Salesman’ role is defined the following way:
Lead:
```read – team
edit – own
delete – no```

Opportunity:
```read – team
edit – own
delete – no```

Users will be able to read only those leads and opportunities which belong to ‘Sales Department’ team (‘Teams’ field).
User will be able to edit only those leads and opportunities which they are assigned to or those they have created.
Users won’t be able to remove any leads or opportunities.

We want to give more rights to a certain user who holds sales manager position in the company. This employee must have an ability to read/edit/delete all records from ‘Sales’ team. The user should belong to our ‘Sales’ team. But we need to create the new role ‘Sales Manager’ and select this role for that user in ‘Roles’ field.

‘Sales Manager’ role is defined the following way:
Lead:
```read – team
edit – team
delete – team```

Opportunity:
```read – team
edit – team
delete – team```

Our user will be able to manager all leads and opportunities from the ‘Sales’ team.