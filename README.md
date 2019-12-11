# HL7 to JSON Converter




Jose A. Ballestero
Caroline Doi
Tim Slanschek
Jonathan Vehaun
Destin Winata

4/19/2019

## Release Notes

In this release we have added the following features:
- Added support for command-line help screen
- Added support for specifying input and output files via the command line
- Added MongoDB support
Install Guide

### Prerequisites
- Gradle
- Java
- MongoDB (See Appendix A)
- This repository

### To Install
- Install the needed prequisites and clone the repository to your computer
- cd into the install directory
- Build the application by running 
./gradlew build
- Run the application by calling
./gradlew run --args="[-h | --help] [-o \<output file path\>] \<input file path\>"

## Appendix A: MongoDB Installation
### Working with MongoDB 

In order to create a MongoDB database first you will need to download it from (https://www.mongodb.com/download-center?lang), after downloading the mongoDB bin file, will you have to add the MongoDB bin folder to the path of that machine. 

### How to set up the Database

Open two command prompts, in one you want to run the mongod command and keep it open, that initializes the database

On the other one you want to run the mongo command, this command prompt will be the one to be used as the main way to work with the database, while the other is just to initialize the database. To create a specific new collection use command db.createCollection(‘name’)

### In order to add files

Run this command in a new command line

Mongoimport --db \<name of your database\> --collection \<name of your collection\> --file “Path to the file” 

To see it go back to the command line with the mongo collections

Type use \<name of your database\> 

Ensure that the collection is there by typing show collections

To see if the file got added successfully type db.\<name of your collection\>.find() this will show you every file and all of the information they have. If it looks very raw you can use find().pretty() to see the actual formatting.

You can see how many files are in the database with db.\<name of your collection\>find().count()

## Querying
Example Hierarchy:
{
    \<attribute\>: {
        \<n1\>: {
            \<n2\>: \<value\>
        }
    }
}
Using ‘:’ signifies equality; i.e. {“id”: 25} will return all documents with “id” attribute of value 25
For nested equalities: db.find(\<attribute\>.\<n1\>.\<n2\> : \<value\>). This will return all documents with “\<attribute\>.\<n1\>.\<n2\>” of value \<value\>.


