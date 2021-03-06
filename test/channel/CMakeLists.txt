#
# Copyright (c) 2018 Mateusz Loskot <mateusz at loskot dot net>
#
# Distributed under the Boost Software License, Version 1.0.
# (See accompanying file LICENSE_1_0.txt or copy at
# http://www.boost.org/LICENSE_1_0.txt)
#
foreach(_name
  channel_concepts
  channel_test_fixture
  channel_traits
  scoped_channel_value
  algorithm_channel_arithmetic
  algorithm_channel_convert
  algorithm_channel_invert
  algorithm_channel_multiply
  algorithm_channel_relation)
  set(_target test_core_${_name})

  add_executable(${_target} "")
  target_sources(${_target} PRIVATE ${_name}.cpp)
  target_link_libraries(${_target}
    PRIVATE
      gil_compile_options
      gil_include_directories
      gil_dependencies)
  add_test(test.core.${_name} ${_target})

  unset(_name)
  unset(_target)
endforeach()
