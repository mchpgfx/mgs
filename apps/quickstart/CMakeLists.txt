cmake_minimum_required(VERSION 3.14)

# Find all files ending with .zip in the current source directory
file(GLOB zipfiles "${CMAKE_CURRENT_SOURCE_DIR}/*.zip")

# Check if any zip files were found
if(zipfiles)
    message(STATUS "Found zip files:")
    # Iterate through the list of found zip files and print them
    foreach(zfile ${zipfiles})
        get_filename_component(appname ${zfile} NAME_WE)
		if(EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/${appname}_gen/gfx)
		    add_executable(mgs_${appname})
		    file(GLOB_RECURSE srcList main.c  apps/*.c ${appname}_gen/gfx/legato/generated/*.c)

        	filter_items(srcList ".*le_gen_harmony.*")
        	filter_items(mgsSrcList ".*gfx_canvas.*")

			target_sources(mgs_${appname} PRIVATE ${srcList})
			target_sources(mgs_${appname} PRIVATE ${mgsSrcList})

			target_include_directories(mgs_${appname} PRIVATE ./${appname}_gen)
			target_include_directories(mgs_${appname} PRIVATE ./apps)

			install(TARGETS mgs_${appname} DESTINATION bin)
		endif()
    endforeach()
else()
    message(STATUS "MGS Composer generated files Not found")
endif()
