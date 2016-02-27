# CIS Benchmarks in Goss

Honestly, this is just an exercise to see if I could make a useful checklist, quickly. It assumes the following:

- Debian Wheezy
- 64 bit machine

It checks against the [CIS Security Benchmarks](https://benchmarks.cisecurity.org/) for Wheezy, version v1.0.0 - 12-31-2015. I'm currently trying to add all scored items, some non-scored do get in as well. In developer terms, a missing scored item is a bug, a missing non-scored item is a feature request.

## Usage

First, install [goss](https://github.com/aelsabbahy/goss).

Next, run it with the yaml you want to use, either the Level 1 or the Level 2:

```
goss -g cis-level1.yaml validate
```

Examine the output. Keep in mind that for a functional server, you should **expect failures**. But for each failure, you should ask yourself whether it is warrented on this specific server. If it's a webserver, it's probably warrented to have an Apache or Nginx installed, for example. Do not change things to fix checks, consider what the effect of the change would be, first.

## Status

Still under heavy development. Pull requests are appreciated!

## Todo

- Split things off so you can do more fine-grained testing. For example, you should be able to specify if you're running a webserver. Or a router.
- Check with the actual CIS Benchmark.
- Create a version for Jessie as well.
- Add comments describing which section the check is for.
- Items that cannot be easily transcribed into single checks:
  - 8.2.4 (checks files that are mentioned in rsyslog.conf)
  - 8.2.5 (checks whether rsyslog sends log to remote server, we can only check if it is send, but we cannot know the destination)

## Assorted notes

### Regarding 8.3.2 (Aide cronjob)

I personally do not recommend implementing a cronjob in a crontab on /var/spool. It's part of the system configuration, which to me means it should go in /etc. I'm implementing the supplied spec, however, so the check is performed as dictated on the personal crontab of root.
