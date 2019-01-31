<H3>control+A delimiter and control+B delimiter 

cut -d $'\x02' -f2 SCI_APPROVED_LIMIT_01.SQL  --> ctrl+B (^B)
cut -d $'\x01' -f2 SCI_APPROVED_LIMIT_01.SQL  --> ctrl+A (^A)

awk -F '\x02' '{ if(($1 == "${prcs_nm}") && ($8 == "P")) { print $2} }' ${PROCESS_META_PATH}/${SOURCE_UPPER}_${COUNTRY_UPPER}_PROCESS.meta

awk '$[column]="[replace]"' FS=, OFS=, inputfile > outputfile

awk -F '\x02' '$4="GB"' inputfile > outputfile

sed -i "s/^BUK^B/^BGB^B/g" *


<H3>hive force execution of script -
--hiveconf hive.cli.errors.ignore=true 

<H3>Beeline force execution of the script -
--force=true

<H3> Beeline command to submit a hql file
beeline -u 'URL' --showHeader=false --outputformat=csv2 -n <user_name> -p <pwd> -f filename.hql

beeline -u '<URL>?tez.queue.name=<QueueName>;serviceDiscoveryMode=zookeeper;zooKeeperNamespace=hiveserver2;' -n <user>  -w <pwd file name>

