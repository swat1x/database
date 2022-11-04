# Simple Database Library

## Usage

``` java
Database database = new Database("localhost:3306", "database", "user", "password", DatabaseDriver.MARIADB);
// Import the database driver separately
// DatabaseDriver.class contains most using presets as MySQL and MariaDB

String targetName = "swat1x";
Double defaultBalance = 0;

// Sync
Double syncBalance = database.sync().query("SELECT * FROM `users` WHERE `username`=?" 
                                      rs -> rs.next() ? rs.getDouble("balance") : defaultName, targetName);
// Async
CompletableFuture<Double> asyncBalance = database.async().query("SELECT * FROM `users` WHERE `username`=?" 
                                      rs -> rs.next() ? rs.getDouble("balance") : defaultName, targetName);
asyncBalance.thenAccept(balance -> System.out.println(String.format("Balance of %s: %d$", targetName, balance)));

// Shutdown database
database.shutdown();
```

## Denendency

**Maven**
``` xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>
<dependencies>
    <dependency>
        <groupId>com.github.swat1x</groupId>
        <artifactId>database</artifactId>
        <version>2.0</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

**Gradle**
``` groovy
repositories {
    maven { url 'https://jitpack.io' }
}
dependencies {
    implementation "com.github.swat1x:database:2.0"
}
```
