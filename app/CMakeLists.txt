# 현재 디렉토리에 있는 모든 파일을 SRC_FILES 변수에 추가한다.
set(SRC_FILES 
  main.cpp
)

add_executable(program ${SRC_FILES})
target_link_libraries(program PUBLIC shape)

# shape 를 C++ 17 로 컴파일
target_compile_features(program PRIVATE cxx_std_17)


IF (WIN32)
  set(OpenCommand start . )
ELSE()
  set(OpenCommand open RenderImage.png)
ENDIF()

ADD_CUSTOM_COMMAND( 
  TARGET program 
  POST_BUILD
  COMMENT "Generating PNG File..." 
  ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}
  COMMAND program > RenderImage.png
  COMMAND ${OpenCommand}
)