<!--
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to You under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

![logo](http://phoenix.apache.org/images/logo.png)

<b>[Apache Phoenix](http://phoenix.apache.org/)</b> is a SQL skin over HBase delivered as a client-embedded JDBC driver targeting low latency queries over HBase data. Visit the Apache Phoenix website <b>[here](http://phoenix.apache.org/)</b>.

Copyright ©2014 [Apache Software Foundation](http://www.apache.org/). All Rights Reserved. 

> This project is derived from the project [chiastic-security/phoenix-for-cloudera](https://github.com/chiastic-security/phoenix-for-cloudera).

# Building

The master branch is based on the Apache Phoenix 4.10.0. You should checkout the branch 4.10-HBase-1.2-cdh5.10 for Cloudera.

To build the jars
    $ mvn clean package
and optionally, to just skip all the tests and build the jars:
    $ mvn clean package -DskipTests

# How to create parcel for Cloudera

There is a folder PHOENIX-4.10.0-1.cdh5.10.0.p0.000 in parcel/. 
* Uncompress the files to PHOENIX-4.10.0-1.cdh5.10.0.p0.000/lib/phoenix/
    tar -zxvf phoenix-assembly/target/phoenix-4.10.0-cdh5.10.0.tar.gz
    mv phoenix-4.10.0-cdh5.10.0/* PHOENIX-4.10.0-1.cdh5.10.0.p0.000/lib/phoenix/
* Create the parcel file
    tar -zcvf PHOENIX-4.10.0-1.cdh5.10.0.p0.000-el6.parcel PHOENIX-4.10.0-1.cdh5.10.0.p0.000/ --owner=root --group=root
* Create sha1 file
    # Echo the command output to the sha1 file
    sha1sum PHOENIX-4.10.0-1.cdh5.10.0.p0.000-el6.parcel
        895edc93aba81afa10f7365a62005d4d3214a640
    echo "895edc93aba81afa10f7365a62005d4d3214a640" > PHOENIX-4.10.0-1.cdh5.10.0.p0.000-el6.parcel.sha1
* Define manifest.json based on the file in parcel/
* Copy the three files to the Cloudera repository
    PHOENIX-4.10.0-1.cdh5.10.0.p0.000-el6.parcel
    PHOENIX-4.10.0-1.cdh5.10.0.p0.000-el6.parcel.sha1
    manifest.json
