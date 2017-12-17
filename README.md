# Nagios monitoring scripts for beelzebub + unicorn

check_beelzebub_open_files : Monitor number of .yaml data files the worker processes are using, report to Nagios.
check_beelzebub_tx_response_time : Monitor the transaction response time with sierge, report to Nagios.


## Example

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
- siege (An HTTP/HTTPS stress tester for benchmarking unicorn)
- nagios-nrpe-server ( Nagios nrpe server for client-side plugins )
- nagios-plugins-basic ( Nagios plugins )
- beelzebub + unicorn (ruby App server)

### Installing

- Install siege
- Install scripts into nrpe
```
apt-get install siege
apt-get install nagios-nrpe-server nagios-plugins-basic
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

- Install and run beelzebub + unicorn specific to your custom installation. 
- 

Add additional notes about how to deploy this on a live system

## Built With

* GNU bash, version 4.3.30(1)-release

## Versioning

These scripts are locally git controlled within the package/archive. See "git log"
``` 
git log
```

## Acknowledgments

* This was a cool code challenge. Thanks BrainTree!
