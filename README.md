# gocov

Coverage reporting tool for The Go Programming Language

[![Build Status](https://travis-ci.org/manilion/gocov.svg?branch=master)](https://travis-ci.org/manilion/gocov)

## Installation

```go get github.com/manilion/gocov/gocov```

## Usage

There are currently four gocov commands: ```test```, ```convert```, ```report``` and ```annotate```.

#### gocov test

Running `gocov test [args...]` will run `go test [args...]` with
an implicit `-coverprofile` added, and then output the result of
`gocov convert` with the profile.

#### gocov convert

Running `gocov convert <coverprofile>` will convert a coverage
profile generated by `go tool cover` to gocov's JSON interchange
format. For example:

    go test -coverprofile=c.out
    gocov convert c.out | gocov annotate -

#### gocov report

Running `gocov report <coverage.json>` will generate a textual
report from the coverage data output by `gocov convert`. It is
assumed that the source code has not changed in between.

Output from ```gocov test``` is printed to stdout so users can
pipe the output to ```gocov report``` to view a summary of the test
coverage, for example: -

    gocov test | gocov report

#### gocov annotate

Running `gocov annotate <coverage.json> <package[.receiver].function>`
will generate a source listing of the specified function, annotating
it with coverage information, such as which lines have been missed.

## Related tools and services

[GoCovGUI](http://github.com/nsf/gocovgui/):
A simple GUI wrapper for the gocov coverage analysis tool.

[gocov-html](https://github.com/matm/gocov-html):
A simple helper tool for generating HTML output from gocov.

[gocov-xml](https://github.com/AlekSi/gocov-xml):
A simple helper tool for generating XML output in Cobertura format for CIs like Jenkins and others from gocov. 
