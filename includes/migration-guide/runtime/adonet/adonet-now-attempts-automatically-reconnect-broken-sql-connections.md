---
ms.openlocfilehash: 4c65cd62b2d84ef2b852d10a04e5f6ce0cc82d3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649261"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET teraz próbuje nawiązać automatycznie przerwane połączenia SQL

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5.1, .NET Framework spróbuje automatycznie ponownie przerwane połączenia SQL. Chociaż zwykle dzięki temu aplikacje bardziej niezawodne, istnieją przypadki brzegowe, w których aplikacja musi poinformować, że połączenie zostało utracone, tak, aby można podjąć akcję na ponowne nawiązanie połączenia.|
|Sugestia|Jeśli ta funkcja jest niepożądany, ze względu na problemy ze zgodnością, można je wyłączyć, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> właściwość parametrów połączenia (lub <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) na wartość 0.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|
