# 현재 디렉토리에 있는 모든 파일을 SRC_FILES 변수에 추가한다.
set(SRC_FILES
  shape.cpp
)

add_library(shape STATIC ${SRC_FILES})

# shape 의 include 경로 지정
target_include_directories(shape PUBLIC ${CMAKE_SOURCE_DIR}/include)

# shape 를 C++ 17 로 컴파일
target_compile_features(shape PRIVATE cxx_std_17)
