---
name: registration-warpfield-workflow
description: Inspect, register, and quality-control 3D microscopy TIFF volumes with GPU Warpfield deformation fields, or apply barcode-matched WarpMaps to Astropy ECSV localization coordinates. Use for image-registration, deformation-field, WarpMap, fiducial-channel, or registered-localization tasks in DNA-FISH and Hi-M workflows.
---

# Registration Warpfield workflow

Use the Registration Warpfield MCP tools for image registration and coordinate correction.

## Image registration

1. Call `warpfield_environment` and stop if the selected CUDA device is unavailable.
2. Inspect the reference and moving volumes with `inspect_image_volume`.
3. Confirm that reference and moving shapes match before registration.
4. Confirm `xybin`, `zbin`, GPU index, reference cycle, moving cycle, and output directory.
5. Use `register_image_volume` for one image or `register_image_directory` for a directory.
6. Inspect the generated HDF5 file with `inspect_warp_map`.
7. Report the registered TIFF, HDF5 WarpMap, overlays, deformation plots, and execution warnings.

Never silently choose a reference image. Never overwrite existing outputs unless the user explicitly requests it.

## Localization correction

1. Inspect the ECSV table with `inspect_localization_table`.
2. Confirm the table includes `Buid`, `Barcode #`, `xcentroid`, `ycentroid`, and `zcentroid`.
3. Inspect representative HDF5 maps and verify their filename cycle identifiers match the table's barcode identifiers.
4. Confirm coordinate units, axis order, XY binning, and Z binning.
5. Write corrections to a new ECSV path with `apply_warp_maps_to_localizations`.
6. Inspect the output table and report corrected row counts and missing barcodes.

## Result format

Report input paths, reference and moving image identities, array shapes, binning, GPU device, generated output paths, WarpMap shape, displacement statistics, localization row counts, warnings, and the recommended QC step.

