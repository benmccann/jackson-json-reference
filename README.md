jackson-json-reference
==============

[![Build Status](https://travis-ci.org/adjohnson916/jackson-json-reference.png)](https://travis-ci.org/adjohnson916/jackson-json-reference)
[![Codecov](https://img.shields.io/codecov/c/github/adjohnson916/jackson-json-reference.svg)](http://codecov.io/github/adjohnson916/jackson-json-reference)
[![Download](https://api.bintray.com/packages/adjohnson916/maven/jackson-json-reference/images/download.svg) ][download]

[JSON Reference] implementation for Java, based on [Jackson]. Process references in JSON documents, such as in [JSON Schema]. Aims for but not limited to full [spec](#specs) compliance.

# Features

* Supports URLs & files.
* Relative & absolute reference URIs.
* Recursive expansion, with options for max depth and stop on circularity.

# Specs

* [JSON Reference]
* [JSON Pointer]
* [JSON Schema]

## Usage

### File
```java
File file = new File("src/test/resources/nest.json");
JsonNode node = (new JsonReferenceProcessor()).process(file);
```

### URL
```java
URL url = new URL("http://json-schema.org/schema");
JsonNode node = (new JsonReferenceProcessor()).process(url);
```

### Settings
```java
ObjectMapper mapper = new ObjectMapper();

JsonReference processor = new JsonReferenceProcessor(mapper);
processor.setStopOnCircular(false); // default true
processor.setMaxDepth(2); // default 1

JsonNode node = processor.process( /*...*/ );
```

### Output
```java
ObjectMapper mapper = new ObjectMapper();
mapper.writeValue(new File("out.json"), node);
```


## Install

### Maven

```xml
<repositories>
    <repository>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
        <id>bintray-adjohnson916-maven</id>
        <name>bintray-adjohnson916-maven</name>
        <url>http://dl.bintray.com/adjohnson916/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>me.andrz.jackson</groupId>
        <artifactId>jackson-json-reference</artifactId>
        <version>0.1.0</version>
    </dependency>
</dependencies>
```

### Gradle

```gradle
repositories {
    maven {
        url  "http://dl.bintray.com/adjohnson916/maven" 
    }
}

dependencies {
    compile 'me.andrz.jackson:jackson-json-reference:0.1.0'
}
```

### Manual

[Download JAR from BinTray][download].

## License

See [LICENSE](LICENSE).

[Jackson]: https://github.com/FasterXML/jackson
[JSON Reference]: http://tools.ietf.org/html/draft-pbryan-zyp-json-ref-03
[JSON Pointer]: http://tools.ietf.org/html/rfc6901
[JSON Schema]: http://json-schema.org/
[download]: https://bintray.com/artifact/download/adjohnson916/maven/me/andrz/jackson/jackson-json-reference/0.1.0/jackson-json-reference-0.1.0.jar
