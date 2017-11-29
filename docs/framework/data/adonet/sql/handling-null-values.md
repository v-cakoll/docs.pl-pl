---
title: "Obsługa wartości Null"
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
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f29cbd51c036ecc15306f67fdd32dee6a4f1b68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-null-values"></a><span data-ttu-id="2c364-102">Obsługa wartości Null</span><span class="sxs-lookup"><span data-stu-id="2c364-102">Handling Null Values</span></span>
<span data-ttu-id="2c364-103">Wartość null w relacyjnej bazie danych jest używany, gdy wartość w kolumnie jest nieznany lub nieobecny.</span><span class="sxs-lookup"><span data-stu-id="2c364-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="2c364-104">Wartość null nie jest ciągiem pustym (dla typów danych daty/godziny lub znakiem) ani wartość zero (dla liczbowych typów danych).</span><span class="sxs-lookup"><span data-stu-id="2c364-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="2c364-105">Ze specyfikacją ANSI SQL-92 się informacja o wartości null musi być taka sama dla wszystkich typów danych tak, aby spójną wszystkie wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="2c364-106"><xref:System.Data.SqlTypes> Przestrzeń nazw zawiera wartości null semantyki zaimplementowanie <xref:System.Data.SqlTypes.INullable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2c364-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="2c364-107">Typy wszystkich danych w <xref:System.Data.SqlTypes> ma własną `IsNull` właściwości i `Null` wartość przypisana do wystąpienia tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="2c364-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c364-108">.NET Framework w wersji 2.0 wprowadzono obsługę typy dopuszczające wartości null, które umożliwiają deweloperom rozszerzenie typu wartości reprezentujący wszystkie wartości typu bazowego.</span><span class="sxs-lookup"><span data-stu-id="2c364-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="2c364-109">Te typy dopuszczające wartości zerowe CLR reprezentuje wystąpienie <xref:System.Nullable> struktury.</span><span class="sxs-lookup"><span data-stu-id="2c364-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="2c364-110">Ta funkcja jest szczególnie przydatne, gdy wartość typów opakowany i rozpakowany zapewniające rozszerzoną zgodność z typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="2c364-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="2c364-111">Typy dopuszczające wartości zerowe CLR nie są przeznaczone do magazynu bazy danych zawiera wartości null, ponieważ null ANSI SQL nie działają tak samo jak `null` odwołania (lub `Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2c364-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="2c364-112">Praca z wartościami null ANSI SQL bazy danych, użyj <xref:System.Data.SqlTypes> wartości null zamiast <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="2c364-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="2c364-113">Aby uzyskać więcej informacji na temat pracy z CLR Zobacz typy dopuszczające wartości zerowe w języku Visual Basic [typy dopuszczające wartości zerowe wartości](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)i C# zobacz [przy użyciu typów dopuszczających wartości zerowe](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c364-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Using Nullable Types](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="2c364-114">Wartości null i przechowywanymi na trzy logiczne</span><span class="sxs-lookup"><span data-stu-id="2c364-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="2c364-115">Stosowanie wartości null w definicjach kolumn wprowadza przechowywanymi w trzech logiki do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c364-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="2c364-116">Porównanie można ocenić do jednego z trzech warunków:</span><span class="sxs-lookup"><span data-stu-id="2c364-116">A comparison can evaluate to one of three conditions:</span></span>  
  
-   <span data-ttu-id="2c364-117">Wartość true</span><span class="sxs-lookup"><span data-stu-id="2c364-117">True</span></span>  
  
-   <span data-ttu-id="2c364-118">False</span><span class="sxs-lookup"><span data-stu-id="2c364-118">False</span></span>  
  
