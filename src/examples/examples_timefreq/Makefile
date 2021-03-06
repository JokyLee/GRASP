#
## This is the SITE_SPECIFIC file
##
## This is the only file that you should need to edit to set up
## your own working copy of GRASP.  Directions for editing this
## file may be found in the GRASP USERS MANUAL.  A PDF version
## of the manual may be found in the doc/ subdirectory, in manual.pdf.
## A number of examples of SiteSpecific files may be found in the
## directory ExamplesSiteSpecific/.  Look in there to find one
## similar to what you might need for your own machine.
##
## First, edit this file.
## Second, run the shell script called InstallGRASP
##
##
## ------------------------------------------------------------##
## START EDITING HERE.  PLEASE SAVE A COPY OF THIS ORIGINAL FILE
##
##
## edit to point to the home directory of the GRASP package.  This
## is where GRASP is installed and where it must be built.
## If the directory structure is already where you want it, just set
## GRASP_HOME to the current directory!
GRASP_HOME=/home/leo/Downloads/GRASP_1.9.8

## ----------------------------------------------------------##
##  THIS SECTION DEFINES YOUR CHOICE OF COMPILER AND OPTIONS ##

# edit to the name of your C compiler:
CC = cc

# edit to include compilation flags that you desire:
CFLAGS= -g

## ---------------------------------------------------------##
##  THIS SECTION REFERENCES THE NUMERICAL RECIPES LIBRARIES ##

# edit to point to directory containing the Numerical Recipes library
RECIPES_LIB=/usr/local/recipes/lib

# edit to give the name of the Numerical Recipes library you wish to use:
LRECIPES=recipes_c

## -----------------------------------------------------------##
##  THIS IS THE SECTION THAT REFERENCES THE MPI/MPE LIBRARIES ##

# If you want to build the MPI code, set this variable to true, else to false
# If it is set to false, all the MPI defines below are ignored.
#BUILD_MPI = false
BUILD_MPI = true

# edit to give the name of your local MPI C compiler (and any flags)
MPICC = mpicc 

# edit to point to the MPI/MPE include directory
MPI_INCLUDES=-I/usr/local/mpi/include

# edit to give the names/paths of the MPI/MPE libraries you wish to use:
# probably not needed if you use mpicc and -mpilog options
# MPI_LIBS = -lmpe -lpmpi -lmpi

## -----------------------------------------------------------##
##  THIS IS THE SECTION THAT REFERENCES THE GL/MESA LIBRARIES ##

# If you have the GL/MESA libraries installed then you should set this
# variable to true. This library is used to display time frequency maps.
HAVE_GL = true
# HAVE_GL = false

XLIBS = -L/usr/X11/lib -L/usr/X11R6/lib -lX11 -lXext -lXmu -lXt -lXi -lSM -lICE
GL_LIBS = $(pkg-config --libs glu) $(XLIBS)
GL_I=$(pkg-config --cflags glu)

## -----------------------------------------------------------##
##  THIS IS THE SECTION THAT REFERENCES THE FRAME LIBRARIES   ##

# If you want to build code that depends upon the FRAME libraries,
# set this variable to true, else to false
# If it is set to false, the FRAME_DIR define is ignored
BUILD_FRAME = true
# BUILD_FRAME = false

# edit to point to the directory containing the FRAME directories
# include and lib.  The required files are include/FrameL.h and
# lib/libFrame.a.  Recent versions of the FRAME library also require
# include/FrIO.h to be in this directory.
FRAME_DIR=/usr/local/frame

## -----------------------------------------------------------##
##  THIS IS THE SECTION THAT REFERENCES THE EPICS LIBRARIES   ##

