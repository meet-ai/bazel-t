load("@rules_foreign_cc//foreign_cc:defs.bzl", "cmake")
load("@rules_foreign_cc//foreign_cc:defs.bzl", "configure_make")
load("@rules_cc//cc:defs.bzl", "cc_test") #for gtest


cmake(
    name = "pcre",
    cache_entries = {
        "CMAKE_C_FLAGS": "-fPIC",
    },
    lib_source = "@pcre//:all_srcs",
    out_static_libs = ["libpcre.a"],
)

cmake(
    name = "libgo",
    lib_name = "libgo",
    lib_source = "@libgo//:all_srcs",
    out_static_libs = ["liblibgo.a"],
    cache_entries = {
        "DISABLE_HOOK": "ON",
    },
    visibility = ["//visibility:public"],
)
cmake(
    name = "cpp-httplib",
    cache_entries = {
        "CMAKE_C_FLAGS": "-fPIC",
        "CMAKE_EXE_LINKER_FLAGS": "-static",
        "ENABLE_STATIC_LIB": "ON",
    },
    lib_name = "cpp-httplib",
    install = True,
    out_headers_only = True,
    lib_source = "@cpp-httplib//:all_srcs",
    visibility = ["//visibility:public"],
)
cmake(
    name = "spdlog",
#    cache_entries = {
#        "CMAKE_EXE_LINKER_FLAGS": "-static",
#    },
    lib_name = "spdlog",
    install = True,
    lib_source = "@spdlog//:all_srcs",
    out_static_libs = ["libspdlog.a"],
    visibility = ["//visibility:public"],
)
configure_make(
    name = "openssl",
    configure_command = "config",
    configure_options = ["no-shared"],
    lib_name = "openssl",
    lib_source = "@openssl//:all_srcs",
    out_static_libs = ["libssl.a","libcrypto.a"],
    visibility = ["//3rdparty:__pkg__"],
)

cmake(
    name = "libhv",
    lib_name = "libhv",
    lib_source = "@libhv//:all_srcs",
    visibility = ["//src/http:__pkg__"],
    out_static_libs = ["libhv_static.a"],
    deps = ["@boringssl//:crypto", "@boringssl//:ssl"],
    cache_entries = {
        "BUILD_EXAMPLES": "OFF",
        "BUILD_SHARED": "OFF",
        "BUILD_STATIC": "ON",
        "WITH_OPENSSL": "ON",
    },
)

cmake(
    name = "fmt",
    lib_name = "fmt",
    install = True,
    lib_source = "@fmt//:all_srcs",
    cache_entries = {
        "FMT_TEST": "OFF",
    },
    out_static_libs = ["libfmt.a"],
    visibility = ["//visibility:public"],
)


cmake(
    name = "evpp",
    lib_name = "evpp",
    install = True,
    cache_entries = {
        "BUILD_SSL": "OFF",
        "BUILD_TESTS": "OFF",
    },
    #deps = ["openssl"],
    out_static_libs = ["libevpp.a"],
    lib_source = "@evpp//:all_srcs",
    visibility = ["//visibility:public"],
    deps = ["@com_github_google_glog//:glog"],

)
cmake(
    name = "nlohman_json",
    lib_name = "nlohman_json",
    install = True,
    cache_entries = {
        "JSON_BuildTests": "OFF",
    },
    lib_source = "@nlohman_json//:all_srcs",
    out_headers_only = True,
    visibility = ["//visibility:public"],
)
cmake(
    name = "mycurl",
    copts = ["-fPIC"],
    lib_name = "curl",
    install = True,
    cache_entries = {
        "BUILD_SHARED_LIBS": "OFF",
        "BUILD_CURL_EXE":"OFF",
        "CMAKE_USE_OPENSSL":"OFF",
        "CMAKE_CXX_FLAGS":"-fPIC",
        "CMAKE_C_FLAGS":"-fPIC",
        "openssl_default":"OFF",
    },
    out_static_libs = ["libcurl.a"],
    lib_source = "@mycurl//:all_srcs",
    visibility = ["//visibility:public"],
)

cmake(
    name = "restclient-cpp",
    lib_name = "restclient-cpp",
    install = True,
    cache_entries = {
        "CMAKE_CXX_FLAGS":"-fPIC",
        "CMAKE_C_FLAGS":"-fPIC",
        "COMPILE_TYPE":"STATIC",
        "BUILD_SHARED_LIBS":"NO",
    },
    copts = ["-fPIC","-DPIC"],
    out_static_libs = ["librestclient-cpp.a"],
    lib_source = "@restclient-cpp//:all_srcs",
    visibility = ["//visibility:public"],
    deps = ["mycurl"],
)


#configure_make(
#    name = "restclient-cpp",
#    lib_name = "restclient-cpp",
#    configure_in_place=True,
#    autogen = True,
#    defines = ["BUILD_SHARED_LIBS=OFF"],
#    lib_source = "@restclient-cpp//:all_srcs",
#    out_static_libs = ["librestclient-cpp.a"],
#    copts = ["-fPIC"],
#    visibility = ["//visibility:public"],
#    deps = ["curl"],
#)

cc_binary(
    name = "main",
    srcs = ["main.cpp"],
)

cc_library(
    name = "minitrace",
    srcs = [
        "minitrace/minitrace.c","minitrace/minitrace.h",
    ],
    hdrs = ["minitrace/minitrace.h"],
    visibility = [
    "//visibility:public",
    ],
    copts = ["-Wall", "-DMTR_ENABLED=1"],
)

cmake(
    name = "mtrace",
    lib_name = "mtrace",
    install = True,
    cache_entries = {
        "MTR_ENABLED": "OFF",
    },
    lib_source = "@mtrace//:all_srcs",
    out_static_libs = ["libminitrace.a"],
    visibility = ["//visibility:public"],
)

cmake(
    name = "uvcpp",
    lib_name = "uvcpp",
    install = True,
    lib_source = "@uvcpp//:all_srcs",
    out_static_libs = ["libuvcpp.a","libuv.a"],
    visibility = ["//visibility:public"],
)
cmake(
    name = "rapidhttp",
    lib_name = "rapidhttp",
    install = True,
    lib_source = "@rapidhttp//:all_srcs",
    #out_static_libs = ["libuvcpp.a","libuv.a"],
    out_headers_only = True,
    visibility = ["//visibility:public"],
    deps = ["@com_google_googletest//:gtest_main"],
)

#cmake(
#    name = "libgonet",
#    lib_name = "libgonet",
#    install = True,
#    lib_source = "@libgonet//:all_srcs",
#    cache_entries = {
#        "ENABLE_BOOST_CONTEXT": "OFF",
#        "ENABLE_SYSTEM_LIBGO":"ON",
#    },
#    out_static_libs = ["libuvcpp.a"],
#    visibility = ["//visibility:public"],
#    deps = ["libgo","@boost//:asio","@boost//:coroutine"],
#)

cc_library(
    name = "libgonet",
    srcs = glob(["libgonet/*.cpp"]),
    hdrs = glob(["libgonet/*.h"]),
    visibility = [
    "//visibility:public",
    ],
 #   out_static_libs = ["libgonet.a"],
    deps = ["//3rdparty:libgo","@boost//:asio","@boost//:coroutine"],
)
