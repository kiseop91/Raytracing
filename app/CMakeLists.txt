# 현재 디렉토리에 있는 모든 파일을 SRC_FILES 변수에 추가한다.
file(GLOB_RECURSE SRC_FILES CONFIGURE_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/*.cc
)

add_executable(program ${SRC_FILES})
target_link_libraries(program PUBLIC shape)

# shape 를 C++ 17 로 컴파일
target_compile_features(program PRIVATE cxx_std_17)

ADD_CUSTOM_COMMAND( 
  TARGET program 
  POST_BUILD
  COMMENT "Generating PNG File..." 
  ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}
  COMMAND program > RenderImage.png
  COMMAND open RenderImage.png
)