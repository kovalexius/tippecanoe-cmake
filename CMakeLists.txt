cmake_minimum_required(VERSION 3.16)

project(tippecanoe)

include_directories(
	./
	./clipper2/include
)

set(CMAKE_CXX_STANDARD 17)

add_executable(tippecanoe
    geojson.cpp
    jsonpull/jsonpull.c
    tile.cpp
    pool.cpp
    mbtiles.cpp
    geometry.cpp
    projection.cpp
    memfile.cpp
    mvt.cpp
    serial.cpp
    main.cpp
    platform.cpp
    text.cpp
    dirtiles.cpp
    pmtiles_file.cpp
    plugin.cpp
    read_json.cpp
    write_json.cpp
    geobuf.cpp
    flatgeobuf.cpp
    evaluator.cpp
    geocsv.cpp
    csv.cpp
    geojson-loop.cpp
    json_logger.cpp
    visvalingam.cpp
    compression.cpp
    clip.cpp
    sort.cpp
    attribute.cpp
    thread.cpp
    shared_borders.cpp
    clipper2/src/clipper.engine.cpp
)

target_link_libraries(tippecanoe
	PRIVATE
	-lsqlite3
	-lpthread
	-lm
	-lz
)

add_executable(tippecanoe-enumerate
	enumerate.cpp
)

target_link_libraries(tippecanoe-enumerate
	-lsqlite3
)

add_executable(tippecanoe-decode
	decode.cpp
	projection.cpp
	mvt.cpp
	write_json.cpp
	text.cpp
	jsonpull/jsonpull.c
	dirtiles.cpp
	pmtiles_file.cpp
)

target_link_libraries(tippecanoe-decode
	-lsqlite3
	-lm
	-lz
)

add_executable(tile-join
	tile-join.cpp
	platform.cpp
	projection.cpp
	mbtiles.cpp
	mvt.cpp
	memfile.cpp
	dirtiles.cpp
	jsonpull/jsonpull.c
	text.cpp
	evaluator.cpp
	csv.cpp
	write_json.cpp
	pmtiles_file.cpp
	clip.cpp
	attribute.cpp
	thread.cpp
	read_json.cpp
	clipper2/src/clipper.engine.cpp
)

target_link_libraries(tile-join
	-lm
	-lz
	-lsqlite3
	-lpthread
)

add_executable(tippecanoe-json-tool
	jsontool.cpp
	jsonpull/jsonpull.c
	csv.cpp
	text.cpp
	geojson-loop.cpp
)

target_link_libraries(tippecanoe-json-tool
	-lm
	-lz
	-lsqlite3
	-lpthread
)

add_executable(unit
	unit.cpp
	text.cpp
	sort.cpp
	mvt.cpp
	projection.cpp
	clip.cpp
	attribute.cpp
	jsonpull/jsonpull.c
	evaluator.cpp
	read_json.cpp
	clipper2/src/clipper.engine.cpp
)

target_link_libraries(unit
	-lm
	-lz
	-lsqlite3
	-lpthread
)

add_executable(tippecanoe-overzoom
	overzoom.cpp
	mvt.cpp
	clip.cpp
	evaluator.cpp
	jsonpull/jsonpull.c
	text.cpp
	attribute.cpp
	read_json.cpp
	projection.cpp
	read_json.cpp
	clipper2/src/clipper.engine.cpp
)

target_link_libraries(tippecanoe-overzoom
	-lm
	-lz
	-lsqlite3
	-lpthread
)
