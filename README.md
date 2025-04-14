# CBT028
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alizon Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 028 IS A SET OF CLISTS TO CONVERT A LIST OF DATASET       *   FILE 028
//*           NAMES TO DISK-TO-TAPE BACKUP JCL.                     *   FILE 028
//*                                                                 *   FILE 028
//*           THE FOLLOWING IS WHAT THIS CLIST PDS CAN DO FOR       *   FILE 028
//*           YOU.  THIS FILE IS NOW IN IEBUPDTE SYSIN FORMAT.      *   FILE 028
//*                                                                 *   FILE 028
//*           This file has now been converted to FB, LRECL=80      *   FILE 028
//*                                                                 *   FILE 028
//*                *****      BACKEMUP      *****                   *   FILE 028
//*                                                                 *   FILE 028
//*              FUNCTION OF CLISTS:                                *   FILE 028
//*                 CONVERT A LIST OF DATASET NAMES TO              *   FILE 028
//*                 DISK-TO-TAPE BACKUP JCL.                        *   FILE 028
//*                                                                 *   FILE 028
//*              READ THE MEMBERS CALLED $$$DOC, $$$DOC1,           *   FILE 028
//*                                      $$$DOC2 and $$$DOC3.       *   FILE 028
//*                                                                 *   FILE 028
//*       >>>>   You will have to modify these CLISTs to            *   FILE 028
//*       >>>>   generate JCL that is appropriate to run            *   FILE 028
//*       >>>>   at your installation.                              *   FILE 028
//*                                                                 *   FILE 028
//*              SHORT DESCRIPTION:                                 *   FILE 028
//*                                                                 *   FILE 028
//*                 THIS FAMILY OF CLISTS SOLVES AN OLD,            *   FILE 028
//*                 NAGGING PROBLEM OF IBM PROGRAMMERS,             *   FILE 028
//*                 NAMELY, THAT OF BACKING UP A LARGE NUMBER       *   FILE 028
//*                 OF PDS'ES AND SEQUENTIAL DATASETS TO TAPE.      *   FILE 028
//*                 THE USUAL WAYS OF DOING THIS REQUIRES           *   FILE 028
//*                 SETTING UP A PROC, AND CODING A LARGE           *   FILE 028
//*                 NUMBER OF EXECUTIONS OF THE PROC, FOR           *   FILE 028
//*                 DIFFERENT DATASETS.  YOU HAVE TO KEEP TRACK     *   FILE 028
//*                 OF THE FILE NUMBERS ON TAPE, AND IT'S A         *   FILE 028
//*                 BIG PAIN IN THE (YOU FILL IN THE BLANK),        *   FILE 028
//*                 AT ITS EASIEST.                                 *   FILE 028
//*                                                                 *   FILE 028
//*                 WITH "BACKEMUP" CLISTS YOU JUST HAVE TO         *   FILE 028
//*                 MAKE A LIST OF THE DATASETS ON A                *   FILE 028
//*                 CARD-IMAGE FILE, RUN A CLIST AGAINST THE        *   FILE 028
//*                 LIST, AND IN A FEW SECONDS, YOU HAVE YOUR       *   FILE 028
//*                 BACKUP JCL !                                    *   FILE 028
//*                                                                 *   FILE 028
//*              FURTHER HELP AND DESCRIPTION:                      *   FILE 028
//*                                                                 *   FILE 028
//*                 PLEASE SEE MEMBER TSOBATV FOR GREAT             *   FILE 028
//*                 ASSISTANCE IN BACKING UP PO AND PS              *   FILE 028
//*                 DATASETS ON A GIVEN VOLUME.  OUTPUT OF          *   FILE 028
//*                 THIS JOB IS CLOSE TO THE FORMAT USED FOR        *   FILE 028
//*                 INPUT TO THE CLIST CALLED "GENVOL".  ONLY       *   FILE 028
//*                 MINOR MASSAGING WITH ISPF EDIT IS               *   FILE 028
//*                 NECESSARY.  "VTOC" PGM FOUND ON CBT TAPE -      *   FILE 028
//*                 FILE 112.                                       *   FILE 028
//*                                                                 *   FILE 028
//*                 JEFF BROIDO WROTE THE ORIGINAL CLIST,           *   FILE 028
//*                 GENUNLD.  I HAVE MODIFIED HIS ORIGINAL          *   FILE 028
//*                 VERSION FOR SEVERAL OF MY PURPOSES, AND HAVE    *   FILE 028
//*                 WRITTEN ANOTHER ONE, GENPOPS, THAT ADDED THE    *   FILE 028
//*                 CAPABILITY OF DUMPING SEQUENTIAL DATASETS       *   FILE 028
//*                 AFTER DOING THE PDS'ES.                         *   FILE 028
//*                                                                 *   FILE 028
//*                 THE THREE CLISTS, GENPOPS, GENPOPSF, AND        *   FILE 028
//*                 GENPOPST, PRODUCE SIMILAR RESULTS, EXCEPT       *   FILE 028
//*                 THAT FOR THE SEQUENTIAL COPIES, GENPOPST        *   FILE 028
//*                 USES THE PROGRAM FTL (SOURCE CODE INCLUDED      *   FILE 028
//*                 HERE).                                          *   FILE 028
//*                                                                 *   FILE 028
//*                 THE GENPOPS AND GENPOPSF CLISTS GENERATE JCL    *   FILE 028
//*                 WHICH USES PROGRAMS SEQCPY AND SEQCPYF TO DO    *   FILE 028
//*                 THE SEQUENTIAL DATASET COPIES.  SEQCPY AND      *   FILE 028
//*                 SEQCPYF LOAD MODULES ARE INCLUDED HERE IN       *   FILE 028
//*                 MEMBER SEQCPY AS AN XMITTED LOAD LIBRARY.       *   FILE 028
//*                                                                 *   FILE 028
//*                 THE CLISTS USE THE TAPEMAP PROGRAM (ORIGINAL    *   FILE 028
//*                 WAS FROM UCLA) WHICH IS ON CBT TAPE FILE        *   FILE 028
//*                 299.  THEY ALSO USE THE INIMITABLE PDS          *   FILE 028
//*                 PROGRAM FROM FILE 182.                          *   FILE 028
//*                                                                 *   FILE 028
//*                 A LOAD MODULE LIBRARY OF THE TAPEMAP PROGRAM    *   FILE 028
//*                 IN XMIT FORMAT IS INCLUDED HERE AS MEMBER       *   FILE 028
//*                 TAPEMAP@.                                       *   FILE 028
//*                                                                 *   FILE 028
//*                 PLEASE NOTE THAT IN ORDER TO RUN THE TAPEMAP    *   FILE 028
//*                 PROGRAM WHOSE JCL IS PRODUCED AT THE END OF     *   FILE 028
//*                 THE JOB HERE, YOU HAVE TO HAVE BLP=YES          *   FILE 028
//*                 CODED IN YOUR JES2PARM MEMBER IN PARMLIB.       *   FILE 028
//*                 IT WON'T WORK WITH BLP=NO.  YOU CAN SET THIS    *   FILE 028
//*                 OPTION TEMPORARILY BY ENTERING (ON THE CONSOLE) *   FILE 028
//*                                                                 *   FILE 028
//*                 $TJOBCLASS(B),BLP=YES                           *   FILE 028
//*                                                                 *   FILE 028
//*                 IF FOR EXAMPLE, YOUR JOB IS RUNNING IN CLASS=B. *   FILE 028
//*                                                                 *   FILE 028
```
