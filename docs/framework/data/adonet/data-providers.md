---
title: Dostawcy danych .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: d343f7be3e26575ee9a1e9ccae9f17314db10ac5
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882104"
---
# <a name="net-framework-data-providers"></a>Dostawcy danych .NET Framework
Dostawca danych .NET Framework służy do nawiązywania połączenia z bazą danych, wykonując polecenia i pobierania wyników. Te wyniki są albo przetwarzane bezpośrednio, umieszczone w <xref:System.Data.DataSet> celu uwidocznienie użytkownika zgodnie z potrzebami, połączone z danymi z wielu źródeł lub węzłach między warstwami. Dostawcy danych .NET framework są uproszczone, tworzenie minimalnej warstwy między źródłem danych i kodu, zwiększenie wydajności bez poświęcania funkcjonalności.  
  
 W poniższej tabeli wymieniono dostawcy danych, które są zawarte w .NET Framework.  
  
|Dostawca danych .NET framework|Opis|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET framework Data Provider for SQL Server|Zapewnia dostęp do danych programu Microsoft SQL Server. Używa <xref:System.Data.SqlClient> przestrzeni nazw.|  
|.NET framework Data Provider for OLE DB|W przypadku źródeł danych dostępne przy użyciu OLE DB. Używa <xref:System.Data.OleDb> przestrzeni nazw.|  
|.NET framework Data Provider for ODBC|W przypadku źródeł danych udostępnianych przez przy użyciu interfejsu ODBC. Używa <xref:System.Data.Odbc> przestrzeni nazw.|  
|.NET framework Data Provider for Oracle|W przypadku źródeł danych programu Oracle. .NET Framework Data Provider for Oracle obsługuje Oracle wersji oprogramowania 8.1.7 lub nowszy i wykorzystuje <xref:System.Data.OracleClient> przestrzeni nazw.|  
|Dostawca EntityClient|Zapewnia dostęp do danych w aplikacji Entity Data Model (EDM) struktury. Używa <xref:System.Data.EntityClient> przestrzeni nazw.|  
|.NET Framework Data Provider for SQL Server Compact 4.0.|Zapewnia dostęp do danych dla programu Microsoft SQL Server Compact 4.0. Używa [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) przestrzeni nazw.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Podstawowych obiektów dostawcy danych .NET Framework  
 W poniższej tabeli przedstawiono cztery podstawowych obiektów, które tworzą dostawcy danych .NET Framework.  
  
|Obiekt|Opis|  
|------------|-----------------|  
|`Connection`|Nawiązuje połączenie z określonym źródłem danych. Klasa bazowa dla wszystkich `Connection` obiektów jest <xref:System.Data.Common.DbConnection> klasy.|  
|`Command`|Wykonuje polecenie w odniesieniu do źródła danych. Udostępnia `Parameters` i może zostać uruchomiony w zakresie `Transaction` z `Connection`. Klasa bazowa dla wszystkich `Command` obiektów jest <xref:System.Data.Common.DbCommand> klasy.|  
|`DataReader`|Odczytuje strumień tylko do przodu, tylko do odczytu danych ze źródła danych. Klasa bazowa dla wszystkich `DataReader` obiektów jest <xref:System.Data.Common.DbDataReader> klasy.|  
|`DataAdapter`|Wypełnia `DataSet` i jest rozpoznawana jako aktualizacje ze źródłem danych. Klasa bazowa dla wszystkich `DataAdapter` obiektów jest <xref:System.Data.Common.DbDataAdapter> klasy.|  
  
 Oprócz klas podstawowych, wymienione w tabeli wcześniej w tym dokumencie dostawcy danych .NET Framework zawiera klasy wymienione w poniższej tabeli.  
  
