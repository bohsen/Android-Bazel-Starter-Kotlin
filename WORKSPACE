load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

android_sdk_repository(
    name = "androidsdk",
    api_level = 30,
    build_tools_version = "30.0.3"
)

http_archive(
    name = "rules_android",
    urls = ["https://github.com/bazelbuild/rules_android/archive/v0.1.1.zip"],
    sha256 = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806",
    strip_prefix = "rules_android-0.1.1",
)

RULES_JVM_EXTERNAL_TAG = "4.0"
RULES_JVM_EXTERNAL_SHA = "31701ad93dbfe544d597dbe62c9a1fdd76d81d8a9150c2bf1ecf928ecdf97169"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    name = "maven",
    artifacts = [
        "androidx.appcompat:appcompat:1.2.0",
        "androidx.activity:activity-ktx:1.2.0",
        "androidx.fragment:fragment-ktx:1.3.0",
        "androidx.core:core:1.5.0-alpha05",
        "androidx.lifecycle:lifecycle-runtime:2.3.0",
        "androidx.lifecycle:lifecycle-viewmodel:2.3.0",
        "androidx.lifecycle:lifecycle-common:2.3.0",
        "androidx.lifecycle:lifecycle-runtime-ktx:2.3.0",
        "androidx.savedstate:savedstate-ktx:1.1.0",
        "androidx.drawerlayout:drawerlayout:1.1.1",
        "androidx.constraintlayout:constraintlayout:2.0.4",
        "com.google.android.material:material:1.3.0",
        "org.jetbrains.kotlinx:kotlinx-coroutines-core:1.4.2",
        "org.jetbrains.kotlinx:kotlinx-coroutines-android:1.4.2"
    ],
    repositories = [
        "https://maven.google.com",
        "https://jcenter.bintray.com",
    ],
    fetch_sources = True,
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

kotlin_version = "1.4.30"
kotlin_release_sha = "7b0aae9dca5ea899ef05dedc0a6fdd6e359451e56ff0dd3354443b3208b31800"
rules_kotlin_compiler_release = {
    "urls": [
    "https://github.com/JetBrains/kotlin/releases/download/v{v}/kotlin-compiler-{v}.zip".format(v = kotlin_version),
    ],
    "sha256": kotlin_release_sha,
}

rules_kotlin_version = "legacy-1.4.0-rc4"
rules_kotlin_sha = "9cc0e4031bcb7e8508fd9569a81e7042bbf380604a0157f796d06d511cff2769"
http_archive(
    name = "io_bazel_rules_kotlin",
    urls = ["https://github.com/bazelbuild/rules_kotlin/releases/download/%s/rules_kotlin_release.tgz" % rules_kotlin_version],
    sha256 = rules_kotlin_sha,
)

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories", "kt_register_toolchains")
kotlin_repositories(compiler_release = rules_kotlin_compiler_release) # if you want the default. Otherwise see custom kotlinc distribution below
kt_register_toolchains() # to use the default toolchain, otherwise see toolchains below