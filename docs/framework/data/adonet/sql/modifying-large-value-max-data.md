---
title: "Modyfikowanie dużej wartości (wartość maksymalna) danych ADO.NET"
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
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 55403df391f6d7d44de46483d945ed32a694a63b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="d44b9-102">Modyfikowanie dużej wartości (wartość maksymalna) danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d44b9-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="d44b9-103">Typy danych dużego obiektu (LOB) to przekracza maksymalny rozmiar wiersza 8 kilobajtów (KB).</span><span class="sxs-lookup"><span data-stu-id="d44b9-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="d44b9-104">Program SQL Server stanowi `max` specyfikatora `varchar`, `nvarchar`, i `varbinary` typy danych umożliwiają przechowywanie wartości tak duże jak 2 ^ 32 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d44b9-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="d44b9-105">Kolumny tabeli i zmienne języka Transact-SQL może określać `varchar(max)`, `nvarchar(max)`, lub `varbinary(max)` typów danych.</span><span class="sxs-lookup"><span data-stu-id="d44b9-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="d44b9-106">W ADO.NET `max` typy danych mogą być pobierane przez `DataReader`, a także można określić jako wartości obu parametrów wejściowych i wyjściowych bez żadnej specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="d44b9-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="d44b9-107">Dla dużych `varchar` typy danych, dane można je pobrać i zaktualizować przyrostowo.</span><span class="sxs-lookup"><span data-stu-id="d44b9-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="d44b9-108">`max` Dla porównania jako zmienne języka Transact-SQL i łączenia można używać typów danych.</span><span class="sxs-lookup"><span data-stu-id="d44b9-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="d44b9-109">Ich można również w DISTINCT, ORDER BY, klauzul GROUP BY w instrukcji SELECT, a także w agregacji, sprzężeń i podzapytania.</span><span class="sxs-lookup"><span data-stu-id="d44b9-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="d44b9-110">Poniższa tabela zawiera linki do dokumentacji programu SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="d44b9-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d44b9-111">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="d44b9-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="d44b9-112">Używanie typów danych dużych wartości</span><span class="sxs-lookup"><span data-stu-id="d44b9-112">Using Large-Value Data Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="d44b9-113">Ograniczenia typu duża wartość</span><span class="sxs-lookup"><span data-stu-id="d44b9-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="d44b9-114">Następujące ograniczenia dotyczące `max` typy danych, które nie istnieją dla mniejszych typów danych:</span><span class="sxs-lookup"><span data-stu-id="d44b9-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
-   <span data-ttu-id="d44b9-115">A `sql_variant` nie może zawierać dużej `varchar` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="d44b9-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
-   <span data-ttu-id="d44b9-116">Duże `varchar` kolumny nie można określić jako kolumna klucza w indeksie.</span><span class="sxs-lookup"><span data-stu-id="d44b9-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="d44b9-117">Mogą w kolumnie uwzględnione w nieklastrowanym indeksie.</span><span class="sxs-lookup"><span data-stu-id="d44b9-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
-   <span data-ttu-id="d44b9-118">Duże `varchar` kolumn nie można używać jako kolumny klucza partycji.</span><span class="sxs-lookup"><span data-stu-id="d44b9-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="d44b9-119">Praca z typami duża wartość w języku Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d44b9-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="d44b9-120">Języka Transact-SQL `OPENROWSET` funkcja to jednorazowe metoda łączenia i uzyskiwania dostępu do danych zdalnych.</span><span class="sxs-lookup"><span data-stu-id="d44b9-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="d44b9-121">Zawiera wszystkie informacje o połączeniu niezbędnych do uzyskania dostępu zdalnego danych ze źródła danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="d44b9-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="d44b9-122">`OPENROWSET`może być przywoływany w klauzuli FROM zapytania tak, jakby była nazwą tabeli.</span><span class="sxs-lookup"><span data-stu-id="d44b9-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="d44b9-123">Jego mogą się też odwoływać jako do tabeli docelowej instrukcji INSERT, UPDATE, lub usuń instrukcji, zależnie od możliwości dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="d44b9-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="d44b9-124">`OPENROWSET` Funkcja zawiera `BULK` dostawca zestawów wierszy, dzięki czemu można odczytać danych bezpośrednio z pliku bez ładowania danych do tabeli docelowej.</span><span class="sxs-lookup"><span data-stu-id="d44b9-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="d44b9-125">Pozwala na użycie `OPENROWSET` w prostej instrukcji INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="d44b9-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="d44b9-126">`OPENROWSET``BULK` Argumentów opcji zapewniają znaczny kontrolę nad gdzie rozpoczynać i kończyć odczytywanie danych, sposób postępowania z błędami i interpretacji danych.</span><span class="sxs-lookup"><span data-stu-id="d44b9-126">The `OPENROWSET``BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="d44b9-127">Na przykład określić, że plik danych go odczytywać jako pojedynczy wiersz, pojedynczej kolumny zestawu wierszy typu `varbinary`, `varchar`, lub `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="d44b9-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="d44b9-128">Pełną składnię i opcje zobacz dokumentację SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="d44b9-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d44b9-129">Poniższy przykład wstawia zdjęcie do tabeli ProductPhoto w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d44b9-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="d44b9-130">Korzystając z `BULK``OPENROWSET` dostawcy, należy podać nazwana lista kolumn, nawet jeśli wartości nie są wstawianie do każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="d44b9-130">When using the `BULK``OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="d44b9-131">W takim przypadku klucz podstawowy jest zdefiniowany jako kolumny tożsamości i można pominąć na liście kolumn.</span><span class="sxs-lookup"><span data-stu-id="d44b9-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="d44b9-132">Należy pamiętać, że nazwa korelacji na koniec należy również podać `OPENROWSET` instrukcji w tym przypadku jest ThumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="d44b9-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="d44b9-133">To są powiązane z kolumną w `ProductPhoto` tabeli, w której plik jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="d44b9-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="d44b9-134">Aktualizowanie danych za pomocą aktualizacji. ZAPISU</span><span class="sxs-lookup"><span data-stu-id="d44b9-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="d44b9-135">Instrukcja Transact-SQL UPDATE ma nowej składni zapisu do modyfikowania zawartości `varchar(max)`, `nvarchar(max)`, lub `varbinary(max)` kolumn.</span><span class="sxs-lookup"><span data-stu-id="d44b9-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="d44b9-136">Dzięki temu można wykonywać częściowej aktualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="d44b9-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="d44b9-137">Aktualizacja. Składnia jest tutaj wyświetlane w formie skróconej zapisu:</span><span class="sxs-lookup"><span data-stu-id="d44b9-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="d44b9-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="d44b9-138">UPDATE</span></span>  
  
 <span data-ttu-id="d44b9-139">{  *\<obiektu >* }</span><span class="sxs-lookup"><span data-stu-id="d44b9-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="d44b9-140">ZESTAW</span><span class="sxs-lookup"><span data-stu-id="d44b9-140">SET</span></span>  
  
 <span data-ttu-id="d44b9-141">{ *column_name* = {. ZAPIS ( *wyrażenie* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="d44b9-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="d44b9-142">Metoda WRITE Określa, że sekcja wartości *column_name* zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="d44b9-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="d44b9-143">Wyrażenie jest wartością, której zostaną skopiowane do *column_name*, `@Offset` jest punkt początkowy, w którym zostanie zapisany wyrażenie, i `@Length` argument jest długość sekcji w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="d44b9-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="d44b9-144">IF</span><span class="sxs-lookup"><span data-stu-id="d44b9-144">If</span></span>|<span data-ttu-id="d44b9-145">Następnie</span><span class="sxs-lookup"><span data-stu-id="d44b9-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="d44b9-146">Wyrażenie ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="d44b9-146">The expression is set to NULL</span></span>|<span data-ttu-id="d44b9-147">`@Length`jest ignorowana, a wartością w *column_name* został obcięty w określonym `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="d44b9-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="d44b9-148">`@Offset`ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="d44b9-148">`@Offset` is NULL</span></span>|<span data-ttu-id="d44b9-149">Operacja aktualizacji dołącza wyrażenia na końcu istniejące *column_name* wartość i `@Length` jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d44b9-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="d44b9-150">`@Offset`jest większa niż długość wartości nazwa_kolumny</span><span class="sxs-lookup"><span data-stu-id="d44b9-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="d44b9-151">Program SQL Server zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="d44b9-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="d44b9-152">`@Length`ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="d44b9-152">`@Length` is NULL</span></span>|<span data-ttu-id="d44b9-153">Operacja aktualizacji powoduje usunięcie wszystkich danych z `@Offset` na końcu `column_name` wartość.</span><span class="sxs-lookup"><span data-stu-id="d44b9-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d44b9-154">Ani `@Offset` ani `@Length` może być liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="d44b9-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d44b9-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="d44b9-155">Example</span></span>  
 <span data-ttu-id="d44b9-156">W tym przykładzie języka Transact-SQL aktualizuje wartości częściowej w DocumentSummary, `nvarchar(max)` kolumny w tabeli dokumentu w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d44b9-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="d44b9-157">Wyraz "składniki" zastępuje według słów "funkcji" określenie słowa zastępczego położenie początku (przesunięcie) słowa, które mają zostać zastąpione w istniejących danych i liczbę znaków do zastąpienia (długości).</span><span class="sxs-lookup"><span data-stu-id="d44b9-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="d44b9-158">Przykład obejmuje instrukcji "SELECT" przed i po instrukcji UPDATE do porównywania wyników.</span><span class="sxs-lookup"><span data-stu-id="d44b9-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="d44b9-159">Praca z typami duża wartość w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d44b9-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="d44b9-160">Możesz pracować z typami duża wartość w ADO.NET, określając typy duża wartość jako <xref:System.Data.SqlClient.SqlParameter> obiekty w <xref:System.Data.SqlClient.SqlDataReader> do zwrócenia wyniku ustawiona, lub za pomocą <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia `DataSet` / `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="d44b9-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="d44b9-161">Nie ma żadnej różnicy między sposób pracy z typu duża wartość a jego typu danych powiązane, mniejszą wartość.</span><span class="sxs-lookup"><span data-stu-id="d44b9-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="d44b9-162">Używanie GetSqlBytes do pobierania danych</span><span class="sxs-lookup"><span data-stu-id="d44b9-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="d44b9-163">`GetSqlBytes` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny.</span><span class="sxs-lookup"><span data-stu-id="d44b9-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="d44b9-164">Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `varbinary(max)` danych z tabeli a <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="d44b9-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="d44b9-165">Używanie GetSqlChars do pobierania danych</span><span class="sxs-lookup"><span data-stu-id="d44b9-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="d44b9-166">`GetSqlChars` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varchar(max)` lub `nvarchar(max)` kolumny.</span><span class="sxs-lookup"><span data-stu-id="d44b9-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="d44b9-167">Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `nvarchar(max)` danych z tabeli a <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="d44b9-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="d44b9-168">Używanie GetSqlBinary do pobierania danych</span><span class="sxs-lookup"><span data-stu-id="d44b9-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="d44b9-169">`GetSqlBinary` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny.</span><span class="sxs-lookup"><span data-stu-id="d44b9-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="d44b9-170">Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `varbinary(max)` danych z tabeli a <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBinary> strumienia.</span><span class="sxs-lookup"><span data-stu-id="d44b9-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="d44b9-171">Używanie GetBytes do pobierania danych</span><span class="sxs-lookup"><span data-stu-id="d44b9-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="d44b9-172">`GetBytes` Metody <xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z przesunięciem określonej kolumny do tablicy typu byte, rozpoczynając od przesunięcia określonej tablicy.</span><span class="sxs-lookup"><span data-stu-id="d44b9-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="d44b9-173">Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` który pobiera bajtów do tablicy typu byte.</span><span class="sxs-lookup"><span data-stu-id="d44b9-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="d44b9-174">Należy zauważyć, że w przeciwieństwie do `GetSqlBytes`, `GetBytes` wymagany rozmiar buforu tablicy.</span><span class="sxs-lookup"><span data-stu-id="d44b9-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="d44b9-175">Używanie GetValue do pobierania danych</span><span class="sxs-lookup"><span data-stu-id="d44b9-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="d44b9-176">`GetValue` Metody <xref:System.Data.SqlClient.SqlDataReader> odczytuje wartość od przesunięcia określona kolumna w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d44b9-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="d44b9-177">Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` przesunięcie pobiera dane binarne z pierwszej kolumny, a następnie dane z drugiego przesunięcia kolumny ciągu.</span><span class="sxs-lookup"><span data-stu-id="d44b9-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="d44b9-178">Konwersja z typu duża wartość do typów CLR</span><span class="sxs-lookup"><span data-stu-id="d44b9-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="d44b9-179">Można konwertować zawartości `varchar(max)` lub `nvarchar(max)` kolumny przy użyciu dowolnej z metod konwersji ciągów, takich jak `ToString`.</span><span class="sxs-lookup"><span data-stu-id="d44b9-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="d44b9-180">Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="d44b9-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="d44b9-181">Przykład</span><span class="sxs-lookup"><span data-stu-id="d44b9-181">Example</span></span>  
 <span data-ttu-id="d44b9-182">Poniższy kod pobiera nazwę i `LargePhoto` obiekt z `ProductPhoto` w tabeli `AdventureWorks` bazy danych i zapisuje je w pliku.</span><span class="sxs-lookup"><span data-stu-id="d44b9-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="d44b9-183">Musi być kompilowana przy użyciu odwołania do zestawu <xref:System.Drawing> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d44b9-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="d44b9-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.SqlTypes.SqlBytes> obiekt ujawniający `Stream` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d44b9-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="d44b9-185">W kodzie użyto, to aby utworzyć nową `Bitmap` obiektu i jest zapisywany w formacie Gif `ImageFormat`.</span><span class="sxs-lookup"><span data-stu-id="d44b9-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="d44b9-186">Za pomocą parametrów typu duża wartość</span><span class="sxs-lookup"><span data-stu-id="d44b9-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="d44b9-187">Duża wartość mogą być używane w <xref:System.Data.SqlClient.SqlParameter> obiektów taki sam sposób, możesz użyć wartości mniejsze typy w <xref:System.Data.SqlClient.SqlParameter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d44b9-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="d44b9-188">Można pobrać typu duża wartość jako <xref:System.Data.SqlClient.SqlParameter> wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d44b9-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="d44b9-189">Kod przyjęto założenie, że poniższej procedury przechowywane GetDocumentSummary istnieje w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d44b9-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="d44b9-190">Procedura składowana przyjmuje parametr wejściowy o nazwie @DocumentID i zwraca zawartość w kolumnie DocumentSummary @DocumentSummary parametru wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d44b9-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```  
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
  
### <a name="example"></a><span data-ttu-id="d44b9-191">Przykład</span><span class="sxs-lookup"><span data-stu-id="d44b9-191">Example</span></span>  
 <span data-ttu-id="d44b9-192">Tworzy kod ADO.NET <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiekty do wykonywania procedury przechowywane GetDocumentSummary i pobierania dokumentu podsumowania, które są przechowywane jako typu duża wartość.</span><span class="sxs-lookup"><span data-stu-id="d44b9-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="d44b9-193">Kod przekazuje wartość @DocumentID danych wejściowych parametru i wyświetla wyniki przekazany z powrotem do @DocumentSummary dane wyjściowe parametru w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d44b9-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d44b9-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d44b9-194">See Also</span></span>  
 [<span data-ttu-id="d44b9-195">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="d44b9-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="d44b9-196">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="d44b9-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="d44b9-197">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d44b9-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="d44b9-198">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="d44b9-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
