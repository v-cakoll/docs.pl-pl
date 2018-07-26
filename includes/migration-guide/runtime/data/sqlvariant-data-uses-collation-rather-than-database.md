### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Dane typu Sql_variant używa sortowania sql_variant, a nie sortowania bazy danych

|   |   |
|---|---|
|Szczegóły|<code>sql_variant</code> danych używa <code>sql_variant</code> sortowania zamiast sortowania bazy danych.|
|Sugestia|Ta zmiana dotyczy możliwego uszkodzenia danych, jeśli sortowanie bazy danych różni się od <code>sql_variant</code> sortowania. W aplikacjach korzystających z uszkodzonych danych może wystąpić błąd.|
|Zakres|Przezroczyste|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

