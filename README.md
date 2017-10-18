ScalaCheck-Contrib
==================
This repository contains additional features for ScalaCheck that are not part of the main repository. At the moment only a JUnit 4 runner is available.

The project was forked from its original (written by Oscar Renalias) https://github.com/oscarrenalias/scalacheck-contrib
and updated for Scala 2.11/ScalaCheck 1.12 by Matt Gumbley, and published to Maven Central.
Since Matt can only publish under his group id 'org.devzendo', the group of the original
code has been changed to this. The copyright remains Oscar and Accenture - see end of page.


JUnit 4 runner for ScalaCheck
-----------------------------

This is a simple JUnit 4 runner that allows "pure" ScalaCheck tests to be run as part of existing JUnit 4 suites. Properties that hold true will be reported as succesful test cases to JUnit, and properties that falsify will be shown as error test cases by JUnit.

The only change needed in our existing ScalaCheck code is to annotate the class with JUnit's @RunWith annotation, as shown in the example below. The rest of the code is exactly like plain ScalaCheck code, and the property suite can still be run using the Properties.check method, as usual (e.g. from Scala's REPL)

```scala
import org.scalacheck.Prop._
import org.junit.runner.RunWith

@RunWith(classOf[ScalaCheckJUnitPropertiesRunner])
class ScalaCheckTest extends Properties("My ScalaCheck test example") {
	property("first test") = forAll {
		...
	}
}
```

Run the test suite now with the "mvn test" command, which by default uses JUnit as the unit testing framework and JUnit will execute the test suite automatically using ScalaCheck for the property checks.

Getting Started
----------------
With Maven:

        <dependency>
            <groupId>org.devzendo</groupId>
            <artifactId>scalacheck-contrib_2.11</artifactId>
            <version>1.0.0</version>
        </dependency>

With SBT (0.7.x):

```scala
	val scalacheckContrib = "org.devzendo" %% "scalacheck-contrib_2.11" % "1.0.0"
```

Please note that I do not use SBT; the above may not work ;)


Please note that the library is currently only compiled for Scala 2.11.7.

With the plain JAR file:

Get the JAR file from here: http://search.maven.org/remotecontent?filepath=org/devzendo/scalacheck-contrib_2.11/1.0.0/scalacheck-contrib_2.11.jar


License
-------
This code is copyrighted by Accenture, and is released under the Apache 2.0 License: http://www.apache.org/licenses/LICENSE-2.0.html.

Update to modern Scala/Maven is copyright by Matt Gumbley, also under the Apache 2.0 License.
