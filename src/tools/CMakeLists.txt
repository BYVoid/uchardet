set(
	UCHARDET_SOURCES
	uchardet.cpp
)

add_executable(
	uchardet
	${UCHARDET_SOURCES}
)

target_link_libraries(
	uchardet
	${UCHARDET_LIBRARY}
)

install(
	TARGETS
		uchardet
	RUNTIME DESTINATION
		${CMAKE_INSTALL_BINDIR}
)
