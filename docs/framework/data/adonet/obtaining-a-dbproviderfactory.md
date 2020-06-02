---
title: Uzyskiwanie DbProviderFactory
description: Dowiedz się, jak uzyskać DbProviderFactory z klasy DbProviderFactories, aby współdziałać z określonymi źródłami danych w .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: b790c87cc3ec293c18bf730567f92b490c7c6594
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286718"
---
# <a name="obtaining-a-dbproviderfactory"></a>Uzyskiwanie DbProviderFactory
Proces uzyskiwania <xref:System.Data.Common.DbProviderFactory> informacji dotyczących dostawcy danych jest przekazywany do <xref:System.Data.Common.DbProviderFactories> klasy. Na podstawie tych informacji <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> Metoda tworzy fabrykę dostawców o jednoznacznie określonym typie. Na przykład, aby utworzyć <xref:System.Data.SqlClient.SqlClientFactory> , można przekazać `GetFactory` ciąg z nazwą dostawcy określoną jako "System. Data. SqlClient". Inne Przeciążenie `GetFactory` trwa <xref:System.Data.DataRow> . Po utworzeniu fabryki dostawcy można użyć jej metod, aby utworzyć dodatkowe obiekty. Niektóre metody `SqlClientFactory` obejmują <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A> , <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> , i <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A> .  
  
> [!NOTE]
> .NET Framework <xref:System.Data.OracleClient.OracleClientFactory> , <xref:System.Data.Odbc.OdbcFactory> i <xref:System.Data.OleDb.OleDbFactory> klasy również zapewniają podobną funkcjonalność.  
  
## <a name="registering-dbproviderfactories"></a>Rejestrowanie DbProviderFactories  
 Każdy dostawca danych .NET Framework, który obsługuje klasy oparte na fabryce, rejestruje informacje o konfiguracji w sekcji **DbProviderFactories** pliku **Machine. config** na komputerze lokalnym. Poniższy fragment pliku konfiguracji przedstawia składnię i format dla <xref:System.Data.SqlClient> .  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"
     description=".Net Framework Data Provider for SqlServer"
     type="System.Data.SqlClient.SqlClientFactory, System.Data,
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 Atrybut **niezmienny** identyfikuje bazowego dostawcę danych. Ta trzykrotna składnia nazewnictwa jest również używana podczas tworzenia nowej fabryki i do identyfikowania dostawcy w pliku konfiguracji aplikacji, tak aby nazwa dostawcy wraz ze skojarzonymi z nim parametrami połączenia mogła zostać pobrana w czasie wykonywania.  
  
## <a name="retrieving-provider-information"></a>Pobieranie informacji o dostawcy  
 Można pobrać informacje o wszystkich dostawcach danych zainstalowanych na komputerze lokalnym przy użyciu <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody. Zwraca <xref:System.Data.DataTable> nazwę **DbProviderFactories** , która zawiera kolumny opisane w poniższej tabeli.  
  
|Numer porządkowy kolumny|Nazwa kolumny|Przykładowe dane wyjściowe|Opis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Nazwa**|Dostawca danych SqlClient|Nazwa możliwa do odczytu dla dostawcy danych|  
|1|**Opis**|Dostawca danych .NET Framework dla programu SqlServer|Czytelny opis dostawcy danych|  
|2|**Invatiantname**|System.Data.SqlClient|Nazwa, która może być używana programowo do odwoływania się do dostawcy danych|  
|3|**AssemblyQualifiedName**|System. Data. SqlClient. SqlClientFactory, system. Data, Version = 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089|W pełni kwalifikowana nazwa klasy fabryki, która zawiera wystarczające informacje do utworzenia wystąpienia obiektu|  
  
 `DataTable`Można go użyć, aby umożliwić użytkownikowi wybranie <xref:System.Data.DataRow> w czasie wykonywania. Wybrane `DataRow` można następnie przesłać do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metody, aby utworzyć silnie wpisaną wartość <xref:System.Data.Common.DbProviderFactory> . Wybrany element <xref:System.Data.DataRow> może zostać przesłany do `GetFactory` metody w celu utworzenia żądanego `DbProviderFactory` obiektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Wyświetlanie listy zainstalowanych klas fabryki dostawców  
 W tym przykładzie pokazano, jak użyć <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody do zwrócenia <xref:System.Data.DataTable> informacji o zainstalowanych dostawcach. Kod wykonuje iterację każdego wiersza w `DataTable` , wyświetlając informacje dla każdego zainstalowanego dostawcy w oknie konsoli.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Przechowywanie informacji o fabryce przy użyciu plików konfiguracji aplikacji  
 Wzorzec projektowy używany do pracy z fabrykami obejmuje przechowywanie informacji o dostawcach i parametrach połączenia w pliku konfiguracyjnym aplikacji, takim jak **App. config** dla aplikacji systemu Windows i **Web. config** dla aplikacji ASP.NET.  
  
 Poniższy fragment pliku konfiguracji pokazuje, jak zapisać dwa nazwane parametry połączenia "NorthwindSQL" dla połączenia z bazą danych Northwind w SQL Server i "NorthwindAccess" w celu połączenia z bazą danych Northwind w pliku Access/Jet. Nazwa **niezmiennej** jest używana dla atrybutu **ProviderName** .  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"
     providerName="System.Data.SqlClient"
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"
     providerName="System.Data.OleDb"
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Pobieranie parametrów połączenia według nazwy dostawcy  
 Aby utworzyć fabrykę dostawcy, należy podać parametry połączenia oraz nazwę dostawcy. W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracyjnego aplikacji, przekazując nazwę dostawcy w formacie niezmiennym "*System. Data. ProviderName*". Kod wykonuje iterację przez <xref:System.Configuration.ConnectionStringSettingsCollection> . Zwraca on <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> sukces; w przeciwnym razie `null` ( `Nothing` w Visual Basic). Jeśli istnieje wiele wpisów dla dostawcy, zostanie zwrócony pierwszy z nich. Aby uzyskać więcej informacji i przykłady pobierania parametrów połączenia z plików konfiguracji, zobacz [parametry połączeń i pliki konfiguracji](connection-strings-and-configuration-files.md).  
  
> [!NOTE]
> Odwołanie do `System.Configuration.dll` jest wymagane w celu uruchomienia kodu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Tworzenie DbProviderFactory i DbConnection  
 Ten przykład ilustruje sposób tworzenia <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection> obiektu i przez przekazanie go do nazwy dostawcy w formacie "*System. Data. ProviderName*" i parametry połączenia. `DbConnection`Obiekt jest zwracany w wyniku sukcesu; `null` ( `Nothing` w Visual Basic) w przypadku dowolnego błędu.  
  
 Kod uzyskuje `DbProviderFactory` przez wywołanie <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> . Następnie <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> Metoda tworzy <xref:System.Data.Common.DbConnection> obiekt, a <xref:System.Data.Common.DbConnection.ConnectionString%2A> Właściwość jest ustawiana na parametry połączenia.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [DbProviderFactories](dbproviderfactories.md)
- [Parametry połączenia](connection-strings.md)
- [Korzystanie z klas konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [Omówienie ADO.NET](ado-net-overview.md)
