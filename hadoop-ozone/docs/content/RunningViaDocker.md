---
title: Alpha Cluster
weight: 1
menu:
   main:
      parent: Starting
      weight: 1
---
<!---
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License. See accompanying LICENSE file.
-->


***This is an alpha release of Ozone. Please don't use this release in
production.*** Please check the road map page for features under
development.

The easiest way to run ozone is to download the release tarball and launch
ozone via Docker. Docker will create a small ozone cluster on your machine,
including the data nodes and ozone services.

## Running Ozone via Docker


**This assumes that you have Docker installed on the machine.**

* Download the Ozone tarball and untar it.

* Go to the directory where the docker compose files exist and tell
`docker-compose` to start Ozone in the background. This will start a small
ozone instance on your machine.

{{< highlight bash >}}
cd ozone-0.2.1-SNAPSHOT/compose/ozone/

docker-compose up -d
{{< /highlight >}}


To verify that ozone is working as expected, let us log into a data node and
run _freon_, the load generator for Ozone. The ```exec datanode bash``` command
will open a bash shell on the datanode. The ozone freon command is executed
within the datanode container. You can quit freon via CTRL-C any time. The
```rk``` profile instructs freon to generate random keys.

{{< highlight bash >}}
docker-compose exec datanode bash
ozone freon rk
{{< /highlight >}}

You can check out the **OzoneManager UI** at http://localhost:9874/ to see the
activity generated by freon.
While you are there, please don't forget to check out the ozone configuration explorer.

***Congratulations, You have just run your first ozone cluster.***

To shutdown the cluster, please run
{{< highlight bash >}}
docker-compose down
{{< /highlight >}}