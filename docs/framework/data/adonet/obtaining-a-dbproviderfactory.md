---
title: Uzyskiwanie DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: c84229dc1c32217099eb7ed8b90accc04cc66148
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097411"
---
# <a name="obtaining-a-dbproviderfactory"></a>Uzyskiwanie DbProviderFactory
Proces uzyskiwania <xref:System.Data.Common.DbProviderFactory> polega na przekazywanie informacji o dostawcy danych do <xref:System.Data.Common.DbProviderFactories> klasy. Na podstawie tych informacji <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda tworzy fabrykę dostawcy silnie typizowanych. Na przykład, aby utworzyć <xref:System.Data.SqlClient.SqlClientFactory>, można przekazać `GetFactory` ciąg zawierający nazwę dostawcy, określony jako "System.Data.SqlClient". Inne przeciążenia `GetFactory` przyjmuje <xref:System.Data.DataRow>. Po utworzeniu fabryki dostawców, następnie umożliwia jej metod do tworzenia obiektów dodatkowych. Niektóre metody `SqlClientFactory` obejmują <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, i <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, i <xref:System.Data.OleDb.OleDbFactory> klasy również zapewniają podobne funkcje.  
  
## <a name="registering-dbproviderfactories"></a>Rejestrowanie DbProviderFactories  
 Każdego dostawcy danych .NET Framework, który obsługuje klasy oparte na fabryce rejestruje informacje o konfiguracji w **DbProviderFactories** części **machine.config** pliku na komputerze lokalnym. Poniższy fragment plik konfiguracji pokazuje składnię i format <xref:System.Data.SqlClient>.  
  
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
  
 **Niezmiennej** atrybut Określa źródłowy dostawca danych. Tej składni nazewnictwa trzyczęściowej jest również używany podczas tworzenia nowej fabryki i identyfikowania dostawcy w pliku konfiguracji aplikacji, aby nazwa dostawcy, wraz z jego skojarzone parametry połączenia, mogą być pobierane w czasie wykonywania.  
  
## <a name="retrieving-provider-information"></a>Trwa pobieranie informacji o dostawcy  
 Można pobrać informacji o wszystkich dostawców danych zainstalowany na komputerze lokalnym przy użyciu <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody. Zwraca <xref:System.Data.DataTable> o nazwie **DbProviderFactories** zawierający kolumny opisane w poniższej tabeli.  
  
|Kolumny o liczbie porządkowej|Nazwa kolumny|Przykładowe dane wyjściowe|Opis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Nazwa**|Dostawca danych SqlClient|Czytelna nazwa dostawcy danych|  
|1|**Opis**|.NET framework Data Provider Pro SqlServer|Czytelny opis dostawcy danych|  
|2|**InvariantName**|System.Data.SqlClient|Nazwy, które umożliwiają programowe do odwoływania się do dostawcy danych|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|W pełni kwalifikowana nazwa klasy fabryki, która zawiera wystarczająco dużo informacji, aby utworzyć wystąpienie obiektu|  
  
 To `DataTable` może służyć do włączyć użytkownikowi na wybranie <xref:System.Data.DataRow> w czasie wykonywania. Wybrane `DataRow` mogą być następnie przekazywany do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodę, aby utworzyć silnie typizowaną <xref:System.Data.Common.DbProviderFactory>. Wybrane <xref:System.Data.DataRow> mogą być przekazywane do `GetFactory` metodę, aby utworzyć żądany `DbProviderFactory` obiektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Lista klas fabryki zainstalowanego dostawcę  
 W tym przykładzie przedstawiono sposób użycia <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metodę, aby zwrócić <xref:System.Data.DataTable> zawierający informacje o zainstalowanych dostawców. Kod wykonuje iterację przez każdego wiersza w `DataTable`, wyświetlanie informacji dla każdego zainstalowanego dostawcę w oknie konsoli.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Za pomocą plików konfiguracji aplikacji do Store informacje o fabryce  
 Wzorzec projektowy używany do pracy z fabryki pociąga za sobą przechowywanie informacji o parametrach połączenia i dostawcy w pliku konfiguracji aplikacji, takich jak **app.config** dla aplikacji Windows i **pliku web.config**  dla aplikacji ASP.NET.  
  
 Poniższy fragment plik konfiguracji pokazuje, jak zapisać dwa parametry połączenia nazwanego, "NorthwindSQL" dla połączenia z bazą danych Northwind w programie SQL Server i "NorthwindAccess" dla połączenia z bazą danych Northwind w dostęp/Jet. **Niezmiennej** nazwa jest używana dla **providerName** atrybutu.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Pobieranie parametrów połączenia, nazwa dostawcy  
 Aby można było utworzyć fabryki dostawców, musisz podać parametry połączenia, a także nazwę dostawcy. W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracji aplikacji, przekazując nazwę dostawcy w formacie niezmiennym "*System.Data.ProviderName*". Kod wykonuje iterację przez <xref:System.Configuration.ConnectionStringSettingsCollection>. Zwraca <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> w przypadku powodzenia; w przeciwnym razie `null` (`Nothing` w języku Visual Basic). Jeśli istnieje wiele wpisów dla dostawcy, zwracany jest pierwszego znalezionego. Aby uzyskać więcej informacji i przykładów pobierania parametrów połączenia z plików konfiguracyjnych, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Odwołanie do `System.Configuration.dll` jest wymagana dla kodu do uruchomienia.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Tworzenie DbProviderFactory i DbConnection  
 Ten przykład przedstawia sposób tworzenia <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection> obiektu przez przekazanie jej nazwę dostawcy, w formacie "*System.Data.ProviderName*" i parametry połączenia. A `DbConnection` obiekt jest zwracany w przypadku powodzenia; `null` (`Nothing` w języku Visual Basic) każdy błąd.  
  
 Kod uzyskuje `DbProviderFactory` przez wywołanie metody <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. A następnie <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda tworzy <xref:System.Data.Common.DbConnection> obiektu i <xref:System.Data.Common.DbConnection.ConnectionString%2A> właściwość jest ustawiona na parametry połączenia.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)
- [Przy użyciu klas konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [Omówienie ADO.NET](ado-net-overview.md)
