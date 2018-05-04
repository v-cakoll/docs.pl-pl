---
title: Nawiązywania połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: a416994e5d5a1be5da9571d9f8e7564f0f14f238
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="establishing-the-connection"></a>Nawiązywania połączenia
Aby nawiązać połączenie programu Microsoft SQL Server, należy użyć <xref:System.Data.SqlClient.SqlConnection> obiekt dostawcy danych programu .NET Framework dla programu SQL Server. Aby połączyć się ze źródłem danych OLE DB, użyć <xref:System.Data.OleDb.OleDbConnection> obiektu .NET Framework Data Provider for OLE DB. Aby połączyć źródła danych ODBC, użyj <xref:System.Data.Odbc.OdbcConnection> obiekt dostawcy danych programu .NET Framework dla ODBC. Aby połączyć się ze źródłem danych programu Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu .NET Framework Data Provider for Oracle. W celu bezpiecznego przechowywania i pobierania parametry połączenia, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Zamykanie połączenia  
 Firma Microsoft zaleca zawsze zamknąć połączenie po zakończeniu korzystania z niego, dzięki czemu połączenie może być zwracany do puli. `Using` Blokowanie w języku Visual Basic i C# automatycznie usuwa połączenia gdy kod jest kończona bloku, nawet w przypadku nieobsługiwany wyjątek. Zobacz [za pomocą instrukcji](~/docs/csharp/language-reference/keywords/using-statement.md) i [instrukcji Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Aby uzyskać więcej informacji.  
  
 Można również użyć `Close` lub `Dispose` metody obiektu połączenia dla dostawcy, którego używasz. Połączenia, które nie są jawnie zamknięty, nie może dodać lub zwrócony do puli. Na przykład, która wykroczyła poza zakres, ale które nie zostały jawnie zamknął połączenie tylko powróci do puli połączeń Osiągnięto maksymalny rozmiar puli, jeśli połączenie jest nadal ważny. Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i użycia puli połączeń Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Nie wywołuj `Close` lub `Dispose` na **połączenia**, **DataReader**, lub innego obiektu zarządzanego w `Finalize` metody klasy. W finalizator zwolnić tylko niezarządzane zasoby, które bezpośrednio należą do klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Zdarzenia logowania i wylogowywania nie będą zgłaszane na serwerze gdy połączenie jest pobranych z lub zwrócony do puli połączeń, ponieważ połączenie nie jest w rzeczywistości zamknięte zwracanie do puli połączeń. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Łączenie z serwerem SQL  
 .NET Framework Data Provider for SQL Server obsługuje format parametrów połączenia, który jest podobny do formatu ciągu połączenia OLE DB (ADO). Nieprawidłowy ciąg formatu nazwy i wartości, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu. Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasę, aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Poniższy przykład kodu pokazuje sposób tworzenia i otwierania połączenia z bazą danych programu SQL Server.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a>Zintegrowane zabezpieczenia i platformy ASP.NET  
 SQL Server zintegrowane zabezpieczenia (znanej także jako zaufanych połączeń) ułatwia ochronę podczas nawiązywania połączenia z programem SQL Server, ponieważ nie ujawnia Identyfikatora użytkownika i hasła w parametrach połączenia i jest to zalecana metoda uwierzytelniania połączenia. Zintegrowane zabezpieczenia używa bieżącej tożsamości zabezpieczeń lub token wykonywania procesu. Dla aplikacji klasycznych zazwyczaj jest to tożsamość aktualnie zalogowanego użytkownika.  
  
 Tożsamość zabezpieczeń dla aplikacji ASP.NET można wybrać jedno z kilku różnych opcji. Aby lepiej zrozumieć tożsamości zabezpieczeń, która aplikacja ASP.NET używa podczas nawiązywania połączenia z programem SQL Server, zobacz [personifikacji aplikacji ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [Uwierzytelnianie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), i [porady: dostęp do programu SQL Zabezpieczenia zintegrowane przy użyciu systemu Windows Server](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Nawiązywanie połączenia źródła danych OLE DB  
 .NET Framework Data Provider for OLE DB udostępnia połączenie ze źródłami danych ujawnianej za pomocą OLE DB (za pośrednictwem SQLOLEDB, dostawca OLE DB dla programu SQL Server), za pomocą **oledbconnection —** obiektu.  
  
 Dla .NET Framework Data Provider for OLE DB format ciągu połączenia jest taki sam jak format parametrów połączenia, które są używane w ADO, z następującymi wyjątkami:  
  
-   **Dostawcy** — słowo kluczowe jest wymagana.  
  
-   **Adres URL**, **dostawcy zdalnym**, i **serwera zdalnego** słowa kluczowe nie są obsługiwane.  
  
 Aby uzyskać więcej informacji dotyczących parametrów połączenia OLE DB, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tematu. Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> Aby utworzyć parametry połączenia w czasie wykonywania.  
  
> [!NOTE]
>  **Oledbconnection —** obiekt nie obsługuje ustawiania lub pobierania właściwości dynamicznych, które są specyficzne dla dostawcy OLE DB. Obsługiwane są tylko właściwości, które mogą zostać przekazane w parametrach połączenia dla dostawcy OLE DB.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia i otwierania połączenia ze źródłem danych OLE DB.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a>Nie używaj Universal Data Link plików  
 Można podać informacje o połączeniu **oledbconnection —** w plik Universal Data Link (UDL); jednak należy unikać w ten sposób. Pliki UDL nie są szyfrowane i ujawniać informacje o parametrach połączenia w postaci zwykłego tekstu. Ponieważ plik UDL zewnętrzny zasób opartych na plikach do aplikacji, nie może być chronione przy użyciu programu .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Nawiązywanie połączenia źródła danych ODBC  
 .NET Framework Data Provider for ODBC udostępnia połączenie ze źródłami danych ujawnianej za pomocą ODBC przy użyciu **OdbcConnection** obiektu.  
  
 Dla .NET Framework Data Provider for ODBC format ciągu połączenia jest przeznaczony do możliwie najbardziej zgodna z formatem ciągu połączenia ODBC. Może też podawać nazwę źródła danych (DSN) ODBC. Aby uzyskać więcej szczegółów na **OdbcConnection** , zobacz <xref:System.Data.Odbc.OdbcConnection>.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia i otwierania połączenia źródła danych ODBC.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a>Połączenie ze źródłem danych programu Oracle  
 .NET Framework Data Provider for Oracle udostępnia połączenie ze źródłami danych Oracle przy użyciu **OracleConnection** obiektu.  
  
 Dla .NET Framework Data Provider for Oracle format ciągu połączenia jest przeznaczony do możliwie najbardziej zgodne z dostawcy OLE DB dla formatu ciągu połączenia Oracle (MSDAORA). Aby uzyskać więcej szczegółów na **OracleConnection**, zobacz <xref:System.Data.OracleClient.OracleConnection>.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia i otwierania połączenia ze źródłem danych programu Oracle.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Buforowanie połączenia Oracle, OLE DB i ODBC](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
