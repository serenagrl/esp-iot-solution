
# componet standalone mode
if(NOT CONFIG_IOT_SOLUTION_EMBED)
    set(COMPONENT_SRCS "fbm320.c"
                        "fbm320_obj.cpp")

    set(COMPONENT_ADD_INCLUDEDIRS ". include")
else()
    if(CONFIG_IOT_fbm320_ENABLE)
        set(COMPONENT_SRCS "fbm320.c"
                            "fbm320_obj.cpp")

        set(COMPONENT_ADD_INCLUDEDIRS ". include")
    else()
        set(COMPONENT_SRCS "")
        set(COMPONENT_ADD_INCLUDEDIRS "")
        message(STATUS "Building empty fbm320 component due to configuration")
    endif()
endif()

# requirements can't depend on config
set(COMPONENT_REQUIRES i2c_bus)

register_component()
