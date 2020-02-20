---
title: Modyfikowanie danych o dużej wartości (maks.)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 7ed036f5ad3a1c042ee277ecd2145f72746ef420
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451840"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="e0de3-102">Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0de3-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="e0de3-103">Typy danych dużego obiektu (LOB) to te, które przekraczają maksymalny rozmiar wiersza wynoszący 8 kilobajtów (KB).</span><span class="sxs-lookup"><span data-stu-id="e0de3-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="e0de3-104">SQL Server zawiera specyfikator `max` dla typów danych `varchar`, `nvarchar`i `varbinary`, aby zezwolić na przechowywanie wartości tak dużych, jak 2 ^ 32 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e0de3-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="e0de3-105">Kolumny tabeli i zmienne języka Transact-SQL mogą określać typy danych `varchar(max)`, `nvarchar(max)`lub `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="e0de3-106">W ADO.NET typy danych `max` mogą być pobierane przez `DataReader`i można je określić jako wartości parametrów wejściowych i wyjściowych bez żadnej specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="e0de3-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="e0de3-107">W przypadku dużych `varchar` typów danych można pobrać i zaktualizować dane przyrostowo.</span><span class="sxs-lookup"><span data-stu-id="e0de3-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="e0de3-108">Typy danych `max` mogą służyć do porównań, jako zmienne Transact-SQL i do łączenia.</span><span class="sxs-lookup"><span data-stu-id="e0de3-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="e0de3-109">Mogą być również używane w klauzulach DISTINCT, ORDER BY, GROUP BY instrukcji SELECT, a także w agregacjach, sprzężeniach i podzapytaniach.</span><span class="sxs-lookup"><span data-stu-id="e0de3-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="e0de3-110">Poniższa tabela zawiera linki do dokumentacji w SQL Server książki online.</span><span class="sxs-lookup"><span data-stu-id="e0de3-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e0de3-111">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="e0de3-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="e0de3-112">[Korzystanie z typów danych o dużej wartości](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="e0de3-112">[Using Large-Value Data Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="e0de3-113">Ograniczenia typu dużej wartości</span><span class="sxs-lookup"><span data-stu-id="e0de3-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="e0de3-114">Poniższe ograniczenia dotyczą typów danych `max`, które nie istnieją dla mniejszych typów danych:</span><span class="sxs-lookup"><span data-stu-id="e0de3-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="e0de3-115">`sql_variant` nie może zawierać dużego `varchar` typu danych.</span><span class="sxs-lookup"><span data-stu-id="e0de3-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="e0de3-116">Nie można określić dużych `varchar` kolumn jako kolumny klucza w indeksie.</span><span class="sxs-lookup"><span data-stu-id="e0de3-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="e0de3-117">Są one dozwolone w uwzględnionej kolumnie w nieklastrowanym indeksie.</span><span class="sxs-lookup"><span data-stu-id="e0de3-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="e0de3-118">Nie można używać dużych kolumn `varchar` jako kolumn klucza partycjonowania.</span><span class="sxs-lookup"><span data-stu-id="e0de3-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="e0de3-119">Praca z typami dużej wartości w języku Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e0de3-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="e0de3-120">Funkcja `OPENROWSET` języka Transact-SQL to jednorazowa Metoda łączenia się i uzyskiwania dostępu do danych zdalnych.</span><span class="sxs-lookup"><span data-stu-id="e0de3-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="e0de3-121">Zawiera wszystkie informacje o połączeniu niezbędne do uzyskania dostępu do danych zdalnych ze źródła danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="e0de3-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="e0de3-122">`OPENROWSET` można przywoływać w klauzuli FROM zapytania, tak jakby była nazwą tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0de3-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="e0de3-123">Może być również przywoływany jako tabela docelowa instrukcji INSERT, UPDATE lub DELETE, z uwzględnieniem możliwości dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="e0de3-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="e0de3-124">Funkcja `OPENROWSET` zawiera dostawcę zestawu wierszy `BULK`, który umożliwia odczytywanie danych bezpośrednio z pliku bez ładowania danych do tabeli docelowej.</span><span class="sxs-lookup"><span data-stu-id="e0de3-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="e0de3-125">Pozwala to na używanie `OPENROWSET` w prostej instrukcji INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="e0de3-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="e0de3-126">Argumenty opcji `OPENROWSET BULK` zapewniają znaczącą kontrolę nad tym, gdzie rozpocząć i zakończyć odczytywanie danych, jak rozwiązywać problemy oraz jak interpretować dane.</span><span class="sxs-lookup"><span data-stu-id="e0de3-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="e0de3-127">Można na przykład określić, że plik danych ma być odczytywany jako pojedynczy wiersz zestawu wierszy jednokolumnowych typu `varbinary`, `varchar`lub `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="e0de3-128">Pełną składnię i opcje można znaleźć w temacie SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="e0de3-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e0de3-129">Poniższy przykład wstawia zdjęcie do tabeli ProductPhoto w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e0de3-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="e0de3-130">W przypadku korzystania z dostawcy `BULK OPENROWSET` należy podać nazwę listy kolumn, nawet jeśli nie wstawiasz wartości do każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="e0de3-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="e0de3-131">Klucz podstawowy w tym przypadku jest definiowany jako kolumna tożsamości i może zostać pominięty z listy kolumn.</span><span class="sxs-lookup"><span data-stu-id="e0de3-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="e0de3-132">Należy pamiętać, że należy również podać nazwę korelacji na końcu instrukcji `OPENROWSET`, która w tym przypadku jest ThumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="e0de3-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="e0de3-133">Jest to skorelowane z kolumną w tabeli `ProductPhoto`, do której plik jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="e0de3-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
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
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="e0de3-134">Aktualizowanie danych przy użyciu polecenia UPDATE. PRAWEM</span><span class="sxs-lookup"><span data-stu-id="e0de3-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="e0de3-135">Instrukcja UPDATE języka Transact-SQL ma nową składnię zapisu do modyfikowania zawartości kolumn `varchar(max)`, `nvarchar(max)`lub `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="e0de3-136">Dzięki temu można wykonywać częściowe aktualizacje danych.</span><span class="sxs-lookup"><span data-stu-id="e0de3-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="e0de3-137">Aktualizacja. Składnia zapisu jest wyświetlana w skróconej formie:</span><span class="sxs-lookup"><span data-stu-id="e0de3-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="e0de3-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="e0de3-138">UPDATE</span></span>  
  
 <span data-ttu-id="e0de3-139">{ *\<obiektu >* }</span><span class="sxs-lookup"><span data-stu-id="e0de3-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="e0de3-140">SET</span><span class="sxs-lookup"><span data-stu-id="e0de3-140">SET</span></span>  
  
 <span data-ttu-id="e0de3-141">{ *column_name* = {. ZAPIS ( *wyrażenie* , @Offset, @Length)}</span><span class="sxs-lookup"><span data-stu-id="e0de3-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="e0de3-142">Metoda WRITE określa, że sekcja wartości *column_name* zostanie zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="e0de3-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="e0de3-143">Wyrażenie jest wartością, która zostanie skopiowana do *column_name*, `@Offset` jest punktem początkowym, w którym zostanie zapisany wyrażenie, a argument `@Length` jest długością sekcji w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="e0de3-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="e0de3-144">Jeśli użytkownik</span><span class="sxs-lookup"><span data-stu-id="e0de3-144">If</span></span>|<span data-ttu-id="e0de3-145">Następnie</span><span class="sxs-lookup"><span data-stu-id="e0de3-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="e0de3-146">Wyrażenie jest ustawione na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="e0de3-146">The expression is set to NULL</span></span>|<span data-ttu-id="e0de3-147">`@Length` jest ignorowana, a wartość w *column_name* zostanie obcięta w określonym `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="e0de3-148">`@Offset` ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="e0de3-148">`@Offset` is NULL</span></span>|<span data-ttu-id="e0de3-149">Operacja Update dołącza wyrażenie na końcu istniejącej wartości *column_name* i `@Length` jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="e0de3-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="e0de3-150">`@Offset` jest większa niż długość wartości column_name</span><span class="sxs-lookup"><span data-stu-id="e0de3-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="e0de3-151">SQL Server zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="e0de3-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="e0de3-152">`@Length` ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="e0de3-152">`@Length` is NULL</span></span>|<span data-ttu-id="e0de3-153">Operacja Update usuwa wszystkie dane z `@Offset` na końcu `column_name` wartości.</span><span class="sxs-lookup"><span data-stu-id="e0de3-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e0de3-154">Żadna `@Offset` ani `@Length` nie może być liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="e0de3-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0de3-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0de3-155">Example</span></span>  
 <span data-ttu-id="e0de3-156">Ten przykład języka Transact-SQL aktualizuje wartość częściową w DocumentSummary, a kolumna `nvarchar(max)` w tabeli dokumentów w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e0de3-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="e0de3-157">Słowo "Components" jest zastępowane słowem "Features", określając wyraz zamienny, początkową lokalizację (przesunięcie) wyrazu, który ma zostać zastąpiony w istniejących danych, oraz liczbę znaków, które mają zostać zastąpione (długość).</span><span class="sxs-lookup"><span data-stu-id="e0de3-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="e0de3-158">Przykład zawiera instrukcje SELECT przed i po instrukcji UPDATE, aby porównać wyniki.</span><span class="sxs-lookup"><span data-stu-id="e0de3-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="e0de3-159">Praca z typami dużej wartości w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0de3-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="e0de3-160">Do pracy z dużymi typami wartości w ADO.NET można określić duże typy wartości jako obiekty <xref:System.Data.SqlClient.SqlParameter> w <xref:System.Data.SqlClient.SqlDataReader>, aby zwrócić zestaw wyników lub użyć <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia `DataSet`/`DataTable`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="e0de3-161">Nie ma różnicy między sposobem pracy z dużym typem wartości i powiązanymi danymi o mniejszych wartości.</span><span class="sxs-lookup"><span data-stu-id="e0de3-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="e0de3-162">Pobieranie danych za pomocą GetSqlBytes</span><span class="sxs-lookup"><span data-stu-id="e0de3-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="e0de3-163">Za pomocą metody `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> można pobrać zawartość kolumny `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="e0de3-164">Poniższy fragment kodu zakłada, że obiekt <xref:System.Data.SqlClient.SqlCommand> o nazwie `cmd`, który wybiera `varbinary(max)` dane z tabeli i obiekt <xref:System.Data.SqlClient.SqlDataReader> o nazwie `reader`, który pobiera dane jako <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="e0de3-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="e0de3-165">Pobieranie danych za pomocą GetSqlChars</span><span class="sxs-lookup"><span data-stu-id="e0de3-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="e0de3-166">Metoda `GetSqlChars` <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości kolumny `varchar(max)` lub `nvarchar(max)`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="e0de3-167">Poniższy fragment kodu zakłada, że obiekt <xref:System.Data.SqlClient.SqlCommand> o nazwie `cmd`, który wybiera `nvarchar(max)` dane z tabeli i obiekt <xref:System.Data.SqlClient.SqlDataReader> o nazwie `reader`, który pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="e0de3-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="e0de3-168">Pobieranie danych za pomocą GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="e0de3-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="e0de3-169">Za pomocą metody `GetSqlBinary` <xref:System.Data.SqlClient.SqlDataReader> można pobrać zawartość kolumny `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="e0de3-170">Poniższy fragment kodu zakłada, że obiekt <xref:System.Data.SqlClient.SqlCommand> o nazwie `cmd`, który wybiera `varbinary(max)` dane z tabeli i obiekt <xref:System.Data.SqlClient.SqlDataReader> o nazwie `reader`, który pobiera dane jako strumień <xref:System.Data.SqlTypes.SqlBinary>.</span><span class="sxs-lookup"><span data-stu-id="e0de3-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="e0de3-171">Pobieranie danych przy użyciu GetBytes</span><span class="sxs-lookup"><span data-stu-id="e0de3-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="e0de3-172">Metoda `GetBytes` <xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z określonego przesunięcia kolumny do tablicy bajtów, rozpoczynając od określonego przesunięcia tablicy.</span><span class="sxs-lookup"><span data-stu-id="e0de3-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="e0de3-173">Poniższy fragment kodu zakłada, że obiekt <xref:System.Data.SqlClient.SqlDataReader> o nazwie `reader`, który pobiera bajty do tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="e0de3-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="e0de3-174">Należy pamiętać, że w przeciwieństwie do `GetSqlBytes`, `GetBytes` wymaga rozmiaru buforu tablicy.</span><span class="sxs-lookup"><span data-stu-id="e0de3-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="e0de3-175">Pobieranie danych za pomocą GetValue</span><span class="sxs-lookup"><span data-stu-id="e0de3-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="e0de3-176">Metoda `GetValue` <xref:System.Data.SqlClient.SqlDataReader> odczytuje wartość z przesunięcia określonego kolumny do tablicy.</span><span class="sxs-lookup"><span data-stu-id="e0de3-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="e0de3-177">Poniższy fragment kodu zakłada, że obiekt <xref:System.Data.SqlClient.SqlDataReader> o nazwie `reader`, który pobiera dane binarne z pierwszego przesunięcia kolumny, a następnie dane ciągu z drugiego przesunięcia kolumny.</span><span class="sxs-lookup"><span data-stu-id="e0de3-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="e0de3-178">Konwertowanie z dużych typów wartości na typy CLR</span><span class="sxs-lookup"><span data-stu-id="e0de3-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="e0de3-179">Można przekonwertować zawartość `varchar(max)` lub `nvarchar(max)` kolumny przy użyciu dowolnej metody konwersji ciągów, takiej jak `ToString`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="e0de3-180">Poniższy fragment kodu zakłada, że obiekt <xref:System.Data.SqlClient.SqlDataReader> o nazwie `reader`, który pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="e0de3-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="e0de3-181">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0de3-181">Example</span></span>  
 <span data-ttu-id="e0de3-182">Poniższy kod pobiera nazwę i obiekt `LargePhoto` z tabeli `ProductPhoto` w bazie danych `AdventureWorks` i zapisuje je w pliku.</span><span class="sxs-lookup"><span data-stu-id="e0de3-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="e0de3-183">Zestaw musi być skompilowany z odwołaniem do przestrzeni nazw <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="e0de3-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="e0de3-184">Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:System.Data.SqlClient.SqlDataReader> zwraca obiekt <xref:System.Data.SqlTypes.SqlBytes>, który uwidacznia Właściwość `Stream`.</span><span class="sxs-lookup"><span data-stu-id="e0de3-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="e0de3-185">Kod używa tego do utworzenia nowego obiektu `Bitmap`, a następnie zapisuje go w `ImageFormat`GIF.</span><span class="sxs-lookup"><span data-stu-id="e0de3-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="e0de3-186">Używanie parametrów typu dużej wartości</span><span class="sxs-lookup"><span data-stu-id="e0de3-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="e0de3-187">Typy dużych wartości mogą być używane w <xref:System.Data.SqlClient.SqlParameter> obiektów w taki sam sposób, jak w przypadku obiektów <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="e0de3-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="e0de3-188">Możesz pobrać duże typy wartości jako wartości <xref:System.Data.SqlClient.SqlParameter>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e0de3-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="e0de3-189">W kodzie założono, że w przykładowej bazie danych AdventureWorks istnieje następująca procedura składowana GetDocumentSummary.</span><span class="sxs-lookup"><span data-stu-id="e0de3-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="e0de3-190">Procedura składowana przyjmuje parametr wejściowy o nazwie @DocumentID i zwraca zawartość kolumny DocumentSummary w parametrze danych wyjściowych @DocumentSummary.</span><span class="sxs-lookup"><span data-stu-id="e0de3-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="e0de3-191">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0de3-191">Example</span></span>  
 <span data-ttu-id="e0de3-192">Kod ADO.NET tworzy obiekty <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> do wykonania procedury składowanej GetDocumentSummary i pobrania podsumowania dokumentu, który jest przechowywany jako typ dużej wartości.</span><span class="sxs-lookup"><span data-stu-id="e0de3-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="e0de3-193">Kod przekazuje wartość @DocumentID parametru wejściowego i wyświetla wyniki przekazane z powrotem @DocumentSummary w parametrze danych wyjściowych w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0de3-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e0de3-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0de3-194">See also</span></span>

- [<span data-ttu-id="e0de3-195">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="e0de3-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="e0de3-196">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="e0de3-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="e0de3-197">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0de3-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="e0de3-198">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0de3-198">ADO.NET Overview</span></span>](../ado-net-overview.md)
