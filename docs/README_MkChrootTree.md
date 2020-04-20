This script mounts the chroot-dev target-disk (previously configured by `DiskSetup.sh`)

~~~
./MkChrootTree.sh --help
Usage: ./MkChrootTree.sh [GNU long option] [option] ...
  Options:
        -d  Device to contain the OS partition(s) (e.g., "/dev/xvdf")
        -f  Filesystem-type used for root filesystems (default: xfs)
        -h  Print this message
        -m  Where to mount chroot-dev (default: "/mnt/ec2-root")
        -p  Comma-delimited string of colon-delimited partition-specs
              Default layout:
                /:rootVol:4
                swap:swapVol:2
                /home:homeVol:1
                /var:varVol:2
                /var/log:logVol:2
                /var/log/audit:auditVol:100%FREE
  GNU long options:
        --disk              See "-d" short-option
        --fstype            See "-f" short-option
        --help              See "-h" short-option
        --mountpoint        See "-m" short-option
        --partition-string  See "-p" short-option
~~~

Each of the functionality flag-options may also be specified by using environment variables:

- `CHROOTDEV`: Stands in for the `-d`/`--disk` flag-option
- `CHROOTMNT`: Stands in for the `-m`/`--mountpoint` flag-option
- `FSTYPE`: Stands in for the `-f`/`--fstype` flag-option. This env (or corresponding flags) is only necessary if the corresponding flag was used to override the `DiskSetup.sh` script's default behavior.
- `GEOMETRYSTRING`: Stands in for the `-p`/`--partition-string` flag-option. This env (or corresponding flags) is only necessary if the corresponding flag was used to override the `DiskSetup.sh` script's default behavior.

Further, additional output/logging can be generated by setting the `DEBUG` environment variable to "`true`". Doing so causes information that is normally only directed to syslog to also be printed to `STDOUT`.

## Notes:

<sup>1</sup>If invoking scripts interactively, the `DEBUG` value is automatically set to true.