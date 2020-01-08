---
title: Dostawcy danych .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 2c986aab33f2c4dcefb5924ea61e8b9f6b3c50a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347811"
---
# <a name="net-framework-data-providers"></a>Dostawcy danych .NET Framework
Dostawca danych .NET Framework jest używany do łączenia się z bazą danych, wykonywania poleceń i pobierania wyników. Te wyniki są przetwarzane bezpośrednio, umieszczane w <xref:System.Data.DataSet>, aby można było je uwidocznić użytkownikowi w razie potrzeby, w połączeniu z danymi z wielu źródeł lub zdalnie między warstwami. Dostawcy danych .NET Framework są lekkie, tworząc minimalną warstwę między źródłem danych i kodem, zwiększając wydajność bez ograniczania funkcjonalności.  
  
 Poniższa tabela zawiera listę dostawców danych uwzględnionych w .NET Framework.  
  
|Dostawca danych .NET Framework|Opis|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET Framework Dostawca danych SQL Server|Zapewnia dostęp do danych Microsoft SQL Server. Używa przestrzeni nazw <xref:System.Data.SqlClient>.|  
|.NET Framework Dostawca danych OLE DB|Dla źródeł danych udostępnianych przy użyciu OLE DB. Używa przestrzeni nazw <xref:System.Data.OleDb>.|  
|.NET Framework Dostawca danych dla ODBC|Dla źródeł danych narażonych na korzystanie z ODBC. Używa przestrzeni nazw <xref:System.Data.Odbc>.|  
|.NET Framework Dostawca danych dla programu Oracle|Dla źródeł danych Oracle. .NET Framework Dostawca danych dla programu Oracle obsługuje oprogramowanie klienckie Oracle w wersji 8.1.7 lub nowszej, a następnie używa przestrzeni nazw <xref:System.Data.OracleClient>.|  
|Dostawca EntityClient|Zapewnia dostęp do danych dla aplikacji Entity Data Model (EDM). Używa przestrzeni nazw <xref:System.Data.EntityClient>.|  
|.NET Framework Dostawca danych SQL Server Compact 4,0.|Zapewnia dostęp do danych dla Microsoft SQL Server Compact 4,0. Używa przestrzeni nazw [System. Data. SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) .|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Podstawowe obiekty dostawców danych .NET Framework  
 W poniższej tabeli przedstawiono cztery podstawowe obiekty, które tworzą .NET Framework dostawcę danych.  
  
|Obiekt|Opis|  
|------------|-----------------|  
|`Connection`|Ustanawia połączenie z określonym źródłem danych. Klasa bazowa dla wszystkich obiektów `Connection` jest klasą <xref:System.Data.Common.DbConnection>.|  
|`Command`|Wykonuje polecenie względem źródła danych. Uwidacznia `Parameters` i może być wykonywany w zakresie `Transaction` z `Connection`. Klasa bazowa dla wszystkich obiektów `Command` jest klasą <xref:System.Data.Common.DbCommand>.|  
|`DataReader`|Odczytuje strumień danych tylko do odczytu z źródła danych. Klasa bazowa dla wszystkich obiektów `DataReader` jest klasą <xref:System.Data.Common.DbDataReader>.|  
|`DataAdapter`|Wypełnia `DataSet` i rozwiązuje aktualizacje ze źródłem danych. Klasa bazowa dla wszystkich obiektów `DataAdapter` jest klasą <xref:System.Data.Common.DbDataAdapter>.|  
  
 Oprócz klas podstawowych wymienionych w tabeli wcześniej w tym dokumencie, dostawca danych .NET Framework również zawiera klasy wymienione w poniższej tabeli.  
  
