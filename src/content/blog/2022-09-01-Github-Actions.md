---
title:  "GitHub Actions"
description: this is a required field
pubDate: 2022 01 Sep
---

Github actions run in response to events including push, issue creation and new
release.  Actions are built by the community for specific services.

## GitHub Actions Primatives
### Workflows
A configurable automated process that will run one or more jobs.  Workflows are
defined by a YAML file
### Events
A specific active which triggers a workflow.  (The creation of a pull request to
a sepcific branch)
### Jobs
A job is a series of steps in a workflow whic execute on the same runner. Each
step is either a shell script or an action
### Actions
### Runners


## Understanding [YAML](https://en.wikipedia.org/wiki/YAML)
A human readable data serialization language which is used primarily for
configuration files.


- indentation is used to indicate nesting (as in Python)
- [...] are used for tests
- {...} are used for maps
- JSON files are valid YAML
- scaler types;  strings, integers, floats
- extention .yaml (YAML Ain't Markup Language)
- character sets UTF-8, UTF-16, UTF-32
- tab may not be used for indentation
- (#) style comments
- (-) list one per line
- [...] list with comma separated elements
- key:value associative array (one per line)
- ... optional ends a document stream
- %YAML is the version of yaml the document uses
- %TAG shortcut for URI prefixe
- '@' and '`' are reserved for future use
- data type are auto detected
- data types and be specifiied with the ! symbol: `!binary`

### Examples

The following are equivlent
```yaml
--- # The Smiths
- {name: John Smith, age: 33}
- name: Mary Smith
  age: 27
- [name, age]: [Rae Smith, 4]   # sequences as keys are supported
--- # People, by gender
men: [John Smith, Bill Jones]
women:
  - Mary Smith
  - Susan Williams
```

Use of the & symbol to create variable which can be referenced later.
```yaml
--- # Sequencer protocols for Laser eye surgery
- step:  &id001                  # defines anchor label &id001
    instrument:      Lasik 2000
    pulseEnergy:     5.4
    pulseDuration:   12
    repetition:      1000
    spotSize:        1mm

- step: &id002
    instrument:      Lasik 2000
    pulseEnergy:     5.0
    pulseDuration:   10
    repetition:      500
    spotSize:        2mm
- step: *id001                   # refers to the first step (with anchor &id001)
- step: *id002                   # refers to the second step
- step: *id002
```

## Refereences
[GitHub Actions product landing page](https://github.com/features/actions)