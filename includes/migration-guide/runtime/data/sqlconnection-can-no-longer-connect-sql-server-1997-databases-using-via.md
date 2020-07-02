---
ms.openlocfilehash: 241184d61d718fedfea396260e739d2dbc05c305
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620287"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>Element SqlConnection nie może już łączyć się z SQL Server 1997 lub bazami danych przy użyciu adaptera VIA

#### <a name="details"></a>Szczegóły

Połączenia z bazami danych SQL Server przy użyciu [protokołu wirtualnej karty interfejsu (Via)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) nie są już obsługiwane. Protokół używany do nawiązywania połączenia z SQL Server bazą danych jest widoczny w parametrach połączenia. Połączenie TELEFONICZne będzie zawierać: &lt; servername &gt; . Jeśli ta aplikacja nawiązuje połączenie z usługą SQL za pośrednictwem protokołu innego niż VIA (TCP: lub np.), nie zostanie napotkana żadna przerwana zmiana. Ponadto połączenia z SQL Server 7 (1997) nie są już obsługiwane.

#### <a name="suggestion"></a>Sugestia

Protokół VIA jest przestarzały, więc do łączenia się z bazami danych SQL należy używać alternatywnego protokołu. Najczęściej używanym protokołem jest TCP/IP. Aby uzyskać więcej informacji na temat nawiązywania połączenia za pośrednictwem protokołu TCP/IP, zobacz [Włączanie protokołu TCP/IP dla wystąpienia bazy danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Jeśli dostęp do bazy danych odbywa się tylko z intranetu, protokół współużytkowanych potoków może zapewnić lepszą wydajność w przypadku powolnej sieci.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)></li></ul>|
