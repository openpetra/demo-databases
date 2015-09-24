Please find generated sample data that is useful for testing and demoing OpenPetra.

The files can be imported into OpenPetra like this: 
* Login as user SYSADMIN and password CHANGEME (case sensitivity is important!),
* and go to System Manager module, Database, Import&Export, select "Restore database from Backup".

You can also use the server console for importing yml.gz files, the command is i for importing...

The following databases are available:

base.yml.gz
* just 2 users: demo with password demo, and sysadmin with password CHANGEME
* one empty ledger, and most lookup tables filled with some reasonable data.
* this database is delivered with the Standalone installer

demoWith1ledger.yml.gz
* Several donors
* Several workers
* Several key ministries (projects)
* Several fields
* Posted and unposted gift batches
* Posted and unposted invoices

demoMultipleYears.yml.gz
* Similar to demoWith1Ledger, but contains a ledger with 2 closed years plus the current open year

demoWith2ledgers.yml.gz
* same as demoWith1ledger.yml.gz, but with 2 ledgers.
* The second ledger with number 44 has a financial year starting in April

All data is generated with benerator.

These files are the base for our generated databases:
* generatedDataUsedForDemodatabases/*.csv
* You have to copy the .csv files to demodata/generated

to reproduce the databases, run in your configured OpenPetra development environment:

To create a database with one ledger with one year of data:

    nant resetDatabase importDemodata

To create a database with a ledger with several years:

    nant resetDatabase importDemodata -D:operation=ledgerMultipleYears

To add a second ledger:

    nant importDemodata -D:operation=secondLedger

To publish the demo database, run nant startServer startAdmin and use the e command to write the yml.gz file
