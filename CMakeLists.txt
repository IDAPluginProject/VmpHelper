# This file is automatically generated from cmake.toml - DO NOT EDIT
# See https://github.com/build-cpp/cmkr for more information

cmake_minimum_required(VERSION 3.15)

if(CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR)
	message(FATAL_ERROR "In-tree builds are not supported. Run CMake from a separate directory: cmake -B build")
endif()

set(CMKR_ROOT_PROJECT OFF)
if(CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR)
	set(CMKR_ROOT_PROJECT ON)

	# Bootstrap cmkr and automatically regenerate CMakeLists.txt
	include(cmkr.cmake OPTIONAL RESULT_VARIABLE CMKR_INCLUDE_RESULT)
	if(CMKR_INCLUDE_RESULT)
		cmkr()
	endif()

	# Enable folder support
	set_property(GLOBAL PROPERTY USE_FOLDERS ON)

	# Create a configure-time dependency on cmake.toml to improve IDE support
	configure_file(cmake.toml cmake.toml COPYONLY)
endif()

# Options
option(CAPSTONE_BPF_SUPPORT "" OFF)
option(CAPSTONE_EVM_SUPPORT "" OFF)
option(CAPSTONE_MIPS_SUPPORT "" OFF)
option(CAPSTONE_BUILD_STATIC_RUNTIME "" ON)
option(CAPSTONE_M680X_SUPPORT "" OFF)
option(CAPSTONE_M68K_SUPPORT "" OFF)
option(CAPSTONE_MOS65XX_SUPPORT "" OFF)
option(CAPSTONE_PPC_SUPPORT "" OFF)
option(CAPSTONE_RISCV_SUPPORT "" OFF)
option(CAPSTONE_SH_SUPPORT "" OFF)
option(CAPSTONE_SPARC_SUPPORT "" OFF)
option(CAPSTONE_SYSZ_SUPPORT "" OFF)
option(CAPSTONE_TMS320C64X_SUPPORT "" OFF)
option(CAPSTONE_TRICORE_SUPPORT "" OFF)
option(CAPSTONE_WASM_SUPPORT "" OFF)
option(CAPSTONE_XCORE_SUPPORT "" OFF)

project(Revampire)

include(FetchContent)

# Fix warnings about DOWNLOAD_EXTRACT_TIMESTAMP
if(POLICY CMP0135)
	cmake_policy(SET CMP0135 NEW)
endif()
message(STATUS "Fetching capstone (5.0.1)...")
FetchContent_Declare(capstone SYSTEM
	GIT_REPOSITORY
		"https://github.com/capstone-engine/capstone"
	GIT_TAG
		5.0.1
)
FetchContent_MakeAvailable(capstone)

message(STATUS "Fetching unicorn (2.0.1)...")
FetchContent_Declare(unicorn SYSTEM
	GIT_REPOSITORY
		"https://github.com/unicorn-engine/unicorn"
	GIT_TAG
		2.0.1
)
FetchContent_MakeAvailable(unicorn)

