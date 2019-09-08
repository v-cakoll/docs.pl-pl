---
title: Wykonywanie równoczesne w ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 0ada258f74338fc7cbc9435fdea8fc896bd2efd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782708"
---
# <a name="side-by-side-execution-in-adonet"></a>Wykonywanie równoczesne w ADO.NET
Wykonywanie równoczesne w .NET Framework jest możliwością wykonywania aplikacji na komputerze, na którym zainstalowano wiele wersji .NET Framework, wyłącznie przy użyciu wersji, dla której aplikacja została skompilowana. Aby uzyskać szczegółowe informacje na temat konfigurowania wykonywania równoczesnego, zobacz [Wykonywanie równoczesne](../../deployment/side-by-side-execution.md).  
  
 Aplikacja skompilowana przy użyciu jednej wersji .NET Framework może być uruchamiana w innej wersji .NET Framework. Zalecamy jednak skompilowanie wersji aplikacji dla każdej zainstalowanej wersji .NET Framework i uruchomienie ich oddzielnie. W każdym scenariuszu należy pamiętać o zmianach w ADO.NET między wersjami, które mogą mieć wpływ na zgodność z poprzednimi wersjami lub zgodność aplikacji.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Zgodność i zgodność z poprzednimi wersjami  
 Zgodność ze starszymi wersjami oznacza, że aplikacja może być skompilowana przy użyciu wcześniejszej wersji .NET Framework, ale nadal będzie działać w nowszej wersji .NET Framework. Kod ADO.NET zapisany dla .NET Framework w wersji 1,1 jest zgodny z nowszymi wersjami.  
  
 Zgodność z poprzednimi wersjami oznacza, że aplikacja jest kompilowana dla nowszej wersji .NET Framework, ale nadal działa we wcześniejszych wersjach .NET Framework bez utraty funkcjonalności. Oczywiście nie będzie to miało zastosowania w przypadku funkcji wprowadzonych w nowej wersji .NET Framework.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>Dostawca danych .NET Framework dla ODBC  
 Począwszy od wersji 1,1, .NET Framework dostawca danych dla ODBC (<xref:System.Data.Odbc>) jest dołączany jako część .NET Framework. Dostawca danych ODBC jest dostępny dla .NET Framework wersji 1,0 deweloperów w ramach pobierania sieci Web z [Centrum deweloperów dostępu do danych i magazynu](https://go.microsoft.com/fwlink/?linkid=4173). Przestrzeń nazw dla pobranych .NET Framework Dostawca danych dla ODBC to **Microsoft. Data. ODBC**.  
  
 Jeśli masz aplikację opracowaną dla .NET Framework w wersji 1,0, która używa dostawcy danych ODBC do nawiązania połączenia ze źródłem danych i chcesz uruchomić tę aplikację w .NET Framework wersji 1,1 lub nowszej, należy zaktualizować przestrzeń nazw dla ODBC dat Dostawca do **System. Data. ODBC**. Następnie należy ponownie skompilować go w celu uzyskania nowszej wersji .NET Framework.  
  
 Jeśli masz aplikację opracowaną dla .NET Framework w wersji 2,0 lub nowszej, która używa dostawcy danych ODBC do nawiązania połączenia ze źródłem danych, a chcesz uruchomić tę aplikację w .NET Framework wersji 1,0, musisz pobrać dostawcę danych ODBC i zainstalować go w systemie .NET Framework w wersji 1,0. Następnie należy zmienić przestrzeń nazw dla dostawcy danych ODBC na **Microsoft. Data. ODBC**i ponownie skompilować aplikację dla .NET Framework w wersji 1,0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Dostawca danych .NET Framework dla programu Oracle  
 Począwszy od wersji 1,1, .NET Framework dostawca danych dla programu Oracle (<xref:System.Data.OracleClient>) jest uwzględniony jako część .NET Framework. Dostawca danych jest dostępny do .NET Framework wersji 1,0 deweloperów w sieci Web, które można pobrać z [Centrum deweloperów dostępu do danych i magazynu](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Jeśli masz aplikację opracowaną dla .NET Framework w wersji 2,0 lub nowszej, która używa dostawcy danych do nawiązywania połączenia ze źródłem danych i chcesz uruchomić tę aplikację w .NET Framework wersji 1,0, należy pobrać dostawcę danych i zainstalować go na. NE System T Framework w wersji 1,0.  
  
## <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 .NET Framework dostawcy danych w .NET Framework wersji 1,0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) są wymagane do uruchamiania z uprawnieniami FullTrust. Każda próba użycia dostawców danych .NET Framework k z .NET Framework wersji 1,0 w strefie z opcją mniejszą niż FullTrust powoduje <xref:System.Security.SecurityException>.  
  
 Jednak począwszy od .NET Framework w wersji 2,0, wszyscy dostawcy danych .NET Framework mogą być używani w strefach częściowo zaufanych. Dodatkowo dodano nową funkcję zabezpieczeń do .NET Framework dostawców danych w .NET Framework wersji 1,1. Ta funkcja umożliwia ograniczenie parametrów połączenia, które mogą być używane w określonej strefie zabezpieczeń. Możesz również wyłączyć korzystanie z pustych haseł dla określonej strefy zabezpieczeń. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](code-access-security.md).  
  
 Ponieważ każda instalacja .NET Framework ma oddzielny plik Security. config, nie występują problemy ze zgodnością z ustawieniami zabezpieczeń. Jeśli jednak aplikacja zależy od dodatkowych funkcji zabezpieczeń ADO.NET, które znajdują się w .NET Framework w wersji 1,1 lub nowszej, nie będzie można dystrybuować jej do systemu w wersji 1,0.  
  
## <a name="sqlcommand-execution"></a>Wykonywanie polecenia SqlCommand  
 Począwszy od .NET Framework w wersji 1,1, sposób <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonywania poleceń w źródle danych został zmieniony.  
  
 W .NET Framework w wersji 1,0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonano wszystkie polecenia w kontekście procedury składowanej **sp_executesql** . W związku z tym polecenia, które wpływają na stan połączenia (na przykład Ustaw NOCOUNT ON), mają zastosowanie tylko do wykonywania bieżącego polecenia. Stan połączenia nie jest modyfikowany dla żadnych kolejnych poleceń wykonywanych podczas otwierania połączenia.  
  
 W .NET Framework w wersji 1,1 i nowszych <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> wykonuje polecenie tylko w kontekście procedury składowanej **sp_executesql** , jeśli polecenie zawiera parametry, które zapewnia korzyść wydajności. W związku z tym, jeśli polecenie mające wpływ na stan połączenia jest zawarte w niesparametryzowane polecenie, modyfikuje stan połączenia dla wszystkich kolejnych poleceń wykonywanych w czasie, gdy połączenie jest otwarte.  
  
 Rozważmy następujący partia poleceń wykonywanych w wywołaniu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 W .NET Framework w wersji 1,1 i nowszych wartość NOCOUNT pozostanie włączona dla wszystkich kolejnych poleceń wykonywanych podczas otwierania połączenia. W .NET Framework w wersji 1,0, NOCOUNT jest tylko w przypadku bieżącego wykonywania polecenia.  
  
 Ta zmiana może mieć wpływ na zgodność aplikacji do przodu i do tyłu, jeśli zależą od zachowania <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> dla każdej wersji .NET Framework.  
  
 W przypadku aplikacji uruchamianych na obu wcześniejszych i nowszych wersjach .NET Framework można napisać kod, aby upewnić się, że zachowanie jest takie samo niezależnie od używanej wersji programu. Jeśli chcesz się upewnić, że polecenie modyfikuje stan połączenia dla wszystkich kolejnych poleceń, zalecamy wykonanie polecenia przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Jeśli chcesz upewnić się, że polecenie nie modyfikuje połączenia dla wszystkich kolejnych poleceń, Zalecamy dołączenie poleceń w celu zresetowania stanu połączenia w poleceniu. Na przykład:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
