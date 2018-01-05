---
title: Wykonanie Side-by-Side w ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60da108fd77465917cdfe1dd744067eac9e88d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="side-by-side-execution-in-adonet"></a>Wykonanie Side-by-Side w ADO.NET
Wykonanie Side-by-side w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jest możliwość uruchamiania aplikacji na komputerze, który ma wiele wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zainstalować wyłącznie przy użyciu wersji, dla którego został skompilowany aplikacji. Aby uzyskać szczegółowe informacje o konfigurowaniu wykonywania side-by-side, zobacz [wykonywania Side-by-Side](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Aplikacji skompilowanych za pomocą jednej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] można uruchomić w innej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Jednak firma Microsoft zaleca, aby skompilować wersji aplikacji dla każdej zainstalowanej wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]i uruchom je oddzielnie. W każdym z tych scenariuszy należy pamiętać o zmianach w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] między wersjami, które mogą mieć wpływ na zgodność z nowszymi wersjami lub zgodności z poprzednimi wersjami aplikacji.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Zgodność z nowszymi wersjami i zgodności z poprzednimi wersjami  
 Zgodność z nowszymi wersjami oznacza, że aplikacji może być kompilowana przy użyciu wcześniejszej wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale nadal będzie działać pomyślnie w nowszej wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]Kod napisany dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 są zgodne wprzód z nowszymi wersjami.  
  
 Zgodność z poprzednimi wersjami oznacza, że aplikacja została skompilowana dla nowszej wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale nadal działa we wcześniejszych wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bez utraty funkcji. Oczywiście nie będzie to w przypadku funkcje wprowadzone w nowej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 Począwszy od wersji 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych ODBC (<xref:System.Data.Odbc>) jest uwzględniana jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Dostawca danych ODBC jest dostępny dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pobrać deweloperów w wersji 1.0 jako sieci Web z [dostęp do danych i magazynu w Centrum deweloperów](http://go.microsoft.com/fwlink/?linkid=4173). Przestrzeń nazw dla pobranego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jest dostawca danych dla ODBC **Microsoft.Data.Odbc**.  
  
 Jeśli korzystasz z aplikacji utworzonych dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.0, która używa dostawcę danych ODBC do nawiązania połączenia źródła danych i chcesz uruchomić tę aplikację [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.1 lub nowszej, musisz zaktualizować przestrzeni nazw dla ODBC Dostawca danych **System.Data.Odbc**. Możesz następnie należy ponownie skompilować go do nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Jeśli korzystasz z aplikacji utworzonych dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 2.0 lub nowszej, który używa dostawcy danych ODBC do nawiązania połączenia źródła danych, a chcesz uruchomić tę aplikację [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0, musisz pobrać dostawcę danych ODBC i zainstaluj na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] system w wersji 1.0. Następnie należy zmienić przestrzeni nazw przez dostawcę danych ODBC **Microsoft.Data.Odbc**i ponownie skompilować aplikację dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle  
 Począwszy od wersji 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu Oracle (<xref:System.Data.OracleClient>) jest uwzględniana jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Dostawca danych jest dostępne dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pobrać deweloperów w wersji 1.0 jako sieci Web z [dostęp do danych i magazynu w Centrum deweloperów](http://go.microsoft.com/fwlink/?linkid=4173).  
  
 Jeśli korzystasz z aplikacji utworzonych dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 2.0 lub nowszej, który używa dostawcy danych do nawiązania połączenia źródła danych, a chcesz uruchomić tę aplikację [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0, musisz pobrać dostawcę danych i zainstalować ją na < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  system w wersji 1.0.  
  
## <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawców danych w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) są wymagane do uruchomienia z uprawnień FullTrust. Próba użycia żadnego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] k dostawców danych z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 w strefie jest mniejsza niż przyczyny uprawnień FullTrust <xref:System.Security.SecurityException>.  
  
 Jednak począwszy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 2.0, wszystkie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych mogą być używane w częściowo zaufanej strefy. Ponadto nowa funkcja zabezpieczeń został dodany do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1. Ta funkcja pozwala ograniczyć połączenia, jakie parametry mogą być używane w strefie zabezpieczeń. Można również wyłączyć używanie pustych haseł dla strefy zabezpieczeń. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Ponieważ każda instalacja [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ma oddzielny plik Security.config — nie ma żadnych problemów ze zgodnością z ustawieniami zabezpieczeń. Jednak jeśli aplikacja zależy od możliwości dodatkowe zabezpieczenia [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] objęte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 lub nowszej, nie będzie mógł rozpowszechnienie go do systemu w wersji 1.0.  
  
## <a name="sqlcommand-execution"></a>Wykonanie SqlCommand  
 Począwszy od [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1, sposób który <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonuje polecenia na dane źródło zostało zmienione.  
  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonać wszystkie polecenia w kontekście **sp_executesql** procedury składowanej. W związku z tym poleceń, które mają wpływ na stan połączenia (na przykład SET NOCOUNT ON), dotyczą tylko wykonywania bieżącego polecenia. Stan połączenia nie jest modyfikowany dla polecenia wykonywać, gdy połączenie jest otwarte.  
  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 lub nowszej, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> tylko uruchamia polecenia w kontekście **sp_executesql** procedury składowanej, jeśli polecenie zawiera parametry, która zapewnia korzyści wydajności. W związku z tym Jeśli polecenie wpływu na stan połączenia jest uwzględniony w poleceniu bez parametrów, modyfikuje stan połączenia dla wszystkich kolejnych poleceń wykonywać, gdy połączenie jest otwarte.  
  
 Należy wziąć pod uwagę następujące partii polecenia wykonywane w wywołaniu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 lub nowszej, NOCOUNT pozostanie ON dla polecenia wykonywać, gdy połączenie jest otwarte. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 NOCOUNT jest tylko włączone dla bieżącego wykonywania polecenia.  
  
 Ta zmiana może wpłynąć na do przodu i do tyłu zgodności aplikacji, jeśli zależy zachowanie <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> dla danej wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Dla aplikacji działających na zarówno wcześniejszych i jego nowsze wersje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], można wpisz swój kod, aby upewnić się, że zachowanie jest takie same, niezależnie od wersji są uruchomione na. Jeśli chcesz upewnić się, że polecenie modyfikuje stan połączenia dla wszystkich kolejnych poleceń, zaleca się wykonanie za pomocą polecenia <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Jeśli chcesz upewnić się, czy polecenie nie modyfikuje połączenia dla wszystkich kolejnych poleceń, firma Microsoft zaleca, czy zawiera polecenia do zresetowania stanu połączenia w poleceniu. Na przykład:  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
