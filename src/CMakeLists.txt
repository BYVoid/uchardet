
set(
	UCHARDET_HEADERS
	uchardet.h
)

set(
	UCHARDET_SOURCES
	CharDistribution.cpp
	JpCntx.cpp
	LangModels/LangBulgarianModel.cpp
	LangModels/LangCyrillicModel.cpp
	LangModels/LangEsperantoModel.cpp
	LangModels/LangFrenchModel.cpp
	LangModels/LangGermanModel.cpp
	LangModels/LangGreekModel.cpp
	LangModels/LangHungarianModel.cpp
	LangModels/LangHebrewModel.cpp
	LangModels/LangThaiModel.cpp
	LangModels/LangTurkishModel.cpp
	nsHebrewProber.cpp
	nsCharSetProber.cpp
	nsBig5Prober.cpp
	nsEUCJPProber.cpp
	nsEUCKRProber.cpp
	nsEUCTWProber.cpp
	nsEscCharsetProber.cpp
	nsEscSM.cpp
	nsGB2312Prober.cpp
	nsMBCSGroupProber.cpp
	nsMBCSSM.cpp
	nsSBCSGroupProber.cpp
	nsSBCharSetProber.cpp
	nsSJISProber.cpp
	nsUTF8Prober.cpp
	nsLatin1Prober.cpp
	nsUniversalDetector.cpp
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

if (BUILD_STATIC)
    add_library(
            ${UCHARDET_STATIC_TARGET}
            STATIC
            ${UCHARDET_SOURCES}
    )
endif (BUILD_STATIC)

set_target_properties(
	${UCHARDET_TARGET}
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

if (BUILD_STATIC)
    set_target_properties(
        ${UCHARDET_STATIC_TARGET}
        PROPERTIES
            LINKER_LANGUAGE
                CXX
            OUTPUT_NAME
                uchardet
    )
endif (BUILD_STATIC)

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
else (NOT WIN32)
install(
	TARGETS
		${UCHARDET_TARGET}
        RUNTIME DESTINATION
                ${DIR_BIN}
	ARCHIVE DESTINATION
		${DIR_LIBRARY}
)
endif (NOT WIN32)

if (BUILD_STATIC)
    install(
        TARGETS
            ${UCHARDET_STATIC_TARGET}
        ARCHIVE DESTINATION
            ${DIR_LIBRARY_STATIC}
    )
endif (BUILD_STATIC)

install(
	FILES
		${UCHARDET_HEADERS}
	DESTINATION
		${DIR_INCLUDE}/uchardet
)

include(symbols.cmake)

add_subdirectory(tools)
