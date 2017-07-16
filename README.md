# graphviz-java-p2
P2 update site for graphviz-java.

**Update site location:** https://kris7t.github.io/graphviz-java-p2/repository/

Use the update site located at https://kris7t.github.io/graphviz-java-p2/repository/ to install the _graphviz-java Feature_ (optionally with sources) that allows using [graphviz-java](https://github.com/nidi3/graphviz-java) from an Eclipse RCP environment. The repository also contains the _J2V8 Feature_ to also install [J2V8](https://github.com/eclipsesource/J2V8), the backend used by graphviz-java to run the Javascript version of [Graphviz](http://www.graphviz.org/).

Using graphviz-java will require an [SLF4J](https://www.slf4j.org/) binding. It is recommended to use the _SLF4J LOG4J-12 Binding_ from [Eclipse Orbit](http://www.eclipse.org/orbit/). Other bindings, and especially rebinding Log4J and Apache Commons Logging to LOG4J-12 by installing other SLF4J bundles from Orbit may lead to unexpected behavior and error from plug-ins that use other logging mechanisms, especially Xtext.

For convenience, this repository mirrors some bundles from Orbit that are required by graphviz-java. However, the _Apache Batik Transcoder_ bundles are not mirrored due to the complex hieararchy of dependencies. Make sure that some version of `org.apache.batik.transcoder` is available in your target platform. Batik version 1.6.0 should be sufficient.

## Notes

The repository is build with the [p2-maven-plugin](https://github.com/reficio/p2-maven-plugin). The graphviz-java artifacts are turned into OSGi bundles, while J2V8 is already an OSGi bundle. Moreover, some required bundles are fetched an mirrored from the Eclipse Orbit Mars.2+ repository. The dependency on the Apache Batik Transcoder is added to the graphviz-java bundle without mirroring (the huge set of dependencies) from Orbit. The repository also contains some feature jars built directly during the Maven build from feature.xml files.

J2V8 is a collection of 4 OSGi bundles for different os/arch combinations. These bundles contains platform filters for their respective os/arch tuples. Therefore a target platform definition with the `planner` include mode must only contain a reference to the bundle appropriate to the os/arch the target definition is configured for, resolving any other bundle leads to an error. This makes it impossible to refer to the J2V8 bundles directly in a target definition intended for multiple os/arch tuples. As a workaround, the `slicer` include mode may be set _for the whole target definition_, but that disables transitive inclusion of dependencies.

Instead, J2V8 is properly packaged as a feature that conditionally refers to the 4 bundles depending on the os/arch tuple being considered. This feature can be referred to in a target platform definition without restriction to a particular os/arch tuple.

In addition, graphviz-java and its sources are also packaged as features that refer to J2V8 and some required Orbit bundles. Normally, there is no need to explicitly refer to the J2V8 feature when the `planner` strategy is used, as it will be included in the target platform transitively.

For convenience, some bundles from Orbit are included in the repository so that there is no need to contact the Orbit update site during installation (unless Batik is not currently installed). Batik is usually installed anyways, as it is required by both the [GMF Runtime](https://www.eclipse.org/modeling/gmp/?project=gmf-runtime#gmf-runtime) and [Sirius](http://www.eclipse.org/sirius/).

## License

The configuration files used to build this P2 repository are available under the [Eclipse Public License - Version 1.0](https://www.eclipse.org/legal/epl-v10.html), Copyright (c) 2017 Kristóf Marussy (kris7topher@gmail.com).

All copyrights of the contents of the P2 repository belong to their respective owners:

   * The graphviz-java library is available under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0), Copyright (c) 2015 Stefan Niederhauser (nidin@gmx.ch).
   * The J2V8 library is available under the [Eclipse Public License - Version 1.0](https://www.eclipse.org/legal/epl-v10.html), Copyright (c) 2014 EclipseSource and others.
   * The Apache Commons library is available under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0), Copyright (c) The Apache Software Foundation.
   * The SLJ4J library is available under the [MIT License](https://www.slf4j.org/license.html), Copyright (c) 2004-2017 QOS.ch.
