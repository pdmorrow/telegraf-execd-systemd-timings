# telegraf-execd-systemd-timings

This is a wrapper around the [systemd_timings](https://github.com/pdmorrow/telegraf-systemd-timings) package which allows systemd boot timing metrics to be collected by the telegraf execd input plugin.

For more details on the metrics collected see the [systemd_timings](https://github.com/pdmorrow/telegraf-systemd-timings) repository.

# Install Instructions

Download the repository:

$ git clone https://github.com/pdmorrow/telegraf-execd-systemd-timings.git

Build the binary:

$ go build -o telegraf-execd-systemd-timings cmd/telegraf-execd-systemd-timings/main.go

You should then be able to call this from telegraf now using:

```
[[inputs.execd]]
   command = ["/path/to/telegraf-execd-systemd-timings", "-config", "/etc/telegraf-execd-systemd-timings.conf"]
```

The -config argument is optional, for information on plugin configuration see [here](https://github.com/pdmorrow/telegraf-systemd-timings#configuration). By default metrics are collected only once since these are boot metrics, however the plugin can be configured to run periodically which will result in metrics being produced continuously even though the metric values will not change unless a unit is restarted.
