load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "new_git_repository")



http_archive(
    name = "rules_foreign_cc",
    # TODO: Get the latest sha256 value from a bazel debug message or the latest
    #       release on the releases page: https://github.com/bazelbuild/rules_foreign_cc/releases
    #
    # sha256 = "...",
    strip_prefix = "rules_foreign_cc-8f6fc67384a1fa63c1667f55568726642bd0ccc4",
    url = "https://github.com/bazelbuild/rules_foreign_cc/archive/8f6fc67384a1fa63c1667f55568726642bd0ccc4.tar.gz",
)

load("@rules_foreign_cc//foreign_cc:repositories.bzl", "rules_foreign_cc_dependencies")

rules_foreign_cc_dependencies()


#load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")
#rules_pkg_dependencies()

_ALL_CONTENT = """\
filegroup(
    name = "all_srcs",
    srcs = glob(["**"]),
    visibility = ["//visibility:public"],
)
"""

# pcre source code repository
http_archive(
    name = "pcre",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "pcre-8.43",
    urls = [
        "https://mirror.bazel.build/ftp.pcre.org/pub/pcre/pcre-8.43.tar.gz",
        "https://ftp.pcre.org/pub/pcre/pcre-8.43.tar.gz",
    ],
    sha256 = "0b8e7465dc5e98c757cc3650a20a7843ee4c3edf50aaf60bb33fd879690d2c73",
)
#git_repository(
http_archive(
    name = "libgo",
    urls  =[ "https://github.com/yyzybb537/libgo/archive/refs/tags/v3.1-stable.tar.gz" ],
    build_file_content = _ALL_CONTENT,
    strip_prefix = "libgo-3.1-stable",
)
new_git_repository(
    name = "evpp",
    remote = "https://github.com/Qihoo360/evpp.git",
    tag = "v0.7.0",
    build_file_content = _ALL_CONTENT,
    #strip_prefix = "libgo-2.6",
)

http_archive(
    name = "asio",
    urls = [
    "https://liquidtelecom.dl.sourceforge.net/project/asio/asio/1.18.1%20%28Stable%29/asio-1.18.1.tar.gz",
    ],
    strip_prefix = "asio-1.18.1",
    build_file_content = _ALL_CONTENT,
)

new_git_repository(
    name = "restbed",
    remote = "https://github.com/Corvusoft/restbed.git",
    tag = "4.8",
    build_file_content = _ALL_CONTENT,
    #strip_prefix = "libgo-2.6",
)
http_archive(
    name = "cpp-httplib",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "cpp-httplib-0.9.4",
    urls = [
        "https://github.com/yhirose/cpp-httplib/archive/refs/tags/v0.9.4.tar.gz",
    ],
)
http_archive(
    name = "openssl",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "openssl-OpenSSL_1_1_1k",
    urls = [
        "https://github.com/openssl/openssl/archive/refs/tags/OpenSSL_1_1_1k.tar.gz",
    ],
    sha256 = "b92f9d3d12043c02860e5e602e50a73ed21a69947bcc74d391f41148e9f6aa95",
)

http_archive(
    name = "spdlog",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "spdlog-1.9.2",
    urls = [
        "https://github.com/gabime/spdlog/archive/refs/tags/v1.9.2.tar.gz",
    ],
    sha256 = "6fff9215f5cb81760be4cc16d033526d1080427d236e86d70bb02994f85e3d38",
)
http_archive(
    name = "dragon",
    build_file_content = _ALL_CONTENT,
    strip_prefix = "dragon-1.7.2",
    urls = [
        "https://github.com/drogonframework/drogon/archive/refs/tags/v1.7.2.tar.gz",
    ],
)

git_repository(
    name = "com_github_gflags_gflags",
    remote = "https://github.com/gflags/gflags.git",
    tag = "v2.2.2"
)

http_archive(
  name = "com_google_googletest",
  urls = ["https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip"],
  strip_prefix = "googletest-609281088cfefc76f9d0ce82e1ff6c30cc3591e5",
)


http_archive(
  name = "fmt",
  build_file_content = _ALL_CONTENT,
  urls = ["https://github.com/fmtlib/fmt/archive/refs/tags/8.0.1.tar.gz"],
  strip_prefix = "fmt-8.0.1",
)

http_archive(
  name = "nlohman_json",
  build_file_content = _ALL_CONTENT,
  urls = ["https://github.com/nlohmann/json/archive/refs/tags/v3.10.2.tar.gz"],
  strip_prefix = "json-3.10.2",
)


