---
title: Wykonywanie równoczesne w ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: d20d8e81d76284509d6fe733e4f283a9ab39cb00
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877093"
---
# <a name="side-by-side-execution-in-adonet"></a>Wykonywanie równoczesne w ADO.NET
Wykonywanie Side-by-side w programie .NET Framework jest możliwość wykonywania aplikacji na komputerze, który ma wiele wersji .NET Framework zainstalowanej, wyłącznie przy użyciu wersji, dla którego aplikacja została skompilowana. Aby uzyskać szczegółowe informacje o konfigurowaniu side-by-side wykonywania, zobacz [Side-by-Side Execution](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Aplikacja skompilowana przy użyciu jednej wersji programu .NET Framework może być uruchomiona w innej wersji programu .NET Framework. Jednak zaleca się skompilować wersję aplikacji dla każdej zainstalowanej wersji programu .NET Framework i uruchomić je oddzielnie. W dowolnym scenariuszu należy pamiętać o zmianach w ADO.NET między wersjami, które mogą wpływać na zgodność z nowszymi wersjami lub zgodności z poprzednimi wersjami aplikacji.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Zgodność z nowszymi wersjami i zgodności z poprzednimi wersjami  
 Zgodność z nowszymi wersjami oznacza, że aplikacja może być skompilowana przy użyciu wcześniejszej wersji programu .NET Framework, ale nadal będzie działać prawidłowo w nowszej wersji programu .NET Framework. ADO.NET kod napisany dla .NET Framework w wersji 1.1 jest zgodny wprzód z nowszymi wersjami.  
  
 Zgodność ze starszymi wersjami oznacza, że aplikacja jest kompilowana do nowszej wersji programu .NET Framework, ale kontynuuje działanie w starszych wersjach programu .NET Framework bez utraty funkcjonalności. Oczywiście nie będzie w przypadku funkcji wprowadzonych w nowej wersji programu .NET Framework.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 Począwszy od wersji 1.1 dla programu .NET Framework Data Provider for ODBC (<xref:System.Data.Odbc>) jest dołączony jako część programu .NET Framework. Dostawca danych ODBC jest dostępna dla programu .NET Framework w wersji 1.0 deweloperów do pobrania w sieci Web z [dostępu do danych i Centrum deweloperów magazynu](https://go.microsoft.com/fwlink/?linkid=4173). Przestrzeń nazw dla pobranego .NET Framework Data Provider for ODBC jest **Microsoft.Data.Odbc**.  
  
 Jeśli masz aplikacja opracowana dla .NET Framework w wersji 1.0, która używa dostawcy danych ODBC nawiązywania połączenia ze źródłem danych, a użytkownik chce uruchomić tę aplikację na .NET Framework w wersji 1.1 lub nowszej wersji, należy zaktualizować przestrzeni nazw dla ODBC dat od dostawcy **System.Data.Odbc**. Możesz następnie należy ponownie skompilować go do nowszej wersji programu .NET Framework.  
  
 Jeśli masz aplikacja opracowana dla .NET Framework w wersji 2.0 lub nowszych korzystającą z dostawcy danych ODBC w celu połączenia ze źródłem danych, a użytkownik chce uruchomić tę aplikację w środowisku .NET Framework w wersji 1.0, należy pobrać dostawcę danych ODBC i zainstaluj ją w systemie .NET Framework w wersji 1.0. Następnie należy zmienić obszar nazw dla dostawcy danych ODBC, aby **Microsoft.Data.Odbc**i ponownie skompilować aplikację dla platformy .NET Framework w wersji 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle  
 Począwszy od wersji 1.1 dla programu .NET Framework Data Provider for Oracle (<xref:System.Data.OracleClient>) jest dołączony jako część programu .NET Framework. Dostawca danych jest dostępna dla programu .NET Framework w wersji 1.0 deweloperów do pobrania w sieci Web z [dostępu do danych i Centrum deweloperów magazynu](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Jeśli masz aplikacja opracowana dla .NET Framework w wersji 2.0 lub nowszej, która używa dostawcy danych do łączenia ze źródłem danych, a użytkownik chce uruchomić tę aplikację w środowisku .NET Framework w wersji 1.0, należy pobrać dostawcy danych i zainstaluj go na .NE T Framework w wersji 1.0 systemu.  
  
## <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Dostawcy danych .NET Framework w programie .NET Framework w wersji 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) są wymagane do uruchomienia przy użyciu uprawnień FullTrust. Dowolne próba użycia dostawcy danych .NET Framework k, z programu .NET Framework w wersji 1.0 w strefie z mniej niż powoduje, że uprawnienie FullTrust <xref:System.Security.SecurityException>.  
  
 Jednak począwszy od programu .NET Framework w wersji 2.0 wszystkie dostawcy danych .NET Framework może służyć w częściowo zaufanej strefy. Ponadto nowa funkcja zabezpieczeń został dodany do dostawcy danych .NET Framework w programie .NET Framework w wersji 1.1. Ta funkcja pozwala ograniczyć połączenia, jakie ciągi mogą być używane w strefie zabezpieczeń. Można również wyłączyć używanie pustych haseł dla określonej strefy. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Każdej instalacji programu .NET Framework jest oddzielnym pliku Security.config —, dlatego nie istnieją żadne problemy ze zgodnością przy użyciu ustawień zabezpieczeń. Jednak jeśli aplikacja zależy od możliwości zapewnienia dodatkowych zabezpieczeń programu ADO.NET, zawarty w .NET Framework w wersji 1.1 lub nowszej, nie będzie możliwe rozprowadzić go na system w wersji 1.0.  
  
## <a name="sqlcommand-execution"></a>Wykonywanie polecenia SqlCommand  
 Począwszy od programu .NET Framework w wersji 1.1, sposób który <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonuje polecenia na dane źródło zostało zmienione.  
  
 W .NET Framework w wersji 1.0 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonane wszystkie polecenia w kontekście **sp_executesql** procedury składowanej. W wyniku polecenia, które wpływają na stan połączenia (na przykład SET NOCOUNT ON), dotyczą tylko wykonywania bieżącego polecenia. Stan połączenia nie jest modyfikowany dla polecenia wykonany, podczas gdy połączenie jest otwarte.  
  
 W .NET Framework w wersji 1.1 i nowszych wersjach <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> tylko uruchamia polecenia w kontekście **sp_executesql** procedury składowanej, jeśli polecenie zawiera parametry, co zapewnia korzyści wydajności. W rezultacie Jeśli polecenie wpływu na stan połączenia znajduje się za pomocą polecenia bez parametrów, modyfikuje stan połączenia dla wszystkich kolejnych poleceń wykonany, podczas gdy połączenie jest otwarte.  
  
 Należy wziąć pod uwagę następujące partii poleceń wykonanych podczas wywołania <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 W .NET Framework w wersji 1.1 i nowszych NOCOUNT pozostanie ON polecenia wykonany, podczas gdy połączenie jest otwarte. W .NET Framework w wersji 1.0 NOCOUNT jest tylko ON dla bieżącego wykonywania polecenia.  
  
 Ta zmiana może wpłynąć na przód i Wstecz zgodności aplikacji, jeśli zależą od zachowania <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> dla danej wersji programu .NET Framework.  
  
 W przypadku aplikacji korzystających z zarówno starszych i nowszych wersjach .NET Framework można napisać kod, aby upewnić się, że zachowanie jest takie same, niezależnie od wersji, które są uruchomione na. Jeśli chcesz upewnić się, że polecenie modyfikuje stan połączenia dla wszystkich kolejnych poleceń, zaleca się wykonanie za pomocą polecenia <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Jeśli chcesz upewnić się, że polecenie nie powoduje modyfikacji połączenia dla wszystkich kolejnych poleceń, zaleca się, że zawrzesz poleceń można zresetować stan połączenia w poleceniu. Na przykład:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
