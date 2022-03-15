# General Description
We provide a preprocessed data set based on the 2019 census data. The data can be directly downloaded here: https://drive.google.com/drive/folders/1Q_YIKvI_OZJVHuZr4SkOs9DtFIgAOqJy?usp=sharing.  

This data was extracted from the census bureau database found at
https://www2.census.gov/programs-surveys/acs/data/pums/2019/1-Year/ (1 year census data), and https://www2.census.gov/programs-surveys/acs/data/pums/2019/5-Year/ (5 year census data).  

Donor: Bargav Jayaraman and Zihao Su, University of Virginia. e-mail: zs3pv@virginia.edu for questions.  

The data records were filtered with conditions that AGEP>16 (age is older than 16 years old) and WKHP>0 (usual hours worked per week in the past 12 months is more than 0).  

The data has 1685316 row records for the 1 year census data and 8199834 row records for the 5 year census data. The data is split into features and labels. To see the data processing methods and the data dictionary, go to the `Features` and `Label` sections. To see how to reproduce the data, go to the `Steps to Reproduce Data` section. Examples usage and benchmarks of the data are demonstrated in `CENSUS_DATA_README.ipynb` jupyter file. To see how to import and use the data, open  and go to the `Usage` section in the jupyter file. To see benchmarks of the training models using the data, go to the `Benchmarks` section in the jupyter file.

# Features
Found in `census_features.p` or `census_features.csv`, the features contain 13 columns, whose values are extracted from the raw census data and processed. Details of each column are listed below in order, along with the processing methods and data dictionary.
- `AGEP`: age in years. Only records with AGEP>16 are included in the dataset. 
- `COW`: class of worker. The values are shifted down by 1, so they start at 0.
	* 0: 'Private For-Profit'
	* 1: 'Private Non-Profit'
	* 2: 'Local Govt'
	* 3: 'State Govt'
	* 4: 'Federal Govt'
	* 5: 'Self-Employed Other'
	* 6: 'Self-Employed Own'
	* 7: 'Unpaid Job'
	* 8: 'Unemployed'
- `SCHL`: education attainment. The values are shifted down by 1, so they start at 0.
	* 0: 'No schooling completed'
	* 1: 'Nursery school, preschool'
	* 2: 'Kindergarten'
	* 3: 'Grade 1'
	* 4: 'Grade 2'
	* 5: 'Grade 3'
	* 6: 'Grade 4'
	* 7: 'Grade 5' 
	* 8: 'Grade 6'
	* 9: 'Grade 7'
	* 10: 'Grade 8'
	* 11: 'Grade 9'
	* 12: 'Grade 10'
	* 13: 'Grade 11'
	* 14: '12th grade - no diploma'
	* 15: 'Regular high school diploma'
	* 16: 'GED or alternative credential'
	* 17: 'Some college, but less than 1 year'
	* 18: '1 or more years of college credit, no degree'
	* 19: 'Associates degree'
	* 20: 'Bachelors degree'
	* 21: 'Masters degree'
	* 22: 'Professional degree beyond a bachelors degree'
	* 23: 'Doctorate degree'
- `MAR`: marital status. The values are shifted down by 1, so they start at 0.
	* 0: 'Married'
	* 1: 'Widowed'
	* 2: 'Divorced'
	* 3: 'Separated'
	* 4: 'Never married'
- `RAC1P`: recoded detailed race code. Alaskan Native and American Indians are combined into a "Native American" class. The values are then replaced by their ranks of the sorted distinct values (in ascending order). Thus, the values start at 0 and are consecutive integers.
	* 0: 'White'
	* 1: 'Black'
	* 2: 'Native American'
	* 3: 'Asian'
	* 4: 'Pacific Islander'
	* 5: 'Some Other Race'
	* 6: 'Two or More Races'
- `SEX`: sex. The values are shifted down by 1, so they start at 0.
	* 0: 'Male'
	* 1: 'Female'
- `DREM`: cognitive difficulty. The 'no' value is changed from 2 to 0, so the values start at 0.
	* 0: 'No'
	* 1: 'Yes'
- `DPHY`: ambulatory difficulty. The 'no' value is changed from 2 to 0, so the values start at 0.
	* 0: 'No'
	* 1: 'Yes'
- `DEAR`: hearing difficulty. The 'no' value is changed from 2 to 0, so the values start at 0.
	* 0: 'No'
	* 1: 'Yes'
- `DEYE`: vision difficulty. The 'no' value is changed from 2 to 0, so the values start at 0.
	* 0: 'No'
	* 1: 'Yes'
- `WKHP`: usual hours worked per week in the past 12 months. Only Records with WKHP>0 are included in the dataset.
- `WAOB`: world area of birth. The values are shifted down by 1, so they start at 0.
	* 0: 'US state'
	* 1: 'PR and US Island Areas'
	* 2: 'Latin America'
	* 3: 'Asia'
	* 4: 'Europe'
	* 5: 'Africa'
	* 6: 'Northern America'
	* 7: 'Oceania and at Sea'
