---
title: Nawiązywanie połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 4606ecb370b7e85cf5ebd92754471f5253321251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149664"
---
# <a name="establishing-the-connection"></a>Nawiązywanie połączenia
Aby połączyć się z <xref:System.Data.SqlClient.SqlConnection> programem Microsoft SQL Server, użyj obiektu dostawcy danych programu .NET Framework dla programu SQL Server. Aby połączyć się ze źródłem <xref:System.Data.OleDb.OleDbConnection> danych OLE DB, należy użyć obiektu dostawcy danych programu .NET Framework dla bazy danych OLE. Aby połączyć się ze źródłem <xref:System.Data.Odbc.OdbcConnection> danych ODBC, należy użyć obiektu dostawcy danych programu .NET Framework dla odbc. Aby połączyć się ze źródłem danych Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu dostawcy danych .NET Framework dla oracle. Aby bezpiecznie przechowywać i pobierać parametry połączenia, zobacz [Ochrona informacji o połączeniu](protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Zamykanie połączeń  
 Zaleca się, aby zawsze zamknąć połączenie po zakończeniu korzystania z niego, tak aby połączenie można było powrócić do puli. Blok `Using` w języku Visual Basic lub C# automatycznie usuwa połączenia, gdy kod kończy blok, nawet w przypadku nieobsługiwany wyjątek. Aby uzyskać więcej [informacji,](../../../csharp/language-reference/keywords/using-statement.md) zobacz korzystanie z instrukcji i [instrukcji.](../../../visual-basic/language-reference/statements/using-statement.md)  
  
 Można również użyć `Close` `Dispose` lub metody obiektu połączenia dla dostawcy, którego używasz. Połączenia, które nie są jawnie zamknięte, mogą nie zostać dodane lub zwrócone do puli. Na przykład połączenie, które wyszło poza zakres, ale nie zostało jawnie zamknięte, zostanie zwrócone do puli połączeń tylko wtedy, gdy osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważne. Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> Nie należy `Close` `Dispose` wywoływać ani na **połączenie**, **DataReader**lub `Finalize` inny obiekt zarządzany w metodzie klasy. W finalizatorze tylko zwolnić niezarządzanych zasobów, które posiada bezpośrednio klasy. Jeśli klasa nie jest właścicielem żadnych zasobów niezarządzanych, nie należy uwzględniać `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Zdarzenia logowania i wylogowania nie będą wywoływane na serwerze, gdy połączenie jest pobierane z puli połączeń lub zwracane do puli połączeń, ponieważ połączenie nie jest faktycznie zamknięte, gdy jest zwracane do puli połączeń. Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Łączenie się z programem SQL Server  
 Dostawca danych programu .NET Framework dla programu SQL Server obsługuje format ciągu połączenia, który jest podobny do formatu ciągu połączenia OLE DB (ADO). Aby uzyskać prawidłowe nazwy i <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> wartości <xref:System.Data.SqlClient.SqlConnection> formatu ciągu, zobacz właściwość obiektu. Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasy do tworzenia syntaktycznie prawidłowych ciągów połączeń w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączeń](connection-string-builders.md).  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie z bazą danych programu SQL Server.  
  
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
  
### <a name="integrated-security-and-aspnet"></a>Zintegrowane zabezpieczenia i ASP.NET  
 Zintegrowane zabezpieczenia programu SQL Server (znane również jako połączenia zaufane) pomagają zapewnić ochronę podczas łączenia się z programem SQL Server, ponieważ nie uwidaczniają identyfikatora użytkownika i hasła w ciągu połączenia i są zalecaną metodą uwierzytelniania połączenia. Zintegrowane zabezpieczenia używa bieżącej tożsamości zabezpieczeń lub tokenu procesu wykonywania. W przypadku aplikacji klasycznych jest to zazwyczaj tożsamość aktualnie zalogowanego użytkownika.  
  
 Tożsamość zabezpieczeń dla aplikacji ASP.NET można ustawić na jedną z kilku różnych opcji. Aby lepiej zrozumieć tożsamość zabezpieczeń używaną przez aplikację ASP.NET podczas łączenia się z programem SQL Server, zobacz [personifikacja ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET uwierzytelnianie](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))i [Jak: Dostęp do programu SQL Server przy użyciu zintegrowanych zabezpieczeń systemu Windows](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Łączenie się ze źródłem danych OLE DB  
 Dostawca danych .NET Framework dla ole db zapewnia łączność ze źródłami danych narażonymi przy użyciu OLE DB (za pośrednictwem SQLOLEDB, dostawcy OLE DB dla programu SQL Server), przy użyciu obiektu **OleDbConnection.**  
  
 Dla dostawcy danych programu .NET Framework dla ole db format ciągu połączenia jest identyczny z formatem ciągu połączenia używanego w ADO, z następującymi wyjątkami:  
  
- Wymagane jest słowo kluczowe **Dostawca.**  
  
- Słowa kluczowe **URL**, **Dostawca zdalny**i **Serwer zdalny** nie są obsługiwane.  
  
 Aby uzyskać więcej informacji na temat ciągów połączeń OLE DB, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> temat. Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> do tworzenia ciągów połączeń w czasie wykonywania.  
  
> [!NOTE]
> **Obiekt OleDbConnection** nie obsługuje ustawiania ani pobierania właściwości dynamicznych specyficznych dla dostawcy ole db. Obsługiwane są tylko właściwości, które mogą być przekazywane w ciągu połączenia dla dostawcy ole db.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie ze źródłem danych OLE DB.  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a>Nie używaj uniwersalnych plików łączy danych  
 Możliwe jest podanie informacji o połączeniu dla **OleDbConnection** w pliku Uniwersalnego łącza danych (UDL); jednak należy tego unikać. Pliki UDL nie są szyfrowane i ujawniają informacje o ciągu połączenia w postaci zwykłego tekstu. Ponieważ plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji, nie można go zabezpieczyć za pomocą programu .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Łączenie się ze źródłem danych ODBC  
 Dostawca danych .NET Framework dla ODBC zapewnia łączność ze źródłami danych narażonymi przy użyciu odbc przy użyciu obiektu **OdbcConnection.**  
  
 Dla dostawcy danych programu .NET Framework dla odbc format ciągu połączenia jest zaprojektowany tak, aby jak najściślijniej dopasować format ciągu połączenia ODBC. Można również podać nazwę źródła danych ODBC (DSN). Aby uzyskać więcej informacji na temat <xref:System.Data.Odbc.OdbcConnection> **OdbcConnection** , zobacz .  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie ze źródłem danych ODBC.  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a>Łączenie się ze źródłem danych Oracle  
 Dostawca danych .NET Framework dla oracle zapewnia łączność ze źródłami danych Oracle przy użyciu obiektu **OracleConnection.**  
  
 Dla dostawcy danych .NET Framework dla Oracle format ciągu połączenia jest zaprojektowany tak, aby jak najdościej dopasować format ciągu połączenia dostawcy OLE DB dla oracle (MSDAORA). Aby uzyskać więcej informacji na temat <xref:System.Data.OracleClient.OracleConnection> **OracleConnection,** zobacz .  
  
 Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie ze źródłem danych Oracle.  
  
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

- [Łączenie się ze źródłem danych](connecting-to-a-data-source.md)
- [Parametry połączenia](connection-strings.md)
- [Buforowanie połączenia Oracle, OLE DB i ODBC](ole-db-odbc-and-oracle-connection-pooling.md)
- [Omówienie ADO.NET](ado-net-overview.md)
