INCLUDES = -I$(top_srcdir)/src/include

pkgcfgdir= $(pkgdatadir)/config.d/

libexecdir= $(pkglibdir)/libexec/

pkgcfg_DATA = \
  ats.conf

if MINGW
 WINFLAGS = -Wl,--no-undefined -Wl,--export-all-symbols 
endif

if USE_COVERAGE
  AM_CFLAGS = -fprofile-arcs -ftest-coverage
endif

if HAVE_LIBGLPK
  GN_LIBGLPK = -lglpk
  GN_MLP_SRC = gnunet-service-ats_addresses_mlp.c gnunet-service-ats_addresses_mlp.h
  GN_MLP_TEST = test_ats_mlp 
  GN_MLP_TEST_AVG = test_ats_mlp_averaging
  GN_MLP_PERF = perf_ats_mlp
endif

lib_LTLIBRARIES = libgnunetats.la

libgnunetats_la_SOURCES = \
  ats_api_scheduling.c \
  ats_api_performance.c 

libgnunetats_la_LIBADD = \
 $(top_builddir)/src/util/libgnunetutil.la \
 $(LTLIBINTL)

libgnunetats_la_LDFLAGS = \
 $(GN_LIB_LDFLAGS) \
  -version-info 4:0:0


libexec_PROGRAMS = \
 gnunet-service-ats

gnunet_service_ats_SOURCES = \
 gnunet-service-ats.c gnunet-service-ats.h\
 gnunet-service-ats_addresses.c gnunet-service-ats_addresses.h \
 gnunet-service-ats_addresses_simplistic.c gnunet-service-ats_addresses_simplistic.h \
 $(GN_MLP_SRC) \
 gnunet-service-ats_performance.c gnunet-service-ats_performance.h \
 gnunet-service-ats_scheduling.c gnunet-service-ats_scheduling.h \
 gnunet-service-ats_reservations.c gnunet-service-ats_reservations.h
gnunet_service_ats_LDADD = \
  $(top_builddir)/src/statistics/libgnunetstatistics.la \
  $(top_builddir)/src/util/libgnunetutil.la \
  libgnunetats.la \
  $(GN_LIBGLPK) \
  $(GN_LIBINTL)
gnunet_service_ats_DEPENDENCIES = \
  libgnunetats.la

check_PROGRAMS = \
 test_ats_api_scheduling_init \
 test_ats_api_scheduling_add_address \
 test_ats_api_scheduling_add_session \
 test_ats_api_scheduling_min_bw \
 test_ats_api_scheduling_check_min_bw_alt \
 test_ats_api_scheduling_update_address \
 test_ats_api_scheduling_destroy_address \
 test_ats_api_scheduling_destroy_session \
 test_ats_api_scheduling_destroy_inbound_connection \
 test_ats_api_scheduling_block_and_reset \
 test_ats_simplistic \
 test_ats_simplistic_switch_networks \
 test_ats_simplistic_change_preference \
 test_ats_simplistic_pref_aging \
 test_ats_api_performance
# $(GN_MLP_TEST) \
# $(GN_MLP_TEST_AVG) \
# $(GN_MLP_PERF)
# test_ats_api_scheduling_get_type
# test_ats_api_bandwidth_consumption

if ENABLE_TEST_RUN
TESTS = $(check_PROGRAMS)
endif

test_ats_api_scheduling_init_SOURCES = \
 test_ats_api_scheduling_init.c \
 test_ats_api_common.c test_ats_api_common.h
test_ats_api_scheduling_init_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

test_ats_api_scheduling_add_address_SOURCES = \
 test_ats_api_scheduling_add_address.c \
 test_ats_api_common.c test_ats_api_common.h
test_ats_api_scheduling_add_address_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

test_ats_api_scheduling_add_session_SOURCES = \
 test_ats_api_scheduling_add_session.c test_ats_api_common.c
test_ats_api_scheduling_add_session_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

test_ats_api_scheduling_min_bw_SOURCES = \
 test_ats_api_scheduling_min_bw.c test_ats_api_common.c
