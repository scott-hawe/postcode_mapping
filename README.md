Project objective: Using a list of hospitals, map the closest hospital to each patient based on postcodes.

To calculate distances between two postcodes, the latitude and longitude values are first calculated which are used in the distance calculation. Python scripts were used to process the data.

The Distance Matrix and Geocoding APIs were used to calculate coordinates and distances. The scripts are separated into separate notebooks to ensure that no patient identifiable information is present when calling the API.

A map is currently produced both using folium and in Power BI until it is decided which is the better option.

The notebooks are as follows:

	1. data_cleaning
		a. Ingests the SPAH raw tables report which needs to be downloaded from BOXI.
		b. Script cleans this data and separates the patient information from the postcodes.
		c. Exports the two pieces of data to excel files: 'patient_data.xlsx' and 'patient_postcodes_data.xlsx'
	2. mapping_coordinates_google
		a. Ingests 'patient_postcodes_data.xlsx'.
		b. Ingests 'hospital_postcodes.xlsx'
		c. Retrieves latitude and longitude coordinates for each patient and hospital postcode.
		d. Iterates through each hospital postcode, calculating the distance between each patient postcode and returns the name and distance of the hospital closest to each patient.
		e. The distance format is in metres by default so a further calculation is performed to return distance in miles.
		f. Exports the list of patient postcodes along with nearest hospital information to 'nearest_hospitals.xlsx'
	3. producing_map
		a. Ingests 'nearest_hospitals.xlsx' and 'hospital_postcodes.xlsx'
		b. Defines unique map marker icons per each hospital
		c. Produces a folium map, plotting a marker for each patient postcode corresponding to the nearest hospital.
	4. data_merge_export
		a. Ingests 'patient_data.xlsx' and 'nearest_hospitals.xlsx'
		b. Merges the two datasets back together on the postcode column
    c. Exports to 'patient_hospitals_merged.xlsx' for use in Power BI.

