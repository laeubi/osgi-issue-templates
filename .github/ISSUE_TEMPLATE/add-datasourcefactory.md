---
name: Add DataSourceFactory to JDBC driver
about: This template can be used to suggest adding a DataSourceFactory to a JDBC driver
title: 'Please support the Data Service Specification for JDBC™ Technology'
labels: ''
assignees: ''

---

OSGi defines a [Data Service Specification for JDBC™ Technology](https://docs.osgi.org/specification/osgi.cmpn/8.0.0/service.jdbc.html) that provides a convenient and save way to obtain DataSources.
Even though it can be implemented by clients it is advised that JDBC driver vendors include an implementation if possible for the following reasons:

1. The vendor has the best knowledge how to create and configure the participating objects.
2. Changes in the internal implementation, e.g. refactoring of class names can be reflected an managed easier in the original repository
3. No gap between deployment of new version and connector code
4. For non-osgi users, this is completely transparent and the is no need for them to change, but OSGi users will be happy to not reinvent the wheel, the library can just be dropped inside a framework and seaming less integrate, for example with the [JPA Specification](http://docs.osgi.org/specification/osgi.cmpn/8.0.0/service.jpa.html). 

Because of this I'd like to propose adding an implementation for a [DataSourceFactory](https://docs.osgi.org/specification/osgi.cmpn/8.0.0/service.jdbc.html#org.osgi.service.jdbc.DataSourceFactory) in this repository and offering to contribute the inital implementation.
