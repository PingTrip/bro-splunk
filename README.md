# bro-splunk

Create the regex for the EXTRACT-\* parameters in props.conf


```
head conn.log |grep ^#fields |sed 's/#fields\t//g' |sed 's/\./_/g' |sed 's/\t/>[^\\t]+)\\t(\?</g' |awk '{print $1">[^\\t]+)"}' |sed 's/^ts>\[^\\t\]+)\\t/^/g'
```

Or if using DELIMITER extractions:

```
head conn.log |grep ^#fields |sed 's/#fields\t//g' | sed 's/\t/","/g' |awk '{print $1"\""}' |sed 's/^ts",//g'
```
