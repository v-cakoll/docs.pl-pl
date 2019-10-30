---
title: Konstruktorzy parametrów połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: e1f8d636e793b2d8b984fe1aa0b823fa58a4981d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040181"
---
# <a name="connection-string-builders"></a>Konstruktorzy parametrów połączeń
We wcześniejszych wersjach programu ADO.NET sprawdzanie czasu kompilacji parametrów połączenia z połączonymi wartościami ciągu nie zakończyło się, więc w czasie wykonywania nieprawidłowe słowo kluczowe wygenerowało <xref:System.ArgumentException>. Każdy dostawca danych .NET Framework obsługuje inną składnię dla słów kluczowych parametrów połączenia, która sprawia, że prawidłowe parametry połączenia są trudne, jeśli zostały wykonane ręcznie. Aby rozwiązać ten problem, ADO.NET 2,0 wprowadził nowe konstruktory parametrów połączenia dla każdego dostawcy danych .NET Framework. Każdy dostawca danych zawiera klasę konstruktora parametrów połączenia o jednoznacznie określonym typie, która dziedziczy po <xref:System.Data.Common.DbConnectionStringBuilder>. Poniższa tabela zawiera listę dostawców danych .NET Framework i skojarzonych z nimi klas konstruktorów parametrów połączenia.  
  
|Dostawcy|Klasa ConnectionStringBuilder|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Ataki przed iniekcją parametrów połączenia  
 Atak polegający na iniekcji parametrów połączenia może wystąpić, gdy dynamiczne łączenie ciągów służy do tworzenia parametrów połączenia opartych na danych wejściowych użytkownika. Jeśli ciąg nie zostanie sprawdzony i złośliwy tekst lub znaki nie zostały zmienione, osoba atakująca może uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Na przykład osoba atakująca może zainstalować atak, dostarczając średnik i dołączając dodatkową wartość. Parametry połączenia są analizowane przy użyciu algorytmu "ostatni jeden WINS", a dane wejściowe nieszkodliwy jest zastępowany dla wiarygodnej wartości.  
  
 Klasy konstruktora parametrów połączenia zostały zaprojektowane w celu wyeliminowania wątpliwości i ochrony przed błędami składni i lukami w zabezpieczeniach. Udostępniają one metody i właściwości odpowiadające znanym par klucz/wartość dozwolonym przez każdego dostawcę danych. Każda klasa przechowuje stałe kolekcje synonimów i może przetłumaczyć ze synonimu na odpowiadającą mu dobrze znaną nazwę klucza. Testy są wykonywane dla prawidłowych par klucz/wartość i nieprawidłowa para zgłasza wyjątek. Ponadto wartości wstrzykiwane są obsługiwane w bezpieczny sposób.  
  
 Poniższy przykład ilustruje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> obsługuje wstawioną dodatkową wartość dla ustawienia `Initial Catalog`.  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 Dane wyjściowe pokazują, że <xref:System.Data.SqlClient.SqlConnectionStringBuilder> prawidłowo obsłużył to przez anulowanie dodatkowej wartości w podwójnym cudzysłowie zamiast dołączania do parametrów połączenia jako nowej pary klucz/wartość.  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Kompilowanie parametrów połączenia z plików konfiguracji  
 Jeśli niektóre elementy parametrów połączenia są znane wcześniej, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania w celu skonstruowania kompletnych parametrów połączenia. Na przykład nazwa bazy danych może być znana z wyprzedzeniem, ale nie z nazwą serwera. Może też być konieczne podanie przez użytkownika nazwy i hasła w czasie wykonywania bez możliwości wprowadzania innych wartości do parametrów połączenia.  
  
 Jeden z przeciążonych konstruktorów dla konstruktora parametrów połączenia przyjmuje <xref:System.String> jako argument, dzięki czemu można podawać częściowe parametry połączenia, które następnie można wykonać przy użyciu danych wejściowych użytkownika. Częściowe parametry połączenia mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.  
  
> [!NOTE]
> Przestrzeń nazw <xref:System.Configuration> umożliwia programistyczny dostęp do plików konfiguracji, które używają <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji sieci Web i <xref:System.Configuration.ConfigurationManager> aplikacji systemu Windows. Aby uzyskać więcej informacji na temat pracy z parametrami połączenia i plikami konfiguracji, zobacz [parametry połączeń i pliki konfiguracji](connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak pobrać częściowe parametry połączenia z pliku konfiguracji i zakończyć je przez ustawienie właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>. Plik konfiguracji jest definiowany w następujący sposób.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Należy ustawić odwołanie do `System.Configuration.dll` w projekcie, aby kod mógł zostać uruchomiony.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Parametry połączeń](connection-strings.md)
- [Bezpieczeństwo danych i poufności informacji](privacy-and-data-security.md)
- [Omówienie ADO.NET](ado-net-overview.md)
