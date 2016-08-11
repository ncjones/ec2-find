Findly Instances
================

CLI tool to find AWS EC2 instances by product tag.


Usage
-----

    ./findly-instances <product_tag>

Product tag can be a partial match. Requires AWS CLI and JQ. AWS default
profile or environment variables will be used.


Example
-------

    ./findly-instances waggle
    10.55.71.178 qa4-be-combinedservices qa4
    10.55.67.46 qa1-be-combinedservices qa1
    10.55.64.179 qa1-combinedwebsites qa1
    10.55.71.27 qa2-be-combinedservices qa2
    10.55.35.112 dev-be-combinedservices development
    10.55.65.5 uat-waggle uat
    10.55.65.131 qa4-combinedwebsites qa4
    ...


Output Format
-------------

Output shows private IP address, "Name" tag and "Environment" tag for each
matched EC2 instance.
