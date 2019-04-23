---
ms.openlocfilehash: fcaee245e98dfe71beb4042a2664a14b64cf2398
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804728"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>Połączenie nie będzie można podłączyć do programu SQL Server 1997 lub baz danych przy użyciu karty VIA

|   |   |
|---|---|
|Szczegóły|Połączenia z bazami danych programu SQL Server przy użyciu [protokołu wirtualnego Interface Adapter (VIA)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229%28v=sql.105%29) nie są już obsługiwane. Protokół używany do łączenia z bazą danych programu SQL Server jest widoczna w parametrach połączenia. Połączenie VIA będzie zawierać za pośrednictwem:&lt;servername&gt;. Jeśli ta aplikacja nawiązuje połączenie z SQL za pomocą protokołu innego niż VIA (tcp: lub nazwane: na przykład), a następnie zostanie napotkana nie istotnej zmiany. Ponadto połączenia z SQL Server 7 (1997) nie są już obsługiwane.|
|Sugestia|Protokołu VIA jest przestarzały, więc alternatywnych protokół powinna być używana z bazami danych SQL. Protokół najczęściej używany jest protokół TCP/IP. Aby uzyskać więcej informacji na temat nawiązywania połączenia za pośrednictwem protokołu TCP/IP, zobacz [włączyć protokół TCP/IP dla wystąpienia bazy danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Jeśli baza danych jest dostępny tylko z firmowej sieci intranet, protokół potoków udostępniony może zapewnić lepszą wydajność, jeśli sieć jest powolne.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|
