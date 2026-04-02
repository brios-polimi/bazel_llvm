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

        # A minimal-but-practical set for most downstream users.
        # Prefer the monolithic shared libraries shipped by LLVM releases.
        "-lclang-cpp",
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

genrule(
    name = "make_clang",
    srcs = ["@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:clang"],
    outs = ["clang"],
    cmd = "cp $< $@ && chmod +x $@",
    target_compatible_with = select({
        "//:darwin": ["@platforms//:incompatible"],
        "//conditions:default": [],
    }),
)

genrule(
    name = "make_clang++",
    srcs = ["@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:clang++"],
    outs = ["clang++"],
    cmd = "cp $< $@ && chmod +x $@",
    target_compatible_with = select({
        "//:darwin": ["@platforms//:incompatible"],
        "//conditions:default": [],
    }),
)

genrule(
    name = "make_opt",
    srcs = ["@clang-llvm-16.0.0-x86_64-linux-gnu-ubuntu-18.04//:opt"],
    outs = ["opt"],
    cmd = "cp $< $@ && chmod +x $@",
    target_compatible_with = select({
        "//:darwin": ["@platforms//:incompatible"],
        "//conditions:default": [],
    }),
)

