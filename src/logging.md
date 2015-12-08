Logging
=======

Logging PHPUnit can produce several types of logfiles.

Test Results (XML) {#logging.xml}
==================

The XML logfile for test results produced by PHPUnit is based upon the
one used by the [JUnit task for Apache
Ant](http://ant.apache.org/manual/Tasks/junit.html). The following
example shows the XML logfile generated for the tests in `ArrayTest`:

    <?xml version="1.0" encoding="UTF-8"?>
    <testsuites>
      <testsuite name="ArrayTest"
                 file="/home/sb/ArrayTest.php"
                 tests="2"
                 assertions="2"
                 failures="0"
                 errors="0"
                 time="0.016030">
        <testcase name="testNewArrayIsEmpty"
                  class="ArrayTest"
                  file="/home/sb/ArrayTest.php"
                  line="6"
                  assertions="1"
                  time="0.008044"/>
        <testcase name="testArrayContainsAnElement"
                  class="ArrayTest"
                  file="/home/sb/ArrayTest.php"
                  line="15"
                  assertions="1"
                  time="0.007986"/>
      </testsuite>
    </testsuites>

The following XML logfile was generated for two tests, `testFailure` and
`testError`, of a test case class named `FailureErrorTest` and shows how
failures and errors are denoted.

    <?xml version="1.0" encoding="UTF-8"?>
    <testsuites>
      <testsuite name="FailureErrorTest"
                 file="/home/sb/FailureErrorTest.php"
                 tests="2"
                 assertions="1"
                 failures="1"
                 errors="1"
                 time="0.019744">
        <testcase name="testFailure"
                  class="FailureErrorTest"
                  file="/home/sb/FailureErrorTest.php"
                  line="6"
                  assertions="1"
                  time="0.011456">
          <failure type="PHPUnit_Framework_ExpectationFailedException">
    testFailure(FailureErrorTest)
    Failed asserting that &lt;integer:2&gt; matches expected value &lt;integer:1&gt;.

    /home/sb/FailureErrorTest.php:8
    </failure>
        </testcase>
        <testcase name="testError"
                  class="FailureErrorTest"
                  file="/home/sb/FailureErrorTest.php"
                  line="11"
                  assertions="0"
                  time="0.008288">
          <error type="Exception">testError(FailureErrorTest)
    Exception:

    /home/sb/FailureErrorTest.php:13
    </error>
        </testcase>
      </testsuite>
    </testsuites>

Test Results (TAP) {#logging.tap}
==================

The [Test Anything Protocol (TAP)](http://testanything.org/) is Perl's
simple text-based interface between testing modules. The following
example shows the TAP logfile generated for the tests in `ArrayTest`:

    TAP version 13
    ok 1 - testNewArrayIsEmpty(ArrayTest)
    ok 2 - testArrayContainsAnElement(ArrayTest)
    1..2

The following TAP logfile was generated for two tests, `testFailure` and
`testError`, of a test case class named `FailureErrorTest` and shows how
failures and errors are denoted.

    TAP version 13
    not ok 1 - Failure: testFailure(FailureErrorTest)
      ---
      message: 'Failed asserting that <integer:2> matches expected value <integer:1>.'
      severity: fail
      data:
        got: 2
        expected: 1
      ...
    not ok 2 - Error: testError(FailureErrorTest)
    1..2

Test Results (JSON) {#logging.json}
===================

The [JavaScript Object Notation (JSON)](http://www.json.org/) is a
lightweight data-interchange format. The following example shows the
JSON messages generated for the tests in `ArrayTest`:

    {"event":"suiteStart","suite":"ArrayTest","tests":2}
    {"event":"test","suite":"ArrayTest",
     "test":"testNewArrayIsEmpty(ArrayTest)","status":"pass",
     "time":0.000460147858,"trace":[],"message":""}
    {"event":"test","suite":"ArrayTest",
     "test":"testArrayContainsAnElement(ArrayTest)","status":"pass",
     "time":0.000422954559,"trace":[],"message":""}

The following JSON messages were generated for two tests, `testFailure`
and `testError`, of a test case class named `FailureErrorTest` and show
how failures and errors are denoted.

    {"event":"suiteStart","suite":"FailureErrorTest","tests":2}
    {"event":"test","suite":"FailureErrorTest",
     "test":"testFailure(FailureErrorTest)","status":"fail",
     "time":0.0082459449768066,"trace":[],
     "message":"Failed asserting that <integer:2> is equal to <integer:1>."}
    {"event":"test","suite":"FailureErrorTest",
     "test":"testError(FailureErrorTest)","status":"error",
     "time":0.0083680152893066,"trace":[],"message":""}

Code Coverage (XML) {#logging.codecoverage.xml}
===================

The XML format for code coverage information logging produced by PHPUnit
is loosely based upon the one used by
[Clover](http://www.atlassian.com/software/clover/). The following
example shows the XML logfile generated for the tests in
`BankAccountTest`:

    <?xml version="1.0" encoding="UTF-8"?>
    <coverage generated="1184835473" phpunit="3.6.0">
      <project name="BankAccountTest" timestamp="1184835473">
        <file name="/home/sb/BankAccount.php">
          <class name="BankAccountException">
            <metrics methods="0" coveredmethods="0" statements="0"
                     coveredstatements="0" elements="0" coveredelements="0"/>
          </class>
          <class name="BankAccount">
            <metrics methods="4" coveredmethods="4" statements="13"
                     coveredstatements="5" elements="17" coveredelements="9"/>
          </class>
          <line num="77" type="method" count="3"/>
          <line num="79" type="stmt" count="3"/>
          <line num="89" type="method" count="2"/>
          <line num="91" type="stmt" count="2"/>
          <line num="92" type="stmt" count="0"/>
          <line num="93" type="stmt" count="0"/>
          <line num="94" type="stmt" count="2"/>
          <line num="96" type="stmt" count="0"/>
          <line num="105" type="method" count="1"/>
          <line num="107" type="stmt" count="1"/>
          <line num="109" type="stmt" count="0"/>
          <line num="119" type="method" count="1"/>
          <line num="121" type="stmt" count="1"/>
          <line num="123" type="stmt" count="0"/>
          <metrics loc="126" ncloc="37" classes="2" methods="4" coveredmethods="4"
                   statements="13" coveredstatements="5" elements="17"
                   coveredelements="9"/>
        </file>
        <metrics files="1" loc="126" ncloc="37" classes="2" methods="4"
                 coveredmethods="4" statements="13" coveredstatements="5"
                 elements="17" coveredelements="9"/>
      </project>
    </coverage>

Code Coverage (TEXT) {#logging.codecoverage.text}
====================

Human readable code coverage output for the command-line or a text file.
The aim of this output format is to provide a quick coverage overview
while working on a small set of classes. For bigger projects this output
can be useful to get an quick overview of the projects coverage or when
used with the `--filter` functionality. When used from the command-line
by writing to `php://stdout` this will honor the `--colors` setting.
Writing to standard out is the default option when used from the
command-line. By default this will only show files that have at least
one covered line. This can only be changed via the `showUncoveredFiles`
xml configuration option. See ?. By default all files and their coverage
status are shown in the detailed report. This can be changed via the
`showOnlySummary` xml configuration option.