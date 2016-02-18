# CIS Benchmarks in Goss

Honestly, this is just an exercise to see if I could make a useful checklist, quickly. It assumes the following:

- Debian Wheezy
- 64 bit machine

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
