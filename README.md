# Grafana Dashboard for (Netdata --> InfluxDB via opentsdb)-based system-health monitoring system

To use this dashboard:
 1. Copy the raw version of the `grafana-dashboard.json` [from here](https://raw.githubusercontent.com/kmonsoor/netdata-influx-grafana/master/grafana-dashboard.json).
 2. Modify **all** the `datasource` from `your-influxdb` to your datastore's name that you've defined in your Grafana.
 3. Update **all** the `measurement`s in the JSON e.g. `"netdata.system.cpu.user"` to `your-prefix.system.cpu.user`.
 4. Now, create a new dashboard using the `Import` button on Grafana's dashboard-list menu.

Initially it was based on [this dashboard on Grafana gallery](https://grafana.com/dashboards/1295). Later updated mainly to include templates for machine names.

## Netdata setup

~~~~
[backend]
    # host tags =
    # enabled = no
    enabled = yes
    # data source = average
    # type = graphite
    type = opentsdb
    # destination = localhost
    destination = localhost:4242
    # prefix = netdata
~~~~

## InfluxDB setup

* Enable `opentsdb` backend and restart. https://github.com/firehol/netdata/issues/3122

## Datasource setup in grafana

Datasource -> New
_Type_: InfluxDB
_Name_: opentsdb
