# Nginx content pack for analysis in Grafana

### Grafana Dashboard:
https://grafana.com/dashboards/8486

### Configuring nginx:
Add this in `/etc/nginx/nginx.conf` and restart server.

### Replace IP-Address to own: 
```
log_format graylog2_json escape=json '{ "timestamp": "$time_iso8601", '
                     '"remote_addr": "$remote_addr", '
                     '"remote_user": "$remote_user",'
                     '"body_bytes_sent": $body_bytes_sent, '
                     '"request_time": $request_time, '
                     '"response_status": $status, '
                     '"request": "$request", '
                     '"request_method": "$request_method", '
                     '"nginx_domain_name": "$host",'
                     '"upstream_cache_status": "$upstream_cache_status",'
                     '"upstream_addr": "$upstream_addr",'
                     '"http_x_forwarded_for": "$http_x_forwarded_for",'
                     '"http_referrer": "$http_referer", '
                     '"http_user_agent": "$http_user_agent" }';

# replace the hostnames with the IP or hostname of your Graylog2 server
access_log syslog:server=192.168.0.110:12304 graylog2_json;
error_log syslog:server=192.168.0.110:12305;
```
