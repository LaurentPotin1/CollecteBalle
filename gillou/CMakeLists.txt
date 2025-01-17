cmake_minimum_required(VERSION 3.5)
project(gillou)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

install(
  DIRECTORY src launch rviz config world scripts
  DESTINATION share/${PROJECT_NAME}
)


install(PROGRAMS
    scripts/detec_robot.py
    DESTINATION lib/${PROJECT_NAME}/
)

install(PROGRAMS
    scripts/detec_ball.py
    DESTINATION lib/${PROJECT_NAME}/
)

install(PROGRAMS
    scripts/ball_order.py
    DESTINATION lib/${PROJECT_NAME}/
)

install(PROGRAMS
    scripts/orientation_robot.py
    DESTINATION lib/${PROJECT_NAME}/
)

install(PROGRAMS
    scripts/control_joystick.py
    DESTINATION lib/${PROJECT_NAME}/
)

install(PROGRAMS
    scripts/joy_sub.py
    DESTINATION lib/${PROJECT_NAME}/
)

install(PROGRAMS
    scripts/pelle.py
    DESTINATION lib/${PROJECT_NAME}/
)


if(BUILD_TESTING)
  find_package(ament_cmake_pep257 REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_pep257()
endif()


ament_package()
