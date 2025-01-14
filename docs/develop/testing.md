---
title: Automated testing
subtitle: Confidence at speed
---

Go comes with excellent built-in support for automated tests.
Encore builds on top of this foundation, and lets you write tests in exactly the same way.
We won't cover how to write tests here; see [the official Go docs](https://golang.org/pkg/testing/) for that.

The main difference is that due to Encore requiring an extra compilation step,
you must run your tests using `encore test` instead of `go test`. This is
a wrapper that compiles the Encore app and then runs `go test`, and supports
all the same flags that the `go test` command does.

For example, use `encore test ./...` to run tests in all sub-directories,
or just `encore test` for the current directory.

## Integration testing

Since Encore removes a lot of boilerplate, a lot of the code you'll be writing
is business logic that involves databases and calling APIs between services.
Such behavior is most easily tested with integration tests.

When running tests, Encore automatically sets up the databases you need
in a separate database cluster. They are additionally configured to skip `fsync`
and to use an in-memory filesystem since durability is not a concern for automated tests.

This drastically reduces the speed overhead of writing integration tests.

In general, Encore applications tend to focus more on integration tests
compared to traditional applications that are heavier on unit tests.
This is nothing to worry about and is the recommended best practice.