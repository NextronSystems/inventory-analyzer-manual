.. index:: Roles

Roles
=====

You can create different roles based on predefined sets of permissions/rights.
After installation, you will only see the ``Admin`` role, but can add new
roles as needed.

The following ``Rights`` can be configured:

.. list-table:: 
    :header-rows: 1
    :widths: 30, 70

    * - Rights
      - Description
    * - Admin
      - **Right**: User has administrative rights
    * - Audit Log
      - **Right**: User can access Audit Logs
    * - Manage ASGARDs
      - **Rights**: Adding, Removing and Updating ASGARDs
    * - Manage Agents
      - **Rights**: Adding, Removing and Updating Agents
    * - Manage Asset Columns
      - **Rights**: Adding, Removing and Updating Columns
    * - Manage Assign Rules
      - **Rights**: Adding, Removing and Updating Assign Rulesets
    * - Manage CSV Templates
      - **Rights**: Adding, Removing and Updating CSV Templates
    * - Manage Tasks
      - **Rights**: Adding, Removing and Updating Tasks
    * - Read Only
      - **Restriction**: User can only read

.. note:: 
    Restrictions overwrite permissions. If you set ``Read Only`` for a Role,
    all users in the group will be restricted to read-only, regardless of
    other permissions in the same role.