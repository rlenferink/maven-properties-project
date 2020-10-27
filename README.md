# maven-properties-project

This is a test project for determining the correct use of the `${project.parent.version}` property.

Steps to reproduce:

```bash
# First clone the repo
git clone git@github.com:rlenferink/maven-properties-project.git maven-properties-project
cd maven-properties-project

# Build product parent
cd product-parent/
mvn clean install

# Build product A (needed for product B)
cd ../productA/
mvn clean install

# Build product B (fails)
cd ../productB/
mvn clean install # This call fails because of the ${project.parent.version} property being evaluated (incorrectly?)

# Build product C (succeeds)
cd ../productC/
mvn clean install
```

