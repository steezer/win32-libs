SOURCES=$(wildcard src/*.cpp)
PROJECT_NAME=utils
TARGET_DIR=lib
CC=g++
AR=ar -rcs
CFLAGS=-DCURL_STATICLIB
LDFLAGS= -lwinhttp -L../curl/lib -lcurl
INC_DIR=-I./include -I../curl/include
BUILD_DIR=build
SHARE_TARGET=$(TARGET_DIR)/lib$(PROJECT_NAME).dll
STATIC_TARGET=$(TARGET_DIR)/lib$(PROJECT_NAME).a
OBJECTS=$(addprefix $(BUILD_DIR)/,$(strip $(SOURCES:.cpp=.o)))

all:share static
share: $(OBJECTS)
	$(CC) -fPIC -shared -o $(SHARE_TARGET) $^ $(LDFLAGS)

static:$(OBJECTS)
	$(AR) $(STATIC_TARGET) $^

$(BUILD_DIR)/%.o:%.cpp
	$(CC) -c -o $@ $(CFLAGS) $(INC_DIR) $<

.PHONY: clean install run stop dev

clean:
	rm -rf $(BUILD_DIR)/src/*

