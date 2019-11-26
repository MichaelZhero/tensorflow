licenses(["notice"])  # 3-Clause BSD

exports_files(["LICENSE"])

load(
    "@org_tensorflow//tensorflow:tensorflow.bzl",
    "tf_cc_test",
)

cc_library(
    name = "ngraph_tf",
    srcs = [
        "logging/ngraph_log.cc",
        "logging/ngraph_log.h",
        "logging/tf_graph_writer.cc",
        "logging/tf_graph_writer.h",
        "src/ngraph_api.cc",
        "src/ngraph_api.h",
        "src/ngraph_assign_clusters.cc",
        "src/ngraph_assign_clusters.h",
        "src/ngraph_backend_manager.cc",
        "src/ngraph_backend_manager.h",
        "src/ngraph_builder.cc",
        "src/ngraph_builder.h",
        "src/ngraph_capture_variables.cc",
        "src/ngraph_capture_variables.h",
        "src/ngraph_cluster_manager.cc",
        "src/ngraph_cluster_manager.h",
        "src/ngraph_conversions.h",
        "src/ngraph_deassign_clusters.cc",
        "src/ngraph_deassign_clusters.h",
        "src/ngraph_encapsulate_clusters.cc",
        "src/ngraph_encapsulate_clusters.h",
        "src/ngraph_encapsulate_op.cc",
        "src/ngraph_freshness_tracker.cc",
        "src/ngraph_freshness_tracker.h",
        "src/ngraph_mark_for_clustering.cc",
        "src/ngraph_mark_for_clustering.h",
        "src/ngraph_rewrite_for_tracking.cc",
        "src/ngraph_rewrite_for_tracking.h",
        "src/ngraph_rewrite_pass.cc",
        "src/ngraph_tracked_variable.cc",
        "src/ngraph_utils.cc",
        "src/ngraph_utils.h",
        "src/ngraph_version_utils.h",
        "src/tf_deadness_analysis.cc",
        "src/tf_deadness_analysis.h",
        "src/tf_graphcycles.cc",
        "src/tf_graphcycles.h",
    ],
    copts = [
        "-I external/ngraph_tf/src",
        "-I external/ngraph_tf/logging",
        "-I external/ngraph/src",
    ],
    visibility = ["//visibility:public"],
    deps = [
        "@com_google_absl//absl/container:container_memory",
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/types:variant",
        "@ngraph//:ngraph_core",
        "@org_tensorflow//tensorflow/core:core_cpu_headers_lib",
        "@org_tensorflow//tensorflow/core:framework_headers_lib",
    ],
    alwayslink = 1,
)

tf_cc_test(
    name = "ngraph_tf_tests",
    size = "small",
    srcs = [
        "test/conversions.cpp",
        "test/graph_rewrites/assign_clusters.cc",
        "test/graph_rewrites/deadness_test.cc",
        "test/main.cpp",
        "test/opexecuter.cpp",
        "test/opexecuter.h",
        "test/padding.cpp",
        "test/test_array_ops.cpp",
        "test/test_math_ops.cpp",
        "test/test_nn_ops.cpp",
        "test/test_utilities.cpp",
        "test/test_utilities.h",
        "test/tf_exec.cpp",
    ],
    extra_copts = [
        "-fexceptions ",
        "-I external/ngraph_tf/src",
        "-I external/ngraph_tf/logging",
        "-I external/ngraph/src",
    ],
    deps = [
        ":ngraph_tf",
        "@com_google_googletest//:gtest",
        "@org_tensorflow//tensorflow/cc:cc_ops",
        "@org_tensorflow//tensorflow/cc:client_session",
        "@org_tensorflow//tensorflow/core:tensorflow",
    ],
)
