# Quality Assured Information Extraction from Historical Address Books for Knowledge Graph Construction

This repository contain the Jupyter Notebooks (MA1-MA10) from the master's thesis 'Quality Assured Information Extraction
from Historical Address Books for Knowledge Graph Construction'.

The workflow was in the following order:

**MA1_reconstructing.ipynb**:
- input: all OCRed transcripts
- this script corrects linebreaks, common OCR mistakes, add missing white spaces, correct common house florr mistakes,..
- output: 2_recon_new_address_book.txt

**MA2_AddAddress.ipynb**
- input: 2_recon_new_address_book.txt
- this scripts adds the missing house numbers and streets infront of entries
- output: 2_Full_address_book.txt

**MA3_segmentation.ipynb**
- input: 2_Full_address_book.txt
- this script segments entries into person entries, company entries and undefined entries (trash)
- output person entries: 2_persons1.txt
- output company entries: 2_companies.txt

**MA4_Creating_Person_DF.ipynb**
- input: 2_persons1.txt
- create dataframe from the extracted person entries
- output: 2_person_df.csv

**MA5_Creating_Company_DF.ipynb**
- input: 2_companies.txt
- create dataframe from the extracted company entries
- output: 2_company_df.csv

**MA6_LevenshteinStreet.ipynb**
- input: 2_person_df.csv, 2_company_df.csv, street reference vocabulary (in files)
- normalization of street names in person and company dataframe
- output: 2_person_df_str.csv, 2_person_df_str_clean.csv, 2_company_df_str.csv, 2_company_df_clean.csv, Unknown Steetnames.txt

**MA7_LevenshteinOccupation.ipynb**
- input: 2_person_df_str_clean.csv, occupation reference vocabulary (in files)
- normalization of occupations in person df
- output: 2_person_df_str_occ.csv, 2_person_df_str_occ_clean.csv

**MA8_Assign_IRI.ipynb**
- input: 2_person_df_str_occ_clean.csv, 2_company_df_clean.csv
- assigning IRIs to the entities
- output: 2_person_df_IRI.csv, 2_company_df_IRI.csv

**MA_Create_DF_from_XML.ipynb**
- input: alto XML files
- create dataframe with coordinates from alto XML files
- output: Coordinates_df.csv

**MA9_AddXMLCoordinates.ipynb**
- input: 2_person_df_IRI.csv, 2_company_df_IRI.csv, Coordinates_df.csv
- adding alto coordinate references to last names, occupations and street names
- output: 2_person_df_fin.csv, 2_company_df_fin.csv

**MA10_AddingToOntology.ipynb**
- input: person_df_fin_Abgabe.csv, company_df_fin_Abgabe.csv (manuell corrected dfs), RDF.owl (in files)
- adding the persons and companies to ontology
- output: final KG AddressBook1908_KG.ttl

All outputs of the notebooks are always stored in the Outputs file.

Additional to the python scripts, the repository contains the SPARQL queries of the use case scenarios in SPARQL Queries.ipynb.
In the Outputs file, also the final NA-KG and the RDF.owl file can be found.