|Obiekt|Opis|  
|------------|-----------------|  
|`Transaction`|Rejestrowane są polecenia w transakcjach w źródle danych. Klasa bazowa dla wszystkich obiektów `Transaction` jest klasą <xref:System.Data.Common.DbTransaction>. ADO.NET zapewnia również obsługę transakcji przy użyciu klas w przestrzeni nazw <xref:System.Transactions>.|  
|`CommandBuilder`|Obiekt pomocnika, który automatycznie generuje właściwości polecenia `DataAdapter` lub dziedziczy informacje o parametrach z procedury składowanej i wypełnia `Parameters` kolekcję obiektu `Command`. Klasa bazowa dla wszystkich obiektów `CommandBuilder` jest klasą <xref:System.Data.Common.DbCommandBuilder>.|  
|`ConnectionStringBuilder`|Obiekt pomocnika, który zapewnia prosty sposób tworzenia zawartości parametrów połączenia używanych przez obiekty `Connection` i zarządzania nią. Klasa bazowa dla wszystkich obiektów `ConnectionStringBuilder` jest klasą <xref:System.Data.Common.DbConnectionStringBuilder>.|  
|`Parameter`|Definiuje parametry danych wejściowych, wyjściowych i wartości zwracanych dla poleceń i procedur składowanych. Klasa bazowa dla wszystkich obiektów `Parameter` jest klasą <xref:System.Data.Common.DbParameter>.|  
|`Exception`|Zwracany w przypadku napotkania błędu w źródle danych. W przypadku błędu na kliencie .NET Framework dostawcy danych zgłaszają wyjątek .NET Framework. Klasa bazowa dla wszystkich obiektów `Exception` jest klasą <xref:System.Data.Common.DbException>.|  
|`Error`|Ujawnia informacje z ostrzeżenia lub błędu zwróconego przez źródło danych.|  
|`ClientPermission`|Dostępne dla atrybutów zabezpieczeń dostępu kodu dostawcy danych .NET Framework. Klasa bazowa dla wszystkich obiektów `ClientPermission` jest klasą <xref:System.Data.Common.DBDataPermission>.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET Framework Dostawca danych SQL Server (SqlClient)  
 Dostawca danych .NET Framework dla SQL Server (SqlClient) używa własnego protokołu do komunikowania się z SQL Server. Jest to lekkie i dobrze działa, ponieważ jest zoptymalizowany pod kątem dostępu do SQL Server bezpośrednio bez dodawania warstwy OLE DB lub Open Database Connectivity (ODBC). Poniższa ilustracja kontrastuje Dostawca danych .NET Framework dla SQL Server z .NET Framework Dostawca danych dla OLE DB. Dostawca danych .NET Framework dla OLE DB komunikuje się ze OLE DB źródłem danych za pomocą składnika usługi OLE DB, który zapewnia obsługę puli połączeń i usług transakcyjnych oraz dostawcę OLE DB dla źródła danych.  
  
> [!NOTE]
> .NET Framework Dostawca danych dla ODBC ma podobną architekturę do .NET Framework Dostawca danych dla OLE DB; na przykład wywołuje do składnika usługi ODBC.  
  
 ![Dostawcy danych](./media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porównanie Dostawca danych .NET Framework dla SQL Server i .NET Framework Dostawca danych dla OLE DB  
  
 Dostawca danych .NET Framework klas SQL Server znajdują się w przestrzeni nazw <xref:System.Data.SqlClient>.  
  
 Dostawca danych .NET Framework dla SQL Server obsługuje zarówno transakcje lokalne, jak i rozproszone. W przypadku transakcji rozproszonych .NET Framework Dostawca danych dla SQL Server domyślnie automatycznie zarejestrowana w transakcji i uzyskuje szczegóły transakcji z usług składników systemu Windows lub <xref:System.Transactions>. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](transactions-and-concurrency.md).  
  
 Poniższy przykład kodu pokazuje, jak uwzględnić przestrzeń nazw `System.Data.SqlClient` w aplikacjach.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET Framework Dostawca danych OLE DB  
 .NET Framework Dostawca danych for OLE DB (OleDb) korzysta z natywnego OLE DB za pośrednictwem modelu COM Interop, aby umożliwić dostęp do danych. Dostawca danych .NET Framework dla OLE DB obsługuje zarówno transakcje lokalne, jak i rozproszone. W przypadku transakcji rozproszonych OLE DB Dostawca danych .NET Framework, domyślnie jest automatycznie rejestrowana w transakcji i uzyskuje szczegóły transakcji z usług składników systemu Windows. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](transactions-and-concurrency.md).  
  
 W poniższej tabeli przedstawiono dostawców, którzy zostali przetestowani za pomocą ADO.NET.  
  
|Sterownik|Provider|  
|------------|--------------|  
|SQLOLEDB|Dostawca OLE DB firmy Microsoft dla SQL Server|  
|MSDAORA|Dostawca OLE DB firmy Microsoft dla oprogramowania Oracle|  
|Microsoft.Jet.OLEDB.4.0|Dostawca OLE DB dla programu Microsoft Jet|  
  
> [!NOTE]
> Nie zaleca się używania bazy danych programu Access (Jet) jako źródła danych dla aplikacji wielowątkowych, takich jak aplikacje ASP.NET. Jeśli konieczne jest użycie aparatu Jet jako źródła danych dla aplikacji ASP.NET, należy pamiętać, że aplikacje ASP.NET nawiązujące połączenie z bazą danych programu Access mogą napotkać problemy z połączeniem.  
  
 Dostawca danych .NET Framework dla OLE DB nie obsługuje interfejsów OLE DB w wersji 2,5. Dostawcy OLE DB, którzy wymagają obsługi interfejsów OLE DB 2,5, nie będą działać poprawnie z Dostawca danych .NET Framework dla OLE DB. Obejmuje to dostawcę OLE DB firmy Microsoft dla programu Exchange i dostawcę OLE DB firmy Microsoft do publikacji w Internecie.  
  
 Dostawca danych .NET Framework dla OLE DB nie działa z dostawcą OLE DB dla ODBC (MSDASQL). Aby uzyskać dostęp do źródła danych ODBC przy użyciu ADO.NET, użyj Dostawca danych .NET Framework dla ODBC.  
  
 .NET Framework Dostawca danych dla klas OLE DB znajdują się w przestrzeni nazw <xref:System.Data.OleDb>. Poniższy przykład kodu pokazuje, jak uwzględnić przestrzeń nazw `System.Data.OleDb` w aplikacjach.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET Framework Dostawca danych dla ODBC  
 .NET Framework Dostawca danych dla ODBC (ODBC) używa natywnego Menedżera sterowników ODBC (DM), aby umożliwić dostęp do danych. Dostawca danych ODBC obsługuje zarówno transakcje lokalne, jak i rozproszone. W przypadku transakcji rozproszonych dostawca danych ODBC jest domyślnie automatycznie zarejestrowany w transakcji i uzyskuje szczegóły transakcji z usług składowych systemu Windows. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](transactions-and-concurrency.md).  
  
 W poniższej tabeli przedstawiono sterowniki ODBC testowane z ADO.NET.  
  
