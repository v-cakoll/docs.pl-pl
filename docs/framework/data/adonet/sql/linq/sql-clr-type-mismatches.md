---
title: "Niezgodność typu SQL CLR"
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
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 20031092f5109fef1bf7167eccab949e2e7c5b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="57aa6-102">Niezgodność typu SQL CLR</span><span class="sxs-lookup"><span data-stu-id="57aa6-102">SQL-CLR Type Mismatches</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="57aa6-103">automatyzuje wiele tłumaczenie między model obiektów i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57aa6-103"> automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="57aa6-104">Niemniej jednak niektórych sytuacjach uniemożliwiają dokładny tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="57aa6-105">Te klucza niedopasowania popularne typy środowiska uruchomieniowego (języka wspólnego CLR) języka i typów bazy danych programu SQL Server podsumowano w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="57aa6-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="57aa6-106">Można znaleźć więcej informacji dotyczących mapowania określonego typu i funkcja translacji na [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) i [typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="57aa6-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="57aa6-107">Typy danych</span><span class="sxs-lookup"><span data-stu-id="57aa6-107">Data Types</span></span>  
 <span data-ttu-id="57aa6-108">Translacja między CLR i SQL Server występuje, gdy zapytanie jest wysyłane do bazy danych, a wyniki są odsyłane do modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="57aa6-109">Na przykład następujące zapytanie języka Transact-SQL wymaga dwóch konwersji wartości:</span><span class="sxs-lookup"><span data-stu-id="57aa6-109">For example, the following Transact-SQL query requires two value conversions:</span></span>  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 <span data-ttu-id="57aa6-110">Aby można było wykonać zapytanie w programie SQL Server, należy określić wartość parametru języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="57aa6-111">W tym przykładzie `id` wartość parametru musi najpierw przeliczane z CLR <xref:System.Int32?displayProperty=nameWithType> typu do programu SQL Server `INT` wpisz, aby bazy danych można zrozumieć, co to jest wartość.</span><span class="sxs-lookup"><span data-stu-id="57aa6-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="57aa6-112">Następnie można pobrać wyników, programu SQL Server `DateOfBirth` kolumny musi być przekonwertowana z programu SQL Server `DATETIME` typu CLR <xref:System.DateTime?displayProperty=nameWithType> typ do użycia w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="57aa6-113">W tym przykładzie typami w modelu obiektu CLR i bazy danych programu SQL Server ma mapowania fizycznych.</span><span class="sxs-lookup"><span data-stu-id="57aa6-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="57aa6-114">Jednak nie zawsze jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="57aa6-114">But, this is not always the case.</span></span>  
  
### <a name="missing-counterparts"></a><span data-ttu-id="57aa6-115">Brak odpowiedniki</span><span class="sxs-lookup"><span data-stu-id="57aa6-115">Missing Counterparts</span></span>  
 <span data-ttu-id="57aa6-116">Następujące typy nie mają uzasadnione odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="57aa6-116">The following types do not have reasonable counterparts.</span></span>  
  
-   <span data-ttu-id="57aa6-117">W środowisku CLR ma niezgodny <xref:System> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="57aa6-117">Mismatches in the CLR <xref:System> namespace:</span></span>  
  
    -   <span data-ttu-id="57aa6-118">**Podpisane liczby całkowite**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-118">**Unsigned integers**.</span></span> <span data-ttu-id="57aa6-119">Zazwyczaj są mapowane te typy ich podpisem odpowiedniki większy rozmiar w celu uniknięcia przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="57aa6-120">Literały można przekonwertować na podpisem liczbowe o tej samej lub mniejszy rozmiar, na podstawie wartości.</span><span class="sxs-lookup"><span data-stu-id="57aa6-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>  
  
    -   <span data-ttu-id="57aa6-121">**Wartość logiczna**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-121">**Boolean**.</span></span> <span data-ttu-id="57aa6-122">Mogą być mapowane te typy bitowych lub większą liczbą lub ciągiem.</span><span class="sxs-lookup"><span data-stu-id="57aa6-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="57aa6-123">Literał mogą być mapowane na wyrażenie obliczane do tej samej wartości (na przykład `1=1` w języku SQL dla `True` w ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="57aa6-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>  
  
    -   <span data-ttu-id="57aa6-124">**Wartość TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-124">**TimeSpan**.</span></span> <span data-ttu-id="57aa6-125">Ten typ przedstawia różnicę między dwiema `DateTime` wartości i nie odpowiada `timestamp` programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57aa6-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="57aa6-126">Środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> może również mapować do programu SQL Server `TIME` typu w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="57aa6-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="57aa6-127">SQL Server `TIME` typu była przeznaczona tylko do reprezentowania wartości dodatnie mniej niż 24 godziny.</span><span class="sxs-lookup"><span data-stu-id="57aa6-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="57aa6-128">Środowisko CLR <xref:System.TimeSpan> ma o wiele większa zakres.</span><span class="sxs-lookup"><span data-stu-id="57aa6-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57aa6-129">Specyficzne dla programu SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] typy w <xref:System.Data.SqlTypes> nie są uwzględnione w tym porównania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-129">SQL Server-specific [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>  
  
-   <span data-ttu-id="57aa6-130">Niezgodność w programie SQL Server:</span><span class="sxs-lookup"><span data-stu-id="57aa6-130">Mismatches in SQL Server:</span></span>  
  
    -   <span data-ttu-id="57aa6-131">**Stałej długości typów znaków**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-131">**Fixed length character types**.</span></span> <span data-ttu-id="57aa6-132">Transact-SQL rozróżnia kategorii Unicode i z systemem innym niż Unicode i ma trzy różne typy w każdej kategorii: stałej długości `nchar` / `char`, o zmiennej długości `nvarchar` / `varchar`, i o większym rozmiarze `ntext` / `text`.</span><span class="sxs-lookup"><span data-stu-id="57aa6-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="57aa6-133">O stałej długości typów znaków mogą zostać zamapowane do środowiska CLR <xref:System.Char?displayProperty=nameWithType> znaków typu pobierania, ale ich nie naprawdę odpowiadają tego samego typu konwersje i zachowania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>  
  
    -   <span data-ttu-id="57aa6-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-134">**Bit**.</span></span> <span data-ttu-id="57aa6-135">Mimo że `bit` domena ma taką samą liczbę wartości jako `Nullable<Boolean>`, są różnych typów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="57aa6-136">`Bit`pobiera wartości `1` i `0` zamiast `true` / `false`i nie można użyć jako równoważne wyrażeń logicznych.</span><span class="sxs-lookup"><span data-stu-id="57aa6-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>  
  
    -   <span data-ttu-id="57aa6-137">**Sygnatura czasowa**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-137">**Timestamp**.</span></span> <span data-ttu-id="57aa6-138">W przeciwieństwie do środowiska CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ, programu SQL Server `TIMESTAMP` typu reprezentuje 8-bajtowa liczba wygenerowanych przez bazę danych, która jest unikatowa dla każdej aktualizacji i nie jest oparty na różnicy między <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="57aa6-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>  
  
    -   <span data-ttu-id="57aa6-139">**Oszczędność pieniędzy** i **SmallMoney**.</span><span class="sxs-lookup"><span data-stu-id="57aa6-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="57aa6-140">Te typy mogą być mapowane na <xref:System.Decimal> , ale są zasadniczo różne typy i są traktowane jako takie funkcje oparte na serwerze i konwersji.</span><span class="sxs-lookup"><span data-stu-id="57aa6-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>  
  
### <a name="multiple-mappings"></a><span data-ttu-id="57aa6-141">Wiele mapowań</span><span class="sxs-lookup"><span data-stu-id="57aa6-141">Multiple Mappings</span></span>  
 <span data-ttu-id="57aa6-142">Istnieje wiele typów danych programu SQL Server, które można mapować na co najmniej jeden typ danych CLR.</span><span class="sxs-lookup"><span data-stu-id="57aa6-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="57aa6-143">Istnieje wiele typów CLR, które można mapować na co najmniej jeden typ SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57aa6-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="57aa6-144">Mimo że mapowanie może być obsługiwana w składniku LINQ to SQL, oznacza to, że dwa typy mapowane między CLR i SQL Server nie są doskonałe dopasowanie dokładność, zakresu i semantyki.</span><span class="sxs-lookup"><span data-stu-id="57aa6-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="57aa6-145">Niektóre mapowania mogą obejmować różnice w całości lub części tych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="57aa6-146">Dla różnych możliwości mapowania na można znaleźć szczegółowe informacje o tych potencjalne różnice [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="57aa6-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
### <a name="user-defined-types"></a><span data-ttu-id="57aa6-147">Typy definiowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="57aa6-147">User-defined Types</span></span>  
 <span data-ttu-id="57aa6-148">Typy danych zdefiniowane przez użytkownika CLR pozwalają rozbieżność system typu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="57aa6-149">Niemniej jednak ich powierzchni interesujące problemy dotyczące wersji typu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="57aa6-150">Zmiana wersji na kliencie może nie można dopasować poprzez zmianę typu przechowywane na serwerze bazy danych.</span><span class="sxs-lookup"><span data-stu-id="57aa6-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="57aa6-151">Taka zmiana powoduje, że inny niezgodność typów, gdzie semantyka typów mogą nie być zgodne, a przerwa wersji mogą być widoczne.</span><span class="sxs-lookup"><span data-stu-id="57aa6-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="57aa6-152">Dalsze komplikacji występować hierarchii dziedziczenia są refaktoryzowane w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="57aa6-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>  
  
## <a name="expression-semantics"></a><span data-ttu-id="57aa6-153">Semantyka wyrażeń</span><span class="sxs-lookup"><span data-stu-id="57aa6-153">Expression Semantics</span></span>  
 <span data-ttu-id="57aa6-154">Oprócz parowania niezgodność typów CLR i bazy danych wyrażenia zwiększenia złożoności niezgodność.</span><span class="sxs-lookup"><span data-stu-id="57aa6-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="57aa6-155">Należy rozważyć użycie niezgodności semantyki operatora, semantyki funkcja niejawna konwersja typu i pierwszeństwo reguły.</span><span class="sxs-lookup"><span data-stu-id="57aa6-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>  
  
 <span data-ttu-id="57aa6-156">Poniższe podpunkty ilustrują niezgodność między najwyraźniej podobne wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="57aa6-157">Może być można wygenerować wyrażenia SQL, które są równoważne semantycznie danego wyrażenia CLR.</span><span class="sxs-lookup"><span data-stu-id="57aa6-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="57aa6-158">Jednak nie jest jasne czy semantycznego różnice między najwyraźniej podobne wyrażenia mają manipulacji użytkownikowi CLR, i w związku z tym czy zmiany, które są wymagane do pełnienia roli równoważnika semantycznego lub nie.</span><span class="sxs-lookup"><span data-stu-id="57aa6-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="57aa6-159">Jest to problem krytyczne znaczenie, gdy wyrażenie jest obliczane dla zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="57aa6-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="57aa6-160">Widoczność różnica może zależą od danych - i jest trudne do zidentyfikowania podczas kodowania i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="57aa6-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>  
  
### <a name="null-semantics"></a><span data-ttu-id="57aa6-161">Semantyka wartości null</span><span class="sxs-lookup"><span data-stu-id="57aa6-161">Null Semantics</span></span>  
 <span data-ttu-id="57aa6-162">Wyrażenia SQL Podaj przechowywanymi w trzech logiki dla wyrażeń logicznych.</span><span class="sxs-lookup"><span data-stu-id="57aa6-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="57aa6-163">Może to spowodować powstanie wartość true, false lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="57aa6-163">The result can be true, false, or null.</span></span> <span data-ttu-id="57aa6-164">Z kolei CLR określa przechowywanymi na dwa logiczne wynik porównania obejmujące wartości null.</span><span class="sxs-lookup"><span data-stu-id="57aa6-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="57aa6-165">Rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="57aa6-165">Consider the following code:</span></span>  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 <span data-ttu-id="57aa6-166">Podobne problem występuje, przy założeniu o wynikach binarnego.</span><span class="sxs-lookup"><span data-stu-id="57aa6-166">A similar problem occurs with the assumption about two-valued results.</span></span>  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 <span data-ttu-id="57aa6-167">W przypadku poprzednich można uzyskać równoważne zachowanie podczas generowania SQL, ale translację dokładnie nie uwzględnia masz zamiar.</span><span class="sxs-lookup"><span data-stu-id="57aa6-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="57aa6-168">nie nakłada C# `null` lub [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` semantykę porównania SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-168"> does not impose C# `null` or [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="57aa6-169">Operatory porównania składniowo są przekształcane na ich odpowiedniki SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="57aa6-170">Semantyka odzwierciedlają semantyki SQL, zgodnie z ustawieniami serwera lub połączenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="57aa6-171">Dwie wartości null są traktowane jako nierówne w domyślnych ustawień programu SQL Server (mimo że można zmienić ustawienia, aby zmienić semantykę).</span><span class="sxs-lookup"><span data-stu-id="57aa6-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="57aa6-172">Niezależnie od tego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie należy wziąć pod uwagę ustawień serwera w Translacja zapytania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>  
  
 <span data-ttu-id="57aa6-173">Porównanie z literałem `null` (`nothing`) jest translacja do odpowiedniej wersji programu SQL (`is null` lub `is not null`).</span><span class="sxs-lookup"><span data-stu-id="57aa6-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>  
  
 <span data-ttu-id="57aa6-174">Wartość `null` (`nothing`) w sortowaniu jest zdefiniowany przez program SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ulega zmianie sortowania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>  
  
### <a name="type-conversion-and-promotion"></a><span data-ttu-id="57aa6-175">Konwersja typów i podwyższenie poziomu</span><span class="sxs-lookup"><span data-stu-id="57aa6-175">Type Conversion and Promotion</span></span>  
 <span data-ttu-id="57aa6-176">SQL obsługuje bogaty zestaw niejawne konwersje w wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="57aa6-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="57aa6-177">Podobne wyrażenia w języku C# wymaga jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="57aa6-178">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="57aa6-178">For example:</span></span>  
  
-   <span data-ttu-id="57aa6-179">`Nvarchar`i `DateTime` typy mogą być porównywane w języku SQL bez żadnych jawnego rzutowania; C# wymaga jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="57aa6-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>  
  
-   <span data-ttu-id="57aa6-180">`Decimal`jest niejawnie przekonwertowana na `DateTime` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="57aa6-181">C# nie pozwala na niejawną konwersję.</span><span class="sxs-lookup"><span data-stu-id="57aa6-181">C# does not allow for an implicit conversion.</span></span>  
  
 <span data-ttu-id="57aa6-182">Podobnie typu pierwszeństwo w języku Transact-SQL różni się od typu pierwszeństwo w języku C#, ponieważ różni się podstawowy zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="57aa6-183">W rzeczywistości istnieje żadna relacja wyczyść podzestawu/nadzbiorem między listami pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="57aa6-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="57aa6-184">Na przykład porównanie `nvarchar` z `varchar` powoduje, że niejawnej konwersji wartości `varchar` wyrażenie `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="57aa6-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="57aa6-185">Środowisko CLR udostępnia nie równoważne podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-185">The CLR provides no equivalent promotion.</span></span>  
  
 <span data-ttu-id="57aa6-186">W prostych przypadkach te różnice spowodować wyrażenia CLR z rzutowania być nadmiarowe dla odpowiedniego wyrażenia SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="57aa6-187">Co więcej, pośrednich wyników wyrażenie SQL może niejawnie podwyższony do typu, który nie ma odpowiednika dokładne w języku C# i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="57aa6-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="57aa6-188">Ogólne testowania, debugowania i sprawdzania poprawności takich wyrażeń dodaje znaczne obciążenie na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57aa6-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>  
  
### <a name="collation"></a><span data-ttu-id="57aa6-189">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="57aa6-189">Collation</span></span>  
 <span data-ttu-id="57aa6-190">Transact-SQL obsługuje sortowanie jawne jako adnotacje typów ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="57aa6-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="57aa6-191">Te sortowania sprawdzania poprawności niektórych porównania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="57aa6-192">Na przykład dwie kolumny z różnych opcji sortowania jawne porównanie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="57aa6-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="57aa6-193">Użyj typu string znacznie uproszczony CTS nie powoduje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="57aa6-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="57aa6-194">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="57aa6-194">Consider the following example:</span></span>  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 <span data-ttu-id="57aa6-195">W efekcie tworzy podklauzuli sortowania *ograniczone typu* nie jest to podstawienia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>  
  
 <span data-ttu-id="57aa6-196">Podobnie kolejność sortowania może być znacznie różni się we wszystkich systemach typu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="57aa6-197">Ta różnica dotyczy sortowania wyników.</span><span class="sxs-lookup"><span data-stu-id="57aa6-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="57aa6-198"><xref:System.Guid>jest sortowany na wszystkich 16 bajtów według kolejności lexicographic (`IComparable()`), podczas gdy T-SQL porównuje identyfikatorów GUID w następującej kolejności: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="57aa6-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="57aa6-199">Ta kolejność została wykonana w programie SQL 7.0, gdy generowane NT identyfikatorów GUID ma kolejności octet.</span><span class="sxs-lookup"><span data-stu-id="57aa6-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="57aa6-200">Podejście zapewnić, że identyfikatorów GUID generowane podczas tego samego węzła klastra pochodzi ze sobą w kolejności sekwencyjnej, zgodnie z sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="57aa6-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="57aa6-201">Podejście było również przydatne w przypadku tworzenia indeksów (wstawia stają się dołącza zamiast losowych operacji We-Wy).</span><span class="sxs-lookup"><span data-stu-id="57aa6-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="57aa6-202">Kolejność zostało zaszyfrowane później w systemie Windows z powodu prywatności, ale SQL musi zapewnić zgodność.</span><span class="sxs-lookup"><span data-stu-id="57aa6-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="57aa6-203">Obejście tego problemu jest użycie <xref:System.Data.SqlTypes.SqlGuid> zamiast <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="57aa6-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>  
  
### <a name="operator-and-function-differences"></a><span data-ttu-id="57aa6-204">Operator i różnice funkcji</span><span class="sxs-lookup"><span data-stu-id="57aa6-204">Operator and Function Differences</span></span>  
 <span data-ttu-id="57aa6-205">Operatory i funkcje, które są zasadniczo porównywalne ma semantykę różną pisowni.</span><span class="sxs-lookup"><span data-stu-id="57aa6-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="57aa6-206">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="57aa6-206">For example:</span></span>  
  
-   <span data-ttu-id="57aa6-207">C# określa semantyki zwarcia oparte na leksykalne Kolejność argumentów operacji dla operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="57aa6-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="57aa6-208">SQL z drugiej strony jest przeznaczony dla zapytań na podstawie zestawu, dlatego zapewnia większą swobodę Optymalizator określić kolejność wykonywania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="57aa6-209">Konsekwencje między innymi następujące:</span><span class="sxs-lookup"><span data-stu-id="57aa6-209">Some of the implications include the following:</span></span>  
  
    -   <span data-ttu-id="57aa6-210">Wymaga tłumaczenia semantycznie równoważne "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="57aa6-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="57aa6-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="57aa6-211">`WHEN` …</span></span> <span data-ttu-id="57aa6-212">`THEN`"tworzenia instrukcji SQL, aby uniknąć zmianę kolejności wykonywania argument.</span><span class="sxs-lookup"><span data-stu-id="57aa6-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>  
  
    -   <span data-ttu-id="57aa6-213">Luźne tłumaczenia na język `AND` / `OR` operatory może spowodować nieoczekiwane błędy, jeśli wyrażenie C# zależy oceny drugiego operandu na wynikiem obliczania pierwszego argumentu operacji.</span><span class="sxs-lookup"><span data-stu-id="57aa6-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>  
  
-   <span data-ttu-id="57aa6-214">`Round()`funkcja ma semantykę różną w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] w T-SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-214">`Round()` function has different semantics in [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] and in T-SQL.</span></span>  
  
-   <span data-ttu-id="57aa6-215">Indeks początkowy dla ciągów jest 0 w środowisku CLR, lecz 1 w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="57aa6-216">W związku z tym każda funkcja, która ma indeks musi tłumaczenia indeksu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-216">Therefore, any function that has index needs index translation.</span></span>  
  
-   <span data-ttu-id="57aa6-217">Środowisko CLR obsługuje operator modulo (%) na liczby zmiennoprzecinkowe, ale nie będzie SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>  
  
-   <span data-ttu-id="57aa6-218">`Like` Operator skutecznie uzyskuje automatyczne przeciążenia oparte na niejawną konwersję.</span><span class="sxs-lookup"><span data-stu-id="57aa6-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="57aa6-219">Mimo że `Like` operator jest zdefiniowana do działania na typy ciąg znaków, niejawna konwersja z typu liczbowego lub `DateTime` typy umożliwia dla tych typów innych niż ciąg do użycia z `Like` równie dobrze.</span><span class="sxs-lookup"><span data-stu-id="57aa6-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="57aa6-220">W CTS można porównywać pod względem niejawne konwersje nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="57aa6-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="57aa6-221">W związku z tym potrzebne są dodatkowe przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-221">Therefore, additional overloads are needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57aa6-222">To `Like` operator zachowanie dotyczy C# Visual Basic `Like` — słowo kluczowe jest bez zmian.</span><span class="sxs-lookup"><span data-stu-id="57aa6-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>  
  
-   <span data-ttu-id="57aa6-223">Przepełnienie zawsze ewidencjonowane SQL, ale musi być jawnie określona w języku C# (nie w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) w celu uniknięcia wraparound.</span><span class="sxs-lookup"><span data-stu-id="57aa6-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) to avoid wraparound.</span></span> <span data-ttu-id="57aa6-224">Podane kolumny całkowitą C1, C2 i C3, jeśli C1 + C2 jest przechowywany w C3 (C3 ustawić T aktualizacji = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="57aa6-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>  
  
    ```  
    create table T3 (  
        Col1      integer,  
        Col2      integer  
    )  
    insert into T3 (col1, col2) values (2147483647, 5)  
    -- Valid values: max integer value and 5.  
    select * from T3 where col1 + col2 < 0  
    -- Produces arithmetic overflow error.  
    ```  
  
 [!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
 [!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]  
  
-   <span data-ttu-id="57aa6-225">SQL wykonuje arytmetyczne symetrycznego zaokrąglania podczas [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] banker używa obiektu zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-225">SQL performs symmetric arithmetic rounding while [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] uses banker’s rounding.</span></span> <span data-ttu-id="57aa6-226">Zobacz artykuł bazy wiedzy 196652, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="57aa6-226">See Knowledgebase article 196652 for additional details.</span></span>  
  
-   <span data-ttu-id="57aa6-227">Domyślnie dla typowych ustawień regionalnych bez uwzględniania wielkości liter w programie SQL są porównania ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="57aa6-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="57aa6-228">W języku Visual Basic i C# są one z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="57aa6-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="57aa6-229">Na przykład `s == "Food"` (`s = "Food"` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) i `s == "Food"` może spowodować uzyskanie innych wyników, jeśli `s` jest `food`.</span><span class="sxs-lookup"><span data-stu-id="57aa6-229">For example, `s == "Food"` (`s = "Food"` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `s == "Food"` can yield different results if `s` is `food`.</span></span>  
  
    ```  
    -- Assume default US-English locale (case insensitive).  
    create table T4 (  
        Col1      nvarchar (256)  
    )  
    insert into T4 values (‘Food’)   
    insert into T4 values (‘FOOD’)  
    select * from T4 where Col1 = ‘food’  
    -- Both the rows are returned because of case-insensitive matching.  
    ```  
  
 [!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
 [!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]  
  
-   <span data-ttu-id="57aa6-230">Operatory / funkcji stosowane do argumentów typu znak o stałej długości w języku SQL ma semantykę znacznie różni się od tego samego operatory/funkcje stosowane do środowiska CLR <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="57aa6-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="57aa6-231">Można to także wyświetlane jako rozszerzenie Brak problemu odpowiednikiem omówionych w sekcji o typach.</span><span class="sxs-lookup"><span data-stu-id="57aa6-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>  
  
    ```  
    create table T4 (  
        Col1      nchar(4)  
    )  
    Insert into T5(Col1) values ('21');  
    Insert into T5(Col1) values ('1021');  
    Select * from T5 where Col1 like '%1'  
    -- Only the second row with Col1 = '1021' is returned.  
    -- Not the first row!  
    ```  
  
     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]  
  
     <span data-ttu-id="57aa6-232">Podobne problemu z ciągów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-232">A similar problem occurs with string concatenation.</span></span>  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 <span data-ttu-id="57aa6-233">Podsumowując zwichrowanych tłumaczenia mogą być wymagane dla wyrażeń CLR i dodatkowe operatory/funkcje mogą być niezbędne do udostępnienia funkcji SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>  
  
### <a name="type-casting"></a><span data-ttu-id="57aa6-234">Rzutowanie typów</span><span class="sxs-lookup"><span data-stu-id="57aa6-234">Type Casting</span></span>  
 <span data-ttu-id="57aa6-235">W języku C# i SQL, użytkownicy mogą zastępować domyślne semantyka wyrażeń przy użyciu typu jawnego rzutowania (`Cast` i `Convert`).</span><span class="sxs-lookup"><span data-stu-id="57aa6-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="57aa6-236">Jednak udostępnianie tej możliwości granicy system typu stanowi dilemma.</span><span class="sxs-lookup"><span data-stu-id="57aa6-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="57aa6-237">Rzutowanie SQL udostępniający żądaną semantyki nie można przetłumaczyć łatwe do odpowiedniego języka C# rzutowania.</span><span class="sxs-lookup"><span data-stu-id="57aa6-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="57aa6-238">Z drugiej strony rzutowania C# nie można bezpośrednio przetłumaczyć równoważne SQL rzutowania z powodu niezgodności typów, brak odpowiedników i hierarchie pierwszeństwo innego typu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="57aa6-239">Istnieje zależność między udostępnianie niezgodność typów systemu i utraty zasilania znaczących wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>  
  
 <span data-ttu-id="57aa6-240">W pozostałych przypadkach rzutowanie typów nie mogą być wymagane w domenie albo do sprawdzania poprawności wyrażenia, ale może być konieczne upewnij się, że mapowanie z systemem innym niż domyślny jest poprawnie zastosowana do wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a><span data-ttu-id="57aa6-241">Problemy z wydajnością</span><span class="sxs-lookup"><span data-stu-id="57aa6-241">Performance Issues</span></span>  
 <span data-ttu-id="57aa6-242">Ewidencjonowanie aktywności dla niektórych programu SQL Server — CLR różnice typu może resut w spadek wydajności przy przekraczaniu między CLR i SQL Server typu systemów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-242">Accounting for some SQL Server-CLR type differences may resut in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="57aa6-243">Następujące przykładowe scenariusze wpływające na wydajność:</span><span class="sxs-lookup"><span data-stu-id="57aa6-243">Examples of scenarios impacting performance include the following:</span></span>  
  
-   <span data-ttu-id="57aa6-244">Wymusić kolejności oceny dla logicznej i/lub operatory</span><span class="sxs-lookup"><span data-stu-id="57aa6-244">Forced order of evaluation for logical and/or operators</span></span>  
  
-   <span data-ttu-id="57aa6-245">Generowanie instrukcji SQL, aby wymusić kolejności oceny predykatu ogranicza możliwość Optymalizator SQL.</span><span class="sxs-lookup"><span data-stu-id="57aa6-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>  
  
-   <span data-ttu-id="57aa6-246">Konwersje typów, czy wprowadzone przez kompilator CLR lub przez implementację obiektu relacyjnego zapytania może ograniczać użycie indeksu.</span><span class="sxs-lookup"><span data-stu-id="57aa6-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>  
  
     <span data-ttu-id="57aa6-247">Na przykład</span><span class="sxs-lookup"><span data-stu-id="57aa6-247">For example,</span></span>  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     <span data-ttu-id="57aa6-248">Należy wziąć pod uwagę tłumaczenia wyrażenia `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="57aa6-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 <span data-ttu-id="57aa6-249">Oprócz semantycznego różnice należy wziąć pod uwagę wpływ na wydajność przy przekraczaniu między serwerem SQL i CLR typu systemów.</span><span class="sxs-lookup"><span data-stu-id="57aa6-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="57aa6-250">Dla dużych zestawów danych takie problemy z wydajnością można określić, czy aplikacja jest możliwy do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="57aa6-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57aa6-251">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57aa6-251">See Also</span></span>  
 [<span data-ttu-id="57aa6-252">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="57aa6-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
