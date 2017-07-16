# graphviz-java-p2
P2 update site for graphviz-java.

**Update site location:** https://kris7t.github.io/graphviz-java-p2/repository/

Use the update site located at https://kris7t.github.io/graphviz-java-p2/repository/ to install the _graphviz-java Feature_ (optionally with sources) that allows using [graphviz-java](https://github.com/nidi3/graphviz-java) from an Eclipse RCP environment. The repository also contains the _J2V8 Feature_ to also install [J2V8](https://github.com/eclipsesource/J2V8), the backend used by graphviz-java to run the Javascript version of [Graphviz](http://www.graphviz.org/).

Using graphviz-java will require an [SLF4J](https://www.slf4j.org/) binding. It is recommended to use the _SLF4J LOG4J-12 Binding_ from [Eclipse Orbit](http://www.eclipse.org/orbit/). Other bindings, and especially rebinding Log4J and Apache Commons Logging to LOG4J-12 by installing other SLF4J bundles from Orbit may lead to unexpected behavior and error from plug-ins that use other logging mechanisms, especially Xtext.

For convenience, this repository mirrors some bundles from Orbit that are required by graphviz-java. However, the _Apache Batik Transcoder_ bundles are not mirrored due to the complex hieararchy of dependencies. Make sure that some version of `org.apache.batik.transcoder` is available in your target platform. Batik version 1.6.0 should be sufficient.

## License

The configuration files used to build this P2 repository are available under the [Eclipse Public License - Version 1.0](https://www.eclipse.org/legal/epl-v10.html), Copyright (c) 2017 Kristóf Marussy (kris7topher@gmail.com).

All copyrights of the contents of the P2 repository belong to their respective owners:

   * The graphviz-java library is available under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0), Copyright (c) 2015 Stefan Niederhauser (nidin@gmx.ch).
   * The J2V8 library is available under the [Eclipse Public License - Version 1.0](https://www.eclipse.org/legal/epl-v10.html), Copyright (c) 2014 EclipseSource and others.
   * The Apache Commons library is available under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0), Copyright (c) The Apache Software Foundation.
   * The SLJ4J library is available under the [MIT License](https://www.slf4j.org/license.html), Copyright (c) 2004-2017 QOS.ch.
