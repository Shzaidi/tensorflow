package(
    default_testonly = True,
    default_visibility = ["//tensorflow:internal"],
)

load("@io_bazel_rules_closure//closure:defs.bzl", "web_library")
load("//tensorflow/tensorboard:hacks.bzl", "tensorboard_typescript_bundle")
load("//tensorflow/tensorboard:defs.bzl", "tensorboard_typescript_genrule")

licenses(["notice"])  # Apache 2.0

web_library(
    name = "test",
    srcs = [
        "bundle.js",
        "tests.html",
    ],
    path = "/vz-sorting/test",
    deps = [
        "//tensorflow/tensorboard/components/vz_sorting",
        "@org_npmjs_registry_web_component_tester",
    ],
)

tensorboard_typescript_genrule(
    name = "ts",
    srcs = ["bundle.ts"],
    typings = [
        "@org_definitelytyped//:mocha.d.ts",
        "@org_definitelytyped//:chai.d.ts",
        "//tensorflow/tensorboard/components/vz_sorting:bundle.d.ts",
    ],
)

tensorboard_typescript_bundle(
    name = "bundle",
    out = "bundle.ts",
    namespace_srcs = {"VZ.Sorting": ["sortingTests.ts"]},
)

filegroup(
    name = "all_files",
    testonly = 0,
    srcs = glob(["**"]),
    tags = ["notsan"],
)