# If you want to build code that will run on a real-time system (in the 40-meter lab)
# and gets the file names from there, you will need to have a set
# of epics libraries and include files available.
# Unless you want to do this, please leave the following lines commented out!
# Directories containing epics includes/libraries:
# EPICS_INCLUDES=-I/home/ballen/epics2 -I/home/ballen/epics1
# EPICS_LIBS=-L/home/ballen/epics2 -L/home/ballen/epics1 -D_POSIX_PTHREAD_SEMANTICS -lezca  -lca -lCom -lnsl -lsocket -ldl -lintl -lposix4
# BUILD_REALTIME = -DREALTIME

## -----------------------------------------------------------##
##  THIS IS THE SECTION THAT DEALS WITH CLAPACK
##  REQUIRED IF YOU WISH TO `CLEAN' DATA USING ENVIRONMENTAL
##  INFORMATION
#  Set to true to build/use CLAPACK code
WITH_CLAPACK = true
#WITH_CLAPACK = false 

# claplack library directory
CLAPACK_LIB=/usr/local/CLAPACK/lib/

# Name of clapack and blas library
LCLAPACK=lapack_linux
LBLAS=blas_linux

# f2c library directory
F2C_LIB=/usr/local/F2C/lib
LF2C=F77
LF2CI=I77
F2C_INC=/usr/local/F2C/include 

CLAPACK_LIBS=-L$(CLAPACK_LIB) -l$(LCLAPACK) -l$(LBLAS) -L$(F2C_LIB) -l$(LF2C)  -l$(LF2CI)

## -----------------------------------------------------------##
## THIS SECTION IS WHERE HARDWIRED OPTIMIZATIONS ARE SWITCHED

# The GRASP code includes some inline optimization tricks which speed
# up the code by having our own implementations of certain standard
# functions like pow(x,1.0/3.0) and sin and cos.  This is at a price - these
# functions are less accurate than the routines that they replace.
# You should only uncomment the following lines if you are doing production
# work, and then only after verifying that the inline functions are
# sufficiently accurate for your purposes.
# DEFINES = -DINLINE_CUBEROOT -DINLINE_TRIGS

## -----------------------------------------------------------##
## THIS SECTION IS WHERE ANY FUNCTIONS ARE OVERLOADED WITH .o FILES
## FOR OPTIMIZATION PURPOSES, AND ANY EXTRA OPTIMIZATION LIBRARIES ARE
## DEFINED.  LEAVE THESE LINES COMMENTED OUT EXCEPT FOR BUILDING
## OPTIMIZED VERSIONS OF LIBRARY FUNCTIONS.  To build optimized glue routines,
## please look in the README files in src/optimization/*.
## We highly recommend that you build the FFTW glue code!
## This is ~5 times faster than Numerical Recipes FFTs

# optimization using FFTW VERSION 1.2
# (a public-domain optimized fft routine: see src/optimization/fftw1/README)
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/fftw1/realft_fftw.o
# OPTIMIZED_LIBS= -L/usr/local/fftw/lib -lfftw

# optimization using FFTW VERSION 2.1
# (a public-domain optimized fft routine: see src/optimization/fftw2/README)
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/fftw2/realft_fftw.o
# OPTIMIZED_LIBS= -L/usr/local/fftw-2.1.1/lib -lfftw

# optimization for the Intel Paragon Supercomputer (w/CLASSPACK library)
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/paragon/realft_paragon_risky.o
# OPTIMIZED_LIBS= -lkmath

# optimization for the Sparc (w/Sun Performance Library)
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/sparc/realft_sparc.o
# OPTIMIZED_LIBS= -xlic_lib=sunperf

# optimization for SGI R10000 CPU machines (w/Cray-SGI computational library):  see src/optimization/sgi/
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/sgi/realft_sgi.o
# OPTIMIZED_LIBS= -lcomplib.sgimath

# optimization for DEC ALPHA machines (w/DEC extended math library: see src/optimization/dec/
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/dec/realft_dec.o
# OPTIMIZED_LIBS= -ldxml

# optimization for IBM SP2 machines (w/IBM extended scientific subroutine library
# see src/optimization/ibm
# OPTIMIZED_OBJECTS=$(GRASP_HOME)/src/optimization/ibm/realft_ibm.o
# OPTIMIZED_LIBS= -lesslp2

