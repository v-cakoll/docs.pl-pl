---
ms.openlocfilehash: 9605352c66f85b6942ba24942cb07c88bdd81f2a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857560"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Pula połączeń blokuje okres dla baz danych Azure SQL jest usuwany.

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2 dla połączenia Otwórz żądania do znanych baz danych Azure SQL (*. database.windows.net, *. database.chinacloudapi.cn, *. database.usgovcloudapi.net, *. database.cloudapi.de), okres blokowania jest puli połączeń usunięty, i otwórz błędy połączenia nie są buforowane. Próbami ponowienia otwartych żądań połączenia wystąpi niemal natychmiast po wystąpieniu błędów przejściowych połączenia. Ta zmiana umożliwia próba otwarcia połączenia należy natychmiast ponowić baz danych Azure SQL, a więc poprawa wydajności aplikacji w chmurze — włączone. Dla wszystkich innych próby nawiązania połączenia połączenia puli czasu blokowania w dalszym ciągu wymuszane.<p/>W .NET Framework 4.6.1 i wcześniejszymi wersjami, gdy aplikacja napotka błąd przejściowy połączenia podczas nawiązywania połączenia z bazą danych, próba połączenia nie mogą zostać powtórzone szybko, ponieważ pula połączeń buforuje błędu i ponownie zgłasza 5 sekund do 1 minuta. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). To zachowanie jest problematyczne dla połączeń z bazami danych Azure SQL, które często zakończona niepowodzeniem z błędami przejściowymi, które są zwykle odzyskała sprawność w ciągu kilku sekund. Funkcji blokowania w puli połączeń oznacza, że aplikacji nie można połączyć z bazą danych na okres rozbudowane nawet, jeśli baza danych jest dostępna i aplikacja potrzebuje do renderowania w ciągu kilku sekund.|
|Sugestia|Jeśli to zachowanie jest niepożądany, ustawiając można skonfigurować połączenia czasu blokowania puli <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> właściwości wprowadzone w programie .NET Framework 4.6.2. Wartość właściwości jest elementem członkowskim <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> wyliczenia, która może przyjąć jedną z trzech wartości:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Można przywrócić poprzednie zachowanie przez ustawienie <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> właściwość <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.|
|Scope|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

