load("@bazel_skylib//lib:selects.bzl", "selects")

package(default_visibility = ["//visibility:public"])

# Add a config setting release for compilation mode
# Assume that people are using `opt` for release mode
# see the bazel user manual for more information
# https://docs.bazel.build/versions/master/be/general.html#config_setting
config_setting(
  name = "release",
  values = {
    "compilation_mode": "opt"
  }
)
config_setting(
  name = "osxCase",
  values = {
    "apple_platform_type": "macos"
  }
)
config_setting(
  name = "tvosCase",
  values = {
    "apple_platform_type": "tvos"
  }
)
config_setting(
  name = "watchosCase",
  values = {
    "apple_platform_type": "watchos"
  }
)

config_setting(
    name = "ios_arm64",
    values = {"cpu": "ios_arm64"},
)
config_setting(
    name = "ios_arm64e",
    values = {"cpu": "ios_arm64e"},
)
config_setting(
    name = "ios_armv7",
    values = {"cpu": "ios_armv7"},
)
config_setting(
    name = "ios_i386",
    values = {"cpu": "ios_i386"},
)
config_setting(
    name = "ios_x86_64",
    values = {"cpu": "ios_x86_64"},
)
config_setting(
    name = "ios_sim_arm64",
    values = {"cpu": "ios_sim_arm64"},
)

selects.config_setting_group(
    name = "ios_device",
    match_any = [
        ":ios_arm64",
        ":ios_arm64e",
        ":ios_armv7",
    ],
)

selects.config_setting_group(
    name = "ios_simulator",
    match_any = [
        ":ios_i386",
        ":ios_x86_64",
        ":ios_sim_arm64",
    ],
)

# Process bundles created by PodSpecToBUILD
# Move a bundle of the convention in Pods
# PackageName_Bundle_BundleName
# @see process_ipa.py
py_binary(
    name = "ipa_process",
    main = "process_ipa.py",
    srcs = ["process_ipa.py"],
)

py_binary(
    name = "acknowledgement_merger",
    srcs = ["acknowledgement_merger.py"],
)

sh_library(
    name = "vendored_srcs",
    srcs = glob(["**"]),
)

py_binary(
    name = "headermap_builder",
    srcs = ["headermap_builder.py", "headermap_tool.py"],
)

