# CI-CD-Project2

#  command to initiate mvn project folder structure
mvn archetype:generate -B -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.1 -DgroupId=com.company -DartifactId=project2 -Dversion=1.0-SNAPSHOT -Dpackage=com.company.project

# run this command in project2 dire
  mvn clean && mvn test

