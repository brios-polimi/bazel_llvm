# LLVM 16.0.0.
package(default_visibility = ["//visibility:public"])

licenses(["notice"])

cc_library(
    name = "16.0.0",
    # LLVM 16.0.0 does not ship an x86_64 macOS release tarball upstream.
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

        # Prefer the monolithic shared library shipped by LLVM releases.
        "-lLLVM",

        # Common system libs (roughly llvm-config --system-libs).
        "-lrt",
        "-ldl",
        "-ltinfo",
        "-lpthread",
        "-lm",
        "-lz",
    ],
    deps = [
        "@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:headers",
        "@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:shared_libs",
    ],
)
