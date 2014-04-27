##################################### STEP 1 ##############################################

subject_test<-read.table('UCI HAR Dataset/test/subject_test.txt')
X_test<-read.table('UCI HAR Dataset/test/X_test.txt')
y_test<-read.table('UCI HAR Dataset/test/y_test.txt')

test_df=cbind(subject_test,y_test,X_test)

subject_train<-read.table('UCI HAR Dataset/train/subject_train.txt')
X_train<-read.table('UCI HAR Dataset/train/X_train.txt')
y_train<-read.table('UCI HAR Dataset/train/y_train.txt')

train_df=cbind(subject_train,y_train,X_train)

all_df=rbind(train_df,test_df)

##################################### STEP 2 ##############################################

####get the list of features
feature_names<-read.table('UCI HAR Dataset/features.txt')
### add the subject and activity id to the begining
all_names=c("subject","activity_id",as.vector(feature_names$V2))

colnames(all_df)<-all_names
#### finding the coloumn numbers that have the "mean" and "std" in their names
mean_ind<-grepl("mean",names(all_df))
std_ind<-grepl("std",names(all_df))

mean_subset<-all_df[,mean_ind]
std_subset<-all_df[,std_ind]

mean_std_subset<-cbind(all_df[,1:2],mean_subset,std_subset)


##################################### STEP 3 & 4 ##############################################
## read the activities list
activity_labels<-read.table("UCI HAR Dataset/activity_labels.txt")
#edit the names of coloumns in dataframe
colnames(activity_labels)<-c("activity_id","activity")

###merging results
labeled_mean_std_subset <- merge(activity_labels,mean_std_subset)



##################################### STEP 5 ##############################################
###aggregating all other variables based on activity and subject
aggr_df<-aggregate(.~activity+subject,data=labeled_mean_std_subset,FUN=mean)

#writing results
write.table(aggr_df,file="aggrgated.txt")
