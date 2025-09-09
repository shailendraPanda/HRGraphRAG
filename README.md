# HRGraphRAG
A Demo Graph RAG pipeline using OnTop VKG , Trino as SQL engine and Postgres as Relation DB.

## compose YAML
### 🔌 Port & Endpoint Summary – Semantic HR Stack

### 🗄️ PostgreSQL

- **Port:** `5432`  
- **Purpose:** SQL access for relational HR data  
- **Used by:** Trino connector  
- **Endpoint:**  
  `jdbc:postgresql://localhost:5432/hr_db`

---

### 🚀 Trino

- **Port:** `8080`  
- **Purpose:** Distributed SQL query engine  
- **Used by:** Ontop (via JDBC), direct SQL clients  
- **Endpoints:**  
  - Web UI: `http://localhost:8080`  
  - JDBC: `jdbc:trino://localhost:8080/postgresql/hr_db`

---

### 🧠 Ontop

- **Port:** `8081`  
- **Purpose:** SPARQL endpoint over virtual RDF graph  
- **Used by:** Semantic clients, reasoning engines  
- **Endpoint:**  
  `http://localhost:8081/sparql`

---

### 📦 Summary Table

| Service     | Port  | Protocol | Endpoint                            | Purpose                          |
|-------------|-------|----------|-------------------------------------|----------------------------------|
| PostgreSQL  | 5432  | JDBC     | `jdbc:postgresql://localhost:5432` | Relational data storage          |
| Trino       | 8080  | HTTP/JDBC| `http://localhost:8080`            | SQL federation & query engine    |
| Ontop       | 8081  | HTTP     | `http://localhost:8081/sparql`     | SPARQL over ontology + OBDA      |

## Ontology File Sample
https://ontop-vkg.org/tutorial/basic/university.ttl

Project has a hr-ontology file

## Markdown to PDF conversion in VS Code
- Install Extension
Open VS Code and install the extension called Markdown PDF by yzane.
- Open Your Markdown File
Load your .md resume file in the editor.
- Export to PDF
Right-click anywhere in the editor and select Markdown PDF: Export (pdf).
The PDF will be saved in the same folder as your Markdown file

## Pipeline
SPARQL Query → Ontop Engine → OBDA Mapping → SQL Query → Trino → PostgreSQL → Result → RDF Triples

## Elasticsearch Index and Document Management APIs

### Index APIs
- **Create Index:**
  `PUT /index_name`
  Creates a new index.

- **Modify Index (Settings/Mappings):**
  `PUT /index_name/_settings`
  `PUT /index_name/_mapping`
  Updates index settings or mappings.

- **Delete Index:**
  `DELETE /index_name`
  Deletes an index.

### Document APIs
- **Create/Index Document:**
  `POST /index_name/_doc`
  `PUT /index_name/_doc/document_id`
  Adds a new document (auto-generated or specified ID).

- **Update Document:**
  `POST /index_name/_update/document_id`
  Updates fields in an existing document.

- **Get Document:**
  `GET /index_name/_doc/document_id`
  Retrieves a document by ID.

- **Delete Document:**
  `DELETE /index_name/_doc/document_id`
  Removes a document.

You can use these APIs via HTTP requests (e.g., with curl, Postman, or any HTTP client).



