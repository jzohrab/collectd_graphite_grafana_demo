# Collectd/Graphite/Grafana demo

This project provides a simple demonstration of Collectd, Graphite,
and Grafana.

## Usage

Use `vagrant up` to start the VM.

Provisioning will take a few minutes as packages are installed and configured.

The provision script seeds your Graphite database with some data:

* some raw data is sent to Graphite via `echo "test.count 4 `date
+%s`" | nc -q0 127.0.0.1 2003`.
* collectd gathers Apached stats, which are also reported at http://localhost:8080/server-status

### Graphite

The Graphite UI is at http://localhost:8080/ or http://192.168.33.10.
The username/password is admin/admin.

You can click on metrics in the Graphite navigation tree review the
graphing options.  See the section "Checking out the Web Interface")
in this
[tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-graphite-on-an-ubuntu-14-04-server)
for more information.

### Grafana

Grafana is at http://192.168.33.10:3000/.  The username/password is
admin/admin.

You have to configure Grafana to use Graphite as a data source.  Click
the Grafana icon (top left corner) and click Data Sources, and Add
New.  Set the name as local_graphite, set as Default, type Graphite.
The URL is http://192.168.33.10, access proxy, no HTTP auth.

![Adding the Graphite data source](img/grafana_add_source.png?raw=true "Adding the Graphite data source")

Save this, and click "Test Connection" to verify.

Once this is verified, you can start building your first dashboard.


## Shutting down

Since provisioning the box from scratch takes time, you may prefer to
`vagrant suspend` the box when you're done using it.  You can then
`vagrant resume` the box.

To destroy the box completely, use `vagrant destroy`.  Note that if
you destroy the box, any manual configuration you've done, such as
creating Grafana or Graphite graphs, is lost.

## References

* The initial configuration for this demo was done following [this
  example](https://www.digitalocean.com/community/tutorials/an-introduction-to-tracking-statistics-with-graphite-statsd-and-collectd)
* If you're new to Grafana, you may find [this Grafana screencast for
  beginners](https://www.youtube.com/watch?v=sKNZMtoSHN4) helpful.

