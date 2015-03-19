netfilter
=========

Utility to filter input files whose lines contain IP addresses
by specific netblocks.

### Example ###

You want to determine all the hosts internal to your network that are
using your service.

Given an Nginx log file:

	```
	80.154.42.54 - - [23/Aug/2010:15:25:35 +0000] "GET /phpmy-admin/scripts/setup.php HTTP/1.1" 404 347 "-" "ZmEu"
	10.154.42.54 - - [23/Aug/2010:15:25:35 +0000] "GET /phpmy-admin/index.php HTTP/1.1" 200 347 "-" "ZmEu"
	```

Run netfilter:

	```
	netfilter --netblocks 10.0.0.0/8,172.16.0.0/12,192.168.0.0/16 \
		--regex "^([^\s]+)" --group 1
		--input "/var/log/nginx/access.log > internal_access.log
	```

