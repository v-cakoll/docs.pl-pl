### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision i DbParameter.Scale są teraz publicznych wirtualnych elementów członkowskich

|   |   |
|---|---|
|Szczegóły|<xref:System.Data.Common.DbParameter.Precision> i <xref:System.Data.Common.DbParameter.Scale> są zaimplementowane jako publiczny właściwości wirtualnych. Zastępują one odpowiedniej implementacji interfejsu jawnego <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> i <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Sugestia|Podczas ponownego tworzenia dostawcy bazy danych programu ADO.NET, te różnice wymaga słowa kluczowego "override" ma zostać zastosowany do właściwości Precision i Scale. Jest to potrzebne tylko wtedy, gdy ponowne utworzenie składników; istniejące pliki binarne będą nadal działać.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

