Findly Instances
================

Bash script to find AWS EC2 instances by tag values and show concise output
that is both human-readable and scripting-friendly. The command syntax is
greatly simplified compared to using `aws ec2 describe-instances` filters.


Usage
-----

```
findly-instances --<tag_name> <tag_value>
```

Instances having the specified tag will be matched. The tag value can be a
partial substring match. If no tag name is specified then the 'Name' tag is
assumed. If no tag value is specified then an asterisk ("\*") is used and will
match all values for the tag.


Dependencies
------------

Requires AWS CLI and JQ. AWS default profile or environment variables will be
used.


Examples
-------

Find instances with a "Name" tag containing "nginx":

    $  findly-instances nginx

Find instances with a "Role" tag containing "gateway":

    $  findly-instances --Role gateway

Find all instances having a "LaunchedBy" tag:

    $  findly-instances --LaunchedBy


Output Format
-------------

Output shows basic instance metadata:

```
State   Id          Private IP      Name
running i-00082ec3  10.55.100.61    prod-gateway-01
running i-e5caf72d  10.55.100.62    prod-gateway-02
running i-ce05170d  10.55.96.56     test-gateway-01
running i-ecb92da9  10.55.96.57     test-gateway-02
```