# Target: Revampire
set(Revampire_SOURCES
	"Revampire/IDAPlugin.cpp"
	"Revampire/main.cpp"
	"Revampire/Ghidra/action.cc"
	"Revampire/Ghidra/address.cc"
	"Revampire/Ghidra/architecture.cc"
	"Revampire/Ghidra/block.cc"
	"Revampire/Ghidra/blockaction.cc"
	"Revampire/Ghidra/callgraph.cc"
	"Revampire/Ghidra/capability.cc"
	"Revampire/Ghidra/cast.cc"
	"Revampire/Ghidra/comment.cc"
	"Revampire/Ghidra/comment_ghidra.cc"
	"Revampire/Ghidra/condexe.cc"
	"Revampire/Ghidra/context.cc"
	"Revampire/Ghidra/coreaction.cc"
	"Revampire/Ghidra/cover.cc"
	"Revampire/Ghidra/cpool.cc"
	"Revampire/Ghidra/cpool_ghidra.cc"
	"Revampire/Ghidra/crc32.cc"
	"Revampire/Ghidra/database.cc"
	"Revampire/Ghidra/database_ghidra.cc"
	"Revampire/Ghidra/double.cc"
	"Revampire/Ghidra/dynamic.cc"
	"Revampire/Ghidra/emulate.cc"
	"Revampire/Ghidra/emulateutil.cc"
	"Revampire/Ghidra/filemanage.cc"
	"Revampire/Ghidra/float.cc"
	"Revampire/Ghidra/flow.cc"
	"Revampire/Ghidra/fspec.cc"
	"Revampire/Ghidra/funcdata.cc"
	"Revampire/Ghidra/funcdata_block.cc"
	"Revampire/Ghidra/funcdata_op.cc"
	"Revampire/Ghidra/funcdata_varnode.cc"
	"Revampire/Ghidra/ghidra_arch.cc"
	"Revampire/Ghidra/ghidra_context.cc"
	"Revampire/Ghidra/ghidra_translate.cc"
	"Revampire/Ghidra/globalcontext.cc"
	"Revampire/Ghidra/grammar.cc"
	"Revampire/Ghidra/graph.cc"
	"Revampire/Ghidra/heritage.cc"
	"Revampire/Ghidra/inject_ghidra.cc"
	"Revampire/Ghidra/inject_sleigh.cc"
	"Revampire/Ghidra/interface.cc"
	"Revampire/Ghidra/jumptable.cc"
	"Revampire/Ghidra/libdecomp.cc"
	"Revampire/Ghidra/loadimage.cc"
	"Revampire/Ghidra/loadimage_ghidra.cc"
	"Revampire/Ghidra/loadimage_xml.cc"
	"Revampire/Ghidra/marshal.cc"
	"Revampire/Ghidra/memstate.cc"
	"Revampire/Ghidra/merge.cc"
	"Revampire/Ghidra/modelrules.cc"
	"Revampire/Ghidra/op.cc"
	"Revampire/Ghidra/opbehavior.cc"
	"Revampire/Ghidra/opcodes.cc"
	"Revampire/Ghidra/options.cc"
	"Revampire/Ghidra/override.cc"
	"Revampire/Ghidra/paramid.cc"
	"Revampire/Ghidra/pcodecompile.cc"
	"Revampire/Ghidra/pcodeinject.cc"
	"Revampire/Ghidra/pcodeparse.cc"
	"Revampire/Ghidra/pcoderaw.cc"
	"Revampire/Ghidra/prefersplit.cc"
	"Revampire/Ghidra/prettyprint.cc"
	"Revampire/Ghidra/printc.cc"
	"Revampire/Ghidra/printjava.cc"
	"Revampire/Ghidra/printlanguage.cc"
	"Revampire/Ghidra/rangeutil.cc"
	"Revampire/Ghidra/raw_arch.cc"
	"Revampire/Ghidra/ruleaction.cc"
	"Revampire/Ghidra/rulecompile.cc"
	"Revampire/Ghidra/semantics.cc"
	"Revampire/Ghidra/signature.cc"
	"Revampire/Ghidra/sleigh.cc"
	"Revampire/Ghidra/sleigh_arch.cc"
	"Revampire/Ghidra/sleighbase.cc"
	"Revampire/Ghidra/slghpatexpress.cc"
	"Revampire/Ghidra/slghpattern.cc"
	"Revampire/Ghidra/slghsymbol.cc"
	"Revampire/Ghidra/space.cc"
	"Revampire/Ghidra/string_ghidra.cc"
	"Revampire/Ghidra/stringmanage.cc"
	"Revampire/Ghidra/subflow.cc"
	"Revampire/Ghidra/transform.cc"
	"Revampire/Ghidra/translate.cc"
	"Revampire/Ghidra/type.cc"
	"Revampire/Ghidra/typegrp_ghidra.cc"
	"Revampire/Ghidra/typeop.cc"
	"Revampire/Ghidra/unify.cc"
	"Revampire/Ghidra/unionresolve.cc"
	"Revampire/Ghidra/userop.cc"
	"Revampire/Ghidra/variable.cc"
	"Revampire/Ghidra/varmap.cc"
	"Revampire/Ghidra/varnode.cc"
	"Revampire/Ghidra/xml.cc"
	"Revampire/Ghidra/xml_arch.cc"
	"Revampire/GhidraExtension/FuncBuildHelper.cpp"
	"Revampire/GhidraExtension/IDALoadImage.cpp"
	"Revampire/GhidraExtension/PrintManager.cpp"
	"Revampire/GhidraExtension/VmpAction.cpp"
	"Revampire/GhidraExtension/VmpArch.cpp"
	"Revampire/GhidraExtension/VmpControlFlow.cpp"
	"Revampire/GhidraExtension/VmpFunction.cpp"
	"Revampire/GhidraExtension/VmpInstruction.cpp"
	"Revampire/GhidraExtension/VmpInstructionBuilder.cpp"
	"Revampire/GhidraExtension/VmpNode.cpp"
	"Revampire/GhidraExtension/VmpRule.cpp"
	"Revampire/Common/Public.cpp"
	"Revampire/Common/StringUtils.cpp"
	"Revampire/Common/VmpCommon.cpp"
	"Revampire/Helper/GhidraHelper.cpp"
	"Revampire/Helper/IDAWrapper.cpp"
	"Revampire/Helper/UnicornHelper.cpp"
	"Revampire/Manager/DisasmManager.cpp"
	"Revampire/Manager/SectionManager.cpp"
	"Revampire/Manager/VmpVersionManager.cpp"
	"Revampire/Manager/exceptions.cpp"
	"Revampire/VmpCore/VmpBlockBuilder.cpp"
	"Revampire/VmpCore/VmpReEngine.cpp"
	"Revampire/VmpCore/VmpTraceFlowGraph.cpp"
	"Revampire/VmpCore/VmpUnicorn.cpp"
	"Revampire/IDAPlugin.h"
	"Revampire/Ghidra/types.h"
	"Revampire/Ghidra/action.hh"
	"Revampire/Ghidra/address.hh"
	"Revampire/Ghidra/architecture.hh"
	"Revampire/Ghidra/block.hh"
	"Revampire/Ghidra/blockaction.hh"
	"Revampire/Ghidra/callgraph.hh"
	"Revampire/Ghidra/capability.hh"
	"Revampire/Ghidra/cast.hh"
	"Revampire/Ghidra/comment.hh"
	"Revampire/Ghidra/comment_ghidra.hh"
	"Revampire/Ghidra/condexe.hh"
	"Revampire/Ghidra/context.hh"
	"Revampire/Ghidra/coreaction.hh"
	"Revampire/Ghidra/cover.hh"
	"Revampire/Ghidra/cpool.hh"
	"Revampire/Ghidra/cpool_ghidra.hh"
	"Revampire/Ghidra/crc32.hh"
	"Revampire/Ghidra/database.hh"
	"Revampire/Ghidra/database_ghidra.hh"
	"Revampire/Ghidra/doccore.hh"
	"Revampire/Ghidra/docmain.hh"
	"Revampire/Ghidra/double.hh"
	"Revampire/Ghidra/dynamic.hh"
	"Revampire/Ghidra/emulate.hh"
	"Revampire/Ghidra/emulateutil.hh"
	"Revampire/Ghidra/error.hh"
	"Revampire/Ghidra/filemanage.hh"
	"Revampire/Ghidra/float.hh"
	"Revampire/Ghidra/flow.hh"
	"Revampire/Ghidra/fspec.hh"
	"Revampire/Ghidra/funcdata.hh"
	"Revampire/Ghidra/ghidra_arch.hh"
	"Revampire/Ghidra/ghidra_context.hh"
	"Revampire/Ghidra/ghidra_translate.hh"
	"Revampire/Ghidra/globalcontext.hh"
	"Revampire/Ghidra/grammar.hh"
	"Revampire/Ghidra/graph.hh"
	"Revampire/Ghidra/heritage.hh"
	"Revampire/Ghidra/inject_ghidra.hh"
	"Revampire/Ghidra/inject_sleigh.hh"
	"Revampire/Ghidra/interface.hh"
	"Revampire/Ghidra/jumptable.hh"
	"Revampire/Ghidra/libdecomp.hh"
	"Revampire/Ghidra/loadimage.hh"
	"Revampire/Ghidra/loadimage_ghidra.hh"
	"Revampire/Ghidra/loadimage_xml.hh"
	"Revampire/Ghidra/marshal.hh"
	"Revampire/Ghidra/memstate.hh"
	"Revampire/Ghidra/merge.hh"
	"Revampire/Ghidra/modelrules.hh"
	"Revampire/Ghidra/op.hh"
	"Revampire/Ghidra/opbehavior.hh"
	"Revampire/Ghidra/opcodes.hh"
	"Revampire/Ghidra/options.hh"
	"Revampire/Ghidra/override.hh"
	"Revampire/Ghidra/paramid.hh"
	"Revampire/Ghidra/partmap.hh"
	"Revampire/Ghidra/pcodecompile.hh"
	"Revampire/Ghidra/pcodeinject.hh"
	"Revampire/Ghidra/pcodeparse.hh"
	"Revampire/Ghidra/pcoderaw.hh"
	"Revampire/Ghidra/prefersplit.hh"
	"Revampire/Ghidra/prettyprint.hh"
	"Revampire/Ghidra/printc.hh"
	"Revampire/Ghidra/printjava.hh"
	"Revampire/Ghidra/printlanguage.hh"
	"Revampire/Ghidra/rangemap.hh"
	"Revampire/Ghidra/rangeutil.hh"
	"Revampire/Ghidra/raw_arch.hh"
	"Revampire/Ghidra/ruleaction.hh"
	"Revampire/Ghidra/rulecompile.hh"
	"Revampire/Ghidra/semantics.hh"
	"Revampire/Ghidra/signature.hh"
	"Revampire/Ghidra/sleigh.hh"
	"Revampire/Ghidra/sleigh_arch.hh"
	"Revampire/Ghidra/sleighbase.hh"
	"Revampire/Ghidra/slghpatexpress.hh"
	"Revampire/Ghidra/slghpattern.hh"
	"Revampire/Ghidra/slghsymbol.hh"
	"Revampire/Ghidra/space.hh"
	"Revampire/Ghidra/string_ghidra.hh"
	"Revampire/Ghidra/stringmanage.hh"
	"Revampire/Ghidra/subflow.hh"
	"Revampire/Ghidra/transform.hh"
	"Revampire/Ghidra/translate.hh"
	"Revampire/Ghidra/type.hh"
	"Revampire/Ghidra/typegrp_ghidra.hh"
	"Revampire/Ghidra/typeop.hh"
	"Revampire/Ghidra/unify.hh"
	"Revampire/Ghidra/unionresolve.hh"
	"Revampire/Ghidra/userop.hh"
	"Revampire/Ghidra/variable.hh"
	"Revampire/Ghidra/varmap.hh"
	"Revampire/Ghidra/varnode.hh"
	"Revampire/Ghidra/xml.hh"
	"Revampire/Ghidra/xml_arch.hh"
	"Revampire/GhidraExtension/FuncBuildHelper.h"
	"Revampire/GhidraExtension/IDALoadImage.h"
	"Revampire/GhidraExtension/PrintManager.h"
	"Revampire/GhidraExtension/VmpAction.h"
	"Revampire/GhidraExtension/VmpArch.h"
	"Revampire/GhidraExtension/VmpControlFlow.h"
	"Revampire/GhidraExtension/VmpFunction.h"
	"Revampire/GhidraExtension/VmpInstruction.h"
	"Revampire/GhidraExtension/VmpNode.h"
	"Revampire/GhidraExtension/VmpRule.h"
	"Revampire/Common/Public.h"
	"Revampire/Common/StringUtils.h"
	"Revampire/Common/VmpCommon.h"
	"Revampire/Helper/GhidraHelper.h"
	"Revampire/Helper/IDAWrapper.h"
	"Revampire/Helper/UnicornHelper.h"
	"Revampire/Manager/DisasmManager.h"
	"Revampire/Manager/SectionManager.h"
	"Revampire/Manager/VmpVersionManager.h"
	"Revampire/Manager/exceptions.h"
	"Revampire/VmpCore/VmpBlockBuilder.h"
	"Revampire/VmpCore/VmpReEngine.h"
	"Revampire/VmpCore/VmpTraceFlowGraph.h"
	"Revampire/VmpCore/VmpUnicorn.h"
	cmake.toml
)

add_library(Revampire SHARED)

target_sources(Revampire PRIVATE ${Revampire_SOURCES})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${Revampire_SOURCES})

target_compile_definitions(Revampire PUBLIC
	_WINDOWS
	_CRT_SECURE_NO_WARNINGS
	USE_STANDARD_FILE_FUNCTIONS
)

target_link_libraries(Revampire PUBLIC
	capstone::capstone
	unicorn
)