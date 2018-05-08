### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Podział opcjonalnych można przywrócić z innego 4.5 generowanie kodu SQL prostsze 4.0 generowanie kodu SQL

|   |   |
|---|---|
|Szczegóły|Zapytania, które generują instrukcje sprzężenia i zawiera wywołanie ograniczającej operacji bez uprzedniego przy użyciu OrderBy teraz tworzyć prostsze SQL. Po uaktualnieniu do programu .NET Framework 4.5, te zapytania wyprodukowanych SQL bardziej skomplikowane niż w poprzednich wersjach.|
|Sugestia|Ta funkcja jest domyślnie wyłączone. Jeśli Entity Framework generuje dodatkowe instrukcje JOIN, które powodują spadek wydajności, należy włączyć tę funkcję, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji pliku konfiguracji (app.config) aplikacji:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|

