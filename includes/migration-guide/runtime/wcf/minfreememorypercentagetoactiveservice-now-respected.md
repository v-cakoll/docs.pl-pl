### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>Teraz jest przestrzegana MinFreeMemoryPercentageToActiveService

|   |   |
|---|---|
|Szczegóły|To ustawienie określa minimalna ilość pamięci, która musi być dostępny na serwerze, zanim można aktywować usługę WCF. Zaprojektowano go, aby zapobiec <xref:System.OutOfMemoryException?displayProperty=name> wyjątków. W programie .NET Framework 4.5 to ustawienie nie miała wpływu. W programie .NET Framework 4.5.1 ustawienie jest przestrzegana.|
|Sugestia|Jeśli ilość wolnej pamięci dostępnej na serwerze sieci web jest mniejsza niż wartość procentowa zdefiniowane przez ustawienie konfiguracji wystąpienia wyjątku. Niektóre usługi WCF, które pomyślnie uruchomiona i został uruchomiony w środowisku ograniczonego pamięci teraz może zakończyć się niepowodzeniem.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

