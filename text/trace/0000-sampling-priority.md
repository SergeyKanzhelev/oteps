# Associating sampling priority with the trace using tracestate

Propagating `sampling.priority` (calculated by probability sampler) in a
`tracestate` will enable a better experience for system with the independent
stateless configuration of components sampling.

## Motivation

Consistent sampling decision made in each app of a distributed trace is
important for better user experience of traces analysis. Consistency is achieved
by aligning stateless hashing algorithm used to make a decision based on
trace-id or explicitly propagating sampling flag.

Increasingly more apps participate in distributed tracing. With the
standardized wire format for context propagation, there is bigger chance that
approach for sampling chosen by one app may not match another app sampling
policy. Since coordination of sampling policies accross many apps not alwasy
possible, OpenTelemetry must provide a way to share sampling hints between apps.

Beyond sampling hints infrastructure, it is beneficial for the community to
agree on standard behavior and hints exposed by probability sampler.

The `sampling.priority` property is used by many vendors for various purposes.
Propagating this field alongside the trace will allow for many improvements and
as a very minimum will simplify transition of customers from SDKs using
different `trace-id` based hash functions to OpenTelemetry SDK.

Also see discussion here: https://github.com/open-telemetry/opentelemetry-specification/pull/570

## Explanation


## Internal details



## Trade-offs and mitigations

What are some (known!) drawbacks? What are some ways that they might be mitigated?

Note that mitigations do not need to be complete *solutions*, and that they do not need to be accomplished directly through your proposal. A suggested mitigation may even warrant its own OTEP!

## Prior art and alternatives

What are some prior and/or alternative approaches? For instance, is there a corresponding feature in OpenTracing or OpenCensus? What are some ideas that you have rejected?

## Open questions

What are some questions that you know aren't resolved yet by the OTEP? These may be questions that could be answered through further discussion, implementation experiments, or anything else that the future may bring.

## Future possibilities

What are some future changes that this proposal would enable?