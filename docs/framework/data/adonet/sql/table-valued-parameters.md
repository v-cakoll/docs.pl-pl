---
title: Parametry o wartościach tabelowych
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: b968c599cf061fbd03b7ba8fb19470f6ace11a55
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202174"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="2d153-102">Parametry o wartościach tabelowych</span><span class="sxs-lookup"><span data-stu-id="2d153-102">Table-Valued Parameters</span></span>
<span data-ttu-id="2d153-103">Parametry z wartościami przechowywanymi w tabeli umożliwiają łatwe kierowanie wielu wierszy danych z aplikacji klienckiej w celu SQL Server bez konieczności wykonywania wielu operacji rundy lub specjalnej logiki po stronie serwera do przetwarzania danych.</span><span class="sxs-lookup"><span data-stu-id="2d153-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="2d153-104">Parametry z wartościami przechowywanymi w tabeli służą do hermetyzowania wierszy danych w aplikacji klienckiej i wysyłania danych na serwer w jednym sparametryzowanym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="2d153-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="2d153-105">Przychodzące wiersze danych są przechowywane w zmiennej tabeli, która może być następnie obsługiwana przy użyciu języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2d153-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="2d153-106">Wartości kolumn w parametrach z wartościami przechowywanymi w tabeli są dostępne za pomocą standardowych instrukcji SELECT języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2d153-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="2d153-107">Parametry z wartościami przechowywanymi w tabeli są jednoznacznie wpisane i ich struktura jest automatycznie sprawdzana.</span><span class="sxs-lookup"><span data-stu-id="2d153-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="2d153-108">Rozmiar parametrów z wartościami przechowywanymi w tabeli jest ograniczony tylko do pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="2d153-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d153-109">Nie można zwrócić danych w parametrze z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="2d153-110">Parametry z wartościami przechowywanymi w tabeli są tylko danymi wejściowymi. słowo kluczowe OUTPUT nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2d153-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="2d153-111">Aby uzyskać więcej informacji na temat parametrów z wartościami przechowywanymi w tabeli, zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="2d153-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="2d153-112">Zasób</span><span class="sxs-lookup"><span data-stu-id="2d153-112">Resource</span></span>|<span data-ttu-id="2d153-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2d153-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2d153-114">Używanie parametrów z wartościami przechowywanymi w tabeli (aparat bazy danych)</span><span class="sxs-lookup"><span data-stu-id="2d153-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="2d153-115">Opisuje sposób tworzenia i używania parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="2d153-116">[Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="2d153-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="2d153-117">Opisuje typy tabel zdefiniowane przez użytkownika, które są używane do deklarowania parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="2d153-118">Przekazywanie wielu wierszy w poprzednich wersjach SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d153-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="2d153-119">Przed wprowadzeniem parametrów z wartościami przechowywanymi w tabeli do SQL Server 2008 opcje przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone.</span><span class="sxs-lookup"><span data-stu-id="2d153-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="2d153-120">Deweloper może wybrać jedną z następujących opcji przekazywania wielu wierszy do serwera:</span><span class="sxs-lookup"><span data-stu-id="2d153-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="2d153-121">Użyj szeregu poszczególnych parametrów do reprezentowania wartości w wielu kolumnach i wierszach danych.</span><span class="sxs-lookup"><span data-stu-id="2d153-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="2d153-122">Ilość danych, które mogą być przesyłane za pomocą tej metody, jest ograniczona przez liczbę dozwolonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2d153-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="2d153-123">Procedury SQL Server mogą mieć co najwyżej 2100 parametrów.</span><span class="sxs-lookup"><span data-stu-id="2d153-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="2d153-124">Logika po stronie serwera jest wymagana do złożenia tych pojedynczych wartości w zmiennej tabeli lub tymczasowej tabeli do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="2d153-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="2d153-125">Należy powiązać wiele wartości danych z rozdzielanymi ciągami lub dokumentami XML, a następnie przekazać te wartości tekstowe do procedury lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2d153-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="2d153-126">Wymaga to wykonania procedury lub instrukcji w celu uwzględnienia logiki niezbędnej do walidacji struktur danych i oddzielania wartości.</span><span class="sxs-lookup"><span data-stu-id="2d153-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="2d153-127">Utwórz serię pojedynczych instrukcji SQL na potrzeby modyfikacji danych, które mają wpływ na wiele wierszy, takich jak te utworzone przez wywołanie `Update` metody <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="2d153-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="2d153-128">Zmiany mogą być przesyłane do serwera pojedynczo lub wsadowo do grup.</span><span class="sxs-lookup"><span data-stu-id="2d153-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="2d153-129">Jednak nawet w przypadku przesyłania w partiach zawierających wiele instrukcji każda instrukcja jest wykonywana osobno na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2d153-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="2d153-130">Użyj `bcp` programu narzędziowego lub <xref:System.Data.SqlClient.SqlBulkCopy> obiektu do załadowania wielu wierszy danych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="2d153-131">Chociaż ta technika jest bardzo wydajna, nie obsługuje przetwarzania po stronie serwera, chyba że dane są ładowane do tabeli tymczasowej ani zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="2d153-132">Tworzenie typów parametrów z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="2d153-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="2d153-133">Parametry z wartościami przechowywanymi w tabeli są oparte na strukturach tabel o jednoznacznie określonym typie, które są zdefiniowane przy użyciu instrukcji CREATE TYPE języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2d153-133">Table-valued parameters are based on strongly typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="2d153-134">Należy utworzyć typ tabeli i zdefiniować strukturę w SQL Server zanim będzie można używać parametrów z wartościami przechowywanymi w tabeli w aplikacjach klienckich.</span><span class="sxs-lookup"><span data-stu-id="2d153-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="2d153-135">Aby uzyskać więcej informacji na temat tworzenia typów tabel, zobacz [Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="2d153-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="2d153-136">Poniższa instrukcja tworzy typ tabeli o nazwie CategoryTableType, która składa się z kolumn IDKategorii i CategoryName:</span><span class="sxs-lookup"><span data-stu-id="2d153-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="2d153-137">Po utworzeniu typu tabeli można zadeklarować parametry z wartościami przechowywanymi w tabeli na podstawie tego typu.</span><span class="sxs-lookup"><span data-stu-id="2d153-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="2d153-138">Poniższy fragment języka Transact-SQL pokazuje, jak zadeklarować parametr z wartościami przechowywanymi w tabeli w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="2d153-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="2d153-139">Należy zauważyć, że słowo kluczowe READONLY jest wymagane do deklarowania parametru z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="2d153-140">Modyfikowanie danych za pomocą parametrów z wartościami przechowywanymi w tabeli (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2d153-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="2d153-141">Parametry z wartościami przechowywanymi w tabeli mogą być używane w modyfikacjach danych opartych na zestawie, które wpływają na wiele wierszy przez wykonanie pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2d153-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="2d153-142">Można na przykład wybrać wszystkie wiersze w parametrze z wartościami przechowywanymi w tabeli i wstawić je do tabeli bazy danych. można też utworzyć instrukcję Update, dołączając parametr z wartościami przechowywanymi w tabeli do tabeli, która ma zostać zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="2d153-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="2d153-143">W poniższej instrukcji Transact-SQL UPDATE pokazano, jak używać parametru z wartościami przechowywanymi w tabeli przez dołączenie go do tabeli Kategorie.</span><span class="sxs-lookup"><span data-stu-id="2d153-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="2d153-144">W przypadku używania parametru z wartościami przechowywanymi w tabeli i SPRZĘŻENIa w klauzuli FROM należy również zastosować alias, jak pokazano tutaj, gdzie parametr z wartościami przechowywanymi w tabeli jest aliasem "EC":</span><span class="sxs-lookup"><span data-stu-id="2d153-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="2d153-145">W tym przykładzie Transact-SQL pokazano, jak wybrać wiersze z parametru z wartościami przechowywanymi w tabeli, aby wykonać operację wstawiania w ramach jednej operacji opartej na zestawie.</span><span class="sxs-lookup"><span data-stu-id="2d153-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="2d153-146">Ograniczenia parametrów z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="2d153-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="2d153-147">Istnieją pewne ograniczenia dotyczące parametrów z wartościami przechowywanymi w tabeli:</span><span class="sxs-lookup"><span data-stu-id="2d153-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="2d153-148">Nie można przekazać parametrów z wartościami przechowywanymi w tabeli do [funkcji zdefiniowanych przez użytkownika CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="2d153-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="2d153-149">Parametry z wartościami przechowywanymi w tabeli można indeksować tylko w celu obsługi ograniczeń UNIQUE lub PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="2d153-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="2d153-150">SQL Server nie utrzymuje statystyk dotyczących parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="2d153-151">Parametry z wartościami przechowywanymi w tabeli są tylko do odczytu w kodzie Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2d153-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="2d153-152">Nie można zaktualizować wartości kolumn w wierszach parametru z wartościami przechowywanymi w tabeli i nie można wstawiać ani usuwać wierszy.</span><span class="sxs-lookup"><span data-stu-id="2d153-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="2d153-153">Aby zmodyfikować dane, które są przesyłane do procedury składowanej lub sparametryzowanych instrukcji w parametrach z wartościami przechowywanymi w tabeli, należy wstawić dane do tabeli tymczasowej lub do zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="2d153-154">Nie można użyć instrukcji ALTER TABLE, aby zmodyfikować projekt parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="2d153-155">Konfigurowanie przykładu SqlParameter</span><span class="sxs-lookup"><span data-stu-id="2d153-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="2d153-156"><xref:System.Data.SqlClient>obsługuje wypełnianie parametrów z wartościami przechowywanymi w tabeli z <xref:System.Data.DataTable> <xref:System.Data.Common.DbDataReader> <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> obiektów lub.</span><span class="sxs-lookup"><span data-stu-id="2d153-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="2d153-157">Należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwości <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="2d153-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="2d153-158">`TypeName`Musi być zgodna z nazwą zgodnego typu, który został wcześniej utworzony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2d153-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="2d153-159">Poniższy fragment kodu ilustruje sposób konfigurowania <xref:System.Data.SqlClient.SqlParameter> programu w celu wstawiania danych.</span><span class="sxs-lookup"><span data-stu-id="2d153-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="2d153-160">W poniższym przykładzie `addedCategories` zmienna zawiera <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="2d153-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2d153-161">Aby zobaczyć, jak jest wypełniana zmienna, zobacz przykłady w następnej sekcji, przekazując parametr z wartościami przechowywanymi w [tabeli do procedury składowanej](#passing).</span><span class="sxs-lookup"><span data-stu-id="2d153-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="2d153-162">Można również użyć dowolnego obiektu pochodnego <xref:System.Data.Common.DbDataReader> do przesyłania strumieniowego danych do parametru z wartościami przechowywanymi w tabeli, jak pokazano w tym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="2d153-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="2d153-163">Przekazywanie parametru z wartościami przechowywanymi w tabeli do procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="2d153-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="2d153-164">Ten przykład ilustruje sposób przekazywania danych parametrów z wartościami przechowywanymi w tabeli do procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="2d153-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="2d153-165">Kod wyodrębnia dodane wiersze do nowego przy <xref:System.Data.DataTable> użyciu <xref:System.Data.DataTable.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d153-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="2d153-166">Następnie kod definiuje <xref:System.Data.SqlClient.SqlCommand> , ustawiając <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Właściwość na <xref:System.Data.CommandType.StoredProcedure> .</span><span class="sxs-lookup"><span data-stu-id="2d153-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="2d153-167"><xref:System.Data.SqlClient.SqlParameter>Jest wypełniana przy użyciu <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metody i <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ma ustawioną wartość `Structured` .</span><span class="sxs-lookup"><span data-stu-id="2d153-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="2d153-168"><xref:System.Data.SqlClient.SqlCommand>Następnie jest wykonywane przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d153-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="2d153-169">Przekazywanie parametru z wartościami przechowywanymi w tabeli do sparametryzowanej instrukcji SQL</span><span class="sxs-lookup"><span data-stu-id="2d153-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="2d153-170">W poniższym przykładzie pokazano, jak wstawić dane do dbo. Tabela kategorii za pomocą instrukcji INSERT z podzapytaniem SELECT, które ma parametr z wartościami przechowywanymi w tabeli jako źródło danych.</span><span class="sxs-lookup"><span data-stu-id="2d153-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="2d153-171">Podczas przekazywania parametru z wartościami przechowywanymi w tabeli do sparametryzowanej instrukcji SQL należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli przy użyciu nowej <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwości <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="2d153-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="2d153-172">`TypeName`Musi być taka sama jak nazwa zgodnego typu, który został wcześniej utworzony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2d153-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="2d153-173">Kod w tym przykładzie używa właściwości, `TypeName` Aby odwołać się do struktury typu zdefiniowanej w dbo. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="2d153-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d153-174">W przypadku podania wartości dla kolumny tożsamości w parametrze z wartościami przechowywanymi w tabeli należy wydać instrukcję SET IDENTITY_INSERT dla sesji.</span><span class="sxs-lookup"><span data-stu-id="2d153-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="2d153-175">Przesyłanie strumieniowe wierszy za pomocą elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="2d153-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="2d153-176">Można również użyć dowolnego obiektu pochodnego <xref:System.Data.Common.DbDataReader> do przesyłania strumieniowego danych do parametru z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="2d153-177">Poniższy fragment kodu ilustruje pobieranie danych z bazy danych programu Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand> i <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="2d153-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="2d153-178">Następnie kod konfiguruje <xref:System.Data.SqlClient.SqlCommand> wywoływanie procedury składowanej z pojedynczym parametrem wejściowym.</span><span class="sxs-lookup"><span data-stu-id="2d153-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="2d153-179"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>Właściwość obiektu <xref:System.Data.SqlClient.SqlParameter> ma ustawioną wartość `Structured` .</span><span class="sxs-lookup"><span data-stu-id="2d153-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="2d153-180"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A>Przekazuje `OracleDataReader` wynik do procedury składowanej jako parametr z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2d153-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d153-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d153-181">See also</span></span>

- [<span data-ttu-id="2d153-182">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="2d153-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="2d153-183">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="2d153-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="2d153-184">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="2d153-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="2d153-185">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2d153-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="2d153-186">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2d153-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