- `ST`: state code. The values are replaced by their ranks of the sorted distinct values (in ascending order). Thus, the values start at 0 and are consecutive integers.
	* 0:'Alabama/AL'
    * 1:'Alaska/AK'
    * 2:'Arizona/AZ'
    * 3:'Arkansas/AR'
    * 4:'California/CA'
    * 5:'Colorado/CO'
    * 6:'Connecticut/CT'
    * 7:'Delaware/DE'
    * 8:'District of Columbia/DC'
    * 9:'Florida/FL'
    * 10:'Georgia/GA'
    * 11:'Hawaii/HI'
    * 12:'Idaho/ID'
    * 13:'Illinois/IL'
    * 14:'Indiana/IN'
    * 15:'Iowa/IA'
    * 16:'Kansas/KS'
    * 17:'Kentucky/KY'
    * 18:'Louisiana/LA'
    * 19:'Maine/ME'
    * 20:'Maryland/MD'
    * 21:'Massachusetts/MA'
    * 22:'Michigan/MI'
    * 23:'Minnesota/MN'
    * 24:'Mississippi/MS'
    * 25:'Missouri/MO'
    * 26:'Montana/MT'
    * 27:'Nebraska/NE'
    * 28:'Nevada/NV'
    * 29:'New Hampshire/NH'
    * 30:'New Jersey/NJ'
    * 31:'New Mexico/NM'
    * 32:'New York/NY'
    * 33:'North Carolina/NC'
    * 34:'North Dakota/ND'
    * 35:'Ohio/OH'
    * 36:'Oklahoma/OK'
    * 37:'Oregon/OR'
    * 38:'Pennsylvania/PA'
    * 39:'Rhode Island/RI'
    * 40:'South Carolina/SC'
    * 41:'South Dakota/SD'
    * 42:'Tennessee/TN'
    * 43:'Texas/TX'
    * 44:'Utah/UT'
    * 45:'Vermont/VT'
    * 46:'Virginia/VA'
    * 47:'Washington/WA'
    * 48:'West Virginia/WV'
    * 49:'Wisconsin/WI'
    * 50:'Wyoming/WY'
    * 51:'Puerto Rico/PR'

After all the column values are processed as described above, all values are divided by the maximum value of their respective column, which normalizes the values to be between 0 and 1. Therefore, the actual values stored in the data files **DO NOT** correspond directly to the data dictionary above. 
 
 # Label
Found in `census_labels.p` or `census_labels.csv`, the labels contain 1 column of value that represents whether a person's total income is at least \$90,000. The value is 1 for records with total income equal to or over \$90,000 (obtained by filtering records through PINCP>=90,000, where PINCP is the total person's income). The value is 0 for records the remaining records.

# Steps to Reproduce Data
The code used to produce the dataset can be found in the `EvaluatingDPML` folder, a submodule cloned from https://github.com/bargavj/EvaluatingDPML. Below are the steps to reproduce the dataset.
1. Assuming python 3 is installed and the terminal is at the project directory, install prerequisites by running `pip3 install -r requirements.txt`.
2. To crawl census data, first create a new folder named `dataset`, then `cd` to the `extra` folder and run `python3 crawl_census_data.py`. The data will be downloaded to the `dataset/census/` folder. By default, the 1 year census data from 2019 will be downloaded. To download the 5 year census data, run `python3 crawl_census_data.py --target_census_data='5year'` instead.
3. Next, to obtain the preprocessed census data, run `python3 preprocess_dataset.py census --preprocess=1`. The preprocessed data will be stored in the `dataset` folder as well.
4. To run a benchmark test of training NN models without performing attacks, go to `evaluating_dpml` folder and run `python3 main.py census --save_data=1` to prepare the data, then run `python3 main.py census --target_model='nn' --target_l2_ratio=1e-4 --benchmark=1`. 
5. To reproduce benchmark results of membership inference attacks, go to `improved_mi` folder and run `./run_experiments.sh census` (Note that this step may take over a day to finish). Then, run `python3 interpret_results.py census --gamma=0.5 --plot='benchmark'` to obtain the results. To explore benchmark results with other test-to-train ratios, try changing the `--gamma` argument value to 0.1, 1, 2, 10. 

# Useful Tools for Experiment Automation
We provide functionalities to make it easy to create and run experiments on custom slices of the census data.  

To create census data files with custom thresholds for high-income label, use `--high_income_threshold` flag to pass in the threshold value. For example, to get data records that use $80,000 as the threshold, run `python3 preprocess_dataset.py census --preprocess=1 --high_income_threshold=80000`.  

To create census data files with custom constraints, use `--constraints` flag to pass in a list of constraints in the format of `<feature column><comparison operator><value>`, separated by `,`. For example, to get data records that have college degrees or higher education and are from the state VA, run `python3 preprocess_dataset.py census --preprocess=1 --constraints='SCHL>=20,ST=46'`. Supported operators include: `=`,`!=`,`>`,`<`,`>=`,`<=`. No space is allowed in the passed in parameter.  

To create census data files with custom features, use `--x` flag to pass in a list of features, separated by `,`. For example, to get data records that use `SCHL`, `MAR`, `AGEP` and `COW` as features, run `python3 preprocess_dataset.py census --preprocess=1 --x='SCHL,MAR,AGEP,COW'`. No space is allowed in the passed in parameter.  

To conveniently manage different custom census data files with data ids, use the `--add_data_id` flag. Data files will have name `<file_name>_<data_id>.<file extension>`. A text document that contains the custom high-income threshold value, constraints, and features will be created with name `census_info_<data_id>.txt`.  

To demonstrate usage of the above features for experiment automation, we provide a full sample experiment script named `run_experiments_sample.sh` in the folder `improved_mi`, where a membership inference experiment is reproduced on a set of custom constraints and features, running from creating and setting up a python environment to preprocessing the dataset, and eventually to producing relevant plots. Within the sample script, a data id is created for each custom condition and is managed internally. To run the script, run `run_experiments_sample.sh census`. To play around with custom high-income thresholds, constraints and features, modify the `HIGH_INCOME_THRESHOLD`, `CONSTRAINT`, and `XS` variables in the script.