test_ats_api_scheduling_min_bw_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

test_ats_api_scheduling_check_min_bw_alt_SOURCES = \
 test_ats_api_scheduling_check_min_bw_alt.c test_ats_api_common.c
test_ats_api_scheduling_check_min_bw_alt_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  


test_ats_api_scheduling_update_address_SOURCES = \
 test_ats_api_scheduling_update_address.c test_ats_api_common.c
test_ats_api_scheduling_update_address_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

test_ats_api_scheduling_destroy_address_SOURCES = \
 test_ats_api_scheduling_destroy_address.c test_ats_api_common.c
test_ats_api_scheduling_destroy_address_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

test_ats_api_scheduling_destroy_session_SOURCES = \
 test_ats_api_scheduling_destroy_session.c test_ats_api_common.c
test_ats_api_scheduling_destroy_session_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la
  
test_ats_api_scheduling_destroy_inbound_connection_SOURCES = \
 test_ats_api_scheduling_destroy_inbound_connection.c test_ats_api_common.c
test_ats_api_scheduling_destroy_inbound_connection_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la
  
test_ats_api_scheduling_block_and_reset_SOURCES = \
 test_ats_api_scheduling_block_and_reset.c test_ats_api_common.c
test_ats_api_scheduling_block_and_reset_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la
  
test_ats_api_performance_SOURCES = \
 test_ats_api_performance.c
test_ats_api_performance_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/hello/libgnunethello.la \
  $(top_builddir)/src/ats/libgnunetats.la    

test_ats_simplistic_SOURCES = \
 test_ats_simplistic.c test_ats_api_common.c
test_ats_simplistic_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/hello/libgnunethello.la \
  $(top_builddir)/src/ats/libgnunetats.la    

test_ats_simplistic_switch_networks_SOURCES = \
 test_ats_simplistic_switch_networks.c test_ats_api_common.c
test_ats_simplistic_switch_networks_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la

test_ats_simplistic_change_preference_SOURCES = \
 test_ats_simplistic_change_preference.c test_ats_api_common.c
test_ats_simplistic_change_preference_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la

test_ats_simplistic_pref_aging_SOURCES = \
 test_ats_simplistic_pref_aging.c test_ats_api_common.c
test_ats_simplistic_pref_aging_LDADD = \
  $(top_builddir)/src/util/libgnunetutil.la \
  $(top_builddir)/src/testing/libgnunettesting.la \
  $(top_builddir)/src/ats/libgnunetats.la  

if HAVE_LIBGLPK
#test_ats_mlp_SOURCES = \
# $(GN_MLP_SRC) \
# test_ats_mlp.c
#test_ats_mlp_LDADD = \
#  $(GN_LIBGLPK) \
#  $(top_builddir)/src/util/libgnunetutil.la \
#  $(top_builddir)/src/statistics/libgnunetstatistics.la

#test_ats_mlp_averaging_SOURCES = \
# $(GN_MLP_SRC) \
# test_ats_mlp_averaging.c
#test_ats_mlp_averaging_LDADD = \
#  $(GN_LIBGLPK) \
#  $(top_builddir)/src/util/libgnunetutil.la \
#  $(top_builddir)/src/statistics/libgnunetstatistics.la

#perf_ats_mlp_SOURCES = \
# $(GN_MLP_SRC) \
# perf_ats_mlp.c
#perf_ats_mlp_LDADD = \
#  $(GN_LIBGLPK) \
#  $(top_builddir)/src/util/libgnunetutil.la \
#  $(top_builddir)/src/statistics/libgnunetstatistics.la
endif

#test_ats_api_bandwidth_consumption_SOURCES = \
# test_ats_api_bandwidth_consumption.c
#test_ats_api_bandwidth_consumption_LDADD = \
#  $(top_builddir)/src/util/libgnunetutil.la \
#  $(top_builddir)/src/testing/libgnunettesting.la \
#  $(top_builddir)/src/ats/libgnunetats.la  


EXTRA_DIST = \
  ats.h \
  test_ats_api.conf

