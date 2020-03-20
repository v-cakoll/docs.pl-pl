---
title: Modyfikowanie danych o dużej wartości (maks.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174280"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="6fadd-102">Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6fadd-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="6fadd-103">Typy danych dużych obiektów (LOB) to te, które przekraczają maksymalny rozmiar wiersza 8 kilobajtów (KB).</span><span class="sxs-lookup"><span data-stu-id="6fadd-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="6fadd-104">SQL Server `max` zapewnia specyfikator `nvarchar`dla `varbinary` `varchar`, i typów danych, aby umożliwić przechowywanie wartości tak dużych, jak 2 ^ 32 bajtów.</span><span class="sxs-lookup"><span data-stu-id="6fadd-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="6fadd-105">Kolumny tabeli i zmienne Transact-SQL mogą określać `varchar(max)`, `nvarchar(max)`lub `varbinary(max)` typy danych.</span><span class="sxs-lookup"><span data-stu-id="6fadd-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="6fadd-106">W ADO.NET, typy `max` danych mogą być pobierane przez `DataReader`, i może być również określony jako wartości parametrów wejściowych i wyjściowych bez żadnej specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="6fadd-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="6fadd-107">W `varchar` przypadku dużych typów danych dane mogą być pobierane i aktualizowane stopniowo.</span><span class="sxs-lookup"><span data-stu-id="6fadd-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="6fadd-108">Typy `max` danych mogą służyć do porównań, jako zmienne Transact-SQL i do łączenia.</span><span class="sxs-lookup"><span data-stu-id="6fadd-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="6fadd-109">Mogą być również używane w distinct, ORDER BY, GROUP BY klauzule SELECT instrukcji, jak również w agregatach, sprzężenia i podksyrii.</span><span class="sxs-lookup"><span data-stu-id="6fadd-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="6fadd-110">Poniższa tabela zawiera łącza do dokumentacji w programie SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="6fadd-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6fadd-111">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="6fadd-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="6fadd-112">[Korzystanie z typów danych o dużej wartości](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="6fadd-112">[Using Large-Value Data Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="6fadd-113">Ograniczenia typu o dużej wartości</span><span class="sxs-lookup"><span data-stu-id="6fadd-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="6fadd-114">Następujące ograniczenia mają zastosowanie `max` do typów danych, które nie istnieją dla mniejszych typów danych:</span><span class="sxs-lookup"><span data-stu-id="6fadd-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="6fadd-115">A `sql_variant` nie może `varchar` zawierać dużego typu danych.</span><span class="sxs-lookup"><span data-stu-id="6fadd-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="6fadd-116">Dużych `varchar` kolumn nie można określić jako kolumny klucza w indeksie.</span><span class="sxs-lookup"><span data-stu-id="6fadd-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="6fadd-117">Są one dozwolone w dołączonej kolumnie w indeksie nieklastrowanym.</span><span class="sxs-lookup"><span data-stu-id="6fadd-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="6fadd-118">Dużych `varchar` kolumn nie można używać jako partycjonowania kolumn klucza.</span><span class="sxs-lookup"><span data-stu-id="6fadd-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="6fadd-119">Praca z typami dużych wartości w transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6fadd-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="6fadd-120">Funkcja Transact-SQL `OPENROWSET` jest jednorazową metodą łączenia i uzyskiwania dostępu do zdalnych danych.</span><span class="sxs-lookup"><span data-stu-id="6fadd-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="6fadd-121">Zawiera wszystkie informacje o połączeniu niezbędne do uzyskania dostępu do zdalnych danych ze źródła danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="6fadd-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="6fadd-122">`OPENROWSET`można odwoływać się w klauzuli FROM kwerendy tak, jakby była to nazwa tabeli.</span><span class="sxs-lookup"><span data-stu-id="6fadd-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="6fadd-123">Można również odwoływać się jako tabela docelowa wstawić, UPDATE, lub DELETE instrukcji, z zastrzeżeniem możliwości dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="6fadd-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="6fadd-124">Funkcja `OPENROWSET` obejmuje `BULK` dostawcę zestawu wierszy, który umożliwia odczytywanie danych bezpośrednio z pliku bez ładowania danych do tabeli docelowej.</span><span class="sxs-lookup"><span data-stu-id="6fadd-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="6fadd-125">Umożliwia to użycie `OPENROWSET` w prostej instrukcji INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="6fadd-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="6fadd-126">Argumenty `OPENROWSET BULK` opcji zapewniają znaczną kontrolę nad tym, od czego zacząć i zakończyć odczyt danych, jak radzić sobie z błędami i jak dane są interpretowane.</span><span class="sxs-lookup"><span data-stu-id="6fadd-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="6fadd-127">Na przykład można określić, że plik danych będzie odczytywany jako jednowierszowy, jednokolumnowy zestaw wierszy typu `varbinary`, `varchar`lub `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="6fadd-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="6fadd-128">Aby uzyskać pełną składnię i opcje, zobacz SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="6fadd-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6fadd-129">Poniższy przykład wstawia zdjęcie do productphoto tabeli w adventureworks przykładowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6fadd-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="6fadd-130">Podczas korzystania `BULK OPENROWSET` z dostawcy, należy podać nazwany listy kolumn, nawet jeśli nie są wstawiania wartości do każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="6fadd-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="6fadd-131">Klucz podstawowy w tym przypadku jest zdefiniowany jako kolumna tożsamości i może zostać pominięty na liście kolumn.</span><span class="sxs-lookup"><span data-stu-id="6fadd-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="6fadd-132">Należy również zauważyć, że należy również podać nazwę `OPENROWSET` korelacji na końcu instrukcji, która w tym przypadku jest ThumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="6fadd-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="6fadd-133">Jest to skorelowane `ProductPhoto` z kolumną w tabeli, do której jest ładowany plik.</span><span class="sxs-lookup"><span data-stu-id="6fadd-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="6fadd-134">Aktualizowanie danych za pomocą aktualizacji . Napisz</span><span class="sxs-lookup"><span data-stu-id="6fadd-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="6fadd-135">Instrukcja Transact-SQL UPDATE zawiera nową składnię WRITE `varchar(max)` `nvarchar(max)`do `varbinary(max)` modyfikowania zawartości , lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="6fadd-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="6fadd-136">Dzięki temu można wykonać częściowe aktualizacje danych.</span><span class="sxs-lookup"><span data-stu-id="6fadd-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="6fadd-137">Aktualizacja . Składnia WRITE jest tutaj pokazana w formie skróconej:</span><span class="sxs-lookup"><span data-stu-id="6fadd-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="6fadd-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="6fadd-138">UPDATE</span></span>  
  
 <span data-ttu-id="6fadd-139">{ \* \<>obiektu\* }</span><span class="sxs-lookup"><span data-stu-id="6fadd-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="6fadd-140">SET</span><span class="sxs-lookup"><span data-stu-id="6fadd-140">SET</span></span>  
  
 <span data-ttu-id="6fadd-141">{ *column_name* = { . WRITE *expression* ( @Offset wyrażenie @Length , , ) }</span><span class="sxs-lookup"><span data-stu-id="6fadd-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="6fadd-142">Write Metoda określa, że sekcja wartości *column_name* zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="6fadd-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="6fadd-143">Wyrażenie jest wartością, która zostanie *column_name*skopiowana do `@Offset` column_name , jest to punkt początkowy, w `@Length` którym wyrażenie zostanie napisane, a argument jest długością sekcji w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="6fadd-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="6fadd-144">Jeśli użytkownik</span><span class="sxs-lookup"><span data-stu-id="6fadd-144">If</span></span>|<span data-ttu-id="6fadd-145">Następnie</span><span class="sxs-lookup"><span data-stu-id="6fadd-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="6fadd-146">Wyrażenie jest ustawione na NULL</span><span class="sxs-lookup"><span data-stu-id="6fadd-146">The expression is set to NULL</span></span>|<span data-ttu-id="6fadd-147">`@Length`jest ignorowana, a wartość w *column_name* jest obcinana w określonym `@Offset`pliku .</span><span class="sxs-lookup"><span data-stu-id="6fadd-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="6fadd-148">`@Offset`ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="6fadd-148">`@Offset` is NULL</span></span>|<span data-ttu-id="6fadd-149">Operacja aktualizacji dołącza wyrażenie na końcu istniejącej wartości *column_name* i `@Length` jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="6fadd-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="6fadd-150">`@Offset`jest większa niż długość wartości column_name</span><span class="sxs-lookup"><span data-stu-id="6fadd-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="6fadd-151">Program SQL Server zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="6fadd-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="6fadd-152">`@Length`ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="6fadd-152">`@Length` is NULL</span></span>|<span data-ttu-id="6fadd-153">Operacja aktualizacji usuwa wszystkie `@Offset` dane z do `column_name` końca wartości.</span><span class="sxs-lookup"><span data-stu-id="6fadd-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6fadd-154">Ani `@Offset` nie `@Length` może być ani liczba ujemna.</span><span class="sxs-lookup"><span data-stu-id="6fadd-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fadd-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fadd-155">Example</span></span>  
 <span data-ttu-id="6fadd-156">W tym przykładzie Transact-SQL aktualizuje wartość częściową w documentsummary, kolumnie `nvarchar(max)` w tabeli Dokument w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6fadd-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="6fadd-157">Wyraz "składniki" zastępuje się słowem "features" przez określenie słowa zastępczego, początkowej lokalizacji (przesunięcia) wyrazu, który ma zostać zastąpiony w istniejących danych, oraz liczby znaków, które mają zostać zastąpione (długość).</span><span class="sxs-lookup"><span data-stu-id="6fadd-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="6fadd-158">Przykład zawiera instrukcje SELECT przed i po update instrukcji, aby porównać wyniki.</span><span class="sxs-lookup"><span data-stu-id="6fadd-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="6fadd-159">Praca z typami o dużych wartościach w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6fadd-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="6fadd-160">Można pracować z dużymi typami wartości w ADO.NET, <xref:System.Data.SqlClient.SqlParameter> określając duże <xref:System.Data.SqlClient.SqlDataReader> typy wartości jako obiekty <xref:System.Data.SqlClient.SqlDataAdapter> w celu `DataSet` / `DataTable`zwrócenia zestawu wyników lub za pomocą a do wypełnienia .</span><span class="sxs-lookup"><span data-stu-id="6fadd-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="6fadd-161">Nie ma różnicy między sposobem pracy z typem dużej wartości a powiązanym z nim typem danych o mniejszej wartości.</span><span class="sxs-lookup"><span data-stu-id="6fadd-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="6fadd-162">Pobieranie danych za pomocą getsqlBytes</span><span class="sxs-lookup"><span data-stu-id="6fadd-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="6fadd-163">Metoda `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny.</span><span class="sxs-lookup"><span data-stu-id="6fadd-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="6fadd-164">Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada `cmd` obiekt o `varbinary(max)` nazwie, który <xref:System.Data.SqlClient.SqlDataReader> wybiera `reader` dane z tabeli <xref:System.Data.SqlTypes.SqlBytes>i obiekt o nazwie, który pobiera dane jako .</span><span class="sxs-lookup"><span data-stu-id="6fadd-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="6fadd-165">Pobieranie danych za pomocą programu GetSqlChars</span><span class="sxs-lookup"><span data-stu-id="6fadd-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="6fadd-166">Metoda `GetSqlChars` <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varchar(max)` kolumny lub `nvarchar(max)` kolumny.</span><span class="sxs-lookup"><span data-stu-id="6fadd-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="6fadd-167">Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada `cmd` obiekt o `nvarchar(max)` nazwie, który <xref:System.Data.SqlClient.SqlDataReader> wybiera `reader` dane z tabeli i obiekt o nazwie, który pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="6fadd-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="6fadd-168">Pobieranie danych za pomocą funkcji GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="6fadd-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="6fadd-169">Metoda `GetSqlBinary` a <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny.</span><span class="sxs-lookup"><span data-stu-id="6fadd-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="6fadd-170">Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada `cmd` obiekt o `varbinary(max)` nazwie, który <xref:System.Data.SqlClient.SqlDataReader> wybiera `reader` dane z tabeli <xref:System.Data.SqlTypes.SqlBinary> i obiekt o nazwie, który pobiera dane jako strumień.</span><span class="sxs-lookup"><span data-stu-id="6fadd-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="6fadd-171">Pobieranie danych za pomocą getbytów</span><span class="sxs-lookup"><span data-stu-id="6fadd-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="6fadd-172">Metoda `GetBytes` <xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z określonej kolumny przesuniętej do tablicy bajtów, zaczynając od określonego przesunięcia tablicy.</span><span class="sxs-lookup"><span data-stu-id="6fadd-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="6fadd-173">Poniższy fragment kodu <xref:System.Data.SqlClient.SqlDataReader> zakłada `reader` obiekt o nazwie, który pobiera bajty do tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="6fadd-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="6fadd-174">Należy zauważyć, `GetSqlBytes` `GetBytes` że w przeciwieństwie do , wymaga rozmiaru buforu tablicy.</span><span class="sxs-lookup"><span data-stu-id="6fadd-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="6fadd-175">Pobieranie danych za pomocą funkcji GetValue</span><span class="sxs-lookup"><span data-stu-id="6fadd-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="6fadd-176">Metoda `GetValue` odczytuje <xref:System.Data.SqlClient.SqlDataReader> wartość z określonej kolumny przesuniętej do tablicy.</span><span class="sxs-lookup"><span data-stu-id="6fadd-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="6fadd-177">Poniższy fragment kodu <xref:System.Data.SqlClient.SqlDataReader> zakłada `reader` obiekt o nazwie, który pobiera dane binarne z pierwszego przesunięcia kolumny, a następnie ciąg danych z drugiej kolumny przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="6fadd-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="6fadd-178">Konwertowanie z dużych typów wartości na typy CLR</span><span class="sxs-lookup"><span data-stu-id="6fadd-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="6fadd-179">Zawartość `varchar(max)` kolumny można `nvarchar(max)` przekonwertować przy użyciu dowolnej metody `ToString`konwersji ciągów, takiej jak .</span><span class="sxs-lookup"><span data-stu-id="6fadd-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="6fadd-180">Poniższy fragment kodu <xref:System.Data.SqlClient.SqlDataReader> zakłada `reader` obiekt o nazwie, który pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="6fadd-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="6fadd-181">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fadd-181">Example</span></span>  
 <span data-ttu-id="6fadd-182">Poniższy kod pobiera nazwę `LargePhoto` i obiekt `ProductPhoto` z `AdventureWorks` tabeli w bazie danych i zapisuje go w pliku.</span><span class="sxs-lookup"><span data-stu-id="6fadd-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="6fadd-183">Zestaw musi być skompilowany z <xref:System.Drawing> odwołaniem do obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="6fadd-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="6fadd-184">Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.SqlTypes.SqlBytes> obiekt, który udostępnia `Stream` właściwość.</span><span class="sxs-lookup"><span data-stu-id="6fadd-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="6fadd-185">Kod używa tego do utworzenia nowego `Bitmap` obiektu, a następnie `ImageFormat`zapisuje go w pliku Gif .</span><span class="sxs-lookup"><span data-stu-id="6fadd-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="6fadd-186">Korzystanie z parametrów typu dużej wartości</span><span class="sxs-lookup"><span data-stu-id="6fadd-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="6fadd-187">Duże typy wartości <xref:System.Data.SqlClient.SqlParameter> mogą być używane w obiektach <xref:System.Data.SqlClient.SqlParameter> w taki sam sposób, w jaki używane są mniejsze typy wartości w obiektach.</span><span class="sxs-lookup"><span data-stu-id="6fadd-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="6fadd-188">Można pobrać duże typy <xref:System.Data.SqlClient.SqlParameter> wartości jako wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6fadd-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="6fadd-189">Kod zakłada, że następująca procedura składowana GetDocumentSummary istnieje w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6fadd-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="6fadd-190">Procedura składowana przyjmuje parametr @DocumentID wejściowy o nazwie i zwraca zawartość @DocumentSummary kolumny DocumentSummary w parametrze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="6fadd-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="6fadd-191">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fadd-191">Example</span></span>  
 <span data-ttu-id="6fadd-192">Kod ADO.NET tworzy <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów do wykonania GetDocumentSummary procedury składowanej i pobrać podsumowanie dokumentu, który jest przechowywany jako typ dużej wartości.</span><span class="sxs-lookup"><span data-stu-id="6fadd-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="6fadd-193">Kod przekazuje wartość parametru wejściowego @DocumentID i wyświetla wyniki @DocumentSummary przekazane z powrotem w parametrze wyjściowym w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6fadd-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6fadd-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fadd-194">See also</span></span>

- [<span data-ttu-id="6fadd-195">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="6fadd-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="6fadd-196">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="6fadd-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="6fadd-197">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6fadd-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="6fadd-198">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6fadd-198">ADO.NET Overview</span></span>](../ado-net-overview.md)
