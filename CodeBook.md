Step 1: In this step code reads training data set and test data sets. Each one of these data sets contain three different files, these files are merged to eachother and saved into "test_df" and "train_df" data frames, finally these data frames are merged and saved in "all_df".

Step 2: In this step code reads "features.txt" file, then adds "subject" and "activity_id" to them and these all together create a vector called "all_names" which is used to name columns of "all_df" data frame. Then code finds the subset of data which has "mean" in their column name and "std" in their column name. Then these two subsets are combined to "mean_st_subset" dataframe.

Step 3 & 4: In this step the "activity_lables" file is read and then "activity_id" and "activity" are added as its column names. Then this data-frame is merged to the data frame created in step 2, i.e. "mean_std_subset".

Step 5: In this step the data is agregated according subject and activity and the result is written in "aggregated.dataframe"