-   <span data-ttu-id="2c364-119">Nieznany</span><span class="sxs-lookup"><span data-stu-id="2c364-119">Unknown</span></span>  
  
 <span data-ttu-id="2c364-120">Ponieważ wartość null jest traktowana jako Nieznany, dwie wartości null w porównaniu do siebie nie są traktowane jako równe.</span><span class="sxs-lookup"><span data-stu-id="2c364-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="2c364-121">W wyrażeniach przy użyciu operatorów arytmetycznych, jeśli dowolny z argumentów jest wartość null, wynik ma wartość null w również.</span><span class="sxs-lookup"><span data-stu-id="2c364-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="2c364-122">Wartości null i SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="2c364-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="2c364-123">Porównanie między żadnego <xref:System.Data.SqlTypes> zwróci <xref:System.Data.SqlTypes.SqlBoolean>.</span><span class="sxs-lookup"><span data-stu-id="2c364-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="2c364-124">`IsNull` Funkcja dla każdego `SqlType` zwraca <xref:System.Data.SqlTypes.SqlBoolean> i może służyć do sprawdzenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="2c364-125">Prawdy następujące tabele Pokaż jak AND, OR i nie operatory funkcji obecności wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="2c364-126">(T = true, F = false, U = nieznany lub wartość null.)</span><span class="sxs-lookup"><span data-stu-id="2c364-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="2c364-127">![Tabela prawdy](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="2c364-127">![Truth Table](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansinulls-option"></a><span data-ttu-id="2c364-128">Opis opcji ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="2c364-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="2c364-129"><xref:System.Data.SqlTypes>udostępnia tej samej semantyki jako, gdy opcja ANSI_NULLS jest ustawiona na w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c364-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="2c364-130">Wszystkie operatory arytmetyczne (+, -, *, /, %), operatory bitowe (~ &, &#124;), a większość funkcji zwracać wartość null, jeśli dowolny z argumentów lub argumentów jest pusta, z wyjątkiem właściwości `IsNull`.</span><span class="sxs-lookup"><span data-stu-id="2c364-130">All arithmetic operators (+, -, *, /, %), bitwise operators (~, &, &#124;), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="2c364-131">Nie obsługuje standardu ANSI SQL-92 *columnName* = NULL w klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="2c364-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="2c364-132">W programie SQL Server opcji ANSI_NULLS steruje dopuszczania wartości null zarówno domyślnej bazy danych i oceny porównania z wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="2c364-133">Jeśli ANSI_NULLS jest włączona (ustawienie domyślne), operatora IS NULL należy używać w wyrażeniach podczas testowania wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="2c364-134">Na przykład poniższe porównanie zawsze daje nieznany, gdy ANSI_NULLS znajduje się na:</span><span class="sxs-lookup"><span data-stu-id="2c364-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```  
colname > NULL  
```  
  
 <span data-ttu-id="2c364-135">Porównanie ze zmienną również zawierających wartości null daje nieznany:</span><span class="sxs-lookup"><span data-stu-id="2c364-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```  
