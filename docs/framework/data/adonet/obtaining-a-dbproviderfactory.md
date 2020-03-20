---
title: Uzyskiwanie DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 0e2efd593019199ff641610b8602825cc60d4661
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149469"
---
# <a name="obtaining-a-dbproviderfactory"></a>Uzyskiwanie DbProviderFactory
Proces uzyskiwania <xref:System.Data.Common.DbProviderFactory> danych obejmuje przekazywanie informacji o <xref:System.Data.Common.DbProviderFactories> dostawcy danych do klasy. Na podstawie tych <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> informacji metoda tworzy silnie typizowana fabryka dostawcy. Na przykład, aby <xref:System.Data.SqlClient.SqlClientFactory>utworzyć , `GetFactory` można przekazać ciąg o nazwie dostawcy określonej jako "System.Data.SqlClient". Inne przeciążenie `GetFactory` trwa <xref:System.Data.DataRow>. Po utworzeniu fabryki dostawcy, można następnie użyć jego metod do tworzenia dodatkowych obiektów. Niektóre z metod `SqlClientFactory` obejmują <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A> <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>i .  
  
> [!NOTE]
> .NET Framework <xref:System.Data.OracleClient.OracleClientFactory> <xref:System.Data.Odbc.OdbcFactory>, <xref:System.Data.OleDb.OleDbFactory> i klasy również zapewniają podobną funkcjonalność.  
  
## <a name="registering-dbproviderfactories"></a>Rejestrowanie DbProviderFactoryries  
 Każdy dostawca danych programu .NET Framework obsługujący klasę fabryczną rejestruje informacje o konfiguracji w sekcji **DbProviderFactories** pliku **machine.config** na komputerze lokalnym. Poniższy fragment pliku konfiguracji przedstawia składnię i format programu <xref:System.Data.SqlClient>.  
  
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
  
 Atrybut **niezmienny** identyfikuje dostawcę danych źródłowych. Ta trzyczęściowa składnia nazewnictwa jest również używana podczas tworzenia nowej fabryki i do identyfikowania dostawcy w pliku konfiguracji aplikacji, dzięki czemu nazwa dostawcy wraz ze skojarzonym ciągiem połączenia może zostać pobrana w czasie wykonywania.  
  
## <a name="retrieving-provider-information"></a>Pobieranie informacji o dostawcy  
 Można pobrać informacje o wszystkich dostawców danych zainstalowanych na <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> komputerze lokalnym przy użyciu metody. Zwraca <xref:System.Data.DataTable> o nazwie **DbProviderFactories,** który zawiera kolumny opisane w poniższej tabeli.  
  
|Liczba porządkowa kolumny|Nazwa kolumny|Przykładowe dane wyjściowe|Opis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Nazwa**|Dostawca danych SqlClient|Czytelna nazwa dostawcy danych|  
|1|**Opis**|Dostawca danych programu .Net Framework dla serwera SqlServer|Czytelny opis dostawcy danych|  
|2|**Niezmiennanama**|System.Data.SqlClient|Nazwa, która może być używana programowo w celu odwoływania się do dostawcy danych|  
|3|**Assemblyqualifiedname**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|W pełni kwalifikowana nazwa klasy fabrycznej, która zawiera wystarczającą ilość informacji do wystąpienia obiektu|  
  
 Może `DataTable` to służyć do umożliwienia <xref:System.Data.DataRow> użytkownikowi, aby wybrać w czasie wykonywania. Wybrane `DataRow` można następnie przekazać <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> do metody, aby <xref:System.Data.Common.DbProviderFactory>utworzyć silnie wpisane . Wybrane <xref:System.Data.DataRow> można przekazać do `GetFactory` metody, aby `DbProviderFactory` utworzyć żądany obiekt.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Wyświetlanie klasy fabrycznej zainstalowanego dostawcy  
 W tym przykładzie pokazano, jak użyć <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody do zwrócenia <xref:System.Data.DataTable> informacji zawierających informacje o zainstalowanych dostawcach. Kod iteruje przez każdy `DataTable`wiersz w , wyświetlanie informacji dla każdego zainstalowanego dostawcy w oknie konsoli.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Używanie plików konfiguracji aplikacji do przechowywania informacji o fabryce  
 Wzorzec projektu używany do pracy z fabrykami pociąga za sobą przechowywanie informacji o dostawcy i ciągu połączenia w pliku konfiguracji aplikacji, takich jak **app.config** dla aplikacji systemu Windows i **web.config** dla aplikacji ASP.NET.  
  
 Poniższy fragment pliku konfiguracji pokazuje, jak zapisać dwa nazwane parametry połączenia, "NorthwindSQL" dla połączenia z bazą danych Northwind w programie SQL Server i "NorthwindAccess" dla połączenia z bazą danych Northwind w programie Access/Jet. **Niezmienna** nazwa jest używana dla atrybutu **providerName.**  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Pobieranie ciągu połączenia według nazwy dostawcy  
 Aby utworzyć fabrykę dostawcy, należy podać parametry połączenia, a także nazwę dostawcy. W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracji aplikacji, przekazując nazwę dostawcy w niezmiennym formacie "*System.Data.ProviderName*". Kod iteruje przez <xref:System.Configuration.ConnectionStringSettingsCollection>. Zwraca na <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> sukces; w `null` `Nothing` przeciwnym razie (w języku Visual Basic). Jeśli istnieje wiele wpisów dla dostawcy, zwracany jest pierwszy znaleziony. Aby uzyskać więcej informacji i przykłady pobierania ciągów połączeń z plików konfiguracyjnych, zobacz [Parametry połączenia i Pliki konfiguracyjne](connection-strings-and-configuration-files.md).  
  
> [!NOTE]
> Odwołanie jest `System.Configuration.dll` wymagane w celu uruchomienia kodu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Tworzenie DbProviderFactory i DbConnection  
 W tym przykładzie pokazano, jak utworzyć <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection> obiekt, przekazując go nazwę dostawcy w formacie *"System.Data.ProviderName*" i parametry połączenia. Obiekt `DbConnection` jest zwracany po sukcesie; `null` (w`Nothing` języku Visual Basic) na każdy błąd.  
  
 Kod uzyskuje się `DbProviderFactory` przez <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>wywołanie . Następnie <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda tworzy <xref:System.Data.Common.DbConnection> obiekt <xref:System.Data.Common.DbConnection.ConnectionString%2A> i właściwość jest ustawiona na ciąg połączenia.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [DbProviderFactories](dbproviderfactories.md)
- [Parametry połączenia](connection-strings.md)
- [Korzystanie z klas konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [Omówienie ADO.NET](ado-net-overview.md)
