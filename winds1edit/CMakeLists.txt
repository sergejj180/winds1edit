cmake_minimum_required (VERSION 3.5)

project (win_ds1edit)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu99")
set(CMAKE_C_FLAGS ${CMAKE_C_FLAGS} "-std=gnu99 -Wl,--subsystem,windows")

set(SOURCES 
	main.c anim.c animdata.c dc6info.c dccinfo.c ds1misc.c ds1save.c dt1_draw.c dt1misc.c editobj.c 
	editpath.c edittile.c error.c gfx_custom.c inicreat.c iniread.c interfac.c misc.c 
	msg_quit.c msg_save.c txtread.c undo.c wBits.c	wEdit.c	wMsg.c wPreview.c
	mpq/Dcl_tbl.c mpq/Explode.c mpq/MpqView.c mpq/Wav_unp.c)

set(INCLUDES 
	anim.h animdata.h dc6info.h dccinfo.h ds1misc.c ds1save.h dt1_draw.h dt1misc.h editobj.h 
	editpath.h edittile.h error.h gfx_custom.h inicreat.h iniread.h interfac.h misc.h 
	msg_quit.h msg_save.h structs.h txtread.h types.h undo.h wBits.h wEdit.h wMsg.h wPreview.h
	mpq/Dclib.h mpq/mpqtypes.h mpq/MpqView.h mpq/Wav_unp.h )
	
set(ALLEGRO_INCLUDES PUBLIC 
	${CMAKE_SOURCE_DIR}/allegro/include
	${CMAKE_SOURCE_DIR}/allegro/include/allegro 
	${CMAKE_SOURCE_DIR}/allegro/include/allegro/inline
	${CMAKE_SOURCE_DIR}/allegro/include/allegro/internal
	${CMAKE_SOURCE_DIR}/allegro/include/allegro/platform)

set(ALLEGRO_LIBRARIES ${CMAKE_SOURCE_DIR}/allegro/lib)

add_executable(${PROJECT_NAME} ${SOURCES} ${INCLUDES})

target_include_directories(${PROJECT_NAME} ${ALLEGRO_INCLUDES})

find_library(ALLEGRO_LIBRARY
	NAME alleg44 alleggl jpgalleg lodpng logg 
	HINTS ${ALLEGRO_LIBRARIES})

TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${ALLEGRO_LIBRARY})