add_compile_options(-fexceptions)

if(DEFINED crypto3_INCLUDE_DIR)
  include_directories(${crypto3_INCLUDE_DIR})
  add_llvm_component_library(LLVMZK
    FieldArithmetics.cpp
    ADDITIONAL_HEADER_DIRS
    ${LLVM_MAIN_INCLUDE_DIR}/llvm/ZK

    LINK_COMPONENTS
    Support
  )
else()
  add_llvm_component_library(LLVMZK
    FieldArithmetics.cpp
    ADDITIONAL_HEADER_DIRS
    ${LLVM_MAIN_INCLUDE_DIR}/llvm/ZK

  LINK_LIBS
  crypto3_algebra
  crypto3_block
  crypto3_blueprint
  crypto3_codec
  crypto3_math
  crypto3_multiprecision
  crypto3_pkpad
  crypto3_pubkey
  crypto3_random
  crypto3_zk
  marshalling_core
  marshalling_crypto3_algebra
  marshalling_crypto3_multiprecision
  marshalling_crypto3_zk

    LINK_COMPONENTS
    Support
  )
endif()