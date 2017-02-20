# bro-splunk

Create the regex for the EXTRACT-\* parameters in props.conf


```
head conn.log |grep ^#fields |sed 's/#fields\t//g' |sed 's/\./_/g' |sed 's/\t/>[^\\t]+)\\t(\?</g' |awk '{print $1">[^\\t]+)"}' |sed 's/^ts>\[^\\t\]+)\\t/^/g'
```

Or if using DELIMS extractions:

```
head conn.log |grep ^#fields |sed 's/#fields\t//g' | sed 's/\t/","/g' |awk '{print $1"\""}' |sed 's/^ts",//g'
```

DELIMS = "\t"
FIELDS = "uid","src_ip","src_port","dst_ip","dst_port","proto","service","duration","orig_bytes","resp_bytes","conn_state","local_orig","local_resp","missed_bytes","history","orig_pkts","orig_ip_bytes","resp_pkts","resp_ip_bytes","tunnel_parents","node","pcr"
