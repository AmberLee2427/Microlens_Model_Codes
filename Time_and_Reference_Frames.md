## Reference frames and time standards

This page lists the reference frames and time standards used by each microlensing modeling code, with a focus on parallax calculations.
The table below contains the input time system, how time is handled for parallax calculations, and the parallax reference frame (i.e., the observer position center used to compute the parallax displacement).

| Code           | Input time system      | Time handling for parallax | Parallax frame        | Refs. |
|----------------|------------------------|----------------------------|-----------------------|-------|
| BAGLE          | MJD                    | BJD_TDB                    | Heliocentric?         | [1](https://ui.adsabs.harvard.edu/abs/2025arXiv251203364L/abstract) |
| VBM / RTModel  | HJD' (JD' optional)    | Internally JD <-> HJD      | Barycentric           | [2](https://github.com/valboz/VBMicrolensing/blob/main/docs/python/Parallax.md)      |
| MulensModel    | Any (if no parallax)   | BJD_TDB                    | Geocentric (`t0_par`) | [3](https://rpoleski.github.io/MulensModel/MulensModel.mulensdata.html)      |
| pyLIMA         | JD                     | Depends on dataset?        | Geocentric?           | [4](https://pylima.readthedocs.io/en/latest/source/Conventions.html) |
| eesunhong      | ... | ... | Heliocentric
| muLAN          | HJD                    | MJD_TDB                    | ...
| microlux       | ... | ... | ...
| microjax       | ... | ... | Heliocentric

BAGLE, MulensModel and pyLIMA retrieve Earth position from the Solar System Barycenter (SSB) with the Astropy function `get_body_barycentric()`.
It depends on the time scale (tipically BJD_TDB) provided by the user, which is used to compute the parallax displacement.
VBMicrolensing instead uses precomputed ephemeris tables from JPL Horizons (DE441).
The different kernel compared to the other packages (DE441 vs. DE430) produces a difference in Earth position of ~100 km, which is not responsible for the parallax difference reported in Lu et al. ([2025](https://ui.adsabs.harvard.edu/abs/2025arXiv251203364L/abstract)).

Regarding microlensing surveys, OGLE data are typically provided in Julian Date (JD), while MOA and KMTNet commonly use Heliocentric Julian Date (HJD).
*This should be verified and extended to other surveys and space missions.*

**Note:** Time difference between heliocentric and SSB is ~1 sec.

**Note:** BJD_TDB stands for Barycentric Julian Date in Barycentric Dynamical Time.
It is a coordinate time defined at the Solar System Barycenter and is the standard time scale used in modern planetary ephemerides. TDB differs from TT by periodic relativistic terms with amplitudes up to ~1.6 milliseconds.

### To-Do List:

- Add missing info about eesunhong, muLAN, microlux and microjax
- Double check with code developers
- Make a separate table for survey conventions for `t_0`?
<!-- - Write notes about the conventions and how to convert from one another -->

Last updated: 25 Feb 2026, Raphael
