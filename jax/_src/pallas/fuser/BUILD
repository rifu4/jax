# Copyright 2025 The JAX Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load(
    "//jaxlib:jax.bzl",
    "py_deps",
    "pytype_strict_library",
)

package(
    default_applicable_licenses = [],
    default_visibility = [
        "//jax:internal",
    ],
)

pytype_strict_library(
    name = "fuser",
    srcs = [
        "__init__.py",
    ],
    deps = [
        ":block_spec",
        ":custom_evaluate",
        ":fusible",
        ":fusion",
        ":jaxpr_fusion",
    ],
)

pytype_strict_library(
    name = "block_spec",
    srcs = [
        "block_spec.py",
    ],
    deps = [
        ":fuser_utils",
        "//jax",
        "//jax:ad_util",
        "//jax:api",
        "//jax:api_util",
        "//jax:core",
        "//jax:custom_derivatives",
        "//jax:lax",
        "//jax:partial_eval",
        "//jax:random",
        "//jax:tree_util",
        "//jax:util",
        "//jax/_src/pallas",
    ] + py_deps("numpy"),
)

pytype_strict_library(
    name = "fusible",
    srcs = [
        "fusible.py",
    ],
    deps = [
        ":fusion",
        "//jax",
        "//jax:api_util",
        "//jax:core",
        "//jax:mlir",
        "//jax:partial_eval",
        "//jax:tree_util",
        "//jax:util",
    ],
)

pytype_strict_library(
    name = "fusion",
    srcs = [
        "fusion.py",
    ],
    deps = [
        "//jax",
        "//jax:util",
    ],
)

pytype_strict_library(
    name = "jaxpr_fusion",
    srcs = [
        "jaxpr_fusion.py",
    ],
    deps = [
        ":fusible",
        ":fusible_dtype",
        ":fusion",
        "//jax",
        "//jax:api_util",
        "//jax:core",
        "//jax:partial_eval",
        "//jax:tree_util",
        "//jax:util",
    ],
)

pytype_strict_library(
    name = "fusible_dtype",
    srcs = [
        "fusible_dtype.py",
    ],
    deps = [
        ":block_spec",
        ":fusible",
        "//jax",
        "//jax:api_util",
        "//jax:core",
        "//jax:custom_derivatives",
        "//jax:dtypes",
        "//jax:lax",
        "//jax:partial_eval",
        "//jax:source_info_util",
        "//jax:tree_util",
        "//jax:util",
        "//jax/_src/pallas",
    ],
)

pytype_strict_library(
    name = "custom_evaluate",
    srcs = ["custom_evaluate.py"],
    deps = [
        ":fuser_utils",
        "//jax",
        "//jax:core",
        "//jax:source_info_util",
        "//jax:tree_util",
        "//jax:util",
    ],
)

pytype_strict_library(
    name = "fuser_utils",
    srcs = ["fuser_utils.py"],
    deps = [
        "//jax:api_util",
        "//jax:core",
        "//jax:partial_eval",
        "//jax:tree_util",
    ],
)
