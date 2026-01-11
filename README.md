# Hostel Room Allocation (mini project)

This is a simple Java console application for managing hostel rooms and student allocations. It can run using an in-memory database (default) or a MySQL database for persistence.

Quick overview
- `App` — interactive console application
- `QuickAdd` / `AddKoushik` — programmatic runners for quick demos
- `InMemoryDatabase` — default ephemeral storage (no external setup)
- `MySQLDatabase` — optional persistent storage (requires MySQL + JDBC driver)

Requirements
- Java 11+ installed and available on `PATH`
- (Optional, recommended) Maven for dependency management and building
- (Optional) MySQL server if you want persistent storage

Run (no external DB — quick demo)
1. Compile sources into `target/classes` (if not already compiled):

```powershell
for /r %i in (src\main\java\*.java) do javac -cp target/classes -d target/classes %i
```

2. Run the interactive app (uses in-memory DB):

```powershell
java -cp target/classes com.hostel.App
```

3. Run the quick demo that auto-adds a student and allocates a room:

```powershell
java -cp target/classes com.hostel.QuickAdd
java -cp target/classes com.hostel.AddKoushik
```

Run with prepared input (non-interactive)
1. Create a plaintext input file (example `input.txt`) with menu choices and values, then:

```powershell
java -cp target/classes com.hostel.App < input.txt
```

Run with MySQL (persistent storage)
1. Ensure MySQL server is running and credentials in `src/main/java/com/hostel/dao/MySQLDatabase.java` match your setup.
2. Create the database and load schema:

```powershell
# adjust mysql command as needed for your installation
mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS hostel_db;"
mysql -u root -p hostel_db < sql/schema.sql
```

3. Make the MySQL JDBC driver available at runtime.
- With Maven (recommended):

```powershell
mvn dependency:copy-dependencies -DoutputDirectory=target/dependency
mvn -DskipTests package
java -cp "target/classes;target/dependency/*" com.hostel.App
```

- Without Maven: download the connector jar and run:

```powershell
curl -L -o mysql-connector.jar https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.33/mysql-connector-java-8.0.33.jar
java -cp "target/classes;mysql-connector.jar" com.hostel.App
```

Notes & troubleshooting
- If you see `No suitable driver found` the connector jar is not on the classpath — follow the JDBC driver steps above.
- The app falls back to the in-memory DB if MySQL connection fails; data will not persist between runs in that mode.
- To change DB credentials, edit `src/main/java/com/hostel/dao/MySQLDatabase.java` and rebuild.

Next improvements you might want
- Add file-based persistence in `InMemoryDatabase` (JSON) for simple persistence without MySQL
- Package a runnable JAR via Maven (`mvn package` with the `shade` plugin)
- Add unit tests for allocation logic

If you want, I can implement file-based persistence now so added students remain after restarting the app — tell me to proceed and I'll make the change and test it.

