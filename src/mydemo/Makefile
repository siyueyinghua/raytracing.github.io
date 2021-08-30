# make path, dir item separate by ":"
vpath %.c 	./src:../common
vpath %.cpp ./src:../common
vpath %.cc  ./src:../common
vpath %.h 	./inc:../common
vpath %.hpp ./inc:../common

# compile and link parameter
# CC := gcc
# CXX := g++
CC := clang
CXX := clang++
CFLAGS :=
CXXFLAGS:= -std=c++17
LDFLAGS := -lX11 -lpthread -lXrandr -lXi -ldl -lXxf86vm -lXinerama -lXcursor
LIBS :=
DEFINES :=
INCLUDE := -I./inc -I../common
INC = -I./inc -I../common
INCLUDE_DIRS = -I./inc -I../common
#DEPS = glad.h glfw3.h glfw3native.h

# target
TARGET := ppm_main
TGT_ALL := $(TARGET).out
TARGET := ray_background
TGT_ALL := $(TARGET).out
TARGET := ray_background_sphere
TGT_ALL := $(TARGET).out
TARGET := ray_background_sphere_normal
TGT_ALL := $(TARGET).out
TARGET := ray_two_sphere
TGT_ALL := $(TARGET).out
TARGET := ray_two_sphere_msaa
TGT_ALL := $(TARGET).out
TARGET := ray_material_diffuse
TGT_ALL := $(TARGET).out
TARGET := ray_material_diffuse_metal
TGT_ALL := $(TARGET).out

# link 
$(TARGET).out: $(TARGET).o
	$(CXX) -o $@ $^ $(LIBS) $(LDFLAGS)
	./$@

.PHONY: all
all: $(TGT_ALL)
	@echo "$^"

%.out: %.o
	$(CXX) -o $@ $^ $(LIBS) $(LDFLAGS)
	./$@

# compile
%.o: %.cpp
	$(CXX) -o $@ -c $<  $(CXXFLAGS) $(INC)

%.o: %.cc
	$(CXX) -o $@ -c $<  $(CXXFLAGS) $(INC)

%.o: %.c
	$(CXX) -o $@ -c $<  $(CXXFLAGS) $(INC)

# run out
.PHONY: run
run:
	./$(TARGET).out

# clean
.PHONY: clean
clean:
	rm -rf *.o *.out $(TARGET).out

