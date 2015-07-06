# Chalk [![Build Status](https://travis-ci.org/markbates/chalk.svg)](https://travis-ci.org/markbates/chalk) [![Godoc](http://img.shields.io/badge/godoc-reference-blue.svg?style=flat)](https://godoc.org/github.com/markbates/chalk) [![license](http://img.shields.io/badge/license-MIT-red.svg?style=flat)](https://raw.githubusercontent.com/markbates/chalk/master/LICENSE)

Quickly and easily create a pool of `go routines`. Create as many "queues" as you want, each with their own number of `go routines` ready to do your bidding.

## Installation

```bash
$ go get https://github.com/markbates/chalk
```

## Usage

```go
// create a pool of 10 go routines
c := chalk.New(10)

c.Tasks <- func() error {
  // do some work here
  return nil
}

// handle err
c.Tasks <- func() error {
  return errors.New("boom!")
}

err := <-c.Errors

// wait for all of the workers to finish
c.Wait()
```
