load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
 name = "build_bazel_rules_android",
 urls = ["https://github.com/bazelbuild/rules_android/archive/v0.1.1.zip"],
 sha256 = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806",
 strip_prefix = "rules_android-0.1.1",
)

# Android SDK
load("@build_bazel_rules_android//android:rules.bzl", "android_sdk_repository")
android_sdk_repository(
    name = "androidsdk",
    path = "/Users/adronina/Library/Android/sdk",
    api_level = 31,
    build_tools_version = "31.0.0"
)

# Android rules
http_archive(
    name = "rules_android",
    urls = ["https://github.com/bazelbuild/rules_android/archive/v0.1.1.zip"],
    sha256 = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806",
    strip_prefix = "rules_android-0.1.1",
)

# Внешние зависимости
RULES_JVM_EXTERNAL_TAG = "4.2"
RULES_JVM_EXTERNAL_SHA = "cd1a77b7b02e8e008439ca76fd34f5b07aecb8c752961f9640dea15e9e5ba1ca"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "androidx.appcompat:appcompat:1.0.2",
        "androidx.fragment:fragment:1.0.0",
        "androidx.core:core:1.0.1",
        "androidx.lifecycle:lifecycle-runtime:2.0.0",
        "androidx.lifecycle:lifecycle-viewmodel:2.0.0",
        "androidx.lifecycle:lifecycle-common:2.0.0",
        "androidx.constraintlayout:constraintlayout:1.1.3",
        "com.google.android.material:material:1.0.0",
        "org.jetbrains.kotlinx:kotlinx-coroutines-core:1.3.2",
        "org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.2",
        "androidx.work:work-runtime:2.7.1",
        "androidx.paging:paging-common:3.1.0",
        "com.squareup.picasso:picasso:2.71828",
        "androidx.room:room-runtime:2.4.1"
    ],
    repositories = [
        "https://maven.google.com",
        "https://jcenter.bintray.com",
    ],
    fetch_sources = True,
)

# Kotlin
kotlin_version = "1.3.61"
kotlin_release_sha = "3901151ad5d94798a268d1771c6c0b7e305a608c2889fc98a674802500597b1c"
rules_kotlin_compiler_release = {
    "urls": [
    "https://github.com/JetBrains/kotlin/releases/download/v{v}/kotlin-compiler-{v}.zip".format(v = kotlin_version),
    ],
    "sha256": kotlin_release_sha,
}

rules_kotlin_version = "legacy-1.3.0-rc1"
rules_kotlin_sha = "9de078258235ea48021830b1669bbbb678d7c3bdffd3435f4c0817c921a88e42"
http_archive(
    name = "io_bazel_rules_kotlin",
    urls = ["https://github.com/bazelbuild/rules_kotlin/archive/%s.zip" % rules_kotlin_version],
    type = "zip",
    strip_prefix = "rules_kotlin-%s" % rules_kotlin_version,
    sha256 = rules_kotlin_sha
)

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories", "kt_register_toolchains")
kotlin_repositories(compiler_release = rules_kotlin_compiler_release)
kt_register_toolchains()