|Sterownik|  
|------------|  
|Serwer SQL|  
|ODBC firmy Microsoft dla programu Oracle|  
|Sterownik programu Microsoft Access (*. mdb)|  
  
 .NET Framework Dostawca danych dla klas ODBC znajdują się w przestrzeni nazw <xref:System.Data.Odbc>.  
  
 Poniższy przykład kodu pokazuje, jak uwzględnić przestrzeń nazw `System.Data.Odbc` w aplikacjach.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
> Dostawca danych .NET Framework dla ODBC wymaga programu MDAC 2,6 lub nowszej wersji, a zaleca się używanie programu MDAC 2,8 z dodatkiem SP1. Program MDAC 2,8 z dodatkiem SP1 można pobrać z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=5793).
  
## <a name="net-framework-data-provider-for-oracle"></a>.NET Framework Dostawca danych dla programu Oracle  
 .NET Framework Dostawca danych dla programu Oracle (OracleClient) umożliwia dostęp do danych w źródłach danych Oracle przy użyciu oprogramowania łączności klienta Oracle. Dostawca danych obsługuje oprogramowanie klienckie Oracle w wersji 8.1.7 lub nowszej. Dostawca danych obsługuje zarówno transakcje lokalne, jak i rozproszone. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](transactions-and-concurrency.md).  
  
 Aby można było nawiązać połączenie ze źródłem danych Oracle, Dostawca danych .NET Framework dla systemu Oracle wymaga oprogramowania klienckiego Oracle (w wersji 8.1.7 lub nowszej).  
  
 .NET Framework Dostawca danych dla klas Oracle znajdują się w <xref:System.Data.OracleClient> przestrzeni nazw i znajdują się w zestawie `System.Data.OracleClient.dll`. Podczas kompilowania aplikacji, która korzysta z dostawcy danych, należy odwoływać się zarówno do `System.Data.dll`, jak i `System.Data.OracleClient.dll`.  
  
 Poniższy przykład kodu pokazuje, jak uwzględnić przestrzeń nazw `System.Data.OracleClient` w aplikacjach.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Wybieranie Dostawca danych .NET Framework  
 W zależności od projektu i źródła danych aplikacji wybór .NET Framework dostawcy danych może poprawić wydajność, możliwości i integralność aplikacji. W poniższej tabeli omówiono zalety i ograniczenia poszczególnych dostawców danych .NET Framework.  
  
|Provider|Uwagi|  
|--------------|-----------|  
|.NET Framework Dostawca danych SQL Server|Zalecane w przypadku aplikacji warstwy środkowej, które używają Microsoft SQL Server.<br /><br /> Zalecane w przypadku aplikacji jednowarstwowych, które korzystają z aparatu Microsoft Database Engine (MSDE) lub SQL Server.<br /><br /> Zalecane użycie dostawcy OLE DB dla SQL Server (SQLOLEDB) z Dostawca danych .NET Framework dla OLE DB.|  
|.NET Framework Dostawca danych OLE DB|W przypadku SQL Server zaleca się .NET Framework Dostawca danych dla SQL Server zamiast tego dostawcy.<br /><br /> Zalecane w przypadku aplikacji jednowarstwowych, które korzystają z baz danych programu Microsoft Access. Nie zaleca się używania bazy danych programu Access dla aplikacji warstwy środkowej.|  
|.NET Framework Dostawca danych dla ODBC|Zalecane w przypadku aplikacji środkowych i jednowarstwowych, które korzystają ze źródeł danych ODBC.|  
|.NET Framework Dostawca danych dla programu Oracle|Zalecane w przypadku aplikacji środkowych i jednowarstwowych, które korzystają ze źródeł danych Oracle.|  
  
## <a name="entityclient-provider"></a>Dostawca EntityClient  
 Dostawca EntityClient służy do uzyskiwania dostępu do danych na podstawie Entity Data Model (EDM). W przeciwieństwie do innych dostawców danych .NET Framework, nie współdziała bezpośrednio ze źródłem danych. Zamiast tego używa Entity SQL do komunikowania się z dostawcą danych bazowych. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
