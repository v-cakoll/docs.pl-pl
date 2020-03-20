---
ms.openlocfilehash: 33c262ebe131aade2b32d824395721f098640cf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857560"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Okres blokowania puli połączeń dla baz danych SQL platformy Azure jest usuwany

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, dla otwartych żądań połączeń ze znanymi bazami danych SQL platformy Azure (*.database.windows.net, *.database.chinacloudapi.cn, *.database.usgovcloudapi.net, *.database.cloudapi.de), okres blokowania puli połączeń jest usunięte, a błędy otwarcia połączenia nie są buforowane. Próby ponowienia próby połączenia otwartych żądań nastąpi niemal natychmiast po błędach połączenia przejściowego. Ta zmiana umożliwia natychmiastowe ponowienie próby ponownego ponawiania otwartej próby połączenia dla baz danych SQL platformy Azure, co zwiększa wydajność aplikacji z obsługą chmury. W przypadku wszystkich innych prób połączenia okres blokowania puli połączeń jest nadal wymuszany.<p/>W .NET Framework 4.6.1 i wcześniejszych wersjach, gdy aplikacja napotka przejściowy błąd połączenia podczas łączenia się z bazą danych, nie można szybko ponowić próby połączenia, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 Minut. Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). To zachowanie jest problematyczne dla połączeń z bazami danych SQL platformy Azure, które często nie z błędami przejściowymi, które są zwykle odzyskane w ciągu kilku sekund. Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna, a aplikacja musi renderować w ciągu kilku sekund.|
|Sugestia|Jeśli to zachowanie jest niepożądane, okres blokowania puli połączeń <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> można skonfigurować przez ustawienie właściwości wprowadzonej w .NET Framework 4.6.2. Wartość właściwości jest członkiem wyliczenia, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> które może przyjmować jedną z trzech wartości:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Poprzednie zachowanie można przywrócić, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> ustawiając <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>właściwość na .|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
