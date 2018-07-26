### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Podział opcjonalnych można przywrócić z innego 4.5 generowanie kodu SQL prostsze 4.0 generowanie kodu SQL

|   |   |
|---|---|
|Szczegóły|Zapytania, które generuje instrukcje JOIN i zawierać wywołanie ograniczającą operacji bez uprzedniego przy użyciu OrderBy teraz tworzyć prostsze SQL. Po uaktualnieniu do wersji .NET Framework 4.5, te zapytania utworzone SQL bardziej skomplikowane niż w starszych wersjach.|
|Sugestia|Ta funkcja jest domyślnie wyłączone. Jeśli Entity Framework wygeneruje dodatkowe instrukcje JOIN, które powodują spadek wydajności, możesz włączyć tę funkcję, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcję pliku konfiguracji aplikacji (app.config):<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|

