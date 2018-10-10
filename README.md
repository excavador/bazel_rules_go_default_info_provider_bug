rules_go added source file to runfiles, if you add source files to "srcs" by filegroup

Let's build binary
```
➜ bazel build //:main
INFO: Analysed target //:main (0 packages loaded).
INFO: Found 1 target...
Target //:main up-to-date:
  bazel-bin/darwin_amd64_stripped/main
INFO: Elapsed time: 0,148s, Critical Path: 0,00s
INFO: 0 processes.
INFO: Build completed successfully, 1 total action
```

Take a look runfiles
```
➜ ls -al bazel-bin/darwin_amd64_stripped/main.runfiles/__main__/
total 0
drwxr-xr-x  4 oleg  wheel  128 Oct 10 09:25 .
drwxr-xr-x  4 oleg  wheel  128 Oct 10 09:25 ..
drwxr-xr-x  3 oleg  wheel   96 Oct 10 09:25 darwin_amd64_stripped
lrwxr-xr-x  1 oleg  wheel  100 Oct 10 09:25 main.go -> XXX/bazel_rules_go_default_info_provider_bug/main.go
➜
```

Actual behavior: "main.go" added to runfiles


Expected behavior: runfiles should be empty

