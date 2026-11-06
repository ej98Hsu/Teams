# 使用官方輕量級 Java 21 執行與建構映像檔
FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app

# 安裝 Maven 以便我們在容器內編譯 Spring Boot 專案
RUN apk add --no-cache maven

# 複製設定檔
COPY pom.xml .

# 先下載依賴（利用 Docker layer cache 機制加速後續建構）
RUN mvn dependency:go-offline -B

# 複製原始碼
COPY src ./src

# 預設對外開放 Spring Boot 埠口
EXPOSE 8080