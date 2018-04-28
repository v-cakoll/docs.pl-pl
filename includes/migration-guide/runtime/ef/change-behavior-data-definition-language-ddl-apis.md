### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Zmiana zachowania w danych Definition Language (DDL) interfejsów API

|   |   |
|---|---|
|Szczegóły|Zachowanie interfejsów API języka DDL, gdy określono AttachDBFilename zostały zmienione w następujący sposób:<ul><li>Parametry połączenia nie trzeba określać wartość katalog początkowy. Wcześniej zarówno AttachDBFilename i katalog początkowy były wymagane.</li><li>Jeśli został określony zarówno AttachDBFilename i katalog początkowy, dany plik MDF istnieje metoda ObjectContext.DatabaseExists zwraca wartość true. Wcześniej zwróciła wartość false.</li><li>Jeśli został określony zarówno AttachDBFilename i wykazu początkowego, a istnieje dany plik MDF, wywołanie metody ObjectContext.DeleteDatabase usuwa pliki.</li><li>Jeśli ObjectContext.DeleteDatabase jest wywoływane, gdy parametry połączenia określa wartość AttachDBFilename o MDF, który nie istnieje i wykazu początkowego, który nie istnieje, metoda zgłasza wyjątku InvalidOperationException. Wcześniej został zwrócony wyjątek SqlException.</li></ul>|
|Sugestia|Te zmiany ułatwiają tworzenie narzędzi i aplikacji używających interfejsów API języka DDL. Te zmiany mogą wpływać na zgodność aplikacji w następujących scenariuszach:<ul><li>Użytkownik zapisuje kod, który wykonuje polecenie DROP DATABASE bezpośrednio zamiast wywoływania ObjectContext.DeleteDatabase, jeśli ObjectContext.DatabaseExists zwraca wartość true. Przerywa to działanie istniejącego kodu, jeśli baza danych nie jest dołączona, ale plik MDF istnieje.</li><li>Użytkownik zapisuje kod, który oczekuje metoda ObjectContext.DeleteDatabase zgłosić wyjątku SqlException zamiast wyjątku InvalidOperationException, gdy plik wykazu początkowego i MDF nie istnieje.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

