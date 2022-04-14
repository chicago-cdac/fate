# Netrics Redesign

## Introduction
Although *netrics* has worked well up to this point, it has become clear that a
concerted redesign of the software will be necessary to meet our future research
and public goals. What follows is a list of current design pain points that may
impede our success:
- **Adding new modules is hard**. To add a new module, one must create an
  executable, write a python wrapper (meaning a function in `netrics.py`) that
  is compatible with our data collection, and handle module execution and
  scheduling. All of this requires fairly intimate familiarity with the system,
  in which the user must manually edit source files.
- **Testing a new module is hard**.  There is no infrastructure to test new
  modules. Instead, the user must either test locally or on an RPi in the lab.
  This means knowing where module output is sent and how to parse the output.
- **Naive job control**. Error handling is currently built into the python
  wrapper. Job scheduling is manually determined in the crontab without
  considering which tests can be parallelized or prioritized. 
- **Lack of configuriability**. While not impossible, it is hard for the user to
  pick which tests to run and when. 

Some of these are not issues for our current needs (we don't expect/want study
participants messing with job scheduling/selection). But these are certainly
issues if we want other researchers to use the *netrics* framework.

## Design Specification

In this section, we outline the desired functionalities of *netrics*. 

### Job Control

**Job Scheduling**
- Periodicity: How often is the module run?
- Prioritization: Does this module need to run alone? Can it be run in the
  background?

**Error Handling**

### Module Testing

- How do we test new modules?

### Data Collection

**Data Format**
- What is the standard data format that the module will output? Probably JSON.

**Data Ingestion**
- How does the data get collection?


### Package Management

- How do users install/upgrade modules?
