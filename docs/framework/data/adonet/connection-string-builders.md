---
title: Konstruktorzy ciągów połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 01bbf726ffa8d1c595b1ef53df420431bf28560f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758480"
---
# <a name="connection-string-builders"></a>Konstruktorzy ciągów połączenia
W starszych wersjach [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], kompilacji Sprawdzanie parametrów połączenia z połączony ciąg wartości nie zostało przeprowadzone, dzięki czemu w czasie wykonywania, generowane jest niepoprawna — słowo kluczowe <xref:System.ArgumentException>. Każdy z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych obsługę różnych składni słowa kluczowe parametrów połączenia, które konstruowania trudne ciągi prawidłowe połączenie, jeśli jest wykonywane ręcznie. Aby rozwiązać ten problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 wprowadzono nowe konstruktorów ciągu połączenia dla każdego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych. Każdy dostawca danych obejmują dziedziczący z klasy konstruktora ciąg połączenia jednoznacznie <xref:System.Data.Common.DbConnectionStringBuilder>. W poniższej tabeli wymieniono [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych i ich skojarzonych z połączeniami ciągu konstruktora klasy.  
  
|Dostawcy|Klasa ConnectionStringBuilder|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Ataki iniekcji ciąg połączenia  
 Atak iniekcji ciągu połączenia może wystąpić, gdy dynamiczne ciągów jest używany do tworzenia parametrów połączenia, które są oparte na danych wejściowych użytkownika. Jeśli ciąg nie jest zweryfikowany i złośliwych tekst lub znaków, które nie miały zmienione znaczenie, osoba atakująca może potencjalnie uzyskać dostęp poufnych danych lub innych zasobów na serwerze. Na przykład osoba atakująca może zainstalować atak dostarczając średnikiem a dołączanie dodatkowych wartości. Ciąg połączenia jest analizowana za pomocą algorytmu "ostatnim miejscu wins", a szkodliwy danych wejściowych zostanie zastąpiony wartością uzasadnione.  
  
 Konstruktor klasy ciąg połączenia są przeznaczone do wyeliminowania czynności i ochronę przed błędy składniowe i luk w zabezpieczeniach. Udostępniają one metody i właściwości odpowiadającej pary znane klucz/wartość, dozwolone przez każdy dostawca danych. Każda klasa obsługuje zbiór stałym synonimy i może dokonywać translacji z synonim do odpowiedniego dobrze znanej nazwy klucza. Testy są wykonywane dla pary klucz wartość prawidłowe i nieprawidłowa para zgłasza wyjątek. Ponadto wprowadzony wartości są obsługiwane w bezpieczny sposób.  
  
 W poniższym przykładzie pokazano sposób <xref:System.Data.SqlClient.SqlConnectionStringBuilder> obsługuje wstawionego dodatkowej wartości dla `Initial Catalog` ustawienie.  
  
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
  
 Dane wyjściowe wskazuje, że <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to poprawnie obsługiwane przez anulowanie dodatkowej wartości w podwójny cudzysłów zamiast dołączenie jej w parametrach połączenia jako nową parę klucz wartość.  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Tworzenie parametrów połączenia z plików konfiguracji  
 Jeśli niektóre elementy parametry połączenia są znane wcześniej, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania, aby utworzyć parametry połączenia pełną. Na przykład nazwa bazy danych może być znane z wyprzedzeniem, ale nie nazwę serwera. Można też użytkownika o podanie nazwy i hasła w czasie wykonywania bez możliwości iniekcję inne wartości do ciągu połączenia.  
  
 Przyjmuje jeden przeciążone konstruktory Konstruktor ciągów połączenia <xref:System.String> jako argument, co umożliwia podać ciąg połączenia częściowy, który można wykonać z danych wejściowych użytkownika. Parametry połączenia z częściowa można przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.  
  
> [!NOTE]
>  <xref:System.Configuration> Przestrzeni nazw umożliwia programowy dostęp do plików konfiguracyjnych, które używają <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji sieci Web i <xref:System.Configuration.ConfigurationManager> dla aplikacji systemu Windows. Aby uzyskać więcej informacji na temat pracy z parametrów połączenia i pliki konfiguracyjne, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Przykład  
 W przykładzie pokazano pobieranie parametry połączenia z częściowa z pliku konfiguracji i kończenie go przez ustawienie <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder>. Plik konfiguracji jest zdefiniowane w następujący sposób.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  Musisz ustawić odwołanie `System.Configuration.dll` w projekcie kodu do uruchomienia.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Bezpieczeństwo danych i poufności informacji](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
