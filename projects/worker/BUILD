package(default_visibility = ["//visibility:public"])

load("@batfish//skylark:junit.bzl", "junit_tests")

java_binary(
    name = "worker_main",
    main_class = "org.batfish.main.Driver",
    runtime_deps = [
        ":worker",
    ],
)

java_library(
    name = "worker",
    srcs = glob([
        "src/main/**/*.java",
    ]),
    plugins = [
        "//:auto_service_plugin",
    ],
    runtime_deps = [
        "//projects/question",
    ],
    deps = [
        "//projects/batfish-common-protocol:common",
        "//projects/lib/bdd",
        "//projects/lib/z3",
        "//projects/question",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/cisco",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/flatjuniper",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/flatvyos",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/iptables",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/juniper",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/mrv",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/palo_alto",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/routing_table/eos",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/routing_table/ios",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/routing_table/nxos",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/vyos",
        "@antlr4_runtime//:compile",
        "@auto_service//:compile",
        "@commons_collections4//:compile",
        "@commons_configuration2//:compile",
        "@commons_lang3//:compile",
        "@grizzly_server//:compile",
        "@guava//:compile",
        "@jackson_annotations//:compile",
        "@jackson_core//:compile",
        "@jackson_databind//:compile",
        "@jaeger_core//:compile",
        "@jaxrs_api//:compile",
        "@jersey_common//:compile",
        "@jersey_container_grizzly2//:compile",
        "@jersey_media_jettison//:compile",
        "@jersey_server//:compile",
        "@jettison//:compile",
        "@jgrapht//:compile",
        "@jsr305//:compile",
        "@lz4//:compile",
        "@opentracing_api//:compile",
        "@opentracing_contrib_jaxrs//:compile",
        "@opentracing_util//:compile",
    ],
)

java_library(
    name = "worker_testlib",
    testonly = True,
    srcs = glob(
        [
            "src/test/**/*.java",
        ],
        exclude = ["src/test/**/*Test.java"],
    ),
    deps = [
        ":worker",
        "//projects/batfish-common-protocol:common",
        "//projects/batfish-common-protocol:common_testlib",
        "//projects/lib/bdd",
        "//projects/lib/z3",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/flatjuniper",
        "@antlr4_runtime//:compile",
        "@commons_collections4//:compile",
        "@guava//:compile",
        "@hamcrest//:compile",
        "@jsr305//:compile",
        "@junit//:compile",
    ],
)

junit_tests(
    name = "worker_tests",
    size = "medium",
    srcs = glob([
        "src/test/**/*Test.java",
    ]),
    resources = glob([
        "src/test/resources/**",
    ]),
    deps = [
        ":worker",
        ":worker_testlib",
        "//projects/batfish-common-protocol:common",
        "//projects/batfish-common-protocol:common_testlib",
        "//projects/lib/bdd",
        "//projects/lib/z3",
        "//projects/worker/src/main/antlr4/org/batfish/grammar/flatjuniper",
        "@antlr4_runtime//:compile",
        "@guava//:compile",
        "@hamcrest//:compile",
        "@jackson_databind//:compile",
        "@jettison//:compile",
        "@junit//:compile",
    ],
)
