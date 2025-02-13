<div style="text-align: center;">

### SFNI_Spanish_Forest_National_Inventory-ready_to_use

---

Tree and plot data from the SFNI ready to use on R

# ***Spanish Forest National Inventory {R}eady to use***

</div>

## :file_folder: Folder Content

- 📜 `0.0_support_data_report.r` `0.0_support_plot_functions.r` `0.0_support_tree_functions.r`
	- :bulb: *purpose*: support functions to create a data report and calculate variables related with both trees and plots
	- :floppy_disk: :arrow_right: :computer: *input*: None
	- :computer: :arrow_right: :floppy_disk: *output*: None
- 📜 `0.1_sfni_harmonisation.r`
	- :bulb: *purpose*: it uses the original datasets to merge information for different tables, rename columns, fix errors in the original data and group the 3 SFNI editions in a single tree and plot data set
	- :floppy_disk: :arrow_right: :computer: *input*: `1_data/1_raw/IFN2/*` `1_data/1_raw/IFN3/*` `1_data/1_raw/IFN4/*`
	- :computer: :arrow_right: :floppy_disk: *output*: temporal datasets with variables not used in the beginning (`1_data/2_processed/tmp/*`) and harmonised data set (`1_data/2_processed/0.1_sfni_harmonised.rdata`)
- 📜 `0.2_sfni_forest_data.r`
	- :bulb: *purpose*: code to calculate basic tree and plot variables with some forest meaning like the expansion factor and plot density
	- :floppy_disk: :arrow_right: :computer: *input*: harmonised data set (`1_data/2_processed/0.1_sfni_harmonised.rdata`)
	- :computer: :arrow_right: :floppy_disk: *output*: previous dataset with additional forest variables (`1_data/2_processed/0.2_sfni_forest_data.rdata`)
- 📜 `0.3.0_sfni_position_data` `0.3.1_explore_plot_distribution` `0.3.2_sfni_corrected_position_data`
	- :bulb: *purpose*: code developed to calculate plot and tree position variables (like latitude and longitude) based on the original data. After finding mistakes in some plots they were corrected is possible (`0.3.1`) and the process was run again (`0.3.2`) with some adaptations
	- :floppy_disk: :arrow_right: :computer: *input*: already processed forest data (`1_data/2_processed/0.2_sfni_forest_data.rdata`)
	- :computer: :arrow_right: :floppy_disk: *output*: dataset with forest and position data (`1_data/2_processed/0.3.2_sfni_corrected_position_data.rdata`)
- 📜 `0.4.0_climatic_classification` 
	- :bulb: *purpose*: code developed to assign climatic variables by geographic regions to each plot. As climatic variables are obtained from different datasets, variables are names with a prefix referred to the original data source:
		- *fito*: data obtained from fitoclimatic regions (*Mapa de Subregiones Fitoclimáticas de España Peninsular y Balear*, accesible [here](https://www.miteco.gob.es/es/biodiversidad/servicios/banco-datos-naturaleza/informacion-disponible/mapa_subregiones_fitoclim_descargas.html))
		- *biogeo*: data obtained from biogeographic regions (*Regiones Biogeográficas de España*, accesible [here](https://www.miteco.gob.es/es/cartografia-y-sig/ide/descargas/biodiversidad/regiones-biogeograficas.html))
		- *veget*: data obtained from vegetation series maps (*Mapa de Series de Vegetación*, accesible [here](https://www.miteco.gob.es/es/biodiversidad/servicios/banco-datos-naturaleza/informacion-disponible/memoria_mapa_series_veg_descargas.html))
	- :floppy_disk: :arrow_right: :computer: *input*: already corrected position data (`1_data/2_processed/0.3.2_sfni_corrected_position_data.rdata`)
	- :computer: :arrow_right: :floppy_disk: *output*: dataset with forest and position data (`1_data/2_processed/0.4.0_climatic_classification.rdata`)
- 📜 `0.4.1.worldclim_climate_data` 
	- :bulb: *purpose*: code developed to extract climate data for each plot using WorldClim database and functions already created to extract information by plot location in *WGS84* 
	- :floppy_disk: :arrow_right: :computer: *input*: already corrected position data (`1_data/2_processed/0.3.2_sfni_corrected_position_data.rdata`)
	- :computer: :arrow_right: :floppy_disk: *output*: different datasets are provided:
		- *historic monthly climate data (tmax, tmean, tmin, prec, Martonne)*: `1_data/2_processed/0.4.1.sfni_historic_monthly_climate_data.rdata` in a single file and `1_data/2_processed/0.4.1/` folder in several files with lower weight
		- *historic yearly climate data (tmax, tmean, tmin, prec, Martonne)*: `0.4.1.sfni_historic_yearly_climate_data.rdata`
		- *historic climate averaged for 70 years period, from 1951 to 2021 (tmax, tmean, tmin, prec, Martonne)*: `0.4.1.sfni_70years_period_climate_data.rdata`
		-  *historic climate averaged for 20 years period, from 2000 to 2020 (tmax, tmean, tmin, prec, Martonne)*:  `0.4.1.sfni_2000-2020_period_climate_data.rdata`
		- *future climate data averaged on 20 years period (2020-2040, 2040-2060, 2060-2080, 2080-2100) for an specific SSPs (1, 2, 3 and 5) using MIROC6 model (tmax, tmean, tmin, prec, Martonne)*: `0.4.1.sfni_future_climate_data_MIROC6_SSPx.rdata`
		- *all the previous data in just one file:* `0.4.1.worldclim_climate_data.rdata
		- ⚠ Some files are too large to be uploaded to GitHub. Consider contacting us to receive them through a different channel.
- 📜 `1.0_hd_support_functions`
	- :bulb: *purpose*: support functions to manage data after harmonisation
	- :floppy_disk: :arrow_right: :computer: *input*: None
	- :computer: :arrow_right: :floppy_disk: *output*: None
- 📜 `1.1_sfni_data_merge_and_report.r`
	- :bulb: *purpose*: load all the previous data already harmonised, merge them and create a data report
	- :floppy_disk: :arrow_right: :computer: *input*: already processed and harmonised data (`1_data/2_processed/9.0.2_sfni_forest_data.rdata`, `1_data/2_processed/0.4.0_climatic_classification.rdata`, `1_data/2_processed/0.3.2_sfni_corrected_position_data.rdata`)
	- :computer: :arrow_right: :floppy_disk: *output*: merged data with some of the most useful columns (`1_data/2_processed/1.1_sfni_clean_data.rdata`) and with all the columns except climate from WorldClim (`1_data/2_processed/1.1_sfni_all_data.rdata`)
  
  :warning: :scroll: Remember to update the script paths in your working directory if you plan to use that code