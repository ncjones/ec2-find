EC2 Find
========

Bash script to find AWS EC2 instances by tag values and show concise output
that is both human-readable and scripting-friendly. The command syntax is
greatly simplified compared to using `aws ec2 describe-instances` filters.


Usage
-----

```
ec2-find ( --<tag_name> <tag_value> )*
```

Instances having the specified tags will be matched. The tag values can be
partial substring matches. If no tag names are specified then the 'Name' tag is
assumed. If no value is specified for a tag then any value for the tag will be
matched.


Dependencies
------------

Requires AWS CLI and JQ. AWS default profile or environment variables will be
used.


Examples
-------

Find all instances (warning, may be very slow):

    $  ec2-find

Find instances with a "Name" tag containing "nginx":

    $  ec2-find nginx

Find instances with a "Role" tag containing "gateway":

    $  ec2-find --Role gateway

Find all instances with an "aws:cloudformation:stack-name" tag of any value:

    $  ec2-find --aws:cloudformation:stack-name

Find instances with a "Role" tag containing "gateway" and "Env" tag containing
"prod":

    $  ec2-find --Role gateway --Env prod


Output Format
-------------

Output shows common basic instance metadata plus any filtered tags. For
example, the output for `ec2-find --Role gateway` may look like:

```
State    Type      Id          Private IP      Name              Role
running  c4.large  i-00082ec3  10.55.100.61    prod-gateway-01   gateway
running  c4.large  i-e5caf72d  10.55.100.62    prod-gateway-02   gateway
running  t2.micro  i-ce05170d  10.55.96.56     test-gateway-01   gateway
running  t2.micro  i-ecb92da9  10.55.96.57     test-gateway-02   gateway
```
