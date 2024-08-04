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

# ListMetric
