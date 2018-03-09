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
export TARGET_LIBRARY_FILE	=	libgcc-out.a

export DIRS_SRC = /
export DIRS_HEADER = /
export BUILD	=	build

# relative path (if you are outside arm9 folder then $(DIR_ARM9), arm7 is $(DIR_ARM7))
RELATIVE_PATH =	

#Prepare ARM9 dirs
DIRLIBS_HDR = $(foreach dirres,$(DIRS_HEADER),-I "$(CURDIR)/$(RELATIVE_PATH)/$(dirres)" )
DIRLIBS_SRC = $(foreach dirres,$(DIRS_SRC),-I "$(CURDIR)/$(RELATIVE_PATH)/$(dirres)" )
file_arm9_src_o=  $(foreach dir,$(DIRS_SRC), $(subst $(CURDIR)/$(RELATIVE_PATH)/$(dir)/,,$(wildcard $(CURDIR)/$(RELATIVE_PATH)/$(dir)/*.o))  )

# Object Target
objs_arm:=	${file_arm9_src_o:.o=.o}

################################################################################################

#Dont modify anything else if not necessary ..
OBJECTS = 	$(objs_arm)
OBJDIR 	=	./$(BUILD)
VPATH 	=	$(DIR_SRC)

# Build Target(s)	(both processors here)
all: $(OBJDIR)|$(TARGET_LIBRARY_FILE)

#Check $(OBJDIR) if not exists: create it
$(OBJDIR):
	@echo "Folder $(OBJDIR) does not exist. Creating"
	mkdir -p $@

#Builder.
$(TARGET_LIBRARY_FILE): $(OBJECTS)
	-@echo 'Entering Build phase'
	$(AR) rvs	$@	$^
	-@echo 'Leaving Linking phase. Output: $@'
	
clean:
	-@echo 'cleanup'

debug:
	-@echo 'debug: $(objs_arm)'