http_archive(
  name = "restclient-cpp",
  build_file_content = _ALL_CONTENT,
  urls = ["https://github.com/mrtazz/restclient-cpp/archive/refs/tags/0.5.2.tar.gz"],
  strip_prefix = "restclient-cpp-0.5.2",
)

#workspace(name = "tf_serving")

# ===== TensorFlow dependency =====
#
# TensorFlow is imported here instead of in tf_serving_workspace() because
# existing automation scripts that bump the TF commit hash expect it here.
#
# To update TensorFlow to a new revision.
# 1. Update the 'git_commit' args below to include the new git hash.
# 2. Get the sha256 hash of the archive with a command such as...
#    curl -L https://github.com/tensorflow/tensorflow/archive/<git hash>.tar.gz | sha256sum
#    and update the 'sha256' arg with the result.
# 3. Request the new archive to be mirrored on mirror.bazel.build for more
#    reliable downloads.
#load("//tensorflow_serving:repo.bzl", "tensorflow_http_archive")
#tensorflow_http_archive(
#    name = "org_tensorflow",
#    sha256 = "baaec2e1a6fbbc906c6f73e91d82d95a1d302764b60797d1e1ec0b84e7230412",
#    git_commit = "b4baf4471d13d16df1cc776447ec86721a0e2122",
#)
#
## Import all of TensorFlow Serving's external dependencies.
## Downstream projects (projects importing TensorFlow Serving) need to
## duplicate all code below in their WORKSPACE file in order to also initialize
## those external dependencies.
#load("//tensorflow_serving:workspace.bzl", "tf_serving_workspace")
#tf_serving_workspace()

# Check bazel version requirement, which is stricter than TensorFlow's.
#load(
#    "@org_tensorflow//tensorflow:version_check.bzl",
#    "check_bazel_version_at_least"
#)
#check_bazel_version_at_least("3.7.2")

# Initialize TensorFlow's external dependencies.
#load("@org_tensorflow//tensorflow:workspace3.bzl", "workspace")
#workspace()
#load("@org_tensorflow//tensorflow:workspace2.bzl", "workspace")
#workspace()
#load("@org_tensorflow//tensorflow:workspace1.bzl", "workspace")
#workspace()
#load("@org_tensorflow//tensorflow:workspace0.bzl", "workspace")
#workspace()

# Initialize bazel package rules' external dependencies.

http_archive(
    name = "com_github_gflags_gflags",
    sha256 = "34af2f15cf7367513b352bdcd2493ab14ce43692d2dcd9dfc499492966c64dcf",
    strip_prefix = "gflags-2.2.2",
    urls = ["https://github.com/gflags/gflags/archive/v2.2.2.tar.gz"],
)

http_archive(
    name = "com_github_google_glog",
    sha256 = "21bc744fb7f2fa701ee8db339ded7dce4f975d0d55837a97be7d46e8382dea5a",
    strip_prefix = "glog-0.5.0",
    urls = ["https://github.com/google/glog/archive/v0.5.0.zip"],
)

http_archive(
    build_file_content = _ALL_CONTENT,
    name = "mycurl",
    strip_prefix = "curl-7.78.0",
    urls = ["https://github.com/curl/curl/releases/download/curl-7_78_0/curl-7.78.0.tar.gz"],
)


new_git_repository(
    name = "mtrace",
    remote = "https://github.com/hrydgard/minitrace.git",
    branch = "master",
    build_file_content = _ALL_CONTENT,
)

new_git_repository(
    name = "libgonet",
    remote = "https://github.com/yyzybb537/libgonet.git",
    branch = "master",
    build_file_content = _ALL_CONTENT,
    recursive_init_submodules = True,
)


new_git_repository(
    name = "libhv",
    remote = "https://github.com/ithewei/libhv.git",
    branch = "master",
    build_file_content = _ALL_CONTENT,
)
git_repository(
    name = "com_github_nelhage_rules_boost",
    commit = "1e3a69bf2d5cd10c34b74f066054cd335d033d71",
    remote = "https://github.com/nelhage/rules_boost",
    shallow_since = "1591047380 -0700",
)


http_archive(
  name = "com_google_googletest",
  urls = ["https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip"],
  strip_prefix = "googletest-609281088cfefc76f9d0ce82e1ff6c30cc3591e5",
)

load("@com_github_nelhage_rules_boost//:boost/boost.bzl", "boost_deps")
boost_deps()
