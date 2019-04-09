---
title: Nawiązywanie połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 7f8cca02e673339e892c16e0de99e20accdfd404
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142347"
---
# <a name="establishing-the-connection"></a>Nawiązywanie połączenia
Aby połączyć z programem Microsoft SQL Server, należy użyć <xref:System.Data.SqlClient.SqlConnection> obiektu .NET Framework Data Provider for SQL Server. Aby połączyć się ze źródłem danych OLE DB, użyj <xref:System.Data.OleDb.OleDbConnection> obiektu .NET Framework Data Provider for OLE DB. Aby połączyć się ze źródłem danych ODBC, użyj <xref:System.Data.Odbc.OdbcConnection> obiekt dostawcy danych programu .NET Framework dla ODBC. Aby połączyć się ze źródłem danych Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu .NET Framework Data Provider for Oracle. Bezpieczne przechowywanie i pobieranie parametrów połączenia, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Zamykanie połączenia  
 Firma Microsoft zaleca, aby zawsze zamykaj połączenie po zakończeniu korzystania z niego, tak aby połączenie mogą być zwrócone do puli. `Using` Blokowania w języku Visual Basic lub C# automatycznie usuwa połączenia gdy kod zamyka blok, nawet w przypadku nieobsługiwanego wyjątku. Zobacz [za pomocą instrukcji](~/docs/csharp/language-reference/keywords/using-statement.md) i [instrukcji Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Aby uzyskać więcej informacji.  
  
 Można również użyć `Close` lub `Dispose` metody obiektu połączenia do dostawcy, którego używasz. Połączenia, które nie są jawnie zamknięty, nie może dodać lub zwrócone do puli. Na przykład połączenia, który przeszedł poza zakresem, ale które nie zostało jawnie zamknięte tylko powróci do puli połączeń, jeśli osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważny. Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i buforowanie połączenia Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Nie wywołuj `Close` lub `Dispose` na **połączenia**, **DataReader**, lub inne obiekt zarządzany w `Finalize` metody klasy. W finalizatora zwolnić tylko niezarządzane zasoby, które należą bezpośrednio do swojej klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w swojej definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Zdarzenia logowania i wylogowania nie zostaną wywołane na serwerze gdy połączenie zostanie pobrana z lub zwrócone do puli połączeń, ponieważ połączenie nie jest w rzeczywistości zamykane, gdy zostaje zwrócony do puli połączeń. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Łączenie z serwerem SQL  
 .NET Framework Data Provider for SQL Server obsługuje format parametrów połączenia, który jest podobny do formatu parametrów połączenia OLE DB (ADO). Nieprawidłowy ciąg formatu nazwy i wartości, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu. Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasy, aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia z bazą danych programu SQL Server.  
  
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
 SQL Server, zintegrowane zabezpieczenia (znany także jako zaufanych połączeń) ułatwia ochronę podczas nawiązywania połączenia z programem SQL Server, ponieważ nie uwidacznia identyfikator użytkownika i hasło w parametrach połączenia i jest to zalecana metoda do uwierzytelniania połączenia. Zintegrowane zabezpieczenia używa bieżącej tożsamości zabezpieczeń lub token wykonywanego procesu. Dla aplikacji klasycznych zazwyczaj jest to tożsamość aktualnie zalogowanego użytkownika.  
  
 Tożsamość zabezpieczeń dla aplikacji platformy ASP.NET można ustawić na jeden z kilku różnych opcji. Aby lepiej zrozumieć tożsamości zabezpieczeń, która aplikacja ASP.NET używa podczas nawiązywania połączenia z programem SQL Server, zobacz [personifikacji aplikacji ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [Uwierzytelnianie ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), i [jak: Dostęp do programu SQL Server przy użyciu Windows zintegrowane zabezpieczenia](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Łączenie ze źródłem danych OLE DB  
 .NET Framework Data Provider for OLE DB zapewnia łączność ze źródłami danych uwidaczniane za pomocą OLE DB (za pośrednictwem SQLOLEDB, dostawca OLE DB dla programu SQL Server), za pomocą **oledbconnection —** obiektu.  
  
 Dla .NET Framework Data Provider for OLE DB format parametrów połączenia jest taka sama jak format parametrów połączenia, które są używane w ADO, z następującymi wyjątkami:  
  
-   **Dostawcy** — słowo kluczowe jest wymagana.  
  
-   **Adresu URL**, **dostawcy zdalnym**, i **zdalnego serwera** słowa kluczowe nie są obsługiwane.  
  
 Aby uzyskać więcej informacji dotyczących parametrów połączenia OLE DB, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tematu. Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> do tworzenia parametrów połączenia w czasie wykonywania.  
  
> [!NOTE]
>  **Oledbconnection —** obiekt nie obsługuje ustawiania lub pobierania właściwości dynamicznych, które są specyficzne dla dostawcy OLE DB. Obsługiwane są tylko te właściwości, które mogą być przekazywane w parametrach połączenia dla dostawcy OLE DB.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia ze źródłem danych OLE DB.  
  
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
 Jest to możliwe, aby podać informacje o połączeniu dla **oledbconnection —** w plik Universal Data Link (UDL); jednak należy unikać sposób. Pliki UDL nie są szyfrowane, a następnie udostępnić informacje o parametrach połączenia w postaci zwykłego tekstu. Ponieważ plik UDL zewnętrznego zasobu opartych na plikach do aplikacji, nie może być chronione przy użyciu programu .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Łączenie ze źródłem danych ODBC  
 .NET Framework Data Provider for ODBC zapewnia łączność ze źródłami danych udostępniane przy użyciu ODBC **OdbcConnection** obiektu.  
  
 Dla .NET Framework Data Provider for ODBC format parametrów połączenia jest przeznaczony do możliwie najdokładniej dopasować format parametrów połączenia ODBC. Może też podawać nazwę źródła danych (DSN) ODBC. Aby uzyskać więcej szczegółów na **OdbcConnection** , zobacz <xref:System.Data.Odbc.OdbcConnection>.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia ze źródłem danych ODBC.  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a>Łączenie ze źródłem danych programu Oracle  
 .NET Framework Data Provider for Oracle zapewnia łączność ze źródłami danych Oracle przy użyciu **OracleConnection** obiektu.  
  
 Dla .NET Framework Data Provider for Oracle format parametrów połączenia jest przeznaczony do możliwie najdokładniej dopasować z dostawcy OLE DB dla format parametrów połączenia bazy danych Oracle (MSDAORA i). Aby uzyskać więcej szczegółów na **OracleConnection**, zobacz <xref:System.Data.OracleClient.OracleConnection>.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia ze źródłem danych programu Oracle.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)
- [Buforowanie połączenia Oracle, OLE DB i ODBC](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
