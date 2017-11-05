# martian_2017
#Assignment 01 - Unix Script
#Shell Script will Create 10000 files, 2000 rows and 50 Columns

#!/bin/sh

#Script to create 10,000 Files, 2000 Rows and 50 Columns

#set different Column, row and file Counter Variables to track
colcnt=1
rowcnt=1
filecnt=1

cleanup()	#remove temp files & earlier files
	{
		rm foo* Assignment*
	}

#Create the 50 rows before converting to Columns

createColumns()
	{
		while [[ “$colcnt” –le 50 ]]
		do
			echo column_$colcnt >> foo
			colcnt=$((colcnt+1))
		done	

#convert rows to 50 Columns
Awk ‘{printf “%s\t”, $1}’ foo > foo.temp
echo “***50 Columns Created***”
}

#Create 2000 rows of the previous content
createFile()
	{
		newcnt=$1
		rowcnt=1
		while [[ “$rowcnt –le 2000 ]]
		do
			cat foo.temp >> Assignment_fileShenoy_$newcnt.out
			rowcnt=$((rowcnt+1))
			echo “\n “ >> Assignment_fileShenoy_$newcnt.out	
		done
		echo “ ***created file Assignment_fileShenoy_$newcnt.out  Successful*** ”
}

#main process 
cleanup
createColumns
		while [[ “$filecnt –le 10000 ]]
		do
			createFile $filecnt
			filecnt=$((filecnt+1))
		done
echo “ THE END”
