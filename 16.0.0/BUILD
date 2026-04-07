# LLVM 16.0.0.
package(default_visibility = ["//visibility:public"])

licenses(["notice"])

cc_library(
    name = "16.0.0",
    target_compatible_with = select({
        "//:darwin": ["@platforms//:incompatible"],
        "//conditions:default": [],
    }),
    data = [
        "@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:libdir",
    ],
    defines = [
        "__STDC_CONSTANT_MACROS",
        "__STDC_LIMIT_MACROS",
    ],
    linkopts = [
        "-Wl,-rpath,$(location @clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:libdir)/",
        "-L$(location @clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:libdir)/",
        "-lLLVM-16",
        "-lrt",
        "-ldl",
        "-ltinfo",
        "-lpthread",
        "-lm",
        "-lz",
    ],
    deps = [
        "@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:headers",
        # Removed :shared_libs — it pulls in broken sanitizer libs from
        # the Ubuntu 18.04 prebuilt that are incompatible with Ubuntu 24.04.
        # libLLVM-16.so is linked directly via linkopts above instead.
    ],
)