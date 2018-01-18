---
title: Uzyskiwanie DbProviderFactory
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a018447b790dde047bd76e1319a13aa3f77ffc61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="obtaining-a-dbproviderfactory"></a>Uzyskiwanie DbProviderFactory
Proces uzyskiwania <xref:System.Data.Common.DbProviderFactory> obejmuje przekazanie informacji o dostawcy danych do <xref:System.Data.Common.DbProviderFactories> klasy. Na podstawie tych informacji <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda tworzy fabrykę jednoznacznie dostawcy. Na przykład, aby utworzyć <xref:System.Data.SqlClient.SqlClientFactory>, można przekazać `GetFactory` ciągu o podanej nazwie dostawcy jako "System.Data.SqlClient". Inne przeciążenia `GetFactory` przyjmuje <xref:System.Data.DataRow>. Po utworzeniu fabryki dostawców można następnie użyć jego metody można utworzyć dodatkowe obiekty. Niektóre metody `SqlClientFactory` obejmują <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, i <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, i <xref:System.Data.OleDb.OleDbFactory> klasy udostępniają podobnych możliwościach.  
  
## <a name="registering-dbproviderfactories"></a>Rejestrowanie DbProviderFactories  
 Każdy dostawca danych .NET Framework obsługującą na podstawie fabryki klasy rejestruje informacje o konfiguracji w **DbProviderFactories** sekcji **machine.config** plik na komputerze lokalnym. Poniższy fragment pliku konfiguracji przedstawiono składnię i format <xref:System.Data.SqlClient>.  
  
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
  
 **Niezmiennej** atrybut określa podstawowego dostawcy danych. Ta składnia nazwy trzyczęściowej służy również podczas tworzenia nowego fabryki i identyfikowania dostawcy w pliku konfiguracji aplikacji, aby nazwa dostawcy, wraz z jego parametrów połączenia skojarzone, mogą być pobierane w czasie wykonywania.  
  
## <a name="retrieving-provider-information"></a>Trwa pobieranie informacji o dostawcy  
 Można pobrać informacji o wszystkich dostawców danych zainstalowany na komputerze lokalnym przy użyciu <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody. Zwraca <xref:System.Data.DataTable> o nazwie **DbProviderFactories** zawiera kolumny opisane w poniższej tabeli.  
  
|Kolumny o liczbie porządkowej|Nazwa kolumny|Przykładowe dane wyjściowe|Opis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Nazwa**|Dostawca danych SqlClient|Czytelna nazwa dostawcy danych|  
|1|**Opis**|Dostawca danych programu .net framework dla serwera SQL|Czytelny opis dostawcy danych|  
|2|**Invatiantname**|System.Data.SqlClient|Nazwa programowo służący do odwoływania się do dostawcy danych|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Pełna nazwa klasy fabryki, która zawiera wystarczających informacji do utworzenia wystąpienia obiektu|  
  
 To `DataTable` może służyć do włączenia użytkownikowi na wybranie <xref:System.Data.DataRow> w czasie wykonywania. Wybrane `DataRow` można następnie przekazać do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodę w celu utworzenia silnie typizowaną <xref:System.Data.Common.DbProviderFactory>. Zaznaczony <xref:System.Data.DataRow> mogą zostać przekazane do `GetFactory` metodę w celu utworzenia żądaną `DbProviderFactory` obiektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Lista zainstalowanego dostawcę fabryki klas  
 W tym przykładzie przedstawiono sposób użycia <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metodę, aby zwrócić <xref:System.Data.DataTable> zawierający informacje o zainstalowanych dostawców. Kod iteruje każdego wiersza w `DataTable`, wyświetlane informacje dotyczące poszczególnych zainstalowanych dostawców w oknie konsoli.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Za pomocą plików konfiguracji aplikacji do przechowywania informacji o fabryki  
 Wzorzec projektowy używane do pracy z fabryki pociąga za sobą przechowywania informacji o ciągu połączenia i dostawcy w pliku konfiguracji aplikacji, takich jak **app.config** dla aplikacji systemu Windows i **pliku web.config**  dla aplikacji ASP.NET.  
  
 Poniższy fragment pliku konfiguracji pokazano, jak zapisać dwa parametry połączenia nazwanego, "NorthwindSQL" dla połączenia z bazą danych Northwind w programie SQL Server, a "NorthwindAccess" dla połączenia z bazą danych Northwind w dostępu/Jet. **Niezmiennej** nazwa jest używana przez **providerName** atrybutu.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Podczas pobierania ciągu połączenia, według nazwy dostawcy  
 Aby można było utworzyć fabryki dostawcy, musisz podać parametry połączenia, a także nazwę dostawcy. W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracji aplikacji przez przekazanie w formacie niezmiennej nazwy dostawcy "*System.Data.ProviderName*". Iteruje po kodzie <xref:System.Configuration.ConnectionStringSettingsCollection>. Zwraca <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> w przypadku powodzenia; w przeciwnym razie `null` (`Nothing` w języku Visual Basic). Jeśli istnieje wiele wpisów dla dostawcy, zwracana jest pierwsza z nich znalezione. Aby uzyskać dodatkowe informacje i przykłady pobierania parametrów połączenia z plików konfiguracyjnych, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Odwołanie do `System.Configuration.dll` jest wymagane dla kodu do uruchomienia.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Tworzenie DbProviderFactory i DbConnection  
 W tym przykładzie pokazano, jak utworzyć <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection> obiektu przez przekazanie jej nazwa dostawcy w formacie "*System.Data.ProviderName*" i parametrów połączenia. A `DbConnection` obiekt jest zwracany w przypadku powodzenia; `null` (`Nothing` w języku Visual Basic) każdy błąd.  
  
 Kod uzyskuje `DbProviderFactory` przez wywołanie metody <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Następnie przy użyciu <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda tworzy <xref:System.Data.Common.DbConnection> obiektu i <xref:System.Data.Common.DbConnection.ConnectionString%2A> właściwość jest ustawiona w parametrach połączenia.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Używanie klas konfiguracji](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
