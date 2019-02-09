---
title: Podczas nawiązywania połączenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 97cae018f8cdf19da390b9586334f7c8b7f1c239
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903815"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="bdca4-102">Podczas nawiązywania połączenia</span><span class="sxs-lookup"><span data-stu-id="bdca4-102">Establishing the Connection</span></span>
<span data-ttu-id="bdca4-103">Aby połączyć z programem Microsoft SQL Server, należy użyć <xref:System.Data.SqlClient.SqlConnection> obiektu .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bdca4-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="bdca4-104">Aby połączyć się ze źródłem danych OLE DB, użyj <xref:System.Data.OleDb.OleDbConnection> obiektu .NET Framework Data Provider for OLE DB.</span><span class="sxs-lookup"><span data-stu-id="bdca4-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="bdca4-105">Aby połączyć się ze źródłem danych ODBC, użyj <xref:System.Data.Odbc.OdbcConnection> obiekt dostawcy danych programu .NET Framework dla ODBC.</span><span class="sxs-lookup"><span data-stu-id="bdca4-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="bdca4-106">Aby połączyć się ze źródłem danych Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu .NET Framework Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="bdca4-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="bdca4-107">Bezpieczne przechowywanie i pobieranie parametrów połączenia, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="bdca4-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="bdca4-108">Zamykanie połączenia</span><span class="sxs-lookup"><span data-stu-id="bdca4-108">Closing Connections</span></span>  
 <span data-ttu-id="bdca4-109">Firma Microsoft zaleca, aby zawsze zamykaj połączenie po zakończeniu korzystania z niego, tak aby połączenie mogą być zwrócone do puli.</span><span class="sxs-lookup"><span data-stu-id="bdca4-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="bdca4-110">`Using` Blokowania w języku Visual Basic lub C# automatycznie usuwa połączenia gdy kod zamyka blok, nawet w przypadku nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="bdca4-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="bdca4-111">Zobacz [za pomocą instrukcji](~/docs/csharp/language-reference/keywords/using-statement.md) i [instrukcji Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bdca4-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="bdca4-112">Można również użyć `Close` lub `Dispose` metody obiektu połączenia do dostawcy, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="bdca4-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="bdca4-113">Połączenia, które nie są jawnie zamknięty, nie może dodać lub zwrócone do puli.</span><span class="sxs-lookup"><span data-stu-id="bdca4-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="bdca4-114">Na przykład połączenia, który przeszedł poza zakresem, ale które nie zostało jawnie zamknięte tylko powróci do puli połączeń, jeśli osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważny.</span><span class="sxs-lookup"><span data-stu-id="bdca4-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="bdca4-115">Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i buforowanie połączenia Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="bdca4-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdca4-116">Nie wywołuj `Close` lub `Dispose` na **połączenia**, **DataReader**, lub inne obiekt zarządzany w `Finalize` metody klasy.</span><span class="sxs-lookup"><span data-stu-id="bdca4-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="bdca4-117">W finalizatora zwolnić tylko niezarządzane zasoby, które należą bezpośrednio do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="bdca4-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="bdca4-118">Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w swojej definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="bdca4-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="bdca4-119">Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="bdca4-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdca4-120">Zdarzenia logowania i wylogowania nie zostaną wywołane na serwerze gdy połączenie zostanie pobrana z lub zwrócone do puli połączeń, ponieważ połączenie nie jest w rzeczywistości zamykane, gdy zostaje zwrócony do puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="bdca4-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="bdca4-121">Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="bdca4-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="bdca4-122">Łączenie z serwerem SQL</span><span class="sxs-lookup"><span data-stu-id="bdca4-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="bdca4-123">.NET Framework Data Provider for SQL Server obsługuje format parametrów połączenia, który jest podobny do formatu parametrów połączenia OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="bdca4-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="bdca4-124">Nieprawidłowy ciąg formatu nazwy i wartości, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="bdca4-125">Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasy, aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bdca4-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="bdca4-126">Aby uzyskać więcej informacji, zobacz [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="bdca4-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="bdca4-127">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia z bazą danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bdca4-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="bdca4-128">Zintegrowane zabezpieczenia i platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bdca4-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="bdca4-129">SQL Server, zintegrowane zabezpieczenia (znany także jako zaufanych połączeń) ułatwia ochronę podczas nawiązywania połączenia z programem SQL Server, ponieważ nie uwidacznia identyfikator użytkownika i hasło w parametrach połączenia i jest to zalecana metoda do uwierzytelniania połączenia.</span><span class="sxs-lookup"><span data-stu-id="bdca4-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="bdca4-130">Zintegrowane zabezpieczenia używa bieżącej tożsamości zabezpieczeń lub token wykonywanego procesu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="bdca4-131">Dla aplikacji klasycznych zazwyczaj jest to tożsamość aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bdca4-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="bdca4-132">Tożsamość zabezpieczeń dla aplikacji platformy ASP.NET można ustawić na jeden z kilku różnych opcji.</span><span class="sxs-lookup"><span data-stu-id="bdca4-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="bdca4-133">Aby lepiej zrozumieć tożsamości zabezpieczeń, która aplikacja ASP.NET używa podczas nawiązywania połączenia z programem SQL Server, zobacz [personifikacji aplikacji ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [Uwierzytelnianie ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), i [jak: Dostęp do programu SQL Server przy użyciu Windows zintegrowane zabezpieczenia](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bdca4-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="bdca4-134">Łączenie ze źródłem danych OLE DB</span><span class="sxs-lookup"><span data-stu-id="bdca4-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="bdca4-135">.NET Framework Data Provider for OLE DB zapewnia łączność ze źródłami danych uwidaczniane za pomocą OLE DB (za pośrednictwem SQLOLEDB, dostawca OLE DB dla programu SQL Server), za pomocą **oledbconnection —** obiektu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="bdca4-136">Dla .NET Framework Data Provider for OLE DB format parametrów połączenia jest taka sama jak format parametrów połączenia, które są używane w ADO, z następującymi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="bdca4-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="bdca4-137">**Dostawcy** — słowo kluczowe jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="bdca4-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="bdca4-138">**Adresu URL**, **dostawcy zdalnym**, i **zdalnego serwera** słowa kluczowe nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bdca4-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="bdca4-139">Aby uzyskać więcej informacji dotyczących parametrów połączenia OLE DB, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tematu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="bdca4-140">Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> do tworzenia parametrów połączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bdca4-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdca4-141">**Oledbconnection —** obiekt nie obsługuje ustawiania lub pobierania właściwości dynamicznych, które są specyficzne dla dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="bdca4-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="bdca4-142">Obsługiwane są tylko te właściwości, które mogą być przekazywane w parametrach połączenia dla dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="bdca4-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="bdca4-143">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia ze źródłem danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="bdca4-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="bdca4-144">Nie używaj Universal Data Link plików</span><span class="sxs-lookup"><span data-stu-id="bdca4-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="bdca4-145">Jest to możliwe, aby podać informacje o połączeniu dla **oledbconnection —** w plik Universal Data Link (UDL); jednak należy unikać sposób.</span><span class="sxs-lookup"><span data-stu-id="bdca4-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="bdca4-146">Pliki UDL nie są szyfrowane, a następnie udostępnić informacje o parametrach połączenia w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="bdca4-147">Ponieważ plik UDL zewnętrznego zasobu opartych na plikach do aplikacji, nie może być chronione przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bdca4-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="bdca4-148">Łączenie ze źródłem danych ODBC</span><span class="sxs-lookup"><span data-stu-id="bdca4-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="bdca4-149">.NET Framework Data Provider for ODBC zapewnia łączność ze źródłami danych udostępniane przy użyciu ODBC **OdbcConnection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="bdca4-150">Dla .NET Framework Data Provider for ODBC format parametrów połączenia jest przeznaczony do możliwie najdokładniej dopasować format parametrów połączenia ODBC.</span><span class="sxs-lookup"><span data-stu-id="bdca4-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="bdca4-151">Może też podawać nazwę źródła danych (DSN) ODBC.</span><span class="sxs-lookup"><span data-stu-id="bdca4-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="bdca4-152">Aby uzyskać więcej szczegółów na **OdbcConnection** , zobacz <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="bdca4-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="bdca4-153">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia ze źródłem danych ODBC.</span><span class="sxs-lookup"><span data-stu-id="bdca4-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="bdca4-154">Łączenie ze źródłem danych programu Oracle</span><span class="sxs-lookup"><span data-stu-id="bdca4-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="bdca4-155">.NET Framework Data Provider for Oracle zapewnia łączność ze źródłami danych Oracle przy użyciu **OracleConnection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="bdca4-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="bdca4-156">Dla .NET Framework Data Provider for Oracle format parametrów połączenia jest przeznaczony do możliwie najdokładniej dopasować z dostawcy OLE DB dla format parametrów połączenia bazy danych Oracle (MSDAORA i).</span><span class="sxs-lookup"><span data-stu-id="bdca4-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="bdca4-157">Aby uzyskać więcej szczegółów na **OracleConnection**, zobacz <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="bdca4-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="bdca4-158">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenia ze źródłem danych programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="bdca4-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdca4-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdca4-159">See also</span></span>
- [<span data-ttu-id="bdca4-160">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="bdca4-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="bdca4-161">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="bdca4-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="bdca4-162">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="bdca4-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="bdca4-163">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="bdca4-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