|Obiekt|Opis|  
|------------|-----------------|  
|`Transaction`|Pozyskuje polecenia w transakcji w źródle danych. Klasa bazowa dla wszystkich `Transaction` obiektów jest <xref:System.Data.Common.DbTransaction> klasy. ADO.NET oferuje również obsługę transakcji za pomocą klasy w <xref:System.Transactions> przestrzeni nazw.|  
|`CommandBuilder`|Obiekt pomocnika, która automatycznie generuje właściwości polecenia `DataAdapter` lub wywodzi się informacje o parametrach z procedury składowanej i wypełnia `Parameters` zbiór `Command` obiektu. Klasa bazowa dla wszystkich `CommandBuilder` obiektów jest <xref:System.Data.Common.DbCommandBuilder> klasy.|  
|`ConnectionStringBuilder`|Obiekt pomocnika, która zapewnia prosty sposób tworzenia i zarządzania zawartością parametry połączenia używane przez `Connection` obiektów. Klasa bazowa dla wszystkich `ConnectionStringBuilder` obiektów jest <xref:System.Data.Common.DbConnectionStringBuilder> klasy.|  
|`Parameter`|Definiuje danych wejściowych, wyjściowych i zwracanej wartości parametrów dla polecenia i procedur składowanych. Klasa bazowa dla wszystkich `Parameter` obiektów jest <xref:System.Data.Common.DbParameter> klasy.|  
|`Exception`|Zwracane po napotkaniu błędu w źródle danych. Napotkano błąd po stronie klienta, aby uzyskać dostawcy danych .NET Framework wyjątku .NET Framework. Klasa bazowa dla wszystkich `Exception` obiektów jest <xref:System.Data.Common.DbException> klasy.|  
|`Error`|Udostępnia informacje z ostrzeżenia lub błędu zwrócony przez źródło danych.|  
|`ClientPermission`|Podana dla atrybutów zabezpieczeń dostępu kodu dostawcy danych .NET Framework. Klasa bazowa dla wszystkich `ClientPermission` obiektów jest <xref:System.Data.Common.DBDataPermission> klasy.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>Dostawca danych .NET framework dla programu SQL Server (SqlClient)  
 .NET Framework Data Provider for SQL Server (SqlClient) używa własnego protokołu do komunikowania się z programem SQL Server. Jest lekkie i wykonuje się dobrze, ponieważ jest zoptymalizowany do dostępu do programu SQL Server bezpośrednio, bez dodawania warstwy OLE DB lub Open Database Connectivity (ODBC). Na poniższej ilustracji zestawiono ze sobą dostawcy danych .NET Framework dla programu SQL Server przy użyciu .NET Framework Data Provider for OLE DB. .NET Framework Data Provider for OLE DB komunikuje się ze źródłem danych OLE DB przy użyciu zarówno składnik usługi OLE DB, który zapewnia buforowanie połączeń i transakcji usług i dostawcy OLE DB dla źródła danych.  
  
