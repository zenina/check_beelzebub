<<<<<<< HEAD
# Nagios monitoring scripts for beelzebub + unicorn

check_beelzebub_open_files : Monitor number of .yaml data files the worker processes are using, report to Nagios.
check_beelzebub_tx_response_time : Monitor the transaction response time with sierge, report to Nagios.


## Example

These check scripts can be called with or with out arguments. If no arguments are specified they will use the defaults defined at the top of the script. 
If the threshold flags are passed through, they will overwrite the defaults.

```bash
# check_beelzebub_open_files -w <warn threshold> -c <critical threshold> 
$ ./check_beelzebub_open_files -w 100 -c 300 

# check_beelzebub_tx_response_time -w <warn threshold> -c <critical threshold> -t <timeframe in sec> [ -s concurrent sessions ]
$ ./check_beelzebub_tx_response_time -w 5 -c 10 -t 10 -s 5
```
```bash
#Output: 
$ ./check_beelzebub_open_files -w 100 -c 300 
[GREEN]: Transaction file count (< 100): 22

$ ./check_beelzebub_tx_response_time -w 5 -c 10 -t 10 -s 5
[GREEN] Response Time (avg < 5 ): 0.00

```

### Prerequisites

Requirements:
- Bash
- siege (An HTTP/HTTPS stress tester for benchmarking unicorn)
- nagios-nrpe-server ( Nagios nrpe server for client-side plugins )
- nagios-plugins-basic ( Nagios plugins )
- beelzebub + unicorn (ruby App server)

### Installing

- Install siege
- Install scripts into nrpe
- Configure nrpe/nagios checks

```
# Install siege on client
$ apt-get install siege

# Install nrpe server on nrpe client using the Nagios NRPE documentation below

# copy scripts to nrpe client
$ scp check_beelzebub_metrics.tgz nrpe-client:

# unpack into /usr/local/nagios/libexec/
$ tar -xvzf ~/check_beelzebub.tgz -C /usr/local/nagios/libexec

# Edit the threshold flags
# test/run the scripts on the client standalone
$ /usr/local/nagios/libexec/check_beelzebub_open_files
$ /usr/local/nagios/libexec/check_beelzebub_tx_files

# Configure Nagios with nrpe checks using the nagios NRPE documentation
 <https://assets.nagios.com/downloads/nagioscore/docs/nrpe/NRPE.pdf>
```

## Deployment

- Install and run beelzebub + unicorn specific to your custom installation. 
- Setup Nagios+nrpe
- Import check scripts 

## Built using

* GNU bash, version 4.3.30(1)-release

## Versioning

These scripts are locally git controlled within the package/archive. See "git log"
``` 
$ git log
```
## Motivation
* My motivations for using bash:
	- Comfortable with bash
	- Native to unix/linux environments
	- Low on resource consumption
	- Few dependencies/requirements for functionality
	- Fairly secure in comparison to other languages, and their dependencies. 
	- Simple and flexible


=======
# check_beelzebub
Beelzebub nrpe api checks for unicorn.rb 
>>>>>>> 85617de469228af4a897b3c54b5aac899d3e74a5
