# Cobol unit testing framework for mainframe programs

The goal of the project is to enable isolated unit testing of individual paragraphs in Cobol programs in a standalone environment with no connection to a zOS system.

Please see [the wiki](https://github.com/neopragma/cobol-unit-test/wiki/) for more information.

## Notice

This is the current version used in Bankdata, Denmark. 

We are no longer doing feature updates, as we are supporting COBOL-Check on the Open Mainframe Project: https://github.com/openmainframeproject/cobol-check 
Our long term goal is to move to COBOL-Check.
We are doing bugfixes for this fork, when we find them.

## Changes from master
### Features:
* Added section mocking.
* Validating more numbers, pic s9(8) is no longer the limit.
* Removed the z/OS version, as it is a very minor fix to use the pc version. Added description of how to fix it.
* All mocks can now contain more mocked lines.
* Added eyecatchers surrounding inserted code, for use with gathering code coverage info.
* Works with mixed case input in both COBOL and test source.
* Updated CALL and EXEC CICS* mocking to work in same way as SECTION and paragraph mocking. 
* Improved reporting with more data about the check and progress.
* Increased mock count to 50.

### Bugfixes:
* Avoid infinite loops when missing . at end of testsuite file.
* Comments in area A of the COBOL program no longer breaks the unit test.
* Resets mock counters between testcases.
* Handling of IN structures in expect statements.
* Handling very long IN structures in expect statements.
* Handling of expect statements that span multiple lines.
* Handling of arrays in expect statements.
* Using max value as end point, when traversing occurs structures containing lines of code, instead of relying on spaces as end marker.
* Multi mock issue from sfauvel.
* fix parsing of multiline SELECT statements without FILE STATUS from mmitch.
* Fixed error caused by END-EXEC not being on position 7, in tested program source.
* Fixed errors in verify mock call.
* Fixed call handling, so a call will terminate at other COBOL reserved words, and not just . or END-CALL.
* Fixed token gathering, so it will correctly pick up tokens like: "Hello 'World'".
* Fixed so you can have a period in a COBOL comment, without the unit test breaking.
* Fixed so you can use unit test keywords like "expect" in testcase or testsuite description. 
* Improved handling of . as section or paragraph end.
* Enable several spaces between section name and section tag.
* Section names of 30 chars now supported.
* Enabled using characters beyond 72 in the testcase file.
* Handling of * was improved
* Section names can now contain "copy".
* Added error when trying to verify unmocked section/paragraph.
* Fixed so mocked calls without end-call does not assume that the next COBOL line is part of the mock.

### Other changes:
* Fixed a lot of warnings and performance issues with the z/OS COBOL compiler.
* Many refactorings for easy of maintenance.
* Removed the usage of PERFORMED keyword, as it was superflouos.

Note: CICS mocking only uses the first two CICS commands as keywords, so it is not possible to mock two very similar CICS commands in the same testsuite.
