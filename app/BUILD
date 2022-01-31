load("@rules_jvm_external//:defs.bzl", "artifact")
load("@rules_android//android:rules.bzl", "android_library")

package(default_visibility = ["//visibility:private"])
load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kt_android_library")


android_library(
    name = "chocolate_res",
    manifest = "AndroidManifest.xml",
    custom_package = "ru.chocolate.medcard",
    resource_files = glob(["src/main/res/**"]),
    deps = [
        artifact("androidx.constraintlayout:constraintlayout"),
        artifact("com.google.android.material:material"),
    ]
)

kt_android_library(
    name = "chocolate_kt",
    srcs = glob(["src/main/java/**/*.kt"]),
    deps = [
        ":chocolate_res",
        artifact("androidx.appcompat:appcompat"),
        artifact("androidx.core:core")
    ]
)

android_binary(
    name = "new-hope",
    manifest = "AndroidManifest.xml",
    custom_package = "ru.chocolate.medcard",
    manifest_values = {
        "minSdkVersion": "24",
        "targetSdkVersion": "31",
    },
    deps = [
        ":chocolate_kt",
        ":chocolate_res"
    ]
)

