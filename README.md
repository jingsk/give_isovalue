# give_isovalue
Given percent density and a cube file, return an appropriate iso-alue for visualizing that much density.

The motivation for this project comes from lack of standard in choosing the threshold for visualizing electron density from a cube file. A typical way to visualize density is to plot volume as isosurfaces with a cutoff value at the isovalue ($\eta$), which a user specify. The volume data in a cube file deoends on normalization and on density localization making the choice of isovalue dependent on each cube file. In visualization programs like VMD, users need to choose an arbritary values to visualize electron densities until they are satisfied with the visual. As the isovalue does not have physical meaning, there is no systematic way to ensure the visual capture sufficient volume/does not visualize noise. This lack of standard could lead to misleading interpretation of results such as over-localized or over-delocalizatiton of electron density.

We hope to standardize visualization by providing a tool to give isovalue given a percent of total density to visualize, a more meaningful metric. We refer an interested reader to this blog by Paul Bourke to learn more about the cube file format: http://paulbourke.net/dataformats/cube/. Briefly, a volume is represented on a discreet grid with a volumetric data per grid point (voxel; a volumetric pixel). An isovalue, given by the user, is the minimum volumetric data below which no data is visualized. 

To obtain the total density ($V_{total}$), we sum over all 3 indices:
$$V_{total}=\sum^{total}_{n1,n2,n3}V(n1, n2, n3)$$.

The density visualized ($V_{shown}$) with isovalue, $\eta$, is
$$V_{shown}=\sum^{total}_{n1,n2,n3}\hat{V}(n1, n2, n3); \eta \leqslant \hat{V}\subset V$$

, and the percent of electron shown is:
$$ratio_{shown}=\frac{V_{total}-V_{shown}}{V_{total}}$$.



