# Rangelang
Cyber range description language.

## Motivation

Cyber ranges come in all shapes and sizes, on different infrastructure provided
by a myriad of on-premises and remote providers. Ranges run different software,
and change state during runtime. Ideally, there should be some way of deploying
and managing cyber ranges easily in a provider-agnostic manner, whose initial
(and possibly runtime) states can be saved and replicated.

## Range language

The state of a range is described by a Rangelang file. Rangelang is a
domain-specific language (DSL) of sorts, which describes the state of a cyber
range at a moment in time. It may also describe events prior and/or after that
moment, which can bring the given range into a past or present state.

All Rangelang must be valid JSON, however there are further constraints that
define Rangelang itself. A full specification is under development in
[doc/spec.md][1]

Hello World in Rangelang:

```json
{
	"type": "machine",
	"name": "hello-world"
}
```

This deploys a single machine with name `hello-world` to a range. More examples
available in the [examples][2] folder.

## Range manager

The state of a range is maintained by a range manager. A range manager is
responsible for tasks such as:

  - **Applying a state to a range.** If there is, say, an empty cloud
    environment, a desired state could be deployed to that environment.

  - **Updating the state of a range.** If a deployed range already exists, the
    range manager can respond to requests for state updates. For example, a
    researcher might need five new machines — the range manager can add them to
    the range on demand, at runtime. It will then update its internal Rangelang
    description of the state, to account for the new machines and the events of
    adding those machines.

There may only be one range manager for a given cyber range.

## Range CLI

A simple CLI can be used to interact with the range manager API. A user can
request the addition/removal of resources, schedule an attack, etc. The user can
provide snippets of Rangelang to achieve this:

```sh
$ cat machine.json
{
	"type": "machine",
	"name": "hello-world"
}
$ range add machine.json	# one "hello-world" machine added
$ range add machine.json	# second "hello-world" machine added
```

## Range GUI

The real power of managing a cyber range would come from a GUI. We are currently
interested in something similar to [CORE][3]. A user could configure desired
states, manage existing ranges using an intuitive graphical interface. Assuming
the underlying language and range manager are flexible, a GUI would be the
cherry on top in this approach to managing cyber ranges.


[1]: doc/spec.md
[2]: examples/
[3]: https://github.com/coreemu/core
