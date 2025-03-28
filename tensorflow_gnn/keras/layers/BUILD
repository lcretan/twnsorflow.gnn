# Copybara rewrites load() statements back and forth; do not reformat.
# buildifier: disable=out-of-order-load, disable=same-origin-load
load("@tensorflow_gnn//tensorflow_gnn:tensorflow_gnn.bzl", "pytype_strict_library")

# buildifier: disable=out-of-order-load, disable=same-origin-load
load("@tensorflow_gnn//tensorflow_gnn:tensorflow_gnn.bzl", "tf_py_test")

licenses(["notice"])

package(
    default_applicable_licenses = ["//tensorflow_gnn:license"],
    default_visibility = [
        "//tensorflow_gnn:__pkg__",
        "//tensorflow_gnn/compat:__subpackages__",
        "//tensorflow_gnn/graph:__subpackages__",
        "//tensorflow_gnn/keras:__subpackages__",
    ],
)

pytype_strict_library(
    name = "layers",
    srcs = ["__init__.py"],
    deps = [
        ":convolution_base",
        ":convolutions",
        ":graph_ops",
        ":graph_update",
        ":item_dropout",
        ":map_features",
        ":next_state",
        ":padding_ops",
        ":parse_example",
        "//tensorflow_gnn/utils:api_utils",
    ],
)

pytype_strict_library(
    name = "convolutions",
    srcs = ["convolutions.py"],
    deps = [
        ":convolution_base",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor_ops",
    ],
)

tf_py_test(
    name = "convolutions_test",
    srcs = ["convolutions_test.py"],
    deps = [
        ":convolutions",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/utils:tf_test_utils",
    ],
)

pytype_strict_library(
    name = "convolution_base",
    srcs = ["convolution_base.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:broadcast_ops",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/graph:pool_ops",
        "//tensorflow_gnn/graph:tag_utils",
    ],
)

tf_py_test(
    name = "convolution_base_test",
    srcs = ["convolution_base_test.py"],
    deps = [
        ":convolution_base",
        ":graph_update",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/graph:normalization_ops",
        "//tensorflow_gnn/utils:tf_test_utils",
    ],
)

pytype_strict_library(
    name = "graph_ops",
    srcs = ["graph_ops.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:broadcast_ops",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/graph:graph_tensor_ops",
        "//tensorflow_gnn/graph:pool_ops",
        "//tensorflow_gnn/graph:readout",
    ],
)

tf_py_test(
    name = "graph_ops_test",
    srcs = ["graph_ops_test.py"],
    deps = [
        ":graph_ops",
        "//third_party/py/mock",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//:expect_ai_edge_litert_installed",
    ],
)

pytype_strict_library(
    name = "graph_update",
    srcs = ["graph_update.py"],
    deps = [
        ":next_state",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:broadcast_ops",
        "//tensorflow_gnn/graph:dict_utils",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
    ],
)

tf_py_test(
    name = "graph_update_test",
    srcs = ["graph_update_test.py"],
    deps = [
        ":convolutions",
        ":graph_ops",
        ":graph_update",
        ":next_state",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/utils:tf_test_utils",
    ],
)

pytype_strict_library(
    name = "item_dropout",
    srcs = ["item_dropout.py"],
    deps = ["//:expect_tensorflow_installed"],
)

tf_py_test(
    name = "item_dropout_test",
    srcs = ["item_dropout_test.py"],
    deps = [
        ":item_dropout",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/utils:tf_test_utils",
    ],
)

pytype_strict_library(
    name = "map_features",
    srcs = ["map_features.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:dict_utils",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
    ],
)

tf_py_test(
    name = "map_features_test",
    srcs = ["map_features_test.py"],
    deps = [
        ":map_features",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/keras:keras_tensors",
        "//tensorflow_gnn/utils:tf_test_utils",
    ],
)

pytype_strict_library(
    name = "next_state",
    srcs = ["next_state.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:graph_constants",
    ],
)

tf_py_test(
    name = "next_state_test",
    srcs = ["next_state_test.py"],
    deps = [
        ":next_state",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/utils:tf_test_utils",
        "//:expect_ai_edge_litert_installed",
    ],
)

pytype_strict_library(
    name = "parse_example",
    srcs = ["parse_example.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/graph:graph_tensor_io",
    ],
)

pytype_strict_library(
    name = "padding_ops",
    srcs = ["padding_ops.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:padding_ops",
        "//tensorflow_gnn/graph:preprocessing_common",
    ],
)

tf_py_test(
    name = "padding_ops_test",
    srcs = ["padding_ops_test.py"],
    deps = [
        ":padding_ops",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/graph:preprocessing_common",
        "//tensorflow_gnn/keras:keras_tensors",
        "//tensorflow_gnn/utils:tf_test_utils",
        "//:expect_ai_edge_litert_installed",
    ],
)

tf_py_test(
    name = "parse_example_test",
    srcs = ["parse_example_test.py"],
    deps = [
        ":parse_example",
        "//:expect_absl_installed_testing",
        "//third_party/py/google/protobuf",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn/graph:adjacency",
        "//tensorflow_gnn/graph:graph_constants",
        "//tensorflow_gnn/graph:graph_tensor",
        "//tensorflow_gnn/utils:tf_test_utils",
    ],
)
