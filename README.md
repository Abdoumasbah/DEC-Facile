# DEC-Facile
DEC Facile is a tool specifically designed for the creation of computational Explanatory Combinatorial Dictionaries (ECDs).
It provides a user-friendly interface for lexicographers to create, edit, and enrich dictionary entries with senses, definitions, lexical functions, government patterns, and examples, following the principles of Explanatory Combinatorial Lexicology (ECL).

The system is composed of two main components:

-   Backend (BE): [LexO-backend](https://github.com/andreabellandi/LexO-backend), built on top of LexO-server, an open-source RESTful API powered by GraphDB.
-   Frontend (FE): [DEC-Facile-FE](https://github.com/Abdoumasbah/DEC-Facile-FE), a web-based graphical user interface for interactive dictionary creation and exploration.

## Features
 
- **Search and filtering panel** with advanced filters by language, status, and editor.
- **Entry creation and editing** (lexeme, phraseme, part of speech, notes).
- **Structured senses** with propositional definitions and linked lexical units.
- **Lexical functions panel** (Syn, IncepOper1, CausReal1, etc.), fully compliant with ECL.
- **Examples panel** to add and view authentic usage examples.
- **Interoperability with OntoLex-Lemon & Lexicog**, enriched with LexFom.
- **Semantic web compliance:** data stored as RDF in GraphDB, exportable in FAIR formats.

## System Architecture
``` 
Frontend (GUI) <---- REST APIs ----> Backend (LexO-server) <---- SPARQL ----> GraphDB Triple Store
``` 
- **Frontend**: JavaScript, HTML, CSS
- **Backend**: Java (Spring), LexO-server REST APIs, OpenAPI-compliant
- **Storage**: GraphDB triple store + MySQL
- **Data Models**: OntoLex-Lemon, Lexicog, LexFom, syntax–semantics schema

## Tech

### Backend (LexO-server):

- Java 15 or later
- Apache Tomcat 9 or later
- [GraphDB Free](https://graphdb.ontotext.com/) - Semantic Graph Database, compliant with W3C Standards.
- [MySql](https://www.mysql.com/) - Open-source relational database management system (RDBMS)

### Frontend:

- Angular + PrimeNG + TailwindCSS

## Installation
### Backend Setup (LexO-server)
1. [Install](https://graphdb.ontotext.com/documentation/free/quick-start-guide.html) GraphDB.
2. [Create](https://graphdb.ontotext.com/documentation/free/creating-a-repository.html) an empty GraphDB repository with default values.
3. Clone the [LexO-backend](https://github.com/andreabellandi/LexO-backend)
4. Edit the pom.xml file, as follows:

```     
    <profile>
        <id>release</id>
        <properties>
            <db.jdbcUrl>leave_empty</db.jdbcUrl>
            <db.user>leave_empty</db.user>
            <db.password>leave_empty</db.password>
            <graphdb.url>$graphdb_intallation_url$</graphdb.url>
            <graphdb.repository>$repo_name$</graphdb.repository>
            <graphdb.poolSize>5</graphdb.poolSize>
        </properties>
    </profile>
```

where _graphdb\_intallation\_url_ is the url of your GraphDB installation (typically on port 7200), and _repo\_name_ is the name of the repository to connect to.

5. Compile the project with Maven.
6. Run the build.
7. Open the browser at http://localhost:8080/LexO-backend/, and the swagger sholud appear.

### Frontend Setup (DEC-Facile Interface)

1. Clone the [DEC-Facile-FE](https://github.com/Abdoumasbah/DEC-Facile-FE)
2. Install dependencies:
```
npm install
```
3. Run the development server:
```     
ng serve
```
4. Open http://localhost:4200 in your browser.

## License

DEC Facile is released under the MIT License.
