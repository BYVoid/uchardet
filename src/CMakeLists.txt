
set(
	UCHARDET_HEADERS
	uchardet.h
)

set(
	UCHARDET_SOURCES
	CharDistribution.cpp
	JpCntx.cpp
	LangBulgarianModel.cpp
	LangCyrillicModel.cpp
	LangGreekModel.cpp
	LangHebrewModel.cpp
	LangHungarianModel.cpp
	LangThaiModel.cpp
	nsBig5Prober.cpp
	nsCharSetProber.cpp
	nsEscCharsetProber.cpp
	nsEscSM.cpp
	nsEUCJPProber.cpp
	nsEUCKRProber.cpp
	nsEUCTWProber.cpp
	nsGB2312Prober.cpp
	nsHebrewProber.cpp
	nsLatin1Prober.cpp
	nsMBCSGroupProber.cpp
	nsMBCSSM.cpp
	nsSBCharSetProber.cpp
	nsSBCSGroupProber.cpp
	nsSJISProber.cpp
	nsUniversalDetector.cpp
	nsUTF8Prober.cpp
	uchardet.cpp
)

set (UCHARDET_TARGET libuchardet)
set (UCHARDET_STATIC_TARGET libuchardet_static)

add_definitions(
	-DPKGDATADIR="${DIR_SHARE_OPENCC}"
	-DLOCALEDIR="${DIR_SHARE_LOCALE}"
	-DVERSION="${UCHARDET_VERSION}"
	-DPACKAGE_NAME="${PACKAGE_NAME}"
	-Wall
)

add_library(
	${UCHARDET_TARGET}
	SHARED
	${UCHARDET_SOURCES}
)

add_library(
	${UCHARDET_STATIC_TARGET}
	STATIC
	${UCHARDET_SOURCES}
)

set_target_properties(
	${UCHARDET_TARGET}
	${UCHARDET_STATIC_TARGET}
	PROPERTIES
		LINKER_LANGUAGE
			CXX
		OUTPUT_NAME
			uchardet
		VERSION
			0.0.0
		SOVERSION
			0
)

if (CMAKE_BUILD_TYPE MATCHES Debug)
	add_definitions(
		-O0
		-g3
	)
endif (CMAKE_BUILD_TYPE MATCHES Debug)

if (NOT WIN32)
install(
	TARGETS
		${UCHARDET_TARGET}
	LIBRARY DESTINATION
		${DIR_LIBRARY}
)
endif (NOT WIN32)

install(
	TARGETS
		${UCHARDET_STATIC_TARGET}
	ARCHIVE DESTINATION
		${DIR_LIBRARY_STATIC}
)

install(
	FILES
		${UCHARDET_HEADERS}
	DESTINATION
		${DIR_INCLUDE}/uchardet
)

include(symbols.cmake)

add_subdirectory(tools)
