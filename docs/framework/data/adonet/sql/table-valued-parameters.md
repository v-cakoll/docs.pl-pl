---
title: Parametry z wartościami przechowywanymi w tabeli
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 130b5338b14bc7c1f36feb620d549295867ef64e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527773"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="a8477-102">Parametry z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="a8477-102">Table-Valued Parameters</span></span>
<span data-ttu-id="a8477-103">Parametry z wartościami przechowywanymi w tabeli zawierają łatwy sposób organizowania wielu wierszy danych z aplikacji klienckiej programu SQL Server, bez konieczności wielu wystąpień komunikacji dwustronnej lub specjalne logiki po stronie serwera związane z przetwarzaniem danych.</span><span class="sxs-lookup"><span data-stu-id="a8477-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="a8477-104">Parametry z wartościami przechowywanymi w tabeli można użyć do hermetyzacji wierszy danych w aplikacji klienckiej i wysyłania danych do serwera za pomocą jednego polecenia sparametryzowanych.</span><span class="sxs-lookup"><span data-stu-id="a8477-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="a8477-105">Przychodzące wiersze danych są przechowywane w zmiennej tabeli, która może być eksploatowana przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8477-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a8477-106">Wartości parametrów z wartościami przechowywanymi w tabeli kolumn można uzyskać dostęp przy użyciu standardu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji "SELECT".</span><span class="sxs-lookup"><span data-stu-id="a8477-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="a8477-107">Parametry z wartościami przechowywanymi w tabeli są silnie typizowane i ich struktury jest automatycznie weryfikowana.</span><span class="sxs-lookup"><span data-stu-id="a8477-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="a8477-108">Rozmiar parametrów z wartościami przechowywanymi w tabeli jest ograniczony tylko ilością pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="a8477-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8477-109">Parametr z wartościami przechowywanymi w tabeli nie może zwrócić danych.</span><span class="sxs-lookup"><span data-stu-id="a8477-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="a8477-110">Parametry z wartościami przechowywanymi w tabeli są tylko wejściowym; dane wyjściowe — słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a8477-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="a8477-111">Aby uzyskać więcej informacji na temat parametrów z wartościami przechowywanymi w tabeli zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="a8477-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="a8477-112">Zasób</span><span class="sxs-lookup"><span data-stu-id="a8477-112">Resource</span></span>|<span data-ttu-id="a8477-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a8477-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a8477-114">[Parametry z wartościami przechowywanymi w tabeli (aparat bazy danych)](https://go.microsoft.com/fwlink/?LinkId=98363) w SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="a8477-114">[Table-Valued Parameters (Database Engine)](https://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server Books Online</span></span>|<span data-ttu-id="a8477-115">W tym artykule opisano sposób tworzenia i używania parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="a8477-116">[Typy tabel zdefiniowane przez użytkownika](https://go.microsoft.com/fwlink/?LinkId=98364) w SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="a8477-116">[User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server Books Online</span></span>|<span data-ttu-id="a8477-117">W tym artykule opisano typy tabel zdefiniowane przez użytkownika, które są używane do deklarowania parametry z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="a8477-118">Przekazywanie wielu wierszy w poprzednich wersjach programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="a8477-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="a8477-119">Zanim parametry z wartościami przechowywanymi w tabeli zostały wprowadzone do programu SQL Server 2008, opcji przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone.</span><span class="sxs-lookup"><span data-stu-id="a8477-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="a8477-120">Deweloper może wybrać spośród następujących opcji przekazywania wiele wierszy do serwera:</span><span class="sxs-lookup"><span data-stu-id="a8477-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="a8477-121">Użyj szereg poszczególne parametry do reprezentowania wartości w wielu kolumn i wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="a8477-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="a8477-122">Ilość danych, który może być przekazywany przy użyciu tej metody jest ograniczona przez liczbę parametry są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="a8477-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="a8477-123">Procedury programu SQL Server może mieć co najwyżej 2100 parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8477-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="a8477-124">Logiki po stronie serwera jest wymagany do budowania tych poszczególne wartości do zmiennej tabeli lub tabeli tymczasowej do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="a8477-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="a8477-125">Pakietu wiele wartości danych do ciągów rozdzielanych lub dokumentów XML, a następnie przekazać te wartości tekstowych do procedury lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a8477-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="a8477-126">Wymaga to procedury lub instrukcję, aby uwzględnić logikę niezbędną do zweryfikowania struktur danych oraz wydzielenie wartości.</span><span class="sxs-lookup"><span data-stu-id="a8477-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="a8477-127">Utwórz serie pojedyncze instrukcje SQL dla modyfikacji danych, które wpływają na wiele wierszy, takich jak te utworzone przez wywołanie metody `Update` metody <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="a8477-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="a8477-128">Zmiany można przesłać na serwer indywidualnie lub partii w grupy.</span><span class="sxs-lookup"><span data-stu-id="a8477-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="a8477-129">Jednak nawet wtedy, gdy przesyłany w partiach, które zawierają wiele instrukcji, każda instrukcja jest wykonywana oddzielnie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="a8477-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="a8477-130">Użyj `bcp` programu narzędziowego lub <xref:System.Data.SqlClient.SqlBulkCopy> obiekt, aby załadować wiele wierszy danych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="a8477-131">Chociaż ta technika jest bardzo wydajny, nie obsługuje przetwarzania po stronie serwera, chyba, że dane są ładowane do tabeli tymczasowej lub zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="a8477-132">Tworzenie typów parametru z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="a8477-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="a8477-133">Parametry z wartościami przechowywanymi w tabeli zależą od struktury silnie typizowane tabel, które są zdefiniowane przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="a8477-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="a8477-134">Masz typ tabeli na utworzenie i zdefiniowanie struktury w programie SQL Server, zanim użyjesz parametry z wartościami przechowywanymi w tabeli w aplikacjach klienckich.</span><span class="sxs-lookup"><span data-stu-id="a8477-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="a8477-135">Aby uzyskać więcej informacji na temat tworzenia użytkownika, typach tabel zobacz [typy tabel zdefiniowane przez użytkownika](https://go.microsoft.com/fwlink/?LinkID=98364) w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="a8477-135">For more information about creating table types, see [User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a8477-136">Poniższa instrukcja umożliwia utworzenie tabeli o nazwie CategoryTableType, który składa się z identyfikatorem kategorii i CategoryName kolumn:</span><span class="sxs-lookup"><span data-stu-id="a8477-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="a8477-137">Po utworzeniu tabeli, możesz deklarować parametry z wartościami przechowywanymi w tabeli na podstawie tego typu.</span><span class="sxs-lookup"><span data-stu-id="a8477-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="a8477-138">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment przedstawia sposób deklarowania parametrem z wartościami przechowywanymi w tabeli, w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="a8477-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="a8477-139">Należy pamiętać, że READONLY — słowo kluczowe jest wymagany do deklarowania parametr z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="a8477-140">Modyfikowanie danych za pomocą parametrów z wartościami przechowywanymi w tabeli (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a8477-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="a8477-141">Parametry z wartościami przechowywanymi w tabeli może służyć w zmiany na podstawie zestawu danych, które mają wpływ na wiele wierszy, wykonując pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a8477-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="a8477-142">Na przykład można wybrać wszystkie wiersze w parametr z wartościami przechowywanymi w tabeli i wstawianie tabeli bazy danych lub można utworzyć instrukcji update, dołączając do parametru z wartościami przechowywanymi w tabeli do tabeli, które chcesz zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="a8477-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="a8477-143">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji UPDATE pokazuje sposób użycia parametru z wartościami przechowywanymi w tabeli przez dołączenie go do tabeli Kategorie.</span><span class="sxs-lookup"><span data-stu-id="a8477-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="a8477-144">Korzystając z parametru z wartościami przechowywanymi w tabeli ze sprzężeniem w klauzuli FROM, musisz mieć również aliasu, jak pokazano w tym miejscu, gdzie parametr z wartościami przechowywanymi w tabeli ma alias "WE":</span><span class="sxs-lookup"><span data-stu-id="a8477-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="a8477-145">To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] przykład pokazuje, jak w celu wybrania wierszy z wartościami przechowywanymi w tabeli parametru przeprowadzić WSTAWIANIA w ramach jednej operacji na podstawie zestawu.</span><span class="sxs-lookup"><span data-stu-id="a8477-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="a8477-146">Ograniczenia dotyczące parametrów z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="a8477-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="a8477-147">Istnieje również kilka ograniczeń do parametrów z wartościami przechowywanymi w tabeli:</span><span class="sxs-lookup"><span data-stu-id="a8477-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="a8477-148">Nie można przekazać parametry wartościami przechowywanymi w tabeli [funkcje zdefiniowane przez użytkownika CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="a8477-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
-   <span data-ttu-id="a8477-149">Parametry z wartościami przechowywanymi w tabeli mogą być indeksowane tylko do obsługi ograniczenia UNIQUE i PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="a8477-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="a8477-150">Program SQL Server nie są zachowywane dane statystyczne dotyczące parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="a8477-151">Parametry z wartościami przechowywanymi w tabeli są tylko do odczytu w [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="a8477-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="a8477-152">Nie można zaktualizować wartości w kolumnach w wierszach parametr z wartościami przechowywanymi w tabeli i nie można wstawić lub usuwania wierszy.</span><span class="sxs-lookup"><span data-stu-id="a8477-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="a8477-153">Aby zmodyfikować danych, który jest przekazywany do procedury składowanej lub sparametryzowanych instrukcji w parametr z wartościami przechowywanymi w tabeli, należy wstawić dane do tabeli tymczasowej lub zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="a8477-154">Nie można użyć instrukcji ALTER TABLE, aby zmodyfikować projekt parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="a8477-155">Konfigurowanie przykładzie parametr SqlParameter</span><span class="sxs-lookup"><span data-stu-id="a8477-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="a8477-156"><xref:System.Data.SqlClient> obsługuje wypełniania wartościami przechowywanymi w tabeli Parametry z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> lub <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a8477-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="a8477-157">Należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="a8477-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="a8477-158">`TypeName` Musi pasować do nazwy zgodne z typem wcześniej utworzony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="a8477-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="a8477-159">Poniższy fragment kodu pokazuje, jak skonfigurować <xref:System.Data.SqlClient.SqlParameter> wstawiania danych.</span><span class="sxs-lookup"><span data-stu-id="a8477-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
 
<span data-ttu-id="a8477-160">W poniższym przykładzie `addedCategories` zmienna zawiera <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a8477-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a8477-161">Aby dowiedzieć się, jak zmienna jest wypełniana, zobacz przykłady w następnej sekcji [przekazywania parametru Table-Valued do procedury składowanej](#passing).</span><span class="sxs-lookup"><span data-stu-id="a8477-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="a8477-162">Można również użyć dowolnego obiektu pochodzącego z <xref:System.Data.Common.DbDataReader> do wierszy strumień danych do parametru wartościami przechowywanymi w tabeli, jak pokazano w tym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="a8477-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing"></a> <span data-ttu-id="a8477-163">Przekazywanie parametru z wartościami przechowywanymi w tabeli do procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="a8477-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="a8477-164">W tym przykładzie pokazano, jak przekazać parametr z wartościami przechowywanymi w tabeli dane do procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="a8477-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="a8477-165">Kod wyodrębnia dodanymi wierszami w nowym <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a8477-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="a8477-166">W kodzie następnie zdefiniowano <xref:System.Data.SqlClient.SqlCommand>, ustawiając <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwość <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="a8477-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="a8477-167"><xref:System.Data.SqlClient.SqlParameter> Jest wypełniana przy użyciu <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metody i <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ustawiono `Structured`.</span><span class="sxs-lookup"><span data-stu-id="a8477-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="a8477-168"><xref:System.Data.SqlClient.SqlCommand> Są następnie wykonywane za pomocą <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a8477-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="a8477-169">Przekazywanie parametru z wartościami przechowywanymi w tabeli do instrukcji SQL — sparametryzowane</span><span class="sxs-lookup"><span data-stu-id="a8477-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="a8477-170">Poniższy przykład pokazuje, jak wstawić dane do dbo. Tabela kategorie za pomocą instrukcji INSERT podzapytania SELECT, która ma parametr z wartościami przechowywanymi w tabeli jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a8477-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="a8477-171">Podczas przekazywania parametru z wartościami przechowywanymi w tabeli do sparametryzowanych instrukcji SQL, należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli za pomocą nowego <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="a8477-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="a8477-172">To `TypeName` musi pasować do nazwy zgodne z typem wcześniej utworzony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="a8477-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="a8477-173">W kodzie, w tym przykładzie użyto `TypeName` właściwości w celu odwołania struktury typ zdefiniowany w dbo. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="a8477-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8477-174">Jeśli podana wartość dla kolumny tożsamości w parametr z wartościami przechowywanymi w tabeli, należy wygenerować instrukcji USTAWIONY atrybut IDENTITY_INSERT dla sesji.</span><span class="sxs-lookup"><span data-stu-id="a8477-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="a8477-175">Wiersze przesyłania strumieniowego przy użyciu elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="a8477-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="a8477-176">Można również użyć dowolnego obiektu pochodzącego z <xref:System.Data.Common.DbDataReader> do wierszy strumień danych do parametru z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="a8477-177">Poniższy fragment kodu przedstawia pobieranie danych z bazy danych Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand> i <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a8477-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="a8477-178">Kod następnie konfiguruje <xref:System.Data.SqlClient.SqlCommand> do wywołania procedury składowanej z jednego parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="a8477-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="a8477-179"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Właściwość <xref:System.Data.SqlClient.SqlParameter> ustawiono `Structured`.</span><span class="sxs-lookup"><span data-stu-id="a8477-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="a8477-180"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Przekazuje `OracleDataReader` zestawu wyników procedury składowanej jako parametr z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a8477-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8477-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8477-181">See also</span></span>
- [<span data-ttu-id="a8477-182">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="a8477-182">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="a8477-183">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="a8477-183">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="a8477-184">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a8477-184">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [<span data-ttu-id="a8477-185">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8477-185">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [<span data-ttu-id="a8477-186">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a8477-186">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
