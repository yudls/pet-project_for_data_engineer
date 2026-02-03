FROM eclipse-temurin:21-jdk

ENV MB_PLUGINS_DIR=/home/plugins/

ADD https://downloads.metabase.com/v0.57.10/metabase.jar /home
ADD https://github.com/motherduckdb/metabase_duckdb_driver/releases/download/1.4.3.1/duckdb.metabase-driver.jar /home/plugins/

RUN chmod 744 /home/plugins/duckdb.metabase-driver.jar

CMD ["java", "-jar", "/home/metabase.jar"]