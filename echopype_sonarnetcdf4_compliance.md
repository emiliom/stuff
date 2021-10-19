# Plan for SONAR-netCDF4 convention adherence work in 0.6.0

Disruptive changes are preced by the prefixed **(D)**

- **(D)** `Beam` subgroup(s). echopype's move of `Beam` subgroup to a top-level group. Move it back into `Sonar`, as `Sonar/Beams` (or a slightly different name?)
- **(D)** Add a `beam` dimension to `Beam` group
  - For single beam or split-beam, it could be a length-1 explicit dimension or an implicit coordinate (scalar `beam` )
  - For multi-beam, an explicit dimension is required. Currently the EK80 parser generates such a structure, but the dimension is named `quadrant` (WJ: there is an extra dimension quadrant — you can call them separate beams, but since Simrad use quadrant i used that for our first shot though I think it should be probably sector since it is not always 4)
  - EM: It occurs to me now that, in terms of match-up with SONAR-netCDF4, the Beam group in AZFP and EK60 echopype nc/zarr files could be described as having an implicit, single-value `beam` dimension. Single-value dimensions can be implemented interchangeably in a netcdf file either explicitly with the dimension or implicitly (refer to the CF convention). In SONAR-netCDF4, since there is an explicit `beam` dimension, single-beam data would be expected to be stored with beam as a dimension.
  - issue of convention use of "beam" dimension (ie, >1 beams per Beam subgroup? Based on "beam mode" alone?)
- `range_bin` issues
  - `range_bin` is not in the convention, but it's central to the echopype data structure
  - [Currently this coordinate variables doesn't have attributes.](https://github.com/OSOceanAcoustics/echopype/issues/373) Add units, long name, etc
  - small TODO, WJ's "convention vlen" comments. See also [this discussion in the SONAR-netCDF4 github repo](https://github.com/ices-publications/SONAR-netCDF4/issues/28) that directly addresses that aspect of the convention, and potential problems with it
  - > (from WJ) Do I understand it correctly that we will keep this format (hence no disruptive changes) but will at some point provide a converter to go back and forth between the echopype format and the convention (or if the convention change to more similar to what we have, then we can just be consistent with variable names and keep going?)

- **(D)** Rename `time` dimensions and coordinates in `Platform` group, to adhere to the convention naming guideline. `location_time` does not comply; it should be `time1`, `time2`, etc
- Restart the element-by-element compliance check tables
- **Fix current errors/issues with EK60**
  - `Sonar/sonar_serial_number` is empty. See [issue 212](https://github.com/OSOceanAcoustics/echopype/issues/212)
  - Populate `Sonar/sonar_software_name`. Right now it's left blank; see [convert/set_groups_ek60.py#L89](https://github.com/OSOceanAcoustics/echopype/blob/class-redesign/echopype/convert/set_groups_ek60.py#L89) and [issue 210 comment](https://github.com/OSOceanAcoustics/echopype/issues/210#issuecomment-822642399)
  - `Sonar/sonar_model attribute` entry is "ER60". It should be EK60. Currently EK60 `Sonar/sonar_model` is set in [convert/set_groups_ek60.py#L87](https://github.com/OSOceanAcoustics/echopype/blob/class-redesign/echopype/convert/set_groups_ek60.py#L87) as `self.parser_obj.config_datagram['sounder_name']`, so that looks fine, unless the datagram `sounder_name` is parsed incorrectly. See [issue 210 comment](https://github.com/OSOceanAcoustics/echopype/issues/210#issuecomment-821761942)
  - `Provenance > src_filenames` should be a list of strings per the convention, but currently it's a string. It's also mispelled, as it should be `source_filenames`
- **Reassess AZFP compliance, and primary issues**
  - There are many first-order issues!
  - Some of the comments under EK60 also apply to AZFP
- **Improved global attributes**
  - `survey_name` top-level attribute is not in the convention
  - When an attribute is empty (specially global attributes), should it still occur but with a blank value, or be ommitted altogether? Current implementation is inconsistent
  - Add missing core CF attributes (feature_type, cdm, etc), where appropriate
  - Add some useful attributes from ACDD, specially ones involving spatial and temporay bounding boxes; roles; etc; in top-level group? Will improve discoverability.
  - See AcMeta to see if we can define an initial subset of it that ideally follows the ACDD attributes we'd be interested in
  - > (from WJ): Do you think these additions would potentially make their way into later versions of the convention?

- **Go over other relevant discussions and notes, to see if I'm missing anything**
  - Google Drive files (mappings, sample nc files, etc) under [echopype/convention_check](https://drive.google.com/drive/u/0/folders/1MPBRzrehXk9qAt8ZuBjFzR2Xh-0WFXXU)
  - [Document and verify compliance with SONAR-netCDF4 convention #210](https://github.com/OSOceanAcoustics/echopype/issues/210)
  - echopype documentation: [Data format](https://echopype.readthedocs.io/en/stable/data-format.html) and [Why echopype?](https://echopype.readthedocs.io/en/stable/why.html)
  - `conventions/SONAR-netCDF4_compliance.ipynb`: code and file instrospection, and comments I've added there
  - I think I've already captured notes from these sources:
    - `sonar-conventions` Slack channel in `uw-echospace` workspace. Going back to the start of the channel in April '21
    - My hand written notes on the SONAR-netCDF4 report
