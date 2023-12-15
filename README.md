# MeanderMigrationDTW
Dynamic Time Warping algorithm for quantifying lateral migration of meandering rivers

This is a modified versione of a custom R code developed by Mikhail Titov.
The original code is freely available at http://mlt.github.io/QGIS-Processing-tools/tags/dtw.html along with tutorials. 

The code version available here has been slightly modified to enable the R-script to be chained up and run using the latest versions of QGIS.
The code has been tested and used with QGIS 3.22 Białowieża and R-4.2.2 on Windows 10 Pro on x86_64 chips with standard hardware.

To install R, visit https://cran.r-project.org/bin/windows/base/old/4.2.2/.
Once installed, make sure to update all R packages: 
https://cran.r-project.org/doc/manuals/r-patched/R-admin.html#Updating-packages. 
This might take up to 15 minutes on a "normal" desktop computer.

Then install the "dtw" package: https://dynamictimewarping.github.io/r/
This step should take a couple of minutes at most on a "normal" desktop computer.

To install QGIS, visit: https://qgis.org/it/site/forusers/download.html
Once QGIS is installed, R scripts can be chained up for use in QGIS: 
https://docs.qgis.org/3.4/en/docs/training_manual/processing/r_intro.html

To run the channel migration dtw algorithm using the QGIS, select "R -> Vector Processing -> Channel Migration" from the QGIS Processing tools.
Two input shapefiles are required: 
- one for the "Start" river centerline 
- another for the "End" centerline. 
Note that both centerlines need to be projected in the same coordinate reference system.

The user is then prompted to input:
- "Years": the timestep in years (or fraction of years) between the two centerlines;
- "spar": the Smoothing parameter for a spline. 0 implies no smoothing and should be used when centerlines have already been smoothed.
- "Curvature multiplier": 
  see http://mlt.github.io/QGIS-Processing-tools/posts/2015/03/how-to-find-an-optimal-curvature-threshold/index.html
  and http://mlt.github.io/QGIS-Processing-tools/posts/2015/03/on-effect-of-curvature-multiplier/index.html for details.
- "Step pattern": This sets constraints for DTW algorithm. "symmetricP05" is the default value. See ?dtw details in R.
- "Step": How often do you want migration lines to be apart (in meters).
- "Migration": output shapefile with migration vectors.

Depending on the length of the river centerlines and on the requested "Step" 
the algorithm might take from a few seconds up to some minutes to run 
on a "normal" desktop computer."
