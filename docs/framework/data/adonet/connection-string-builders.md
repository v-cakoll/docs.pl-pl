---
title: Konstruktorzy parametrów połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8788c97842d157e09f7058411db43f86c66769cd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583802"
---
# <a name="connection-string-builders"></a>Konstruktorzy parametrów połączeń
We wcześniejszych wersjach programu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], w czasie kompilacji sprawdzania tak, aby w czasie wykonywania, generowany jest niepoprawna — słowo kluczowe parametrów połączenia parametrami połączonych wartości nie były wykonywane, <xref:System.ArgumentException>. Różnej składni każdego dostawcy danych .NET Framework obsługiwane w przypadku słowa kluczowe parametrów połączenia, które wprowadzone tworzenia ciągów prawidłowe połączenie jest trudne, jeśli jest wykonywane ręcznie. Aby rozwiązać ten problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 wprowadzono nowe Konstruktorzy parametrów połączeń dla każdego dostawcy danych .NET Framework. Każdy dostawca danych obejmuje połączenia silnie typizowane parametry konstruktora klasy dziedziczącej z klasy <xref:System.Data.Common.DbConnectionStringBuilder>. W poniższej tabeli wymieniono dostawcy danych .NET Framework i ich skojarzone z nimi połączenie parametry konstruktora klasy.  
  
|Dostawca|Klasa ConnectionStringBuilder|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Ataki polegające na iniekcji ciąg połączenia  
 Ataku polegającego na iniekcji ciąg połączenia może wystąpić, gdy dynamiczne ciągów jest używany do tworzenia parametrów połączenia, które są oparte na danych wejściowych użytkownika. Jeśli ciąg nie jest tekst zweryfikowane i złośliwych lub znaków, nie zawiera wyjścia, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Na przykład osoba atakująca może zainstalować ataku przez dostarczenie średnika i dołączanie dodatkowych wartości. Ciąg połączenia jest analizowany przy użyciu algorytmu "wins ostatnim miejscu", a szkodliwy danych wejściowych zostanie zastąpiony wartością uzasadnione.  
  
 Konstruktor klasy ciąg połączenia są przeznaczone do wyeliminowania wątpliwości i ochrony przed błędy składniowe i luk w zabezpieczeniach. Zapewniają one, metody i właściwości odpowiadający pary znanych klucz/wartość, w dozwolonym przez każdego dostawcy danych. Każda klasa przechowuje stałej kolekcji synonimów i może dokonywać translacji z synonimem do odpowiedniego dobrze znaną nazwą klucza. Testy są wykonywane dla pary klucz/wartość prawidłowy, i zgłasza wyjątek, parę nieprawidłowy. Ponadto wprowadzonego wartości są obsługiwane w bezpieczny sposób.  
  
 W poniższym przykładzie pokazano sposób, w jaki <xref:System.Data.SqlClient.SqlConnectionStringBuilder> obsługuje wstawiono wartość dodatkowego `Initial Catalog` ustawienie.  
  
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
  
 Dane wyjściowe pokazują, że <xref:System.Data.SqlClient.SqlConnectionStringBuilder> poprawnej obsługi to przez zmianę znaczenia wartości dodatkowej w podwójnym cudzysłowie zamiast dołączenie jej do połączenia jako nową parę klucz wartość.  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Tworzenie parametrów połączenia z plików konfiguracji  
 Jeśli wcześniej wiadomo, niektóre elementy ciągu połączenia, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania do konstruowania pełne parametry połączenia. Na przykład nazwą bazy danych może być znane z wyprzedzeniem, ale nie nazwę serwera. Można też użytkownika o podanie nazwy i hasła w czasie wykonywania bez możliwości wprowadzić inne wartości do parametrów połączenia.  
  
 Jedno z przeciążenia konstruktorów dla konstruktora parametrów połączenia wykorzystuje <xref:System.String> jako argument, co umożliwia podać ciąg połączenia częściowe, który można wykonać z danych wejściowych użytkownika. Parametry połączenia częściowe można przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.  
  
> [!NOTE]
>  <xref:System.Configuration> Przestrzeń nazw umożliwia programowy dostęp do plików konfiguracyjnych, które używają <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji sieci Web i <xref:System.Configuration.ConfigurationManager> dla aplikacji Windows. Aby uzyskać więcej informacji na temat pracy z parametrów połączenia i pliki konfiguracji, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono pobieranie parametrów połączenia częściowe z pliku konfiguracji i jego ukończenia, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder>. Plik konfiguracji jest zdefiniowana w następujący sposób.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  Należy ustawić odwołanie `System.Configuration.dll` w projekcie kodu do uruchomienia.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)
- [Bezpieczeństwo danych i poufności informacji](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
