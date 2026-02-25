## Reference frames and time standards

This page lists the reference frames and time standards used by each microlensing modeling code, with a focus on parallax calculations.
The table below contains the input time system, how time is handled for parallax calculations, and the parallax reference frame (i.e., the observer position center used to compute the parallax displacement).

| Code           | Input time system      | Time handling for parallax | Parallax frame        | Refs. |
|----------------|------------------------|----------------------------|-----------------------|-------|
| BAGLE          | MJD                    | BJD_TDB                    | Heliocentric?         | [1](https://ui.adsabs.harvard.edu/abs/2025arXiv251203364L/abstract) |
| VBM / RTModel  | HJD' (JD' optional)    | Internally JD <-> HJD      | Barycentric           | [2](https://github.com/valboz/VBMicrolensing/blob/main/docs/python/Parallax.md)      |
| MulensModel    | Any (if no parallax)   | BJD_TDB                    | Geocentric (`t0_par`) | [3](https://rpoleski.github.io/MulensModel/MulensModel.mulensdata.html)      |
| pyLIMA         | JD                     | Depends on dataset?        | Geocentric?           | [4](https://pylima.readthedocs.io/en/latest/source/Conventions.html) |
| eesunhong      | ... | | Heliocentric
| muLAN          | HJD                    | MJD_TDB                    | 
| microlux       | ...
| microjax       | ... | | Heliocentric

When retrieving ephemeris, BAGLE, MulensModel and pyLIMA obtain Solar System Barycenter (SSB) position with astropy.coordinates.get_body_barycentric(), which depends on the time scale (tipically BJD_TDB).
The user has to provide BJD times (or at least HJD) for the parallax calculations.
VBM instead uses precomputed ephemeris tables from JPL Horizons (DE441).

Regarding microlensing surveys, OGLE data are typically provided in Julian Date (JD), while MOA and KMTNet commonly use Heliocentric Julian Date (HJD).
*This should be verified and extended to other surveys and space missions.*

Note: Time difference between heliocentric and SSB is ~1 sec.

Note: BJD_TDB stands for Barycentric Julian Date in Barycentric Dynamical Time.
It is a coordinate time defined at the Solar System Barycenter and is the standard time scale used in modern planetary ephemerides. TDB differs from TT by periodic relativistic terms with amplitudes up to ~1.6 milliseconds.

### To-Do List:

- Double checking with code developers
- Make a separate table for survey conventions for `t_0`
<!-- - Write notes about the conventions and how to convert from one another -->
- Check DE430 (default) and more recent kernels, how much they affect the Earth position

<!-- Internal notes (to be deleted...) -->
<!-- Raphael: It seems that in retrieving the ephemeris, everyone is converging to barycentric... -->
<!-- Radek's notes about JPL Horizons output format: -->
<!-- https://github.com/rpoleski/MulensModel/blob/73008fb1ed7f3504fa4ae55e0ecf1257eeb0a83a/documents/Horizons_notes.md -->
<!-- Jessica notes about survey conventions -->
<!-- ``OGLE uses heliocentric (not SSB), MOA uses geocentric JD, KMTNet uses heliocentric.'' -->
<!-- MulensModel notes about astropy's get_body_barycentric() function -->
<!-- Seems that get_body_barycentric depends on time system, but there is no way to set BJD part of BJD_TDB in astropy.Time(). The option *format* above indicates if the first argument of Time() is a float indicating JD or e.g., a string in the form '1999-01-01T00:00:00.123' - this would be value 'fits'. Hence, the user has to provide BJD times (or at least HJD). -->
