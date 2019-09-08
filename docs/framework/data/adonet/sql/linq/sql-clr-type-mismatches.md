---
title: Niezgodność typu SQL CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 27708f4bb8e191156f578132602570bc4a6337b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781199"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="503a8-102">Niezgodność typu SQL CLR</span><span class="sxs-lookup"><span data-stu-id="503a8-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="503a8-103">automatyzuje większość tłumaczenia między modelem obiektów i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="503a8-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="503a8-104">Niemniej jednak niektóre sytuacje uniemożliwiają dokładne tłumaczenie.</span><span class="sxs-lookup"><span data-stu-id="503a8-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="503a8-105">Te klucze nie są zgodne z typami środowiska uruchomieniowego języka wspólnego (CLR) i SQL Server typy baz danych zostały podsumowane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="503a8-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="503a8-106">Więcej szczegółów na temat mapowania określonego typu i tłumaczenia funkcji można znaleźć w [mapowaniu typu SQL-CLR](sql-clr-type-mapping.md) oraz w [funkcjach i typach danych](data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="503a8-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](sql-clr-type-mapping.md) and [Data Types and Functions](data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="503a8-107">Typy danych</span><span class="sxs-lookup"><span data-stu-id="503a8-107">Data Types</span></span>

<span data-ttu-id="503a8-108">Tłumaczenie między środowiskiem CLR i SQL Server występuje, gdy zapytanie jest wysyłane do bazy danych, a wyniki są wysyłane z powrotem do modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="503a8-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="503a8-109">Na przykład następujące zapytanie w języku Transact-SQL wymaga dwóch konwersji wartości:</span><span class="sxs-lookup"><span data-stu-id="503a8-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="503a8-110">Aby można było wykonać zapytanie na SQL Server, należy podać wartość parametru Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="503a8-111">W tym przykładzie `id` wartość parametru musi być najpierw przetłumaczona z typu CLR <xref:System.Int32?displayProperty=nameWithType> na typ SQL Server `INT` , aby baza danych mogła zrozumieć, co to jest wartość.</span><span class="sxs-lookup"><span data-stu-id="503a8-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="503a8-112">Następnie, aby pobrać wyniki, kolumna SQL Server `DateOfBirth` musi być przetłumaczona z typu SQL Server `DATETIME` na typ CLR <xref:System.DateTime?displayProperty=nameWithType> do użycia w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="503a8-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="503a8-113">W tym przykładzie typy w modelu obiektów CLR i SQL Server Database mają naturalne mapowania.</span><span class="sxs-lookup"><span data-stu-id="503a8-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="503a8-114">Jednak nie zawsze jest to przypadek.</span><span class="sxs-lookup"><span data-stu-id="503a8-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="503a8-115">Brakujące odpowiedniki</span><span class="sxs-lookup"><span data-stu-id="503a8-115">Missing Counterparts</span></span>

<span data-ttu-id="503a8-116">Następujące typy nie mają odpowiednich odpowiedników.</span><span class="sxs-lookup"><span data-stu-id="503a8-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="503a8-117">Niezgodności w przestrzeni nazw CLR <xref:System> :</span><span class="sxs-lookup"><span data-stu-id="503a8-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="503a8-118">**Liczby całkowite bez znaku**.</span><span class="sxs-lookup"><span data-stu-id="503a8-118">**Unsigned integers**.</span></span> <span data-ttu-id="503a8-119">Te typy są zwykle mapowane na ich podpisywane im odpowiedniki o większym rozmiarze, aby uniknąć przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="503a8-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="503a8-120">Literały mogą być konwertowane na wartość liczbową o takim samym lub mniejszym rozmiarze, na podstawie wartości.</span><span class="sxs-lookup"><span data-stu-id="503a8-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="503a8-121">**Wartość logiczna**.</span><span class="sxs-lookup"><span data-stu-id="503a8-121">**Boolean**.</span></span> <span data-ttu-id="503a8-122">Te typy mogą być mapowane na wartość bitową lub większą numeryczną lub ciąg.</span><span class="sxs-lookup"><span data-stu-id="503a8-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="503a8-123">Literał można zamapować na wyrażenie, którego wynikiem jest taka sama wartość (na przykład `1=1` w języku SQL dla `True` języka CLS).</span><span class="sxs-lookup"><span data-stu-id="503a8-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="503a8-124">Wartość **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="503a8-124">**TimeSpan**.</span></span> <span data-ttu-id="503a8-125">Ten typ reprezentuje różnicę między dwiema `DateTime` wartościami i nie odpowiada `timestamp` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="503a8-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="503a8-126">Środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> może również być mapowane na SQL Server `TIME` typu w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="503a8-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="503a8-127">Typ SQL Server `TIME` był przeznaczony tylko do reprezentowania wartości dodatnich mniejszych niż 24 godziny.</span><span class="sxs-lookup"><span data-stu-id="503a8-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="503a8-128">Środowisko CLR <xref:System.TimeSpan> ma znacznie większy zakres.</span><span class="sxs-lookup"><span data-stu-id="503a8-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="503a8-129">W tym porównaniu nie zamieszczono typów <xref:System.Data.SqlTypes> .NET Framework specyficznych dla SQL Server.</span><span class="sxs-lookup"><span data-stu-id="503a8-129">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="503a8-130">Niezgodności w SQL Server:</span><span class="sxs-lookup"><span data-stu-id="503a8-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="503a8-131">**Typy znaków o stałej długości**.</span><span class="sxs-lookup"><span data-stu-id="503a8-131">**Fixed length character types**.</span></span> <span data-ttu-id="503a8-132">Język Transact-SQL rozróżnia kategorie Unicode i inne niż Unicode i ma trzy odrębne typy w każdej kategorii: stała długość `nchar` `varchar` / `char`, zmienna długość `nvarchar`i / większy rozmiar `ntext`. / `text`</span><span class="sxs-lookup"><span data-stu-id="503a8-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="503a8-133">Typy znaków o stałej długości można zamapować na typ CLR <xref:System.Char?displayProperty=nameWithType> w celu pobierania znaków, ale nie są naprawdę zgodne z tym samym typem w konwersji i zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="503a8-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="503a8-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="503a8-134">**Bit**.</span></span> <span data-ttu-id="503a8-135">Chociaż domena ma taką samą liczbę wartości jak `Nullable<Boolean>`, dwa typy są różne. `bit`</span><span class="sxs-lookup"><span data-stu-id="503a8-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="503a8-136">`Bit`Pobiera wartości `1` i `0` zamiast `true`i niemożebyćużywanejakoodpowiednikwyrażeńlogicznych./ `false`</span><span class="sxs-lookup"><span data-stu-id="503a8-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="503a8-137">**Sygnatura czasowa**.</span><span class="sxs-lookup"><span data-stu-id="503a8-137">**Timestamp**.</span></span> <span data-ttu-id="503a8-138">W przeciwieństwie do <xref:System.TimeSpan?displayProperty=nameWithType> typu CLR, typ `TIMESTAMP` SQL Server reprezentuje 8-bajtowy numer wygenerowany przez bazę danych unikatową dla każdej aktualizacji i nie jest oparty na różnicy między <xref:System.DateTime> wartościami.</span><span class="sxs-lookup"><span data-stu-id="503a8-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="503a8-139">**Money** i **smallmoney**.</span><span class="sxs-lookup"><span data-stu-id="503a8-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="503a8-140">Te typy mogą być mapowane na <xref:System.Decimal> , ale są zasadniczo różne typy i są traktowane jako takie jak funkcje i konwersje oparte na serwerze.</span><span class="sxs-lookup"><span data-stu-id="503a8-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="503a8-141">Wiele mapowań</span><span class="sxs-lookup"><span data-stu-id="503a8-141">Multiple Mappings</span></span>

<span data-ttu-id="503a8-142">Istnieje wiele typów danych SQL Server, które można mapować na jeden lub więcej typów danych CLR.</span><span class="sxs-lookup"><span data-stu-id="503a8-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="503a8-143">Istnieje również wiele typów CLR, które można zamapować na jeden lub więcej typów SQL Server.</span><span class="sxs-lookup"><span data-stu-id="503a8-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="503a8-144">Chociaż mapowanie może być obsługiwane przez LINQ to SQL, nie oznacza to, że dwa typy mapowane między CLR i SQL Server są idealnym dopasowaniem dokładności, zakresu i semantyki.</span><span class="sxs-lookup"><span data-stu-id="503a8-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="503a8-145">Niektóre mapowania mogą obejmować różnice w dowolnych lub wszystkich tych wymiarach.</span><span class="sxs-lookup"><span data-stu-id="503a8-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="503a8-146">Szczegółowe informacje na temat tych potencjalnych różnic można znaleźć w odniesieniu do różnych możliwości mapowania w [mapowaniu typu SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="503a8-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="503a8-147">Typy zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="503a8-147">User-defined Types</span></span>

<span data-ttu-id="503a8-148">Typy CLR zdefiniowane przez użytkownika zostały zaprojektowane w celu ułatwienia mostkowania przerwy w działaniu systemu.</span><span class="sxs-lookup"><span data-stu-id="503a8-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="503a8-149">Niemniej jednak są to interesujące problemy związane z przechowywaniem wersji.</span><span class="sxs-lookup"><span data-stu-id="503a8-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="503a8-150">Zmiana wersji na kliencie może nie być zgodna ze zmianą typu przechowywanego na serwerze bazy danych.</span><span class="sxs-lookup"><span data-stu-id="503a8-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="503a8-151">Każda taka zmiana powoduje inny niezgodność typów, w którym Semantyka typów może być niezgodna i przerwy w działaniu mogą być widoczne.</span><span class="sxs-lookup"><span data-stu-id="503a8-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="503a8-152">Kolejne komplikacje występują, ponieważ hierarchie dziedziczenia są refaktoryzacji w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="503a8-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="503a8-153">Semantyka wyrażeń</span><span class="sxs-lookup"><span data-stu-id="503a8-153">Expression Semantics</span></span>

<span data-ttu-id="503a8-154">Oprócz niezgodności parowania między typami CLR i bazy danych, wyrażenia zwiększają złożoność do niezgodności.</span><span class="sxs-lookup"><span data-stu-id="503a8-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="503a8-155">Niezgodność z semantyką operatora, semantyką funkcji, niejawną konwersją typów i regułami pierwszeństwa należy rozważyć.</span><span class="sxs-lookup"><span data-stu-id="503a8-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="503a8-156">Poniższe podsekcje ilustrują niezgodność między podobnymi wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="503a8-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="503a8-157">Może być możliwe wygenerowanie wyrażeń SQL, które są semantycznie równoważne z danym wyrażeniem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="503a8-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="503a8-158">Jednakże nie jest jasne, czy różnice semantyczne między wyrazami podobnymi są oczywiste dla użytkownika CLR, a w związku z tym, czy zmiany wymagane dla równoważności semantycznej są zamierzone, czy nie.</span><span class="sxs-lookup"><span data-stu-id="503a8-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="503a8-159">Jest to szczególnie problem krytyczny, gdy wyrażenie jest oceniane dla zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="503a8-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="503a8-160">Widoczność różnic może zależeć od danych i być trudno do zidentyfikowania podczas kodowania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="503a8-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="503a8-161">Semantyka wartości Null</span><span class="sxs-lookup"><span data-stu-id="503a8-161">Null Semantics</span></span>

<span data-ttu-id="503a8-162">Wyrażenia SQL zapewniają wielowartościową logikę dla wyrażeń logicznych.</span><span class="sxs-lookup"><span data-stu-id="503a8-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="503a8-163">Wynik może mieć wartość true, false lub null.</span><span class="sxs-lookup"><span data-stu-id="503a8-163">The result can be true, false, or null.</span></span> <span data-ttu-id="503a8-164">Z kolei środowisko CLR Określa wynik wartości logicznej dwuwartościowej w przypadku porównań, w których wartość jest równa null.</span><span class="sxs-lookup"><span data-stu-id="503a8-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="503a8-165">Rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="503a8-165">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="503a8-166">Podobny problem występuje z założeniem dotyczącym wyników dwóch wartości.</span><span class="sxs-lookup"><span data-stu-id="503a8-166">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="503a8-167">W poprzednim przypadku można uzyskać równoważne zachowanie podczas generowania kodu SQL, ale tłumaczenie może nie odzwierciedlać zamierzonego celu.</span><span class="sxs-lookup"><span data-stu-id="503a8-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="503a8-168">nie nakłada C# `null` ani nie Visual Basic `nothing` semantyki porównania w SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="503a8-169">Operatory porównania są syntaktycznie przetłumaczone na ich odpowiedniki języka SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="503a8-170">Semantyka odzwierciedla semantykę SQL zgodnie z definicją serwera lub ustawienia połączenia.</span><span class="sxs-lookup"><span data-stu-id="503a8-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="503a8-171">Dwie wartości null są uznawane za nierówne w domyślnych ustawieniach SQL Server (chociaż można zmienić ustawienia w celu zmiany semantyki).</span><span class="sxs-lookup"><span data-stu-id="503a8-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="503a8-172">Bez względu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na to, czy ustawienia serwera nie są uwzględniane w tłumaczeniu zapytań.</span><span class="sxs-lookup"><span data-stu-id="503a8-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="503a8-173">Porównanie z literałem `null` (`nothing`) jest tłumaczone na odpowiednią wersję SQL (`is null` lub `is not null`).</span><span class="sxs-lookup"><span data-stu-id="503a8-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="503a8-174">Wartość `null` (`nothing`) w sortowaniu jest definiowana przez SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie zmienia sortowania.</span><span class="sxs-lookup"><span data-stu-id="503a8-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="503a8-175">Konwersja i promocja typu</span><span class="sxs-lookup"><span data-stu-id="503a8-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="503a8-176">SQL obsługuje bogaty zestaw niejawnych konwersji w wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="503a8-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="503a8-177">Podobne wyrażenia w C# programie wymagają jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="503a8-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="503a8-178">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="503a8-178">For example:</span></span>

- <span data-ttu-id="503a8-179">`Nvarchar`typy `DateTime` i można porównać w języku SQL bez żadnych jawnych rzutowania; C# wymaga jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="503a8-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="503a8-180">`Decimal`jest niejawnie konwertowany `DateTime` na w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="503a8-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="503a8-181">C#nie zezwala na niejawną konwersję.</span><span class="sxs-lookup"><span data-stu-id="503a8-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="503a8-182">Analogicznie, pierwszeństwo typów w języku Transact-SQL różni się C# od priorytetu typu w, ponieważ podstawowy zestaw typów jest inny.</span><span class="sxs-lookup"><span data-stu-id="503a8-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="503a8-183">W rzeczywistości nie istnieje relacja Wyczyść podzbiór/nadzbiór z listy pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="503a8-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="503a8-184">Na `nvarchar` przykład porównanie `varchar` z wystąpieniem powoduje niejawną konwersję `varchar` wyrażenia na `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="503a8-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="503a8-185">Środowisko CLR nie zapewnia równoważnej promocji.</span><span class="sxs-lookup"><span data-stu-id="503a8-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="503a8-186">W prostych przypadkach te różnice powodują, że wyrażenia CLR z rzutowania są nadmiarowe dla odpowiedniego wyrażenia SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="503a8-187">Co ważniejsze, pośrednie wyniki wyrażenia SQL mogą zostać niejawnie podwyższone do typu, który nie ma dokładnego odpowiednika w C#i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="503a8-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="503a8-188">Ogólnie, testowanie, debugowanie i sprawdzanie poprawności takich wyrażeń zwiększa duże obciążenie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="503a8-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="503a8-189">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="503a8-189">Collation</span></span>

<span data-ttu-id="503a8-190">Język Transact-SQL obsługuje jawne sortowania jako adnotacje w typach ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="503a8-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="503a8-191">Te sortowania określają prawidłowość niektórych porównań.</span><span class="sxs-lookup"><span data-stu-id="503a8-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="503a8-192">Na przykład porównywanie dwóch kolumn z różnymi jawnymi sortowaniami jest błędem.</span><span class="sxs-lookup"><span data-stu-id="503a8-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="503a8-193">Użycie znacznie uproszczonego typu ciągu CTS nie powoduje błędów.</span><span class="sxs-lookup"><span data-stu-id="503a8-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="503a8-194">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="503a8-194">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="503a8-195">W efekcie Podklauzula sortowania tworzy *ograniczony typ* , który nie jest zamienny.</span><span class="sxs-lookup"><span data-stu-id="503a8-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="503a8-196">Podobnie porządek sortowania może być znacząco różny w systemach typów.</span><span class="sxs-lookup"><span data-stu-id="503a8-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="503a8-197">Różnica ta ma wpływ na sortowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="503a8-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="503a8-198"><xref:System.Guid>jest sortowany dla wszystkich 16 bajtów według kolejności leksykograficznych`IComparable()`(), podczas gdy język T-SQL porównuje identyfikatory GUID w następującej kolejności: node (10-15), Clock-SEQ (8-9), Time-High (6-7), Time-Mid (4-5), czas-niski (0-3).</span><span class="sxs-lookup"><span data-stu-id="503a8-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="503a8-199">Takie porządkowanie zostało wykonane w programie SQL 7,0, gdy identyfikatory GUID generowane przez NT mają takie zamówienie oktetowe.</span><span class="sxs-lookup"><span data-stu-id="503a8-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="503a8-200">Podejście to gwarantuje, że identyfikatory GUID wygenerowane w tym samym klastrze węzłów zostały połączone w kolejności sekwencyjnej zgodnie z sygnaturą czasową.</span><span class="sxs-lookup"><span data-stu-id="503a8-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="503a8-201">Podejście było również przydatne do kompilowania indeksów (wstawiane są dołączenia zamiast losowego systemu IOs).</span><span class="sxs-lookup"><span data-stu-id="503a8-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="503a8-202">Zamówienie zostało zaszyfrowane później w systemie Windows z powodu kwestii związanych z ochroną prywatności, ale program SQL Server musi zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="503a8-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="503a8-203">Obejściem jest użycie <xref:System.Data.SqlTypes.SqlGuid> <xref:System.Guid>zamiast.</span><span class="sxs-lookup"><span data-stu-id="503a8-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="503a8-204">Różnice między operatorami i funkcjami</span><span class="sxs-lookup"><span data-stu-id="503a8-204">Operator and Function Differences</span></span>

<span data-ttu-id="503a8-205">Operatory i funkcje, które są zasadniczo porównywalne, mają zbliżoną inną semantykę.</span><span class="sxs-lookup"><span data-stu-id="503a8-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="503a8-206">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="503a8-206">For example:</span></span>

- <span data-ttu-id="503a8-207">C#Określa semantykę krótkiego obwodu opartą na leksykalnej kolejności operandów `&&` dla `||`operatorów logicznych i.</span><span class="sxs-lookup"><span data-stu-id="503a8-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="503a8-208">Program SQL z drugiej strony jest przeznaczony dla zapytań opartych na zestawie i dlatego zapewnia większą swobodę dla Optymalizatora decydującego o kolejności wykonywania.</span><span class="sxs-lookup"><span data-stu-id="503a8-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="503a8-209">Poniżej wymieniono niektóre konsekwencje:</span><span class="sxs-lookup"><span data-stu-id="503a8-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="503a8-210">Semantycznie równoważne tłumaczenie wymaga "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="503a8-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="503a8-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="503a8-211">`WHEN` …</span></span> <span data-ttu-id="503a8-212">`THEN`"konstrukcja w języku SQL, aby uniknąć zmiany kolejności wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="503a8-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="503a8-213">`AND` Luźne tłumaczenie / operatorów`OR` może spowodować nieoczekiwane błędy, C# Jeśli wyrażenie polega na ocenie drugiego operandu na podstawie wyniku oceny pierwszego operandu.</span><span class="sxs-lookup"><span data-stu-id="503a8-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="503a8-214">`Round()`Funkcja ma inną semantykę w .NET Framework i w języku T-SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-214">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="503a8-215">Początkowy indeks dla ciągów ma wartość 0 w CLR, ale 1 w SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="503a8-216">W związku z tym każda funkcja, która ma indeks, wymaga tłumaczenia indeksu.</span><span class="sxs-lookup"><span data-stu-id="503a8-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="503a8-217">Środowisko CLR obsługuje operator modułu ("%") dla liczb zmiennoprzecinkowych, ale nie jest on obsługiwany przez program SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="503a8-218">`Like` Operator efektywnie uzyskuje automatyczne przeciążenia na podstawie niejawnych konwersji.</span><span class="sxs-lookup"><span data-stu-id="503a8-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="503a8-219">Mimo że `DateTime` `Like` operator jest zdefiniowany do działania w typach ciągów znaków, niejawna konwersja z typów numerycznych lub typów pozwala na użycie tych typów niebędących ciągami. `Like`</span><span class="sxs-lookup"><span data-stu-id="503a8-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="503a8-220">W programie CTS porównywalne konwersje niejawne nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="503a8-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="503a8-221">W związku z tym konieczne są dodatkowe przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="503a8-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="503a8-222">To `Like` zachowanie operatora ma zastosowanie C# tylko do słowa kluczowego Visual Basic `Like` bez zmian.</span><span class="sxs-lookup"><span data-stu-id="503a8-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="503a8-223">Przepełnienie jest zawsze sprawdzane w języku SQL, ale musi być C# jawnie określone w (nie w Visual Basic), aby uniknąć wraparound.</span><span class="sxs-lookup"><span data-stu-id="503a8-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="503a8-224">Podano kolumny liczb całkowitych C1, C2 i C3, jeśli C1 + C2 jest przechowywany w C3 (aktualizacja T zestawu C3 = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="503a8-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
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

- <span data-ttu-id="503a8-225">Funkcja SQL wykonuje symetryczne zaokrąglenie arytmetyczne, podczas gdy .NET Framework używa zaokrągleń przez Bank.</span><span class="sxs-lookup"><span data-stu-id="503a8-225">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="503a8-226">Więcej informacji można znaleźć w artykule bazy wiedzy 196652.</span><span class="sxs-lookup"><span data-stu-id="503a8-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="503a8-227">Domyślnie w przypadku wspólnych ustawień regionalnych porównania ciągów znaków nie uwzględniają wielkości liter w SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="503a8-228">W Visual Basic i w C#programie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="503a8-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="503a8-229">`s == "Food"` Na przykład `food`(`s = "Food"` w Visual Basic) i mogą `s == "Food"` dać różne wyniki, jeśli `s` jest.</span><span class="sxs-lookup"><span data-stu-id="503a8-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
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

- <span data-ttu-id="503a8-230">Operatory/funkcje zastosowane do argumentów typu o stałej długości w programie SQL mają znacznie inną semantykę niż te same operatory/funkcje zastosowane do środowiska <xref:System.String?displayProperty=nameWithType>CLR.</span><span class="sxs-lookup"><span data-stu-id="503a8-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="503a8-231">Może to również być widoczne jako rozszerzenie brakującego, odpowiadającego problemu omówionego w sekcji Informacje o typach.</span><span class="sxs-lookup"><span data-stu-id="503a8-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
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

     <span data-ttu-id="503a8-232">Podobny problem występuje w przypadku łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="503a8-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="503a8-233">Podsumowując, tłumaczenie zawiłe może być wymagane dla wyrażeń CLR, a dodatkowe operatory/funkcje mogą być niezbędne do udostępnienia funkcji SQL.</span><span class="sxs-lookup"><span data-stu-id="503a8-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="503a8-234">Rzutowanie typu</span><span class="sxs-lookup"><span data-stu-id="503a8-234">Type Casting</span></span>

<span data-ttu-id="503a8-235">W C# programie i w języku SQL użytkownicy mogą zastąpić domyślną semantykę wyrażeń przy użyciu jawnych rzutowania typu (`Cast` i `Convert`).</span><span class="sxs-lookup"><span data-stu-id="503a8-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="503a8-236">Jednak udostępnienie tej funkcji w granicach systemu typów stanowi dylematem.</span><span class="sxs-lookup"><span data-stu-id="503a8-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="503a8-237">Rzutowanie kodu SQL, które zapewnia odpowiednią semantykę, nie może być łatwo przetłumaczone na odpowiednie C# rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="503a8-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="503a8-238">Z drugiej strony C# rzutowanie nie może być bezpośrednio przetłumaczone na równoważne rzutowanie SQL ze względu na niezgodności typów, brakujące odpowiedniki i różne hierarchie pierwszeństwa typu.</span><span class="sxs-lookup"><span data-stu-id="503a8-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="503a8-239">Istnieje kompromis między ujawnieniem niezgodności systemu typów i utratą znaczących możliwości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="503a8-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="503a8-240">W innych przypadkach rzutowanie typów może nie być potrzebne w żadnej domenie do walidacji wyrażenia, ale może być wymagane, aby upewnić się, że mapowanie inne niż domyślne jest prawidłowo stosowane do wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="503a8-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="503a8-241">Problemy z wydajnością</span><span class="sxs-lookup"><span data-stu-id="503a8-241">Performance Issues</span></span>

<span data-ttu-id="503a8-242">Księgowanie niektórych różnic typu SQL Server-CLR może spowodować spadek wydajności w przypadku przekroczenia między systemami typów CLR i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="503a8-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="503a8-243">Oto przykładowe scenariusze wpływające na wydajność:</span><span class="sxs-lookup"><span data-stu-id="503a8-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="503a8-244">Wymuszona kolejność obliczeń dla operatorów logicznych i/or</span><span class="sxs-lookup"><span data-stu-id="503a8-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="503a8-245">Generowanie kodu SQL w celu wymuszenia kolejności szacowania predykatu ogranicza możliwość korzystania z programu SQL Optymalizatora.</span><span class="sxs-lookup"><span data-stu-id="503a8-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="503a8-246">Konwersje typu, wprowadzone przez kompilator CLR lub przez implementację zapytania Object-relacyjnego, mogą ograniczać użycie indeksu.</span><span class="sxs-lookup"><span data-stu-id="503a8-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="503a8-247">Na przykład</span><span class="sxs-lookup"><span data-stu-id="503a8-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="503a8-248">Rozważ tłumaczenie wyrażenia `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="503a8-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="503a8-249">Oprócz różnic semantycznych należy wziąć pod uwagę wpływ na wydajność w przypadku przekroczenia między SQL Server i systemami typów CLR.</span><span class="sxs-lookup"><span data-stu-id="503a8-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="503a8-250">W przypadku dużych zestawów danych takie problemy z wydajnością mogą określić, czy aplikacja jest wdrażana.</span><span class="sxs-lookup"><span data-stu-id="503a8-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="503a8-251">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="503a8-251">See also</span></span>

- [<span data-ttu-id="503a8-252">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="503a8-252">Background Information</span></span>](background-information.md)
