---
ms.openlocfilehash: 4a60f4b135d5710ad0cc4900337e2970ffb8dd58
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83435398"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Okres blokowania puli połączeń dla baz danych Azure SQL Database został usunięty

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6.2, w przypadku żądań otwarcia dla połączeń z znanymi bazami danych Azure SQL Database ( \* . Database.Windows.NET, \* . Database.chinacloudapi.CN, \* . database.usgovcloudapi.net, \* . Database.cloudapi.de), okres blokowania puli połączeń zostanie usunięty, a błędy otwarcia połączenia nie są buforowane. Próby ponownego nawiązania połączenia będą wykonywane niemal natychmiast po błędach połączenia przejściowego. Ta zmiana umożliwia natychmiastowe ponawianie próby nawiązania połączenia z bazami danych Azure SQL, co poprawia wydajność aplikacji obsługujących chmurę. W przypadku wszystkich innych prób połączenia będzie wymuszany okres blokowania puli połączeń.<p/>W .NET Framework 4.6.1 i starszych wersjach, gdy podczas łączenia się z bazą danych w aplikacji wystąpi przejściowy błąd połączenia, próba połączenia nie może być podejmowana szybko, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 minuty. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). To zachowanie jest przyczyną problemów z połączeniami z bazami danych Azure SQL, co często kończy się niepowodzeniem z błędami przejściowymi, które zwykle są odzyskiwane z ciągu kilku sekund. Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna i aplikacja musi być renderowana w ciągu kilku sekund.|
|Sugestia|Jeśli to zachowanie jest niepożądane, okres blokowania puli połączeń można skonfigurować przez ustawienie <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> Właściwości wprowadzonej w .NET Framework 4.6.2. Wartość właściwości jest składową <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> wyliczenia, która może przyjmować jedną z trzech wartości:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Poprzednie zachowanie można przywrócić, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> Właściwość na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> .|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
