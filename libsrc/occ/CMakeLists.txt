add_library(occ ${NG_LIB_TYPE}
        Partition_Inter2d.cxx Partition_Inter3d.cxx 
        Partition_Loop.cxx Partition_Loop2d.cxx Partition_Loop3d.cxx Partition_Spliter.cxx 
        occconstruction.cpp occgenmesh.cpp occgeom.cpp occmeshsurf.cpp
        )

if(USE_GUI)
    add_library(occvis ${NG_LIB_TYPE} vsocc.cpp)
endif(USE_GUI)

if(NOT WIN32)
    target_link_libraries( occ ${OCC_LIBRARIES} ${PYTHON_LIBS})
    if(USE_GUI)
        target_link_libraries( occvis occ )
        install( TARGETS occ occvis ${ng_install_dir})
    else()
        install( TARGETS occ ${ng_install_dir})
    endif(USE_GUI)
endif(NOT WIN32)

