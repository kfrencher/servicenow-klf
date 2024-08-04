# KLF Utilities

These are general script includes that are used across projects. There is a brief description of each utility below. A more detailed description is included inside each script include.
- [DateUtils](#DateUtils)
- [Evaluator](#Evaluator)
- [GlideRecordUtils](#GlideRecordUtils)
- [GroupUtils](#GroupUtils)
- [ListMetric](#ListMetric)

# DateUtils

Utility object for date-related operations. This object is particularly useful for
getting information related to the Federal Government's fiscal year.

Functions such as getFiscalYear, getCurrentFiscalYear, getFiscalYearStartDate.

As well as doing calculations based on business days such as addBusinessDaysToDate.

# Evaluator

Script that exposes an `eval` function for scoped applications.
`GlideEvaluator.eval` is not available in scoped applications.
This script gives an alternative way to execute a script given as a string dynamically.

Example:
```javascript
 var script = 'gs.info("Hello World")';
 x_912467_klfx_snb_common.Evaluator.evaluate(script);
```

# GlideRecordUtils

Exposes some general methods for working with GlideRecords

Some of the methods are:
- getRecord: Quickly retrieve a GlideRecord or null by sys_id
- getExtendedGlideRecord: Some GlideRecords are extended tables. This method will always return the extended GlideRecord
even if the passed in GlideRecord is the parent table
- getFieldLabel: Returns the sys_documentation label associated with a field. This can be useful if you want to get
some information that is stored on the sys_documentation record
- extendsTable: Returns whether or not a child table extends an ancestor table
- getRecordUrl: Returns the ServicePortal form URL
- getRecordHtmllink: Returns HTML anchor link to the ServicePortal form

# GroupUtils

Utility functions for Group (sys_user_group) table

Some of the functions include:
- isMemberOfSomeGroup: Returns true if the user is a member of any of the groups
- getGroupSysIdsForUser: Returns the list of sys_user_group.sys_id for the user
- getGroupByName: Returns the sys_user_group record with the given name
- isMemberOf: Returns true is the user is a member of the sys_user_group
- createGroup: Creates a new sys_user_group record   
- createUser: Creates a new sys_user record
- addUserToGroup: Adds a user to a group

# ListMetric

Helps to produce a metric based on the "List" field in ServiceNow. Metrics are located in the "Metrics" module.

It can be difficult to report on a list field in ServiceNow because the list values are aggregated into a single field.

This script helps to produce a metric based on the list field. A metric instance will be produced for each value in the
list field. This way you can create a report based on the individual values instead of the aggregated field.

Metrics are documented at [Metrics](https://docs.servicenow.com/csh?topicname=c_MetricDefinitionSupport.html&version=latest) in the
ServiceNow docs site.

> NOTE: to produce metrics on tables that do not extend Task, you will need to duplicate the "metrics events" business rule that
sits on the Task table. That business rule is responsible for creating the metric instances. Duplicate the business rule and
change the table name to the table you want to produce metrics on.

> When you duplicate the business rule, you will need to call the "queueMetricUpdate" function from the "onAfter" business rule.
The default "queueMetricUpdate" function can only be called from "global" scope. I have created a version of this function
in the KLF Global application called "KLF_MetricUtils.queueMetricUpdate" that can be called from the application scope. Refer to
the KLF_MetricUtils script include for more information.

Example:
```javascript
// Create a Metric Definition
// In the "Script" field of the definition add the following script:
x_912467_klf.ListMetric.createMetric(current, definition);
```
