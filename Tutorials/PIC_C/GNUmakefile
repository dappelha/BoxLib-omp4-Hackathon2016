BOXLIB_HOME ?= ../../

DEBUG	= TRUE
DEBUG	= FALSE

DIM	= 3

COMP    = gcc
FCOMP   = gfortran

USE_PARTICLES = TRUE

PRECISION = DOUBLE

USE_MPI   = TRUE
USE_OMP   = FALSE

###################################################

EBASE     = main

# location of finite-volume HPGMG on edison
HPGMG_DIR ?= ../../../hpgmg/finite-volume

USE_HPGMG = FALSE
HPGMG_FCYCLES = TRUE
HPGMG_POST_F_CYCLE_TYPE = F
HPGMG_HELMHOLTZ = FALSE
HPGMG_STENCIL_VARIABLE_COEFFICIENT = FALSE
HPGMG_USE_SUBCOMM = TRUE
HPGMG_BOTTOM_SOLVER= BICGSTAB
HPGMG_SMOOTHER = GSRB

include ./Make.package
include $(BOXLIB_HOME)/Tools/C_mk/Make.defs

include $(BOXLIB_HOME)/Src/C_BaseLib/Make.package
INCLUDE_LOCATIONS += $(BOXLIB_HOME)/Src/C_BaseLib
VPATH_LOCATIONS   += $(BOXLIB_HOME)/Src/C_BaseLib

include $(BOXLIB_HOME)/Src/C_BoundaryLib/Make.package
INCLUDE_LOCATIONS += $(BOXLIB_HOME)/Src/C_BoundaryLib
VPATH_LOCATIONS   += $(BOXLIB_HOME)/Src/C_BoundaryLib

include $(BOXLIB_HOME)/Src/LinearSolvers/C_to_F_MG/Make.package
INCLUDE_LOCATIONS += $(BOXLIB_HOME)/Src/LinearSolvers/C_to_F_MG
VPATH_LOCATIONS   += $(BOXLIB_HOME)/Src/LinearSolvers/C_to_F_MG

include $(BOXLIB_HOME)/Src/LinearSolvers/C_CellMG/Make.package
INCLUDE_LOCATIONS += $(BOXLIB_HOME)/Src/LinearSolvers/C_CellMG
VPATH_LOCATIONS   += $(BOXLIB_HOME)/Src/LinearSolvers/C_CellMG

include $(BOXLIB_HOME)/Src/LinearSolvers/F_MG/FParallelMG.mak
INCLUDE_LOCATIONS += $(BOXLIB_HOME)/Src/LinearSolvers/F_MG
VPATH_LOCATIONS   += $(BOXLIB_HOME)/Src/LinearSolvers/F_MG

include $(BOXLIB_HOME)/Src/F_BaseLib/FParallelMG.mak
INCLUDE_LOCATIONS += $(BOXLIB_HOME)/Src/F_BaseLib
VPATH_LOCATIONS   += $(BOXLIB_HOME)/Src/F_BaseLib

vpath %.c   : . $(VPATH_LOCATIONS)
vpath %.h   : . $(VPATH_LOCATIONS)
vpath %.cpp : . $(VPATH_LOCATIONS)
vpath %.H   : . $(VPATH_LOCATIONS)
vpath %.F   : . $(VPATH_LOCATIONS)
vpath %.f   : . $(VPATH_LOCATIONS)
vpath %.f90 : . $(VPATH_LOCATIONS)

all: $(executable)

include $(BOXLIB_HOME)/Tools/C_mk/Make.rules
