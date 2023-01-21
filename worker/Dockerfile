FROM iv41879/worker-base:latest AS build
WORKDIR /code
COPY . .
RUN mvn package -DskipTests

FROM arm64v8/openjdk:latest AS run
WORKDIR /run
COPY --from=build /code/target/worker-jar-with-dependencies.jar worker.jar
CMD java -jar worker.jar

