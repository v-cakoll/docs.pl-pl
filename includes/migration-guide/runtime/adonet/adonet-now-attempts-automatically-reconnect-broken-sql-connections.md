---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620185"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET teraz próbuje automatycznie ponownie nawiązać połączenie z przerwanymi połączeniami SQL

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.5.1 .NET Framework spróbuje automatycznie ponownie nawiązać połączenie z przerwanymi połączeniami SQL. Chociaż zwykle aplikacje są bardziej niezawodne, istnieją przypadki brzegowe, w których aplikacja musi wiedzieć, że połączenie zostało utracone, dzięki czemu może podejmować pewne działania po ponownej nawiązaniu połączenia.

#### <a name="suggestion"></a>Sugestia

Jeśli ta funkcja jest niepożądana z powodu problemów ze zgodnością, można ją wyłączyć, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> Właściwość parametrów połączenia (lub <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> ) na 0.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
