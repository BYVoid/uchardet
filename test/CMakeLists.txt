set(
	UCHARDET_TEST_SOURCES
	uchardet-tests.c
)

add_executable(
	uchardet-tests
	${UCHARDET_TEST_SOURCES}
)

target_link_libraries(
	uchardet-tests
	libuchardet
)

set_target_properties(
	uchardet-tests
	PROPERTIES
		LINKER_LANGUAGE
			C
		OUTPUT_NAME
			uchardet-tests
)

# Iterate through all langs.
file(GLOB dirs "[a-z][a-z]")
foreach(dir ${dirs})
    get_filename_component(lang ${dir} NAME)
    file(GLOB files "${dir}/*")
    # Iterate through all files.
    foreach(file ${files})
        get_filename_component(charset ${file} NAME_WE)
        add_test(NAME "${lang}-${charset}"
                 COMMAND uchardet-tests ${file})
    endforeach()
endforeach()

