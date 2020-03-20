---
title: Konstruktorzy parametrów połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8cadeac0bcbf301f7d973e93435885de82052603
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151666"
---
# <a name="connection-string-builders"></a>Konstruktorzy parametrów połączeń
We wcześniejszych wersjach ADO.NET nie wystąpiło sprawdzanie w czasie kompilacji ciągów połączeń z wartościami ciągu łączonego, <xref:System.ArgumentException>dzięki czemu w czasie wykonywania niepoprawne słowo kluczowe wygenerowało plik . Każdy z dostawców danych programu .NET Framework obsługiwane różne składni dla słów kluczowych ciągu połączenia, co utrudniło konstruowanie prawidłowych ciągów połączeń, jeśli odbywa się ręcznie. Aby rozwiązać ten problem, ADO.NET 2.0 wprowadziła nowe konstruktory ciągów połączeń dla każdego dostawcy danych programu .NET Framework. Każdy dostawca danych zawiera silnie typizowana klasę konstruktora ciągów połączeń, która dziedziczy po <xref:System.Data.Common.DbConnectionStringBuilder>programie . W poniższej tabeli wymieniono dostawców danych platformy .NET Framework i skojarzone z nimi klasy konstruktora ciągów połączeń.  
  
|Dostawca|ConnectionStringBuilder, klasa|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Ataki iniekcji ciągu połączenia  
 Atak iniekcji ciągu połączenia może wystąpić, gdy dynamiczne łączenie ciągów jest używane do tworzenia ciągów połączeń, które są oparte na danych wejściowych użytkownika. Jeśli ciąg nie zostanie zweryfikowany, a złośliwy tekst lub znaki nie zostaną zmienione, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Na przykład osoba atakująca może zamontować atak, podając średnik i dołączając dodatkową wartość. Parametry połączenia są analizowane przy użyciu algorytmu "ostatni wygrywa", a wrogie dane wejściowe są zastępowane wartością uzasadnioną.  
  
 Klasy konstruktora ciągów połączeń mają na celu wyeliminowanie zgadywania i ochronę przed błędami składni i lukami w zabezpieczeniach. Zapewniają one metody i właściwości odpowiadające znanym parom klucz/wartość dozwolonym przez każdego dostawcę danych. Każda klasa utrzymuje stałą kolekcję synonimów i może tłumaczyć z synonimu na odpowiednią dobrze znaną nazwę klucza. Sprawdza są wykonywane dla prawidłowych par klucz/wartość i nieprawidłowa para zgłasza wyjątek. Ponadto wartości wstrzyknięte są obsługiwane w bezpieczny sposób.  
  
 W poniższym przykładzie <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pokazano, jak obsługuje wstawioną dodatkową wartość dla `Initial Catalog` ustawienia.  
  
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
  
 Dane wyjściowe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pokazuje, że obsługiwane to poprawnie, uciekając od dodatkowej wartości w cudzysłowie podwójne zamiast dołączania go do ciągu połączenia jako nowa para klucz/wartość.  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Tworzenie ciągów połączeń z plików konfiguracyjnych  
 Jeśli niektóre elementy ciągu połączenia są znane wcześniej, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania, aby utworzyć pełny ciąg połączenia. Na przykład nazwa bazy danych może być znana z wyprzedzeniem, ale nie nazwa serwera. Możesz też chcieć, aby użytkownik podał nazwę i hasło w czasie wykonywania bez możliwości wstrzyknąć inne wartości do ciągu połączenia.  
  
 Jeden z przeciążonych konstruktorów dla konstruktora ciągów połączeń przyjmuje <xref:System.String> jako argument, który umożliwia dostarczenie częściowego ciągu połączenia, który następnie można ukończyć z danych wejściowych użytkownika. Ciąg połączenia częściowego mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.  
  
> [!NOTE]
> Obszar <xref:System.Configuration> nazw umożliwia programowy dostęp do <xref:System.Web.Configuration.WebConfigurationManager> plików konfiguracyjnych, które używają aplikacji sieci Web i aplikacji <xref:System.Configuration.ConfigurationManager> dla systemu Windows. Aby uzyskać więcej informacji na temat pracy z ciągami połączeń i plikami konfiguracyjnymi, zobacz [Parametry połączenia i pliki konfiguracyjne](connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano pobieranie częściowego ciągu połączenia z pliku <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>konfiguracyjnego i wypełnianie go przez ustawienie programu , i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder>pliku . Plik konfiguracyjny jest zdefiniowany w następujący sposób.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Należy ustawić odwołanie do `System.Configuration.dll` w projekcie, aby kod do uruchomienia.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Parametry połączenia](connection-strings.md)
- [Bezpieczeństwo danych i poufności informacji](privacy-and-data-security.md)
- [Omówienie ADO.NET](ado-net-overview.md)
