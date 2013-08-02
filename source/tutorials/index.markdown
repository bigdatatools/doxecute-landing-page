---
layout: page
title: "Tutorials"
date: 2013-08-01 17:59
comments: true
sharing: true
footer: true
---

Setup Doxecute on EC2 
=====================
You can deploy and start Doxecute server in your EC2 node running Linux by running a command in your laptop.

Unzip the tarball
-----------------
{% codeblock %}
tester@bigdatatools:~$ tar xvfz doxecute-1.0.tar.gz
tester@bigdatatools:~$ cd doxecute-1.0
tester@bigdatatools:~$ 
{% endcodeblock %}

Deploy Doxecute on EC2
----------------------
Run deploy-ec2.sh to deploy Doxecute on your EC2 node. 
{% codeblock %}
tester@bigdatatools:~$ ./deploy-ec2.sh -node ec2-123-123-123-123.compute-1.amazonaws.com
Doxecute version 1.0 deployed on ec2-123-123-123-123.compute-1.amazonaws.com.

tester@bigdatatools:~$
{% endcodeblock %}

Run an interactive shell, Doxi
==============================
Simply run Doxi, an interactive shell for communicating with Doxecute. 
You don't need to specify the address of your EC2 node, as it is stored in config.yml in doxecute-1.0.
{% codeblock %}
tester@bigdatatools:~$ ./doxi
Hey, doxecute your documents! 
Doxi> 
{% endcodeblock %}

From now on, you are in Doxi shell. 

Create a collection
-------------------
A collection is where your JSON documents are stored. There are two kinds of collections; VOLATILE and PERSISTENT. A volatile collection keeps data in memory for fast access to your data, but your working set should fit into the size of your RAM. A persistent collection preserves your data on disk, but it may require more time to keep your data on disk. 
{% codeblock %}
Doxi> CREATE PERSISTENT COLLECTION people; 

Collection people created. 
Took 0.2 ms. 

Doxi>
{% endcodeblock %} 

Insert a document
-----------------
Issue an INSERT statement to insert your JSON document.
{% codeblock %}
Doxi> INSERT INTO people VALUES(
{
    "firstName": "John",
    "lastName": "Smith",
    "age": 25,
    "address": {
        "streetAddress": "21 2nd Street",
        "city": "New York",
        "state": "NY",
        "postalCode": 10021
    },
    "phoneNumbers": [
        {
            "type": "home",
            "number": "212 555-1234"
        },
        {
            "type": "fax",
            "number": "646 555-4567"
        }
    ]
});

1 document inserted.
Took 0.005 ms. 

Doxi> 
{% endcodeblock %}

Create indexes
--------------
Create indexes using CREATE INDEX statement.

{% codeblock %}
Doxi> CREATE INDEX people_name ON (firstName, lastName);

Index people_name created. 
Took 0.003 ms.

Doxi>
{% endcodeblock %}

Select documents
----------------
Issue SELECT statement to select JSON documents.

{% codeblock %}
Doxi> SELECT firstName, lastName, age FROM people WHERE phoneNumbers.number = '212 555-1234' 

--------- -------- ---
firstName lastName age
--------- -------- ---
     John    Smith  25

1 document selected.
Took 0.003 ms.

Doxi> 
{% endcodeblock %}

Update documents
----------------
Issue UPDATE statement to update your JSON documents.

{% codeblock %}
Doxi> UPDATE people SET age=age+1 WHERE firstName='John';

1 document updated.
Took 0.004 ms.

Doxi> 
{% endcodeblock %}

Delete documents
----------------
Issue DELETE statement to delete your JSON documents.

{% codeblock %}
Doxi> DELETE FROM people WHERE firstName='John';

1 document deleted.
Took 0.002 ms.

Doxi> 
{% endcodeblock %}

Drop collections
-----------------
Issue DROP COLLECTION statement to drop a collection.

{% codeblock %}
Doxi> DROP COLLECTION people;

Collection people dropped.
Took 0.002 ms.

Doxi> 
{% endcodeblock %} 
