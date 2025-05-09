# Copybara rewrites load() statements back and forth; do not reformat.
# buildifier: disable=out-of-order-load, disable=same-origin-load
load("@tensorflow_gnn//tensorflow_gnn:tensorflow_gnn.bzl", "pytype_strict_contrib_test")

# buildifier: disable=out-of-order-load, disable=same-origin-load
load("@tensorflow_gnn//tensorflow_gnn:tensorflow_gnn.bzl", "pytype_strict_library")

# buildifier: disable=out-of-order-load, disable=same-origin-load
load("@tensorflow_gnn//tensorflow_gnn:tensorflow_gnn.bzl", "tf_py_test")

licenses(["notice"])

package(
    default_visibility = [":__subpackages__"],
)

package_group(name = "users")

pytype_strict_library(
    name = "hgt",
    srcs = ["__init__.py"],
    visibility = [
        ":__subpackages__",
        ":users",
    ],
    deps = [
        ":config_dict",
        ":layers",
        "//tensorflow_gnn/utils:api_utils",
    ],
)

# A special BUILD target with a declaration of the model's hyperparameter search space.
# Unlike the model itself, this does not depend on TF/TF-GNN, but does depend on Vizier.
pytype_strict_library(
    name = "hparams_vizier",
    srcs = ["hparams_vizier.py"],
    visibility = [
        ":__subpackages__",
        ":users",
    ],
    deps = [
        "//:expect_vizier_service_pyvizier_installed",
    ],
)

exports_files(
    srcs = ["hparams_vizier.py"],
    visibility = [
        ":__subpackages__",
    ],
)

pytype_strict_contrib_test(
    name = "hparams_vizier_test",
    srcs = ["hparams_vizier_test.py"],
    deps = [
        ":hparams_vizier",
        "//:expect_vizier_service_pyvizier_installed",
        "//third_party/py/absl/testing:absltest",
    ],
)

pytype_strict_library(
    name = "config_dict",
    srcs = ["config_dict.py"],
    deps = [
        ":layers",
        "//third_party/py/ml_collections/config_dict",
        "//:expect_tensorflow_installed",
    ],
)

tf_py_test(
    name = "config_dict_test",
    srcs = ["config_dict_test.py"],
    deps = [
        ":config_dict",
        ":layers",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn",
    ],
)

pytype_strict_library(
    name = "layers",
    srcs = ["layers.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn",
    ],
)

tf_py_test(
    name = "layers_test",
    srcs = ["layers_test.py"],
    deps = [
        ":layers",
        "//:expect_absl_installed_testing",
        "//:expect_tensorflow_installed",
        "//tensorflow_gnn",
        "//tensorflow_gnn/utils:tf_test_utils",
        "//:expect_ai_edge_litert_installed",
    ],
)
