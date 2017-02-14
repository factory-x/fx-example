# Factory-X example project

## What is Factory-X?

factory-x.io is a code generator for well structured and maintainable PLC/PAC/DCS logic.

## Why?
* Programming industrial controllers is labor-intensive and often a very repetitive job.
* As with any other programming ecosystems it is prone to errors, however there are no automated testing frameworks.
* Functional and control logic is not separated, severaly limiting scalability, innovation and possibility to open-sourcing parts of the programs.

## How does it work?
The input is an FDS/DA document in the format as specified by the customer or integrator. Open-source import-scripts translate the FDS/DA in a model (Model-A). Model-A is a json structure closely representing the FDS/DA.

Once Model-A is generated it is transformed into Model-T (T standing for Tranformed or Template-Model). The goal of this transform is to generate another json-model that is very easy to iterate over by a standard templating engine. This transfor is also the most complex part of the code generater, and running as an AWS Lambda service.

Finally Model-T is sent through a templating engine that creates the the controller logic. The code-generator is brand and language-independent. Generating code for a different type of controller or language is as simple as changing the templates. 

## What is the status of Factory-X?
The project is currently in beta, with two pilot projects having been auto-generated for more than 90%, including phases and equipment modules. The templates for the pilots are Siemens S7 STL. (Not TIA)

## What does it take to use Factory-X for our own projects?

### Option 1: Do it yourself
See example project instructions below, and iterate from there.
We're currently working on full documentation

### Option 2: Ask us to set you up
We'll probably do it for free in return for a lot of user-feedback

## Instructions for the example project

Install the latest version of node.js for your system:
(This include a javascript runtime and NPM: the most popular package manager at this moment)

<https://nodejs.org/en/download/>

Install git for your system:

<https://git-scm.com/download>

Start up a terminal (Windows cmd, or powershell, or whatever yo prefer)

Go to the folder where you want to create the project

Clone the example project
```
git clone https://github.com/factory-x/fx-example fx-example
```

This will clone the project in the directory called fx-example

In this directory there is a directory for the model (fx-example/mode => this is where the FDS/DA is stored)

Unzip the example model in this directory:

<https://s3-us-west-2.amazonaws.com/factory-x/model.zip>

Go back to the terminal an make sure you're in the folder 'fx-example':

```
npm install
```
Install the CLI tools:
```
npm install factory-x-cli --save
```
finally render the project:
```
fx render
```
The result can be found in fx-example\output\plc and fx-example\output\model

From here on you can make changes to the templates and the model,
Re-render with:
```
fx render
```


