#
#			Copyright (C) 2017  Coto
#This program is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 2 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful, but
#WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
#General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301
#USA
#

#coto: script that builds a collection of objects (*.o) into $(TARGET_LIBRARY_FILE)

#TGDS1.3 compatible Makefile

#Shared
include $(DEFAULT_GCC_PATH)Makefile.basenewlib
export TARGET_LIBRARY_FILE_OUT	=	libgcc-out.a
export TARGET_LIBRARY_FILE_IN	=	libgcc.a

export DIRS_SRC = /
export DIRS_HEADER = /
export BUILD	=	build

# relative path (if you are outside arm9 folder then $(DIR_ARM9), arm7 is $(DIR_ARM7))
RELATIVE_PATH =	

#Prepare ARM9 dirs
ifeq ($(TGDS_ENV),windows)
	DIRLIBS_HDR = $(foreach dirres,$(DIRS_HEADER),-I "$(CURDIR)/$(RELATIVE_PATH)/$(dirres)" )
	DIRLIBS_SRC = $(foreach dirres,$(DIRS_SRC),-I "$(CURDIR)/$(RELATIVE_PATH)/$(dirres)" )
	file_arm9_src_o=  $(foreach dir,$(DIRS_SRC), $(subst $(CURDIR)/$(RELATIVE_PATH)/$(dir)/,,$(wildcard $(CURDIR)/$(RELATIVE_PATH)/$(dir)/*.o))  )
endif
ifeq ($(TGDS_ENV),linux)
	DIRLIBS_HDR = $(foreach dirres,$(DIRS_HEADER),-I "$(PWD)/$(RELATIVE_PATH)/$(dirres)" )
	DIRLIBS_SRC = $(foreach dirres,$(DIRS_SRC),-I "$(PWD)/$(RELATIVE_PATH)/$(dirres)" )
	file_arm9_src_o=  $(foreach dir,$(DIRS_SRC), $(subst $(PWD)/$(RELATIVE_PATH)/$(dir)/,,$(wildcard $(PWD)/$(RELATIVE_PATH)/$(dir)/*.o))  )
endif

# Object Target
objs_arm:=	${file_arm9_src_o:.o=.o}

################################################################################################

#Dont modify anything else if not necessary ..
OBJECTS = 	$(objs_arm)
OBJDIR 	=	./$(BUILD)
VPATH 	=	$(DIR_SRC)

# Build Target(s)	(both processors here)
all: usage

#Check $(OBJDIR) if not exists: create it
$(OBJDIR):
	@echo "Folder $(OBJDIR) does not exist. Creating"
	mkdir -p $@

#Builder.
$(TARGET_LIBRARY_FILE): $(OBJECTS)
	-@echo 'Entering Build phase'
	$(AR) rvs	$@	$^
	-@echo 'Leaving Linking phase. Output: $@'
	
build:	$(OBJDIR)|$(TARGET_LIBRARY_FILE)

export:	$(TARGET_LIBRARY_FILE_IN)
	

usage:
	-@echo 'usage:
	-@echo 'make build: *.o here exports into gnu librarian $(TARGET_LIBRARY_FILE_OUT)'
	-@echo 'make export: imports gnu librarian $(TARGET_LIBRARY_FILE_IN) into *.o'
		
