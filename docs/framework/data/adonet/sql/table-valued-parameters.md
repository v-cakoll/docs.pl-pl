---
title: Parametry przechowywanymi w tabeli
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
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47009516d4118fec1a075a2dbccfa747f9a63131
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="table-valued-parameters"></a><span data-ttu-id="da000-102">Parametry przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="da000-102">Table-Valued Parameters</span></span>
<span data-ttu-id="da000-103">Parametry przechowywanymi w tabeli umożliwiają łatwe do organizowania wielu wierszy danych z aplikacji klienckiej [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] bez konieczności wiele rund lub specjalną logikę po stronie serwera do przetwarzania danych.</span><span class="sxs-lookup"><span data-stu-id="da000-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="da000-104">Hermetyzuj wierszy danych w aplikacji klienckiej i wysyłania danych do serwera za pomocą jednego polecenia sparametryzowane, mogą używać parametrów przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="da000-105">Przychodzące wiersze danych są przechowywane w zmiennej tabeli, która następnie może być obsługiwany przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da000-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="da000-106">Wartości w kolumnie w parametrach przechowywanymi w tabeli jest możliwy przy użyciu standardu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji "SELECT".</span><span class="sxs-lookup"><span data-stu-id="da000-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="da000-107">Parametry przechowywanymi w tabeli są silnie typizowane i ich struktury automatycznie zostanie zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="da000-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="da000-108">Rozmiar parametrów przechowywanymi w tabeli jest ograniczona tylko przez ilość pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="da000-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da000-109">Nie można zwrócić dane w parametrze przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="da000-110">Parametry przechowywanymi w tabeli są tylko wejściowym; dane wyjściowe — słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="da000-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="da000-111">Aby uzyskać więcej informacji na temat parametrów przechowywanymi w tabeli zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="da000-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="da000-112">Zasób</span><span class="sxs-lookup"><span data-stu-id="da000-112">Resource</span></span>|<span data-ttu-id="da000-113">Opis</span><span class="sxs-lookup"><span data-stu-id="da000-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="da000-114">[Parametry z wartościami przechowywanymi w tabeli (aparat bazy danych)](http://go.microsoft.com/fwlink/?LinkId=98363) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online</span><span class="sxs-lookup"><span data-stu-id="da000-114">[Table-Valued Parameters (Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="da000-115">Opisuje sposób tworzenia i używania parametrów przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="da000-116">[Zdefiniowane przez użytkownika typy tabel](http://go.microsoft.com/fwlink/?LinkId=98364) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online</span><span class="sxs-lookup"><span data-stu-id="da000-116">[User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkId=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="da000-117">W tym artykule opisano typy tabel zdefiniowanych przez użytkownika, które są używane do deklarowania parametry przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="da000-118">Przekazywanie wielu wierszy w poprzednich wersjach programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="da000-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="da000-119">Przed wprowadzeniem przechowywanymi w tabeli parametrów do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, opcje przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone.</span><span class="sxs-lookup"><span data-stu-id="da000-119">Before table-valued parameters were introduced to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="da000-120">Deweloper może wybrać spośród następujących opcji wiele wierszy może być przekazywany do serwera:</span><span class="sxs-lookup"><span data-stu-id="da000-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="da000-121">Używanie serii poszczególnych parametrów do reprezentowania wartości w wielu kolumn i wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="da000-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="da000-122">Ilość danych, które mogą zostać przekazane za pomocą tej metody jest ograniczona liczba parametry są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="da000-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="da000-123">procedury może mieć co najwyżej 2100 parametrów.</span><span class="sxs-lookup"><span data-stu-id="da000-123"> procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="da000-124">Logika po stronie serwera jest wymagany do włączenia tych poszczególne wartości do zmiennej tabeli lub tabeli tymczasowej do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="da000-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="da000-125">Powiązać wiele wartości danych do ciągów rozdzielanych lub dokumentów XML, a następnie przekazać te wartości tekstowe do instrukcji lub procedury.</span><span class="sxs-lookup"><span data-stu-id="da000-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="da000-126">Wymaga to procedury lub instrukcji Dołącz logikę niezbędne do sprawdzania poprawności struktur danych oraz wydzielenia wartości.</span><span class="sxs-lookup"><span data-stu-id="da000-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="da000-127">Utwórz serię poszczególnych instrukcji SQL dla modyfikacji danych, które mają wpływ na wiele wierszy, takich jak te utworzone przez wywołanie metody `Update` metody <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="da000-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="da000-128">Zmiany można przesłać na serwer indywidualnie lub przetwarzane wsadowo w grupach.</span><span class="sxs-lookup"><span data-stu-id="da000-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="da000-129">Jednak nawet wtedy, gdy przesłać w partiach zawierających wiele instrukcji, każda instrukcja jest wykonywana osobno na serwerze.</span><span class="sxs-lookup"><span data-stu-id="da000-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="da000-130">Użyj `bcp` program narzędziowy lub <xref:System.Data.SqlClient.SqlBulkCopy> obiekt, aby załadować wiele wierszy danych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="da000-131">Ta technika jest bardzo wydajny, nie obsługuje przetwarzania po stronie serwera, chyba że dane zostaną załadowane do tabeli tymczasowej lub zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="da000-132">Tworzenie typów parametru przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="da000-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="da000-133">Parametry przechowywanymi w tabeli są oparte na struktury jednoznacznie tabeli, które zdefiniowano przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="da000-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="da000-134">Należy utworzyć typ tabeli i definiowania struktury w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] przed użyciem parametrów przechowywanymi w tabeli w aplikacjach klienckich.</span><span class="sxs-lookup"><span data-stu-id="da000-134">You have to create a table type and define the structure in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="da000-135">Aby uzyskać więcej informacji o tworzeniu typach tabel, zobacz [typach tabel zdefiniowanych przez użytkownika](http://go.microsoft.com/fwlink/?LinkID=98364) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online.</span><span class="sxs-lookup"><span data-stu-id="da000-135">For more information about creating table types, see [User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkID=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="da000-136">Poniższa instrukcja tworzy typ tabeli o nazwie CategoryTableType składający się z identyfikatorem kategorii i CategoryName kolumn:</span><span class="sxs-lookup"><span data-stu-id="da000-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="da000-137">Po utworzeniu tabeli można zadeklarować parametry przechowywanymi w tabeli na podstawie tego typu.</span><span class="sxs-lookup"><span data-stu-id="da000-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="da000-138">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragmentu pokazuje, jak do zadeklarowania parametru przechowywanymi w tabeli w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="da000-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="da000-139">Należy pamiętać, że READONLY — słowo kluczowe jest wymagana dla deklarowaniu parametru przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="da000-140">Modyfikowanie danych z parametrami przechowywanymi w tabeli (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="da000-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="da000-141">Parametry przechowywanymi w tabeli mogą być używane w modyfikacji na podstawie zestawu danych, które mają wpływ na wiele wierszy, wykonując jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="da000-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="da000-142">Na przykład można wybrać wszystkie wiersze w parametrze przechowywanymi w tabeli i wstawić je do tabeli bazy danych lub instrukcji update można utworzyć przez dołączenie do tabeli, które chcesz zaktualizować parametru przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="da000-143">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji UPDATE pokazano, jak użyć parametru przechowywanymi w tabeli przez dołączenie go do tabeli Kategorie.</span><span class="sxs-lookup"><span data-stu-id="da000-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="da000-144">Gdy używasz parametru przechowywanymi w tabeli z sprzężenia w klauzuli FROM, należy również aliasu, jak pokazano w tym miejscu, gdzie parametr przechowywanymi w tabeli jest używane z aliasem jako "WE":</span><span class="sxs-lookup"><span data-stu-id="da000-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="da000-145">To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] przykładzie pokazano sposób wybierania z parametrem przechowywanymi w tabeli w celu wykonania instrukcji INSERT w jednej operacji na podstawie zestawu wierszy.</span><span class="sxs-lookup"><span data-stu-id="da000-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="da000-146">Ograniczenia parametrów przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="da000-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="da000-147">Istnieje kilka ograniczeń dotyczących przechowywanymi w tabeli Parametry:</span><span class="sxs-lookup"><span data-stu-id="da000-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="da000-148">Nie można przekazać parametry przechowywanymi w tabeli [funkcje zdefiniowane przez użytkownika CLR](http://msdn.microsoft.com/library/ms131077.aspx).</span><span class="sxs-lookup"><span data-stu-id="da000-148">You cannot pass table-valued parameters to [CLR user-defined functions](http://msdn.microsoft.com/library/ms131077.aspx).</span></span>  
  
-   <span data-ttu-id="da000-149">Parametry przechowywanymi w tabeli mogą być indeksowane tylko do obsługi ograniczenia UNIQUE i PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="da000-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="da000-150">nie przechowuje dane statystyczne dotyczące parametrów przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-150"> does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="da000-151">Parametry przechowywanymi w tabeli są tylko do odczytu w [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="da000-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="da000-152">Nie można zaktualizować wartości w kolumnach w wierszach parametru przechowywanymi w tabeli i nie można wstawić lub usuwania wierszy.</span><span class="sxs-lookup"><span data-stu-id="da000-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="da000-153">Aby zmodyfikować dane, które są przekazywane do procedury składowanej lub sparametryzowanych instrukcji w parametrze przechowywanymi w tabeli, należy wstawić dane do tabeli tymczasowej lub zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="da000-154">Za pomocą instrukcji ALTER TABLE nie można modyfikować projektu parametry przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="da000-155">Konfigurowanie przykład SqlParameter</span><span class="sxs-lookup"><span data-stu-id="da000-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="da000-156"><xref:System.Data.SqlClient>obsługuje wypełnianie przechowywanymi w tabeli parametrów z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> lub System.Collections.Generic.IEnumerable\<<xref:Microsoft.SqlServer.Server.SqlDataRecord>> (<xref:System.Collections.Generic.IEnumerable%601>? qualifyHint = False & autoUpgrade = True) obiektów.</span><span class="sxs-lookup"><span data-stu-id="da000-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or System.Collections.Generic.IEnumerable\<<xref:Microsoft.SqlServer.Server.SqlDataRecord>> (<xref:System.Collections.Generic.IEnumerable%601>?qualifyHint=False&autoUpgrade=True) objects.</span></span> <span data-ttu-id="da000-157">Należy określić nazwę typu dla parametru przechowywanymi w tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="da000-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="da000-158">`TypeName` Musi być zgodna z nazwą zgodne z typem wcześniej utworzony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="da000-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="da000-159">Poniższy fragment kodu przedstawia sposób konfigurowania <xref:System.Data.SqlClient.SqlParameter> do wstawiania danych.</span><span class="sxs-lookup"><span data-stu-id="da000-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="da000-160">Umożliwia także dowolnego obiektu pochodną <xref:System.Data.Common.DbDataReader> do wierszy strumienia danych do parametru przechowywanymi w tabeli, jak pokazano w tym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="da000-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="da000-161">Przekazywanie parametru przechowywanymi w tabeli do procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="da000-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="da000-162">W tym przykładzie pokazano, jak przekazywać dane parametru przechowywanymi w tabeli do procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="da000-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="da000-163">Kod wyodrębnia dodanych wierszy w nowym <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da000-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="da000-164">Kod definiuje <xref:System.Data.SqlClient.SqlCommand>, ustawienie <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwości <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="da000-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="da000-165"><xref:System.Data.SqlClient.SqlParameter> Jest wypełniany przy użyciu <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> — metoda i <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ma ustawioną wartość `Structured`.</span><span class="sxs-lookup"><span data-stu-id="da000-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="da000-166"><xref:System.Data.SqlClient.SqlCommand> Następnie jest wykonywane przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da000-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="da000-167">Przekazywanie parametru przechowywanymi w tabeli w instrukcji SQL sparametryzowane</span><span class="sxs-lookup"><span data-stu-id="da000-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="da000-168">W poniższym przykładzie pokazano, jak wstawianie danych do dbo. Kategorie tabeli za pomocą instrukcji INSERT podzapytania SELECT, który ma parametr przechowywanymi w tabeli jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="da000-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="da000-169">Podczas przekazywania parametru przechowywanymi w tabeli do sparametryzowanych instrukcji SQL, należy określić nazwę typu dla parametru przechowywanymi w tabeli, używając nowego <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="da000-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="da000-170">To `TypeName` musi być zgodna z nazwą zgodne z typem wcześniej utworzony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="da000-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="da000-171">W kodzie w tym przykładzie użyto `TypeName` właściwości, aby odwołać struktury typ zdefiniowany w dbo. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="da000-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da000-172">Jeśli zostanie podana wartość dla kolumny tożsamości w parametrze przechowywanymi w tabeli, należy wygenerować instrukcji USTAWIONY atrybut IDENTITY_INSERT dla sesji.</span><span class="sxs-lookup"><span data-stu-id="da000-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="da000-173">Przesyłania strumieniowego wiersze z elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="da000-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="da000-174">Umożliwia także dowolnego obiektu pochodną <xref:System.Data.Common.DbDataReader> do wierszy strumienia danych do parametru przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="da000-175">Poniższy fragment kodu przedstawia pobieranie danych z bazy danych Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand> i <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="da000-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="da000-176">Następnie konfiguruje kod <xref:System.Data.SqlClient.SqlCommand> można wywołać procedury składowanej z jednego parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="da000-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="da000-177"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Właściwość <xref:System.Data.SqlClient.SqlParameter> ma ustawioną wartość `Structured`.</span><span class="sxs-lookup"><span data-stu-id="da000-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="da000-178"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Przekazuje `OracleDataReader` zestawu wyników procedury składowanej jako parametru przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="da000-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="da000-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da000-179">See Also</span></span>  
 [<span data-ttu-id="da000-180">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="da000-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="da000-181">Poleceń i parametrów</span><span class="sxs-lookup"><span data-stu-id="da000-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="da000-182">Element DataAdapter parametrów</span><span class="sxs-lookup"><span data-stu-id="da000-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="da000-183">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="da000-183">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="da000-184">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="da000-184">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
