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
# <a name="establishing-the-connection"></a><span data-ttu-id="0b100-102">Nawiązywania połączenia</span><span class="sxs-lookup"><span data-stu-id="0b100-102">Establishing the Connection</span></span>
<span data-ttu-id="0b100-103">Aby nawiązać połączenie programu Microsoft SQL Server, należy użyć <xref:System.Data.SqlClient.SqlConnection> obiekt dostawcy danych programu .NET Framework dla programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0b100-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="0b100-104">Aby połączyć się ze źródłem danych OLE DB, użyć <xref:System.Data.OleDb.OleDbConnection> obiektu .NET Framework Data Provider for OLE DB.</span><span class="sxs-lookup"><span data-stu-id="0b100-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="0b100-105">Aby połączyć źródła danych ODBC, użyj <xref:System.Data.Odbc.OdbcConnection> obiekt dostawcy danych programu .NET Framework dla ODBC.</span><span class="sxs-lookup"><span data-stu-id="0b100-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="0b100-106">Aby połączyć się ze źródłem danych programu Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu .NET Framework Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="0b100-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="0b100-107">W celu bezpiecznego przechowywania i pobierania parametry połączenia, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="0b100-108">Zamykanie połączenia</span><span class="sxs-lookup"><span data-stu-id="0b100-108">Closing Connections</span></span>  
 <span data-ttu-id="0b100-109">Firma Microsoft zaleca zawsze zamknąć połączenie po zakończeniu korzystania z niego, dzięki czemu połączenie może być zwracany do puli.</span><span class="sxs-lookup"><span data-stu-id="0b100-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="0b100-110">`Using` Blokowanie w języku Visual Basic i C# automatycznie usuwa połączenia gdy kod jest kończona bloku, nawet w przypadku nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0b100-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="0b100-111">Zobacz [za pomocą instrukcji](~/docs/csharp/language-reference/keywords/using-statement.md) i [instrukcji Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0b100-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="0b100-112">Można również użyć `Close` lub `Dispose` metody obiektu połączenia dla dostawcy, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="0b100-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="0b100-113">Połączenia, które nie są jawnie zamknięty, nie może dodać lub zwrócony do puli.</span><span class="sxs-lookup"><span data-stu-id="0b100-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="0b100-114">Na przykład, która wykroczyła poza zakres, ale które nie zostały jawnie zamknął połączenie tylko powróci do puli połączeń Osiągnięto maksymalny rozmiar puli, jeśli połączenie jest nadal ważny.</span><span class="sxs-lookup"><span data-stu-id="0b100-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="0b100-115">Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i użycia puli połączeń Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b100-116">Nie wywołuj `Close` lub `Dispose` na **połączenia**, **DataReader**, lub innego obiektu zarządzanego w `Finalize` metody klasy.</span><span class="sxs-lookup"><span data-stu-id="0b100-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="0b100-117">W finalizator zwolnić tylko niezarządzane zasoby, które bezpośrednio należą do klasy.</span><span class="sxs-lookup"><span data-stu-id="0b100-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="0b100-118">Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="0b100-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="0b100-119">Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b100-120">Zdarzenia logowania i wylogowywania nie będą zgłaszane na serwerze gdy połączenie jest pobranych z lub zwrócony do puli połączeń, ponieważ połączenie nie jest w rzeczywistości zamknięte zwracanie do puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="0b100-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="0b100-121">Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="0b100-122">Łączenie z serwerem SQL</span><span class="sxs-lookup"><span data-stu-id="0b100-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="0b100-123">.NET Framework Data Provider for SQL Server obsługuje format parametrów połączenia, który jest podobny do formatu ciągu połączenia OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="0b100-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="0b100-124">Nieprawidłowy ciąg formatu nazwy i wartości, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b100-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="0b100-125">Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasę, aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0b100-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="0b100-126">Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="0b100-127">Poniższy przykład kodu pokazuje sposób tworzenia i otwierania połączenia z bazą danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0b100-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="0b100-128">Zintegrowane zabezpieczenia i platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0b100-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="0b100-129">SQL Server zintegrowane zabezpieczenia (znanej także jako zaufanych połączeń) ułatwia ochronę podczas nawiązywania połączenia z programem SQL Server, ponieważ nie ujawnia Identyfikatora użytkownika i hasła w parametrach połączenia i jest to zalecana metoda uwierzytelniania połączenia.</span><span class="sxs-lookup"><span data-stu-id="0b100-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="0b100-130">Zintegrowane zabezpieczenia używa bieżącej tożsamości zabezpieczeń lub token wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="0b100-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="0b100-131">Dla aplikacji klasycznych zazwyczaj jest to tożsamość aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0b100-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="0b100-132">Tożsamość zabezpieczeń dla aplikacji ASP.NET można wybrać jedno z kilku różnych opcji.</span><span class="sxs-lookup"><span data-stu-id="0b100-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="0b100-133">Aby lepiej zrozumieć tożsamości zabezpieczeń, która aplikacja ASP.NET używa podczas nawiązywania połączenia z programem SQL Server, zobacz [personifikacji aplikacji ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [Uwierzytelnianie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), i [porady: dostęp do programu SQL Zabezpieczenia zintegrowane przy użyciu systemu Windows Server](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span><span class="sxs-lookup"><span data-stu-id="0b100-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET Authentication](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), and [How to: Access SQL Server Using Windows Integrated Security](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="0b100-134">Nawiązywanie połączenia źródła danych OLE DB</span><span class="sxs-lookup"><span data-stu-id="0b100-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="0b100-135">.NET Framework Data Provider for OLE DB udostępnia połączenie ze źródłami danych ujawnianej za pomocą OLE DB (za pośrednictwem SQLOLEDB, dostawca OLE DB dla programu SQL Server), za pomocą **oledbconnection —** obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b100-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="0b100-136">Dla .NET Framework Data Provider for OLE DB format ciągu połączenia jest taki sam jak format parametrów połączenia, które są używane w ADO, z następującymi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="0b100-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="0b100-137">**Dostawcy** — słowo kluczowe jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="0b100-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="0b100-138">**Adres URL**, **dostawcy zdalnym**, i **serwera zdalnego** słowa kluczowe nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0b100-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="0b100-139">Aby uzyskać więcej informacji dotyczących parametrów połączenia OLE DB, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tematu.</span><span class="sxs-lookup"><span data-stu-id="0b100-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="0b100-140">Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> Aby utworzyć parametry połączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0b100-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b100-141">**Oledbconnection —** obiekt nie obsługuje ustawiania lub pobierania właściwości dynamicznych, które są specyficzne dla dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="0b100-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="0b100-142">Obsługiwane są tylko właściwości, które mogą zostać przekazane w parametrach połączenia dla dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="0b100-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="0b100-143">W poniższym przykładzie przedstawiono sposób tworzenia i otwierania połączenia ze źródłem danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="0b100-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="0b100-144">Nie używaj Universal Data Link plików</span><span class="sxs-lookup"><span data-stu-id="0b100-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="0b100-145">Można podać informacje o połączeniu **oledbconnection —** w plik Universal Data Link (UDL); jednak należy unikać w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="0b100-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="0b100-146">Pliki UDL nie są szyfrowane i ujawniać informacje o parametrach połączenia w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="0b100-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="0b100-147">Ponieważ plik UDL zewnętrzny zasób opartych na plikach do aplikacji, nie może być chronione przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b100-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="0b100-148">Nawiązywanie połączenia źródła danych ODBC</span><span class="sxs-lookup"><span data-stu-id="0b100-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="0b100-149">.NET Framework Data Provider for ODBC udostępnia połączenie ze źródłami danych ujawnianej za pomocą ODBC przy użyciu **OdbcConnection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b100-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="0b100-150">Dla .NET Framework Data Provider for ODBC format ciągu połączenia jest przeznaczony do możliwie najbardziej zgodna z formatem ciągu połączenia ODBC.</span><span class="sxs-lookup"><span data-stu-id="0b100-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="0b100-151">Może też podawać nazwę źródła danych (DSN) ODBC.</span><span class="sxs-lookup"><span data-stu-id="0b100-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="0b100-152">Aby uzyskać więcej szczegółów na **OdbcConnection** , zobacz <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="0b100-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="0b100-153">W poniższym przykładzie przedstawiono sposób tworzenia i otwierania połączenia źródła danych ODBC.</span><span class="sxs-lookup"><span data-stu-id="0b100-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="0b100-154">Połączenie ze źródłem danych programu Oracle</span><span class="sxs-lookup"><span data-stu-id="0b100-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="0b100-155">.NET Framework Data Provider for Oracle udostępnia połączenie ze źródłami danych Oracle przy użyciu **OracleConnection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b100-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="0b100-156">Dla .NET Framework Data Provider for Oracle format ciągu połączenia jest przeznaczony do możliwie najbardziej zgodne z dostawcy OLE DB dla formatu ciągu połączenia Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="0b100-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="0b100-157">Aby uzyskać więcej szczegółów na **OracleConnection**, zobacz <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="0b100-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="0b100-158">W poniższym przykładzie przedstawiono sposób tworzenia i otwierania połączenia ze źródłem danych programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="0b100-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b100-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b100-159">See Also</span></span>  
 [<span data-ttu-id="0b100-160">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="0b100-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="0b100-161">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="0b100-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="0b100-162">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="0b100-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="0b100-163">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="0b100-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
