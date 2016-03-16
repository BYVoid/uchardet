
set(
	UCHARDET_HEADERS
	uchardet.h
)

set(
	UCHARDET_SOURCES
	CharDistribution.cpp
	JpCntx.cpp
	LangModels/LangArabicModel.cpp
	LangModels/LangBulgarianModel.cpp
	LangModels/LangRussianModel.cpp
	LangModels/LangEsperantoModel.cpp
	LangModels/LangFrenchModel.cpp
	LangModels/LangGermanModel.cpp
	LangModels/LangGreekModel.cpp
	LangModels/LangHungarianModel.cpp
	LangModels/LangHebrewModel.cpp
	LangModels/LangSpanishModel.cpp
	LangModels/LangThaiModel.cpp
	LangModels/LangTurkishModel.cpp
	LangModels/LangVietnameseModel.cpp
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
if (BUILD_STATIC AND BUILD_SHARED_LIBS)
set (UCHARDET_STATIC_TARGET libuchardet_static)
endif ()

add_definitions(
	-DPKGDATADIR="${DIR_SHARE_OPENCC}"
	-DLOCALEDIR="${DIR_SHARE_LOCALE}"
	-DVERSION="${UCHARDET_VERSION}"
	-DPACKAGE_NAME="${PACKAGE_NAME}"
	-Wall
)

add_library(
	${UCHARDET_TARGET}
	${UCHARDET_SOURCES}
)

if (UCHARDET_STATIC_TARGET)
    add_library(
            ${UCHARDET_STATIC_TARGET}
            STATIC
            ${UCHARDET_SOURCES}
    )
endif (UCHARDET_STATIC_TARGET)

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

if (UCHARDET_STATIC_TARGET)
    set_target_properties(
        ${UCHARDET_STATIC_TARGET}
        PROPERTIES
            LINKER_LANGUAGE
                CXX
            OUTPUT_NAME
                uchardet
    )
endif (UCHARDET_STATIC_TARGET)

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
    ARCHIVE DESTINATION
        ${DIR_LIBRARY}
)
else (NOT WIN32)
install(
    TARGETS
        ${UCHARDET_TARGET}
    RUNTIME DESTINATION
        ${CMAKE_INSTALL_BINDIR}
    ARCHIVE DESTINATION
        ${DIR_LIBRARY}
)
endif (NOT WIN32)

if (UCHARDET_STATIC_TARGET)
    install(
        TARGETS
            ${UCHARDET_STATIC_TARGET}
        ARCHIVE DESTINATION
            ${DIR_LIBRARY_STATIC}
    )
endif (UCHARDET_STATIC_TARGET)

install(
	FILES
		${UCHARDET_HEADERS}
	DESTINATION
		${DIR_INCLUDE}/uchardet
)

include(symbols.cmake)

if (BUILD_BINARY)
add_subdirectory(tools)
endif (BUILD_BINARY)
