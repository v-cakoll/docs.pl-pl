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
# <a name="establishing-the-connection"></a><span data-ttu-id="712b2-102">Nawiązywanie połączenia</span><span class="sxs-lookup"><span data-stu-id="712b2-102">Establishing the Connection</span></span>
<span data-ttu-id="712b2-103">Aby połączyć się z <xref:System.Data.SqlClient.SqlConnection> programem Microsoft SQL Server, użyj obiektu dostawcy danych programu .NET Framework dla programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="712b2-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="712b2-104">Aby połączyć się ze źródłem <xref:System.Data.OleDb.OleDbConnection> danych OLE DB, należy użyć obiektu dostawcy danych programu .NET Framework dla bazy danych OLE.</span><span class="sxs-lookup"><span data-stu-id="712b2-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="712b2-105">Aby połączyć się ze źródłem <xref:System.Data.Odbc.OdbcConnection> danych ODBC, należy użyć obiektu dostawcy danych programu .NET Framework dla odbc.</span><span class="sxs-lookup"><span data-stu-id="712b2-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="712b2-106">Aby połączyć się ze źródłem danych Oracle, użyj <xref:System.Data.OracleClient.OracleConnection> obiektu dostawcy danych .NET Framework dla oracle.</span><span class="sxs-lookup"><span data-stu-id="712b2-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="712b2-107">Aby bezpiecznie przechowywać i pobierać parametry połączenia, zobacz [Ochrona informacji o połączeniu](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="712b2-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="712b2-108">Zamykanie połączeń</span><span class="sxs-lookup"><span data-stu-id="712b2-108">Closing Connections</span></span>  
 <span data-ttu-id="712b2-109">Zaleca się, aby zawsze zamknąć połączenie po zakończeniu korzystania z niego, tak aby połączenie można było powrócić do puli.</span><span class="sxs-lookup"><span data-stu-id="712b2-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="712b2-110">Blok `Using` w języku Visual Basic lub C# automatycznie usuwa połączenia, gdy kod kończy blok, nawet w przypadku nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="712b2-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="712b2-111">Aby uzyskać więcej [informacji,](../../../csharp/language-reference/keywords/using-statement.md) zobacz korzystanie z instrukcji i [instrukcji.](../../../visual-basic/language-reference/statements/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="712b2-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="712b2-112">Można również użyć `Close` `Dispose` lub metody obiektu połączenia dla dostawcy, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="712b2-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="712b2-113">Połączenia, które nie są jawnie zamknięte, mogą nie zostać dodane lub zwrócone do puli.</span><span class="sxs-lookup"><span data-stu-id="712b2-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="712b2-114">Na przykład połączenie, które wyszło poza zakres, ale nie zostało jawnie zamknięte, zostanie zwrócone do puli połączeń tylko wtedy, gdy osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważne.</span><span class="sxs-lookup"><span data-stu-id="712b2-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="712b2-115">Aby uzyskać więcej informacji, zobacz [OLE DB, ODBC i Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="712b2-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="712b2-116">Nie należy `Close` `Dispose` wywoływać ani na **połączenie**, **DataReader**lub `Finalize` inny obiekt zarządzany w metodzie klasy.</span><span class="sxs-lookup"><span data-stu-id="712b2-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="712b2-117">W finalizatorze tylko zwolnić niezarządzanych zasobów, które posiada bezpośrednio klasy.</span><span class="sxs-lookup"><span data-stu-id="712b2-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="712b2-118">Jeśli klasa nie jest właścicielem żadnych zasobów niezarządzanych, nie należy uwzględniać `Finalize` metody w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="712b2-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="712b2-119">Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="712b2-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="712b2-120">Zdarzenia logowania i wylogowania nie będą wywoływane na serwerze, gdy połączenie jest pobierane z puli połączeń lub zwracane do puli połączeń, ponieważ połączenie nie jest faktycznie zamknięte, gdy jest zwracane do puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="712b2-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="712b2-121">Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="712b2-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="712b2-122">Łączenie się z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="712b2-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="712b2-123">Dostawca danych programu .NET Framework dla programu SQL Server obsługuje format ciągu połączenia, który jest podobny do formatu ciągu połączenia OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="712b2-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="712b2-124">Aby uzyskać prawidłowe nazwy i <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> wartości <xref:System.Data.SqlClient.SqlConnection> formatu ciągu, zobacz właściwość obiektu.</span><span class="sxs-lookup"><span data-stu-id="712b2-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="712b2-125">Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> klasy do tworzenia syntaktycznie prawidłowych ciągów połączeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="712b2-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="712b2-126">Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączeń](connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="712b2-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="712b2-127">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie z bazą danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="712b2-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="712b2-128">Zintegrowane zabezpieczenia i ASP.NET</span><span class="sxs-lookup"><span data-stu-id="712b2-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="712b2-129">Zintegrowane zabezpieczenia programu SQL Server (znane również jako połączenia zaufane) pomagają zapewnić ochronę podczas łączenia się z programem SQL Server, ponieważ nie uwidaczniają identyfikatora użytkownika i hasła w ciągu połączenia i są zalecaną metodą uwierzytelniania połączenia.</span><span class="sxs-lookup"><span data-stu-id="712b2-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="712b2-130">Zintegrowane zabezpieczenia używa bieżącej tożsamości zabezpieczeń lub tokenu procesu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="712b2-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="712b2-131">W przypadku aplikacji klasycznych jest to zazwyczaj tożsamość aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="712b2-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="712b2-132">Tożsamość zabezpieczeń dla aplikacji ASP.NET można ustawić na jedną z kilku różnych opcji.</span><span class="sxs-lookup"><span data-stu-id="712b2-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="712b2-133">Aby lepiej zrozumieć tożsamość zabezpieczeń używaną przez aplikację ASP.NET podczas łączenia się z programem SQL Server, zobacz [personifikacja ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET uwierzytelnianie](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))i [Jak: Dostęp do programu SQL Server przy użyciu zintegrowanych zabezpieczeń systemu Windows](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="712b2-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="712b2-134">Łączenie się ze źródłem danych OLE DB</span><span class="sxs-lookup"><span data-stu-id="712b2-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="712b2-135">Dostawca danych .NET Framework dla ole db zapewnia łączność ze źródłami danych narażonymi przy użyciu OLE DB (za pośrednictwem SQLOLEDB, dostawcy OLE DB dla programu SQL Server), przy użyciu obiektu **OleDbConnection.**</span><span class="sxs-lookup"><span data-stu-id="712b2-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="712b2-136">Dla dostawcy danych programu .NET Framework dla ole db format ciągu połączenia jest identyczny z formatem ciągu połączenia używanego w ADO, z następującymi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="712b2-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="712b2-137">Wymagane jest słowo kluczowe **Dostawca.**</span><span class="sxs-lookup"><span data-stu-id="712b2-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="712b2-138">Słowa kluczowe **URL**, **Dostawca zdalny**i **Serwer zdalny** nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="712b2-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="712b2-139">Aby uzyskać więcej informacji na temat ciągów połączeń OLE DB, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> temat.</span><span class="sxs-lookup"><span data-stu-id="712b2-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="712b2-140">Można również użyć <xref:System.Data.OleDb.OleDbConnectionStringBuilder> do tworzenia ciągów połączeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="712b2-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="712b2-141">**Obiekt OleDbConnection** nie obsługuje ustawiania ani pobierania właściwości dynamicznych specyficznych dla dostawcy ole db.</span><span class="sxs-lookup"><span data-stu-id="712b2-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="712b2-142">Obsługiwane są tylko właściwości, które mogą być przekazywane w ciągu połączenia dla dostawcy ole db.</span><span class="sxs-lookup"><span data-stu-id="712b2-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="712b2-143">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie ze źródłem danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="712b2-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="712b2-144">Nie używaj uniwersalnych plików łączy danych</span><span class="sxs-lookup"><span data-stu-id="712b2-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="712b2-145">Możliwe jest podanie informacji o połączeniu dla **OleDbConnection** w pliku Uniwersalnego łącza danych (UDL); jednak należy tego unikać.</span><span class="sxs-lookup"><span data-stu-id="712b2-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="712b2-146">Pliki UDL nie są szyfrowane i ujawniają informacje o ciągu połączenia w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="712b2-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="712b2-147">Ponieważ plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji, nie można go zabezpieczyć za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="712b2-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="712b2-148">Łączenie się ze źródłem danych ODBC</span><span class="sxs-lookup"><span data-stu-id="712b2-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="712b2-149">Dostawca danych .NET Framework dla ODBC zapewnia łączność ze źródłami danych narażonymi przy użyciu odbc przy użyciu obiektu **OdbcConnection.**</span><span class="sxs-lookup"><span data-stu-id="712b2-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="712b2-150">Dla dostawcy danych programu .NET Framework dla odbc format ciągu połączenia jest zaprojektowany tak, aby jak najściślijniej dopasować format ciągu połączenia ODBC.</span><span class="sxs-lookup"><span data-stu-id="712b2-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="712b2-151">Można również podać nazwę źródła danych ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="712b2-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="712b2-152">Aby uzyskać więcej informacji na temat <xref:System.Data.Odbc.OdbcConnection> **OdbcConnection** , zobacz .</span><span class="sxs-lookup"><span data-stu-id="712b2-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="712b2-153">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie ze źródłem danych ODBC.</span><span class="sxs-lookup"><span data-stu-id="712b2-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="712b2-154">Łączenie się ze źródłem danych Oracle</span><span class="sxs-lookup"><span data-stu-id="712b2-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="712b2-155">Dostawca danych .NET Framework dla oracle zapewnia łączność ze źródłami danych Oracle przy użyciu obiektu **OracleConnection.**</span><span class="sxs-lookup"><span data-stu-id="712b2-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="712b2-156">Dla dostawcy danych .NET Framework dla Oracle format ciągu połączenia jest zaprojektowany tak, aby jak najdościej dopasować format ciągu połączenia dostawcy OLE DB dla oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="712b2-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="712b2-157">Aby uzyskać więcej informacji na temat <xref:System.Data.OracleClient.OracleConnection> **OracleConnection,** zobacz .</span><span class="sxs-lookup"><span data-stu-id="712b2-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="712b2-158">Poniższy przykład kodu pokazuje, jak utworzyć i otworzyć połączenie ze źródłem danych Oracle.</span><span class="sxs-lookup"><span data-stu-id="712b2-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="712b2-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="712b2-159">See also</span></span>

- [<span data-ttu-id="712b2-160">Łączenie się ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="712b2-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="712b2-161">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="712b2-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="712b2-162">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="712b2-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="712b2-163">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="712b2-163">ADO.NET Overview</span></span>](ado-net-overview.md)
