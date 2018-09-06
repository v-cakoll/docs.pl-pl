---
title: Wykonanie Side-by-Side w ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 7435f64afa9ce45a29f4d0a537219f31968eb3f5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747278"
---
# <a name="side-by-side-execution-in-adonet"></a>Wykonanie Side-by-Side w ADO.NET
Wykonywanie Side-by-side w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jest możliwość wykonywania aplikacji na komputerze, który ma wiele wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zainstalowany, wyłącznie przy użyciu wersji, dla którego aplikacja została skompilowana. Aby uzyskać szczegółowe informacje o konfigurowaniu side-by-side wykonywania, zobacz [Side-by-Side Execution](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Aplikacja skompilowana przy użyciu jednej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] można uruchamiać na inną wersję [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Jednak zaleca się że kompilujesz wersję aplikacji dla każdej zainstalowanej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]i uruchomić je oddzielnie. W dowolnym scenariuszu, należy pamiętać o zmianach w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] między wersjami, które mogą wpływać na zgodność z nowszymi wersjami lub zgodności z poprzednimi wersjami aplikacji.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Zgodność z nowszymi wersjami i zgodności z poprzednimi wersjami  
 Zgodność z nowszymi wersjami oznacza, że aplikacja może być kompilowane przy użyciu wcześniejszej wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale nadal będzie działać prawidłowo w nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Kod napisany dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 jest zgodny wprzód z nowszymi wersjami.  
  
 Zgodność ze starszymi wersjami oznacza, że aplikacja jest kompilowana do nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale kontynuuje działanie we wcześniejszych wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bez utraty funkcjonalności. Oczywiście nie będzie to w przypadku funkcji wprowadzonych w nowej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 Począwszy od wersji 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for ODBC (<xref:System.Data.Odbc>) jest dołączony jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Dostawca danych ODBC jest dostępna dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] deweloperów w wersji 1.0 jako stronę internetową pobierać z [dostępu do danych i Centrum deweloperów magazynu](https://go.microsoft.com/fwlink/?linkid=4173). W obszarze nazw pobrany [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for ODBC jest **Microsoft.Data.Odbc**.  
  
 Jeśli aplikacja opracowana dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.0, która używa dostawcy danych ODBC, aby nawiązać połączenie źródła danych, a chcesz uruchomić tę aplikację na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 lub nowszej, musisz zaktualizować przestrzeni nazw dla ODBC Dostawca danych **System.Data.Odbc**. Możesz następnie należy ponownie skompilować go do nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Jeśli aplikacja opracowana dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 2.0 lub nowszej, która używa dostawcy danych ODBC, aby nawiązać połączenie źródła danych, a chcesz uruchomić tę aplikację na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 należy pobrać dostawcę danych ODBC i zainstalować je na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] system w wersji 1.0. Następnie należy zmienić obszar nazw dla dostawcy danych ODBC, aby **Microsoft.Data.Odbc**i ponownie skompilować aplikację dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle  
 Począwszy od wersji 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle (<xref:System.Data.OracleClient>) jest dołączony jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Dostawca danych jest dostępna dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] deweloperów w wersji 1.0 jako stronę internetową pobierać z [dostępu do danych i Centrum deweloperów magazynu](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Jeśli aplikacja opracowana dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 2.0 lub nowszej, która używa dostawcy danych, aby nawiązać połączenie źródła danych, a chcesz uruchomić tę aplikację na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 należy pobrać dostawcy danych i zainstaluj go na < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  system w wersji 1.0.  
  
## <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawców danych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) są wymagane do uruchomienia przy użyciu uprawnień FullTrust. Dowolne próba użycia [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych k [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 w strefie z mniej niż powoduje, że uprawnienie FullTrust <xref:System.Security.SecurityException>.  
  
 Jednakże poczynając od wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 2.0, wszystkie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych mogą być używane w częściowo zaufanej strefy. Ponadto nowa funkcja zabezpieczeń został dodany do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1. Ta funkcja pozwala ograniczyć połączenia, jakie ciągi mogą być używane w strefie zabezpieczeń. Można również wyłączyć używanie pustych haseł dla określonej strefy. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Ponieważ każda instalacja [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ma osobny plik Security.config —, nie ma żadnych problemów ze zgodnością przy użyciu ustawień zabezpieczeń. Jednakże jeśli aplikacja zależy od możliwości zapewnienia dodatkowych zabezpieczeń [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] objęte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.1 i nowszych, nie będzie możliwe rozprowadzić go na system w wersji 1.0.  
  
## <a name="sqlcommand-execution"></a>Wykonywanie polecenia SqlCommand  
 Począwszy od [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1, sposób który <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonuje polecenia na dane źródło zostało zmienione.  
  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonane wszystkie polecenia w kontekście **sp_executesql** procedury składowanej. W wyniku polecenia, które wpływają na stan połączenia (na przykład SET NOCOUNT ON), dotyczą tylko wykonywania bieżącego polecenia. Stan połączenia nie jest modyfikowany dla polecenia wykonany, podczas gdy połączenie jest otwarte.  
  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.1 i nowszych, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> tylko uruchamia polecenia w kontekście **sp_executesql** procedury składowanej, jeśli polecenie zawiera parametry, co zapewnia korzyści wydajności. W rezultacie Jeśli polecenie wpływu na stan połączenia znajduje się za pomocą polecenia bez parametrów, modyfikuje stan połączenia dla wszystkich kolejnych poleceń wykonany, podczas gdy połączenie jest otwarte.  
  
 Należy wziąć pod uwagę następujące partii poleceń wykonanych podczas wywołania <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.1 i nowszych, NOCOUNT pozostanie ON na wszystkie kolejne polecenia wykonany, podczas gdy połączenie jest otwarte. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0, NOCOUNT jest tylko ON dla bieżącego wykonywania polecenia.  
  
 Ta zmiana może wpłynąć na przód i Wstecz zgodności aplikacji, jeśli zależą od zachowania <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> dla obu wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 W przypadku aplikacji korzystających z zarówno starszych i nowszych wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], można napisać kod, aby upewnić się, że zachowanie jest takie same, niezależnie od wersji są uruchomione na. Jeśli chcesz upewnić się, że polecenie modyfikuje stan połączenia dla wszystkich kolejnych poleceń, zaleca się wykonanie za pomocą polecenia <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Jeśli chcesz upewnić się, że polecenie nie powoduje modyfikacji połączenia dla wszystkich kolejnych poleceń, zaleca się, że zawrzesz poleceń można zresetować stan połączenia w poleceniu. Na przykład:  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
