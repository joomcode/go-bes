This directory contains .proto definitions copied from:
* https://github.com/bazelbuild/bazel/tree/master/src/main/protobuf
* https://github.com/bazelbuild/bazel/tree/master/src/main/java/com/google/devtools/build/lib/buildeventstream/proto

They aren't used for Go code generation in the original repository, so importing them directly is inconvenient. We need them to be able to read binary bazel eventlog files. 

Current solution is to use a slightly modified copy of these files. Original files can be found in commit #[75a16b7](https://github.com/bazelbuild/bazel/tree/75a16b7107479441274fa983c04264cdf8556479/src/main/protobuf). If the Bazel event protocol changes, this copy will require a manual update.

Changelist:
* `failure_details.WorkspaceStatus` -> `FailureWorkspaceStatus`, to avoid collision with `build_event_stream.WorkspaceStatus`
* `go_package` instead of `java_package`
* proto-files use local import paths instead of original paths
