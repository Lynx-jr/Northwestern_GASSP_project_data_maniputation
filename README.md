# Northwestern_GASSP_project_data_maniputation

This personal project stemmed from an issue I encountered while maintaining the Northwestern GASSP (Global COVID-19 Assessment and Surveillance System) project led by Dr. Lori Post. We observed that when North America switched to a weekly reporting pattern during Oct 2022, the infection rate does not look right. Upon investigating a portion of the initial data extraction code (which was written by a former contractor), I discovered that one line of code mistakenly treated the weekly data as daily data and performed a rolling operation, resulting in the distortion of the remaining data.

To rectify this issue and restore the weekly data to its original daily format, I independently delved into interpolation methods. Drawing upon my background in oceanography during college, I found the task relatively straightforward. I stumbled upon a helpful resource at https://coast.nd.edu/jjwteach/www/www/index_30125.html, courtesy of professors from the University of Notre Dame. Among the various interpolation techniques available, I opted for cubic spline interpolation. Although it is not inherently superior to other methods, I personally favor the aesthetic appeal of the resulting curves. (grin)

First, I slice the North America data off from the all_combined file, naming it na_data.
Second, I apply cubic spline interpolation.
Third, I have an old raw data file with daily Canadian data (Canada switched all its data into weekly hence to preserve granularity I had to replace the overlapped time with the old data), then find the common columns, then only keep olddata[common_cols] and newdata[common_cols] that starts right after the old data, and in the end concatenate the common cols.
Fourth and Fifth, depending on where you're using it and if you want a particular time frame, there are two versions of code.

