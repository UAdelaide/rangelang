# The Rangelang Specification

## Introduction

This is the official specification for the Rangelang cyber range description
language. **This is a rapidly evolving specification; nothing is set in stone.**

Rangelang describes the state of a cyber range at a moment in time. It may also
describe events prior and/or after that moment, which can bring the given range
into a past or present state.

Rangelang is designed for readability by both humans and machines. It is
possible to describe objects without specifying values for all available
attributes — the range manager will use sane defaults for unspecified
attributes. The range manager should also not be overly verbose when updating
the state of a range, ensuring only relevant and required details are included.

## Notation

At the moment, valid Rangelang must be valid JSON as defined in [RFC 7159][1].
All further constraints are imposed by this specification.

**TODO: write this**


[1]: https://rfc-editor.org/rfc/rfc7159.html
