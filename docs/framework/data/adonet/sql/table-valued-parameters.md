---
title: Parametry o wartościach tabelowych
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2917a8d9b42d831566855271a2f2110637db586f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174475"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="0acc9-102">Parametry o wartościach tabelowych</span><span class="sxs-lookup"><span data-stu-id="0acc9-102">Table-Valued Parameters</span></span>
<span data-ttu-id="0acc9-103">Parametry wyceniane w tabeli umożliwiają organizowanie wielu wierszy danych z aplikacji klienckiej do programu SQL Server bez konieczności wielokrotnego rund lub specjalnej logiki po stronie serwera do przetwarzania danych.</span><span class="sxs-lookup"><span data-stu-id="0acc9-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="0acc9-104">Za pomocą parametrów wycenionych w tabeli można hermetyzować wiersze danych w aplikacji klienckiej i wysyłać dane do serwera za pomocą jednego parametru.</span><span class="sxs-lookup"><span data-stu-id="0acc9-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="0acc9-105">Wiersze danych przychodzących są przechowywane w zmiennej tabeli, która następnie może być obsługiwana przy użyciu transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="0acc9-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="0acc9-106">Wartości kolumn w parametrach wycenionych w tabeli są dostępne przy użyciu standardowych instrukcji Transact-SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="0acc9-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="0acc9-107">Parametry wyceniane w tabeli są silnie wpisywane, a ich struktura jest automatycznie sprawdzana.</span><span class="sxs-lookup"><span data-stu-id="0acc9-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="0acc9-108">Rozmiar parametrów wycenianych w tabeli jest ograniczony tylko przez pamięć serwera.</span><span class="sxs-lookup"><span data-stu-id="0acc9-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0acc9-109">Nie można zwrócić danych w parametrze wycenianym w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="0acc9-110">Parametry wyceniane w tabeli są tylko wejściowe; słowo kluczowe OUTPUT nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0acc9-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="0acc9-111">Aby uzyskać więcej informacji na temat parametrów wycenianych w tabeli, zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="0acc9-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="0acc9-112">Zasób</span><span class="sxs-lookup"><span data-stu-id="0acc9-112">Resource</span></span>|<span data-ttu-id="0acc9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0acc9-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="0acc9-114">Użyj parametrów wycenionych tabelą (aparat bazy danych)</span><span class="sxs-lookup"><span data-stu-id="0acc9-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="0acc9-115">W tym artykule opisano sposób tworzenia i używania parametrów wycenianych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="0acc9-116">[Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="0acc9-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="0acc9-117">Opisuje typy tabel zdefiniowane przez użytkownika, które są używane do deklarowania parametrów wycenianych przez tabelę.</span><span class="sxs-lookup"><span data-stu-id="0acc9-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="0acc9-118">Przekazywanie wielu wierszy w poprzednich wersjach programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="0acc9-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="0acc9-119">Przed wprowadzeniem parametrów wycenianych w tabeli do programu SQL Server 2008 opcje przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone.</span><span class="sxs-lookup"><span data-stu-id="0acc9-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="0acc9-120">Deweloper może wybrać jedną z następujących opcji przekazywania wielu wierszy do serwera:</span><span class="sxs-lookup"><span data-stu-id="0acc9-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="0acc9-121">Użyj serii poszczególnych parametrów do reprezentowania wartości w wielu kolumnach i wierszach danych.</span><span class="sxs-lookup"><span data-stu-id="0acc9-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="0acc9-122">Ilość danych, które mogą być przekazywane przy użyciu tej metody jest ograniczona przez liczbę dozwolonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="0acc9-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="0acc9-123">Procedury programu SQL Server mogą mieć co najwyżej 2100 parametrów.</span><span class="sxs-lookup"><span data-stu-id="0acc9-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="0acc9-124">Logika po stronie serwera jest wymagana do zmontowanie tych poszczególnych wartości w zmiennej tabeli lub tabeli tymczasowej do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="0acc9-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="0acc9-125">Łącz wiele wartości danych w rozdzielone ciągi lub dokumenty XML, a następnie przekaż te wartości tekstowe do procedury lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0acc9-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="0acc9-126">Wymaga to, aby procedura lub instrukcja zawierała logikę niezbędną do sprawdzania poprawności struktur danych i rozdziału wartości.</span><span class="sxs-lookup"><span data-stu-id="0acc9-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="0acc9-127">Utwórz serię pojedynczych instrukcji SQL dla modyfikacji danych, które wpływają `Update` na wiele <xref:System.Data.SqlClient.SqlDataAdapter>wierszy, takich jak te utworzone przez wywołanie metody .</span><span class="sxs-lookup"><span data-stu-id="0acc9-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="0acc9-128">Zmiany można przesyłać do serwera indywidualnie lub wsadowo w grupach.</span><span class="sxs-lookup"><span data-stu-id="0acc9-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="0acc9-129">Jednak nawet po przesłaniu w partiach, które zawierają wiele instrukcji, każda instrukcja jest wykonywana oddzielnie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0acc9-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="0acc9-130">Użyj `bcp` programu narzędziowego <xref:System.Data.SqlClient.SqlBulkCopy> lub obiektu, aby załadować wiele wierszy danych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="0acc9-131">Mimo że ta technika jest bardzo wydajne, nie obsługuje przetwarzania po stronie serwera, chyba że dane są ładowane do tabeli tymczasowej lub zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="0acc9-132">Tworzenie typów parametrów wycenianych według tabel</span><span class="sxs-lookup"><span data-stu-id="0acc9-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="0acc9-133">Parametry wyceniane w tabeli są oparte na silnie typizowanych strukturach tabel, które są definiowane przy użyciu instrukcji Transact-SQL CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="0acc9-133">Table-valued parameters are based on strongly-typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="0acc9-134">Należy utworzyć typ tabeli i zdefiniować strukturę w programie SQL Server, zanim będzie można użyć parametrów wycenionych w tabeli w aplikacjach klienckich.</span><span class="sxs-lookup"><span data-stu-id="0acc9-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="0acc9-135">Aby uzyskać więcej informacji na temat tworzenia typów tabel, zobacz [Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="0acc9-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="0acc9-136">Następująca instrukcja tworzy typ tabeli o nazwie CategoryTableType, który składa się z kolumn CategoryID i CategoryName:</span><span class="sxs-lookup"><span data-stu-id="0acc9-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="0acc9-137">Po utworzeniu typu tabeli można zadeklarować parametry wyceniane w tabeli na podstawie tego typu.</span><span class="sxs-lookup"><span data-stu-id="0acc9-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="0acc9-138">Poniższy fragment Transact-SQL pokazuje, jak zadeklarować parametr wyceniony tabelą w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="0acc9-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="0acc9-139">Należy zauważyć, że READONLY słowo kluczowe jest wymagane do deklarowania parametru wyceniony tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="0acc9-140">Modyfikowanie danych za pomocą parametrów wycenianych w tabeli (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0acc9-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="0acc9-141">Parametry wyceniane w tabeli mogą być używane w modyfikacjach danych opartych na zestawie, które wpływają na wiele wierszy, wykonując pojedynczą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="0acc9-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="0acc9-142">Na przykład można zaznaczyć wszystkie wiersze w parametrze wycenianym w tabeli i wstawić je do tabeli bazy danych lub utworzyć instrukcję aktualizacji, łącząc parametr wyceniony tabelą z tabelą, którą chcesz zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="0acc9-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="0acc9-143">Poniższa instrukcja Transact-SQL UPDATE pokazuje, jak używać parametru wycenianego przez tabelę, łącząc go z tabelą Kategorie.</span><span class="sxs-lookup"><span data-stu-id="0acc9-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="0acc9-144">W przypadku użycia parametru wyceny tabeli z klauzulą JOIN w klauzuli FROM należy również alias, jak pokazano w tym miejscu, gdzie parametr wyceny tabeli jest aliasowany jako "ec":</span><span class="sxs-lookup"><span data-stu-id="0acc9-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="0acc9-145">W tym przykładzie Transact-SQL pokazano, jak wybrać wiersze z parametru wycenionego w tabeli, aby wykonać insert w operacji opartej na jednym zestawie.</span><span class="sxs-lookup"><span data-stu-id="0acc9-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="0acc9-146">Ograniczenia parametrów wycenionych w tabeli</span><span class="sxs-lookup"><span data-stu-id="0acc9-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="0acc9-147">Istnieje kilka ograniczeń parametrów wycenianych w tabeli:</span><span class="sxs-lookup"><span data-stu-id="0acc9-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="0acc9-148">Nie można przekazać parametrów wycenionych w tabeli do [funkcji zdefiniowanych przez użytkownika CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="0acc9-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="0acc9-149">Parametry wyceniane w tabeli mogą być indeksowane tylko w celu obsługi ograniczeń UNIQUE lub PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="0acc9-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="0acc9-150">SQL Server nie przechowuje statystyk dotyczących parametrów wycenianych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="0acc9-151">Parametry wyceniane w tabeli są tylko do odczytu w kodzie Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="0acc9-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="0acc9-152">Nie można zaktualizować wartości kolumn w wierszach parametru wycenionego w tabeli i nie można wstawiać ani usuwać wierszy.</span><span class="sxs-lookup"><span data-stu-id="0acc9-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="0acc9-153">Aby zmodyfikować dane przekazywane do procedury składowanej lub sparametryzowanej instrukcji w parametrze wycenionym w tabeli, należy wstawić dane do tabeli tymczasowej lub do zmiennej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="0acc9-154">Nie można użyć instrukcji ALTER TABLE do modyfikowania projektu parametrów wycenianych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="0acc9-155">Konfigurowanie przykładu programu SqlParameter</span><span class="sxs-lookup"><span data-stu-id="0acc9-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="0acc9-156"><xref:System.Data.SqlClient>obsługuje wypełnianie parametrów wycenionych <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> w tabeli z <xref:System.Data.DataTable>obiektów <xref:System.Data.Common.DbDataReader> lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="0acc9-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="0acc9-157">Należy określić nazwę typu dla parametru tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwości <xref:System.Data.SqlClient.SqlParameter>programu .</span><span class="sxs-lookup"><span data-stu-id="0acc9-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="0acc9-158">Musi `TypeName` odpowiadać nazwie zgodnego typu wcześniej utworzonego na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0acc9-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="0acc9-159">Poniższy fragment kodu pokazuje, <xref:System.Data.SqlClient.SqlParameter> jak skonfigurować wstawianie danych.</span><span class="sxs-lookup"><span data-stu-id="0acc9-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="0acc9-160">W poniższym przykładzie zmienna `addedCategories` zawiera plik <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="0acc9-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="0acc9-161">Aby zobaczyć, jak zmienna jest wypełniana, zobacz przykłady w następnej sekcji [Przekazywanie parametru wyceny tabeli do procedury składowanej](#passing).</span><span class="sxs-lookup"><span data-stu-id="0acc9-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="0acc9-162">Można również użyć dowolnego obiektu <xref:System.Data.Common.DbDataReader> uzyskanego z do strumienia wierszy danych do parametru wycenionego w tabeli, jak pokazano w tym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="0acc9-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="0acc9-163">Przekazywanie parametru wyceny tabeli do procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="0acc9-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="0acc9-164">W tym przykładzie pokazano, jak przekazać dane parametrów wyceniane w tabeli do procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="0acc9-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="0acc9-165">Kod wyodrębnia dodane wiersze <xref:System.Data.DataTable> do nowego <xref:System.Data.DataTable.GetChanges%2A> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="0acc9-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="0acc9-166">Następnie kod definiuje <xref:System.Data.SqlClient.SqlCommand>, ustawienie <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwości <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="0acc9-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="0acc9-167">Wypełniana <xref:System.Data.SqlClient.SqlParameter> jest przy <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> użyciu <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> metody, `Structured`a ustawiona jest na .</span><span class="sxs-lookup"><span data-stu-id="0acc9-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="0acc9-168">Następnie <xref:System.Data.SqlClient.SqlCommand> jest wykonywany przy <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="0acc9-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="0acc9-169">Przekazywanie parametru wyceny tabeli do sparametryzowanej instrukcji SQL</span><span class="sxs-lookup"><span data-stu-id="0acc9-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="0acc9-170">W poniższym przykładzie pokazano, jak wstawić dane do dbo. Tabela Kategorie przy użyciu instrukcji INSERT z podkwerendą SELECT, która ma parametr wyceniony tabelą jako źródło danych.</span><span class="sxs-lookup"><span data-stu-id="0acc9-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="0acc9-171">Podczas przekazywania parametru wyceny tabeli do sparametryzowanej instrukcji SQL należy określić <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> nazwę <xref:System.Data.SqlClient.SqlParameter>typu parametru wycenionego przez tabelę przy użyciu nowej właściwości programu .</span><span class="sxs-lookup"><span data-stu-id="0acc9-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="0acc9-172">Musi `TypeName` to być zgodne z nazwą zgodnego typu wcześniej utworzonego na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0acc9-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="0acc9-173">Kod w tym przykładzie `TypeName` używa właściwości do odwoływania się do struktury typu zdefiniowanej w dbo. Typ kategorii.</span><span class="sxs-lookup"><span data-stu-id="0acc9-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0acc9-174">Jeśli podasz wartość kolumny tożsamości w parametrze wycenionym w tabeli, musisz wydać instrukcję SET IDENTITY_INSERT dla sesji.</span><span class="sxs-lookup"><span data-stu-id="0acc9-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="0acc9-175">Przesyłanie strumieniowe wierszy za pomocą czytnika danych</span><span class="sxs-lookup"><span data-stu-id="0acc9-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="0acc9-176">Można również użyć dowolnego obiektu <xref:System.Data.Common.DbDataReader> uzyskanego z do strumienia wierszy danych do parametru wycenionego w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="0acc9-177">Poniższy fragment kodu demonstruje pobieranie danych z <xref:System.Data.OracleClient.OracleCommand> bazy <xref:System.Data.OracleClient.OracleDataReader>danych Oracle przy użyciu i .</span><span class="sxs-lookup"><span data-stu-id="0acc9-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="0acc9-178">Kod następnie konfiguruje <xref:System.Data.SqlClient.SqlCommand> wywołać procedurę składowaną z jednym parametrem wejściowym.</span><span class="sxs-lookup"><span data-stu-id="0acc9-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="0acc9-179">Właściwość <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> jest <xref:System.Data.SqlClient.SqlParameter> ustawiona `Structured`na .</span><span class="sxs-lookup"><span data-stu-id="0acc9-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="0acc9-180">Przekazuje <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> `OracleDataReader` zestaw wyników do procedury składowanej jako parametr wyceniony w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0acc9-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0acc9-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0acc9-181">See also</span></span>

- [<span data-ttu-id="0acc9-182">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="0acc9-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="0acc9-183">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="0acc9-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="0acc9-184">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="0acc9-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="0acc9-185">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0acc9-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="0acc9-186">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0acc9-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