> [!NOTE]
>  .NET Framework Data Provider for ODBC ma podobną architekturę do .NET Framework Data Provider for OLE DB; na przykład wywołania do składnika usługi ODBC.  
  
 ![Data providers](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porównanie dla programu .NET Framework Data Provider for SQL Server i .NET Framework Data Provider for OLE DB  
  
 Dostawcy danych programu .NET Framework dla klas SQL Server znajdują się w <xref:System.Data.SqlClient> przestrzeni nazw.  
  
 .NET Framework Data Provider for SQL Server obsługuje zarówno lokalnych, jak i rozproszonych. Dla transakcji rozproszonych, dostawcy danych programu .NET Framework dla programu SQL Server domyślnie rejestruje w transakcji i automatycznie uzyskuje dostęp do szczegółów transakcji z usługi składowe Windows lub <xref:System.Transactions>. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Poniższy przykład kodu pokazuje, jak dołączyć `System.Data.SqlClient` przestrzeni nazw w swoich aplikacjach.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET framework Data Provider for OLE DB  
 .NET Framework Data Provider for OLE DB (OLE DB) używa natywnych OLE DB przy użyciu modelu COM, aby umożliwić dostęp do danych. .NET Framework Data Provider for OLE DB obsługuje zarówno lokalnych, jak i rozproszonych. Dla transakcji rozproszonych dostawcy danych programu .NET Framework dla OLE DB, domyślnie rejestruje w transakcji i automatycznie uzyskuje dostęp do szczegółów transakcji z usługi składowe Windows. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 W poniższej tabeli przedstawiono dostawców, które zostały przetestowane za pomocą narzędzia ADO.NET.  
  
|Sterownik|Dostawca|  
|------------|--------------|  
|SQLOLEDB|Dostawca Microsoft OLE DB dla programu SQL Server|  
|MSDAORA|Dostawca Microsoft OLE DB dla Oracle|  
|Microsoft.Jet.OLEDB.4.0|Dostawca OLE DB dla programu Microsoft Jet|  
  
> [!NOTE]
>  Przy użyciu bazy danych programu Access (Jet) jako źródło danych dla aplikacji wielowątkowych, takich jak aplikacje programu ASP.NET nie jest zalecane. Jeśli musisz użyć Jet jako źródło danych dla aplikacji ASP.NET, należy pamiętać, że aplikacje ASP.NET nawiązywania połączenia z bazą danych programu Access, mogą wystąpić problemy z połączeniem.  
  
 .NET Framework Data Provider for OLE DB nie obsługuje interfejsów wersji 2.5 OLE DB. Dostawców OLE DB, potrzebujesz pomocy technicznej dotyczącej interfejsów OLE DB 2.5 nie będzie działać prawidłowo z .NET Framework Data Provider for OLE DB. Obejmuje to dostawcy Microsoft OLE DB dla programu Exchange i dostawcy Microsoft OLE DB dla publikowania w Internecie.  
  
 .NET Framework Data Provider for OLE DB nie działa z dostawcy OLE DB dla ODBC (MSDASQL). Aby uzyskać dostęp do źródła danych ODBC, za pomocą programu ADO.NET, należy użyć dostawcy danych .NET Framework dla ODBC.  
  
 .NET framework Data Provider for OLE DB klasy znajdują się w <xref:System.Data.OleDb> przestrzeni nazw. Poniższy przykład kodu pokazuje, jak dołączyć `System.Data.OleDb` przestrzeni nazw w swoich aplikacjach.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET framework Data Provider for ODBC  
 .NET Framework Data Provider for ODBC (Odbc) używa natywnego Menedżera sterowników ODBC (DM), aby umożliwić dostęp do danych. Dostawca danych ODBC obsługuje zarówno lokalnych, jak i rozproszonych. Dla transakcji rozproszonych dostawcy danych ODBC, domyślnie rejestruje w transakcji i automatycznie uzyskuje dostęp do szczegółów transakcji z usługi składowe Windows. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 W poniższej tabeli przedstawiono sterowników ODBC, przetestowane za pomocą narzędzia ADO.NET.  
  
|Sterownik|  
|------------|  
|SQL Server|  
|Microsoft ODBC dla bazy danych Oracle|  
|Sterownika Microsoft Access (*.mdb)|  
  
 .NET framework Data Provider for ODBC — klasy znajdują się w <xref:System.Data.Odbc> przestrzeni nazw.  
  
 Poniższy przykład kodu pokazuje, jak dołączyć `System.Data.Odbc` przestrzeni nazw w swoich aplikacjach.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  .NET Framework Data Provider for ODBC wymaga MDAC w wersji 2.6 lub nowszej wersji, a MDAC 2.8 SP1 jest zalecane. Możesz pobrać MDAC 2.8 SP1 z [dostępu do danych i Centrum deweloperów magazynu](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>.NET framework Data Provider for Oracle  
 .NET Framework Data Provider for Oracle (programu OracleClient) umożliwia dostęp do danych ze źródłami danych Oracle przy użyciu łączności klienta Oracle. Dostawca danych obsługuje wersję oprogramowania klienta Oracle 8.1.7 lub nowsza wersja. Dostawca danych obsługuje zarówno lokalnych, jak i rozproszonych. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 .NET Framework Data Provider for Oracle wymaga oprogramowania klienta Oracle (wersja 8.1.7 lub nowsza wersja) w systemie, aby nawiązać połączenie ze źródłem danych programu Oracle.  
  
 .NET framework Data Provider for Oracle klasy znajdują się w <xref:System.Data.OracleClient> przestrzeni nazw i są zawarte w `System.Data.OracleClient.dll` zestawu. Użytkownik musi odwoływać się do zarówno `System.Data.dll` i `System.Data.OracleClient.dll` podczas kompilacji aplikacji, która używa dostawcy danych.  
  
 Poniższy przykład kodu pokazuje, jak dołączyć `System.Data.OracleClient` przestrzeni nazw w swoich aplikacjach.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Wybieranie dostawcy danych .NET Framework  
 W zależności od projektu i źródła danych dla aplikacji wybranego dostawcy danych .NET Framework może poprawić wydajność, możliwości i integralność aplikacji. Poniższa tabela w tym artykule omówiono zalety i ograniczenia dotyczące każdego dostawcy danych .NET Framework.  
  
|Dostawca|Uwagi|  
|--------------|-----------|  
|.NET framework Data Provider for SQL Server|Zalecane w przypadku aplikacji warstwy środkowej, które używają programu Microsoft SQL Server.<br /><br /> Zalecane w przypadku aplikacji jednowarstwowej, które używają Microsoft Database Engine (MSDE) lub SQL Server.<br /><br /> Zalecane przez użycie dostawcy OLE DB dla programu SQL Server (SQLOLEDB) przy użyciu .NET Framework Data Provider for OLE DB.|  
|.NET framework Data Provider for OLE DB|Dla programu SQL Server dla programu .NET Framework Data Provider for SQL Server jest zalecane, zamiast tego dostawcy.<br /><br /> Zalecane w przypadku aplikacji jednowarstwowej, które używają bazy danych Microsoft Access. Nie zaleca się korzystanie z bazy danych programu Access dla aplikacji warstwy środkowej.|  
|.NET framework Data Provider for ODBC|Zalecane dla Środkowej i warstwy pojedynczej aplikacji, które używają źródła danych ODBC.|  
|.NET framework Data Provider for Oracle|Zalecane dla Środkowej i warstwy pojedynczej aplikacji, które używają źródła danych programu Oracle.|  
  
## <a name="entityclient-provider"></a>Dostawca EntityClient  
 Dostawca EntityClient jest używany do uzyskiwania dostępu do danych opartych na Entity Data Model (EDM). W przeciwieństwie do innych dostawcy danych .NET Framework nie współdziała bezpośrednio ze źródłem danych. Zamiast tego używa jednostki SQL do komunikowania się z podstawowym dostawcą danych. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
