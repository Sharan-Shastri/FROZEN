EXEDIR = .
F90 = gfortran
OBJDIR = .
SRCDIR = .
FFLAGS = -O2
LAPACK = -llapack



#
Executables= $(EXEDIR)/Make2DMesh \

#
#
#
Routines = $(OBJDIR)/DEMVar.o $(OBJDIR)/Initialisation.o $(OBJDIR)/READ_DEM.o $(OBJDIR)/CreateSol.o $(OBJDIR)/Metric.o $(OBJDIR)/biquad.o $(OBJDIR)/MeshToElmer.o 

Routines2 = $(OBJDIR)/DEMVar.o  $(OBJDIR)/READ_DEM.o


$(EXEDIR)/read_dem_austfonna: $(SRCDIR)/read_dem_austfonna.f90 $(OBJDIR)/DEMVar.o
	$(F90) $(FFLAGS)  $^ -o $@ 

$(EXEDIR)/Make2DMesh : $(SRCDIR)/Make2DMesh.f90 $(Routines) 
	$(F90) $(FFLAGS)  $^ -o $@ $(LAPACK)


$(EXEDIR)/reduce_dem : $(SRCDIR)/reduce_dem.f90 $(Routines2) 
	$(F90) $(FFLAGS)  $^ -o $@ 


$(OBJDIR)/DEMVar.o : $(SRCDIR)/DEMVar.f90
	$(F90) $(FFLAGS) -c $^ -o $@

$(OBJDIR)/Initialisation.o: $(SRCDIR)/Initialisation.f90 $(OBJDIR)/DEMVar.o
	$(F90) $(FFLAGS) -c $^ -o $@



$(OBJDIR)/READ_DEM.o : $(SRCDIR)/READ_DEM.f90 
	$(F90) $(FFLAGS) -c $^ -o $@


$(OBJDIR)/CreateSol.o : $(SRCDIR)/CreateSol.f90 $(OBJDIR)/DEMVar.o 
	$(F90) $(FFLAGS) -c $^ -o $@

$(OBJDIR)/Metric.o : $(SRCDIR)/Metric.f90 $(OBJDIR)/DEMVar.o 
	$(F90) $(FFLAGS) -c $^ -o $@

$(OBJDIR)/biquad.o : $(SRCDIR)/biquad.f90
	$(F90) $(FFLAGS) $(LAPACK) -c $^ -o $@


$(OBJDIR)/MeshToElmer.o : $(SRCDIR)/MeshToElmer.f90
	$(F90) $(FFLAGS) -c $^ -o $@

