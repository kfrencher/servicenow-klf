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

# GroupUtils

# ListMetric
