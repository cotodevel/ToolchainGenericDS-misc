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

NEWLIB2_NTR 	=	$(CURDIR)/newlib-nano-2/newlib-nds
TOOLCHAIN_DIR 	= $(CURDIR)/ToolchainGenericDS/src
PROY_DIR		= $(CURDIR)/ToolchainGenericDS-zlib-example
all: toolchain_and_project

#Make
toolchain_and_project:
	$(MAKE)	-R	-C	$(TOOLCHAIN_DIR)/
	$(MAKE)	-R	-C	$(PROY_DIR)/
	
clean:
	$(MAKE)	clean	-C	$(TOOLCHAIN_DIR)/
	$(MAKE)	clean	-C	$(PROY_DIR)/
	
newlib:
	$(MAKE)	-R	-C	$(NEWLIB2_NTR)/
	
cleannewlib:
	$(MAKE)	clean	-C	$(NEWLIB2_NTR)/

makeall:
	$(MAKE)	-R	-C	$(TOOLCHAIN_DIR)/
	$(MAKE)	-R	-C	$(CURDIR)/armv4core/
	$(MAKE)	-R	-C	$(CURDIR)/gbaARMHook/
	$(MAKE)	-R	-C	$(CURDIR)/gbaemu4DS/
	$(MAKE)	-R	-C	$(CURDIR)/NesDS/
	$(MAKE)	-R	-C	$(CURDIR)/SnemulDS/
	$(MAKE)	-R	-C	$(CURDIR)/ToolchainGenericDS-gdbstub-example/
	$(MAKE)	-R	-C	$(CURDIR)/ToolchainGenericDS-multiplayer-example/
	$(MAKE)	-R	-C	$(CURDIR)/ToolchainGenericDS-template/
	$(MAKE)	-R	-C	$(CURDIR)/ToolchainGenericDS-zlib-example/

cleanall:
	$(MAKE)	clean	-C	$(TOOLCHAIN_DIR)/
	$(MAKE)	clean	-C	$(CURDIR)/armv4core/
	$(MAKE)	clean	-C	$(CURDIR)/gbaARMHook/
	$(MAKE)	clean	-C	$(CURDIR)/gbaemu4DS/
	$(MAKE)	clean	-C	$(CURDIR)/NesDS/
	$(MAKE)	clean	-C	$(CURDIR)/SnemulDS/
	$(MAKE)	clean	-C	$(CURDIR)/ToolchainGenericDS-gdbstub-example/
	$(MAKE)	clean	-C	$(CURDIR)/ToolchainGenericDS-multiplayer-example/
	$(MAKE)	clean	-C	$(CURDIR)/ToolchainGenericDS-template/
	$(MAKE)	clean	-C	$(CURDIR)/ToolchainGenericDS-zlib-example/
	