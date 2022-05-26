---
name: Migrate from maven-bundle-plugin to bnd-maven-plugin
about: This Template can be used for a project currently using the maven-bundle-plugin
  to ask for migration to the bnd-maven-plugin
title: Migrate from maven-bundle-plugin to bnd-maven-plugin
labels: ''
assignees: ''

---

# Migrate from maven-bundle-plugin to bnd-maven-plugin

This project currently uses the (Apache Felix) [maven-bundle-plugin](https://felix.apache.org/documentation/subprojects/apache-felix-maven-bundle-plugin-bnd.html) to generate [OSGi](https://www.osgi.org/) metadata here:

... add reference to pom where it is used ...

while the plugin has helped since 2007 to easily generate [OSGi](https://www.osgi.org/) metadata for maven projects today there is a more modern and flexible way to do so with the [bnd-maven-plugin](https://github.com/bndtools/bnd/blob/master/maven/bnd-maven-plugin/README.md) (available since 2014).

## What are the benefits of using the bnd-maven-plugin over maven-bundle-plugin?

1. [bnd-maven-plugin](https://github.com/bndtools/bnd/blob/master/maven/bnd-maven-plugin/README.md) is maintained and released by the people that are also develop the [bnd-lib](https://github.com/bndtools/bnd) and thus always up-to-date with the latest features, while [maven-bundle-plugin](https://felix.apache.org/documentation/subprojects/apache-felix-maven-bundle-plugin-bnd.html), that uses bnd-lib under the hood, is always a bit behind as it requires to wait for a bnd-lib release, then incooperate new versions and maybe adjust the code and then have another release of the maven-bundle-plugin itself.
2. [bnd-maven-plugin](https://github.com/bndtools/bnd/blob/master/maven/bnd-maven-plugin/README.md) more directly integrates with the maven-jar plugin while [maven-bundle-plugin](https://felix.apache.org/documentation/subprojects/apache-felix-maven-bundle-plugin-bnd.html) either requires a special packaging type or additional configuration.
3. There are even more [bnd-maven-plugins](https://github.com/bndtools/bnd/tree/master/maven) that nicely can interact and help you perform common tasks.
4. As bnd-maven-plugin supports all what maven-bundle-plugin supports it is very easy to migrate and as both plugins using the same technology ([BND](https://github.com/bndtools/bnd)) it also not required for developers to learn new things.

## Migration Steps

In general migration can be done with these simple steps:

1. Changing the pom to use `<groupId>biz.aQute.bnd</groupId><artifactId>bnd-maven-plugin</artifactId>` instead of `<groupId>org.apache.felix</groupId><artifactId>maven-bundle-plugin</artifactId>`
2. All instructions from `<instructions>` element are now placed inside a file called `bnd.bnd`

To help with that migration, I like to propose a PR for this repository which includes the necessary steps so we can discuss possible issues or concerns there with actual code changes.