## -----------------------------------------------------------##
##  THIS IS THE SECTION THAT REFERENCES THE GRTOOLBOX WHICH
##  PROVIDES A MATLAB INTERFACE TO GRASP AND THE FRAME
##  LIBRARY.
##
##  NOTE: IF YOU SET BUILD_GRTOOLBOX TO TRUE YOU MUST ALSO
##        HAVE SET BUILD_FRAME TO TRUE.
##


# If you want to build code that depends upon the GRtoolbox,
# set this variable to true, else to false
# If it is set to false, the varriables MEX, MEXFLAGS, and
# EXT varriables are ignored.
# 
BUILD_GRTOOLBOX = false
#BUILD_GRTOOLBOX = true

# edit to the name of your mex compiler:
#MEX = mex

# edit to include compilation flags that you desire:
# debugging and developement
#MEXFLAGS=-g
# speed and optimization
#MEXFLAGS=-O

# Set the EXT varriable to indicate your platform. 
# Mex-files have different filenames for different 
# platforms.
# 
# Alpha
#EXT = axp
# HP9000 series 700
#EXT = mexhp7
# IBM RS6000
#EXT = mexrs6
# Linux
#EXT = lx
# SGI
#EXT = sg
# SGI 6.4
#EXT = sg64
# Solaris
#EXT = sol
# SunOS4x
#EXT = 4

## -----------------------------------------------------------##
## NO EDITING SHOULD BE NEEDED BELOW THIS POINT

GRASP_I=$(GRASP_HOME)/include
#############################################################################
#  THE REGION ABOVE THIS SPACE IS FILLED IN BY InstallGRASP                 #
#############################################################################

INCLUDES= -I$(GRASP_I)

LIBS= $(OPTIMIZED_OBJECTS) -L$(GRASP_HOME)/lib -lgrasp $(OPTIMIZED_LIBS) -lm


all: tfmain readertf combine

tfmain: tfmain.o tf_misc.o tf_get_data.o $(GRASP_HOME)/lib/libgrasp.a
	if [ '$(BUILD_MPI)' = 'true' ]; then \
	if [ '$(HAVE_GL)' =  'true' ]; then \
	$(MPICC) tfmain.o tf_misc.o tf_get_data.o -o tfmain $(GL_LIBS) $(LIBS) $(MPI_LIBS);\
	else \
	$(MPICC) tfmain.o tf_misc.o tf_get_data.o -o tfmain $(LIBS) $(MPI_LIBS);\
	fi;\
	fi


tfmain.o: tfmain.c tfmain.h $(GRASP_I)/grasp.h 
	if [ '$(BUILD_MPI)' = 'true' ]; then \
        if [ '$(HAVE_GL)' =  'true' ]; then \
        $(MPICC) -DHAVE_GL -c $(CFLAGS) $(MPI_INCLUDES) $(INCLUDES) tfmain.c;\
        else\
        $(MPICC) -c $(CFLAGS) $(MPI_INCLUDES) $(INCLUDES) tfmain.c;\
        fi;\
        fi

tf_misc.o: tf_misc.c tfmain.h $(GRASP_I)/grasp.h 
	if [ '$(BUILD_MPI)' = 'true' ]; then \
	$(CC) -c $(CFLAGS) $(MPI_INCLUDES) $(INCLUDES) tf_misc.c;\
	fi

tf_get_data.o: tf_get_data.c tfmain.h $(GRASP_I)/grasp.h 
	if [ '$(BUILD_MPI)' = 'true' ]; then \
	$(CC) -c $(CFLAGS) $(MPI_INCLUDES) $(INCLUDES) tf_get_data.c;\
	fi

readertf: readertf.c
	$(CC) readertf.c $(CFLAGS)  -o readertf

combine: combine.c
	$(CC) combine.c $(CFLAGS)  -o combine








