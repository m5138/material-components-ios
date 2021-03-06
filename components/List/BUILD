# Copyright 2018-present The Material Components for iOS Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load(
    "//:material_components_ios.bzl",
    "mdc_examples_objc_library",
    "mdc_examples_swift_library",
    "mdc_extension_objc_library",
    "mdc_objc_library",
    "mdc_public_objc_library",
    "mdc_snapshot_objc_library",
    "mdc_snapshot_test",
    "mdc_unit_test_suite",
)
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")

licenses(["notice"])  # Apache 2.0

mdc_public_objc_library(
    name = "List",
    sdk_frameworks = [
        "CoreGraphics",
        "UIKit",
    ],
    deps = [
        "//components/Ink",
        "//components/ShadowElevations",
        "//components/ShadowLayer",
        "//components/Typography",
        "//components/private/Application",
        "@material_internationalization_ios//:MDFInternationalization",
    ],
)

mdc_extension_objc_library(
    name = "TypographyThemer",
    deps = [
        ":List",
        "//components/Typography",
        "//components/schemes/Typography",
    ],
)

mdc_extension_objc_library(
    name = "ColorThemer",
    deps = [
        ":List",
        "//components/schemes/Color",
    ],
)

mdc_extension_objc_library(
    name = "Theming",
    deps = [
        ":List",
        ":ColorThemer",
        ":TypographyThemer",
        "//components/schemes/Container",
    ],
)

mdc_extension_objc_library(
    name = "ListThemer",
    deps = [
        ":ColorThemer",
        ":List",
        ":TypographyThemer",
    ],
)

mdc_objc_library(
    name = "unit_test_sources",
    testonly = 1,
    srcs = native.glob([
        "tests/unit/*.m",
    ]),
    sdk_frameworks = [
        "UIKit",
        "XCTest",
    ],
    visibility = ["//visibility:private"],
    deps = [
        ":ColorThemer",
        ":List",
        ":ListThemer",
        ":TypographyThemer",
        "//components/Typography",
        "//components/schemes/Typography",
    ],
)

swift_library(
    name = "unit_test_swift_sources",
    srcs = glob([
        "tests/unit/*.swift",
        "tests/unit/Theming/*.swift",
    ]),
    copts = [
        "-swift-version",
        "4.2",
    ],
    visibility = ["//visibility:private"],
    deps = [
        ":List",
        ":ColorThemer",
        ":TypographyThemer",
        ":Theming",
    ],
)

mdc_unit_test_suite(
    name = "unit_tests",
    deps = [
        ":unit_test_sources",
        ":unit_test_swift_sources",
    ],
)

mdc_examples_objc_library(
    name = "ObjcExamples",
    deps = [
        ":List",
        ":ListThemer",
        "//components/private/Icons/icons/ic_info",
    ],
)

mdc_examples_swift_library(
    name = "SwiftExamples",
    deps = [
        ":List",
    ],
)

mdc_snapshot_objc_library(
    name = "snapshot_test_lib",
    deps = [
        ":List",
        "//components/schemes/Typography",
    ],
)

mdc_snapshot_test(
    name = "snapshot_tests",
    deps = [
        ":snapshot_test_lib",
    ],
)
