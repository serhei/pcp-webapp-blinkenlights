# 'Blinkenlights' demo for `pcp-webapi`

This is a basic HTML demo demonstrating how to access Performance Co-Pilot metrics using the JSON API provided by `pmwebd`. You can specify a set of [PMIE predicates](http://pcp.io/docs/lab.pmie.html) and watch little lights that turn green and red depending on whether the predicates are true or not.

The code is meant to be simple enough to quickly understand, rather than full-featured. For full-featured visualization of Performance Co-Pilot metrics in a web application, you probably want [Grafana](https://github.com/performancecopilot/pcp-webapp-grafana), [Graphite](https://github.com/performancecopilot/pcp-webapp-graphite) or [Vector](https://github.com/performancecopilot/pcp-webapp-vector).

More information about PCP's web services is available in the [PCP quick reference guide](http://pcp.io/docs/guide.html#web).

## Give it a Spin

Quickly, on Fedora: install the packages for PCP, `pcp-webapi` and `pcp-webapp-blinkenlights`. Launch `pmwebd` and open http://localhost:44323/blinkenlights. The page will be served from `pmwebd`'s resources folder (configured in `/etc/pcp/pmwebd/pmwebd.options`). This usually defaults to `/usr/share/pcp/webapps/blinkenlights`.

Less quickly, from a checkout of the repo:

1. Set up Performance Co-Pilot using the [official instructions](http://pcp.io/download.html), which will tell you to start up `pmcd` and `pmie`.

2. Also make sure you install `pcp-webapi` (provided as a separate package on some systems!) and start up `pmwebd`. For example, on recent Fedoras:

    sudo dnf install pcp-webapi
    systemctl start pmwebd

3. Open `index.html` in a web browser. (You could also serve it from `pmwebd`'s resources folder.). By default, the app will connect to `localhost:44323/pmapi` and you will get blinkenlights for the [PMIE predicate](http://pcp.io/docs/lab.pmie.html) `kernel.all.load[*] > 0.2`.