colname > @MyVariable  
```  
  
 <span data-ttu-id="2c364-136">Próba na wartość null, należy użyć predykatu IS NULL i IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="2c364-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="2c364-137">To zwiększenia złożoności klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="2c364-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="2c364-138">Na przykład TerritoryID kolumny w tabeli Nabywca AdventureWorks dozwolone wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="2c364-139">W przypadku instrukcji SELECT do sprawdzenia wartości null, oprócz innych osób, musi on zawierać predykat IS NULL:</span><span class="sxs-lookup"><span data-stu-id="2c364-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="2c364-140">Jeśli ustawisz ANSI_NULLS off w programie SQL Server, można utworzyć wyrażenia używające operatora równości do porównania wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="2c364-141">Nie można jednak zapobiec różnych połączeń z ustawień wartości null dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="2c364-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="2c364-142">Aby przetestować wartości null zawsze działa niezależnie od ustawienia ANSI_NULLS połączenia za pomocą IS NULL.</span><span class="sxs-lookup"><span data-stu-id="2c364-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="2c364-143">Ustawienie ANSI_NULLS wyłączanie nie jest obsługiwany w `DataSet`, który jest zawsze zgodny standardu ANSI SQL-92 dla Obsługa wartości zerowych w <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="2c364-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="2c364-144">Przypisanie wartości Null</span><span class="sxs-lookup"><span data-stu-id="2c364-144">Assigning Null Values</span></span>  
 <span data-ttu-id="2c364-145">Wartości null są specjalne, a ich semantyki magazynu i przypisywania różnią się i systemami magazynu innego typu.</span><span class="sxs-lookup"><span data-stu-id="2c364-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="2c364-146">A `Dataset` jest przeznaczony do użycia z innego typu i systemów pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="2c364-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="2c364-147">W tej sekcji opisano null semantyki przypisywania wartości null do <xref:System.Data.DataColumn> w <xref:System.Data.DataRow> we wszystkich systemach innego typu.</span><span class="sxs-lookup"><span data-stu-id="2c364-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="2c364-148">To przypisanie jest nieprawidłowa dla `DataColumn` dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="2c364-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="2c364-149">Jeśli typ implementuje `INullable`, `DBNull.Value` jest przekształcić na odpowiednie silnie typizowaną wartość Null.</span><span class="sxs-lookup"><span data-stu-id="2c364-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="2c364-150">Wszystkie <xref:System.Data.SqlTypes> typy danych implementuje `INullable`.</span><span class="sxs-lookup"><span data-stu-id="2c364-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="2c364-151">Przypisanie silnie typizowaną wartość null, mogą być konwertowane na typ danych kolumny przy użyciu operatorów niejawne rzutowanie, należy przejść przez.</span><span class="sxs-lookup"><span data-stu-id="2c364-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="2c364-152">W przeciwnym razie Nieprawidłowe rzutowanie jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2c364-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="2c364-153">Jeśli wartość "null" jest dozwoloną wartością dla danego `DataColumn` typ danych, jest on przekształcić na odpowiedni `DbNull.Value` lub `Null` skojarzone z `INullable` typu (`SqlType.Null`)</span><span class="sxs-lookup"><span data-stu-id="2c364-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="2c364-154">Dla kolumny UDT wartości null są zawsze zapisywane na podstawie typu skojarzonego z `DataColumn`.</span><span class="sxs-lookup"><span data-stu-id="2c364-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="2c364-155">Rozważmy przypadek UDT skojarzone z `DataColumn` nie zawiera implementacji `INullable` podczas jego klasa podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2c364-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="2c364-156">W tym przypadku jeśli przypisany jest skojarzony z klasy pochodnej silnie typizowaną wartość null, jest przechowywany jako bez typu `DbNull.Value`, ponieważ Magazyn wartość null jest zawsze zgodny z typem danych DataColumn.</span><span class="sxs-lookup"><span data-stu-id="2c364-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c364-157">`Nullable<T>` Lub <xref:System.Nullable> struktury nie jest obecnie obsługiwany w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="2c364-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="2c364-158">Wiele przypisania kolumnie (wiersz)</span><span class="sxs-lookup"><span data-stu-id="2c364-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="2c364-159">`DataTable.Add`, `DataTable.LoadDataRow`, lub innych interfejsów API, które akceptują <xref:System.Data.DataRow.ItemArray%2A> który pobiera zamapowana na wiersz, Mapa "null", wartość domyślna elementu DataColumn.</span><span class="sxs-lookup"><span data-stu-id="2c364-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="2c364-160">Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego odpowiednik jednoznacznie regułom opisanych powyżej są stosowane.</span><span class="sxs-lookup"><span data-stu-id="2c364-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="2c364-161">Ponadto, obowiązują następujące reguły dla wystąpienia `DataRow.["columnName"]` null przypisania:</span><span class="sxs-lookup"><span data-stu-id="2c364-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1.  <span data-ttu-id="2c364-162">Wartość domyślna *domyślne* wartość jest `DbNull.Value` wszystkie z wyjątkiem jednoznacznie kolumny wartości null, gdzie jest silnie typizowanej wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2.  <span data-ttu-id="2c364-163">Wartości null nie są zapisywane podczas serializacji, aby pliki XML (jak "xsi: nil").</span><span class="sxs-lookup"><span data-stu-id="2c364-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3.  <span data-ttu-id="2c364-164">Wszystkich wartości innych niż null, w tym ustawienia domyślne, są zawsze zapisywane podczas serializowania do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="2c364-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="2c364-165">To w odróżnieniu od semantyki XSD/XML, gdzie wartość null (xsi: nil) jest jawne, a wartość domyślna to niejawne (Jeśli nie znajduje się w pliku XML, parserze można pobrać go ze schematu XSD skojarzone).</span><span class="sxs-lookup"><span data-stu-id="2c364-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="2c364-166">Dotyczy to także przeciwieństwem `DataTable`: wartość null jest niejawnie i wartością domyślną jest jawne.</span><span class="sxs-lookup"><span data-stu-id="2c364-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4.  <span data-ttu-id="2c364-167">Wszystkie brakujące wartości kolumny dla wierszy odczytywać dane wejściowe XML są przypisane wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="2c364-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="2c364-168">Wiersze utworzone za pomocą <xref:System.Data.DataTable.NewRow%2A> lub podobnych metod są przypisane DataColumn wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2c364-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5.  <span data-ttu-id="2c364-169"><xref:System.Data.DataRow.IsNull%2A> Metoda zwraca `true` dla obu `DbNull.Value` i `INullable.Null`.</span><span class="sxs-lookup"><span data-stu-id="2c364-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="2c364-170">Przypisanie wartości Null</span><span class="sxs-lookup"><span data-stu-id="2c364-170">Assigning Null Values</span></span>  
 <span data-ttu-id="2c364-171">Wartością domyślną dla każdego <xref:System.Data.SqlTypes> wystąpienie ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2c364-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="2c364-172">Wartość null w <xref:System.Data.SqlTypes> są specyficzne dla danego typu i nie może być reprezentowany przez pojedynczą wartość, takich jak `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="2c364-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="2c364-173">Użyj `IsNull` właściwość do sprawdzenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="2c364-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="2c364-174">Można przypisać wartości null do <xref:System.Data.DataColumn> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2c364-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="2c364-175">Można bezpośrednio przypisać wartości null do `SqlTypes` zmienne bez wyzwalania Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2c364-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c364-176">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c364-176">Example</span></span>  
 <span data-ttu-id="2c364-177">Poniższy przykład kodu tworzy <xref:System.Data.DataTable> z dwiema kolumnami zdefiniowany jako <xref:System.Data.SqlTypes.SqlInt32> i <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="2c364-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="2c364-178">Ten kod dodaje jeden wiersz znane wartości, jeden wiersz null wartości, a następnie wykonuje iterację <xref:System.Data.DataTable>, przypisywanie wartości do zmiennych i wyświetlanie danych wyjściowych w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2c364-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="2c364-179">W tym przykładzie wyświetlono następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2c364-179">This example displays the following results:</span></span>  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="2c364-180">Porównanie wartości Null z właściwości SqlTypes i typów CLR</span><span class="sxs-lookup"><span data-stu-id="2c364-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="2c364-181">Porównując wartości null, ważne jest, aby zrozumieć różnicę między sposób `Equals` metody oblicza wartości null w <xref:System.Data.SqlTypes> porównaniu sposób działa z typami CLR.</span><span class="sxs-lookup"><span data-stu-id="2c364-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="2c364-182">Wszystkie <xref:System.Data.SqlTypes> `Equals` metody korzystają bezpośrednio z semantyki bazy danych do obliczenia wartości null: w przypadku jednego lub obu wartości null, porównanie daje wartość null.</span><span class="sxs-lookup"><span data-stu-id="2c364-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="2c364-183">Z drugiej strony, przy użyciu środowiska CLR `Equals` metody na dwóch <xref:System.Data.SqlTypes> umożliwia uzyskanie wartość true, jeśli oba mają wartość null.</span><span class="sxs-lookup"><span data-stu-id="2c364-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="2c364-184">Ta właściwość odzwierciedla różnicę między za pomocą metody wystąpienia takich jak środowisko CLR `String.Equals` — metoda i przy użyciu metody statycznej/udostępnione `SqlString.Equals`.</span><span class="sxs-lookup"><span data-stu-id="2c364-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="2c364-185">W poniższym przykładzie pokazano różnica w wynikach między `SqlString.Equals` — metoda i `String.Equals` metody w przypadku każdego przekazania pary wartości null, a następnie dwa puste ciągi.</span><span class="sxs-lookup"><span data-stu-id="2c364-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="2c364-186">Kod tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2c364-186">The code produces the following output:</span></span>  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a><span data-ttu-id="2c364-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c364-187">See Also</span></span>  
 [<span data-ttu-id="2c364-188">Danych programu SQL Server typy i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2c364-188">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="2c364-189">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="2c364-189">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
