aws-cfn-compiler
================

A simple script to compile and perform some validation for CloudFormation scrips.  The idea is to create a folder structure to better manage pieces of a CloudFormation deployment.  Additionally, writing in JSON is hard, so the compiler takes YAML files as well.


Installation
------------

    gem install bundler
    bundle install
    
Usage
-----

```
./compile.rb -d ROOT_DIRECTORY -o OUTPUT_JSON_FILE
```

Directory Structure
-------------------

The pieces of the CloudFormation script is split into four groups:

* Parameters
* Mappings
* Resources
* Outputs

For each group, you can define a single file at the root directory with that name (i.e. outputs.json or outputs.yml) or a directory with that name containing any structure of JSON or YAML files (i.e. resources/nat.yml or resources/app/hello.json).  The script is responsible for combining everything into one JSON file.

Reference Validation
--------------------

After all the pieces are stiched together, the system runs through the file finding references to names and then attempt to validate that those names exist in the file.
