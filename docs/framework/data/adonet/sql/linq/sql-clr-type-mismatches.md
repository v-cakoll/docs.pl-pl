---
title: Niezgodność typu SQL CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 13d8d68140b68652b5e059ae9fb106f32142f698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974860"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="594b9-102">Niezgodność typu SQL CLR</span><span class="sxs-lookup"><span data-stu-id="594b9-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="594b9-103">automatyzuje większość tłumaczenie między model obiektu i programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="594b9-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="594b9-104">Niemniej jednak czasami uniemożliwić dokładnego tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="594b9-105">Tych kluczy niezgodności między wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) typów i typów bazy danych programu SQL Server są podsumowywane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="594b9-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="594b9-106">Można znaleźć więcej szczegółów na temat mapowania określony typ i funkcję tłumaczenia w [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) i [typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="594b9-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="594b9-107">Typy danych</span><span class="sxs-lookup"><span data-stu-id="594b9-107">Data Types</span></span>

<span data-ttu-id="594b9-108">Tłumaczenie między CLR i programu SQL Server występuje, gdy zapytanie jest wysyłane do bazy danych, a wyniki są odsyłane do modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="594b9-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="594b9-109">Na przykład poniższe zapytanie Transact-SQL wymaga dwóch konwersji wartości:</span><span class="sxs-lookup"><span data-stu-id="594b9-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="594b9-110">Zapytania mogą być wykonywane w programie SQL Server, należy określić wartość dla parametru języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="594b9-111">W tym przykładzie `id` wartość parametru, najpierw musi podlegać translacji z aparatu CLR <xref:System.Int32?displayProperty=nameWithType> typu do programu SQL Server `INT` wpisz, aby baza danych może zrozumieć, co to jest wartość.</span><span class="sxs-lookup"><span data-stu-id="594b9-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="594b9-112">Następnie, aby pobrać wyniki programu SQL Server `DateOfBirth` kolumny musi podlegać translacji z programu SQL Server `DATETIME` typu CLR <xref:System.DateTime?displayProperty=nameWithType> typ do użycia w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="594b9-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="594b9-113">W tym przykładzie typy w modelu obiektów CLR i bazy danych programu SQL Server ma naturalny mapowań.</span><span class="sxs-lookup"><span data-stu-id="594b9-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="594b9-114">Ale nie zawsze jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="594b9-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="594b9-115">Brak odpowiedniki</span><span class="sxs-lookup"><span data-stu-id="594b9-115">Missing Counterparts</span></span>

<span data-ttu-id="594b9-116">Następujące typy nie mają odpowiedniki uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="594b9-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="594b9-117">Nie jest zgodny w CLR <xref:System> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="594b9-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="594b9-118">**Niepodpisane liczby całkowite**.</span><span class="sxs-lookup"><span data-stu-id="594b9-118">**Unsigned integers**.</span></span> <span data-ttu-id="594b9-119">Zazwyczaj są mapowane te typy odpowiadają elementom podpisem większy rozmiar w celu uniknięcia przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="594b9-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="594b9-120">Literały mogą być konwertowane na podpisane liczbowy o tej samej lub mniejszym rozmiarze, na podstawie wartości.</span><span class="sxs-lookup"><span data-stu-id="594b9-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="594b9-121">**Wartość logiczna**.</span><span class="sxs-lookup"><span data-stu-id="594b9-121">**Boolean**.</span></span> <span data-ttu-id="594b9-122">Te typy mogą być mapowane na bit lub większych numeryczny lub ciąg.</span><span class="sxs-lookup"><span data-stu-id="594b9-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="594b9-123">Literał można zamapować na wyrażenie obliczane na tę samą wartość (na przykład `1=1` w języku SQL dla `True` w ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="594b9-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="594b9-124">**TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="594b9-124">**TimeSpan**.</span></span> <span data-ttu-id="594b9-125">Ten typ przedstawia różnicę między dwoma `DateTime` wartości i nie odpowiada żadnemu `timestamp` programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="594b9-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="594b9-126">Środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> może również mapować do programu SQL Server `TIME` typu w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="594b9-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="594b9-127">SQL Server `TIME` typu była przeznaczona tylko do reprezentowania wartości dodatnich mniej niż 24 godziny.</span><span class="sxs-lookup"><span data-stu-id="594b9-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="594b9-128">Środowisko CLR <xref:System.TimeSpan> ma znacznie większy zakres.</span><span class="sxs-lookup"><span data-stu-id="594b9-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="594b9-129">Specyficzne dla programu SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wpisuje <xref:System.Data.SqlTypes> nie są uwzględnione w tym porównania.</span><span class="sxs-lookup"><span data-stu-id="594b9-129">SQL Server-specific [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="594b9-130">Niezgodność w programie SQL Server:</span><span class="sxs-lookup"><span data-stu-id="594b9-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="594b9-131">**Stałej długości typów znaków**.</span><span class="sxs-lookup"><span data-stu-id="594b9-131">**Fixed length character types**.</span></span> <span data-ttu-id="594b9-132">Transact-SQL rozróżnia między kategoriami Unicode i innego niż Unicode i ma trzy różne typy w każdej kategorii: stała długość `nchar` / `char`, o zmiennej długości `nvarchar` / `varchar`, i o większym rozmiarze `ntext` / `text`.</span><span class="sxs-lookup"><span data-stu-id="594b9-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="594b9-133">Typy znaków o stałej długości mógłby być mapowany na środowisko CLR <xref:System.Char?displayProperty=nameWithType> typu pobierania znaków, ale nie naprawdę odpowiadają one tego samego typu w zakresie konwersji i zachowań.</span><span class="sxs-lookup"><span data-stu-id="594b9-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="594b9-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="594b9-134">**Bit**.</span></span> <span data-ttu-id="594b9-135">Mimo że `bit` domena ma taką samą liczbę wartości jako `Nullable<Boolean>`, dwa są różnych typów.</span><span class="sxs-lookup"><span data-stu-id="594b9-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="594b9-136">`Bit` pobiera wartości `1` i `0` zamiast `true` / `false`i nie można użyć jako równoważne wyrażeń logicznych.</span><span class="sxs-lookup"><span data-stu-id="594b9-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="594b9-137">**Sygnatura czasowa**.</span><span class="sxs-lookup"><span data-stu-id="594b9-137">**Timestamp**.</span></span> <span data-ttu-id="594b9-138">W przeciwieństwie do środowiska CLR <xref:System.TimeSpan?displayProperty=nameWithType> wpisz programu SQL Server `TIMESTAMP` typ reprezentuje 8-bajtowa liczba wygenerowanych przez bazę danych, który jest unikatowy dla każdej aktualizacji i nie jest oparty na różnicę między <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="594b9-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="594b9-139">**Pieniędzy** i **SmallMoney**.</span><span class="sxs-lookup"><span data-stu-id="594b9-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="594b9-140">Te typy mogą zostać zmapowane do <xref:System.Decimal> , ale są po prostu różnych typów i są traktowane jako takie konwersje i funkcji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="594b9-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="594b9-141">Wiele mapowań</span><span class="sxs-lookup"><span data-stu-id="594b9-141">Multiple Mappings</span></span>

<span data-ttu-id="594b9-142">Istnieje wiele typów danych programu SQL Server, mapowane na jeden lub więcej typów danych CLR.</span><span class="sxs-lookup"><span data-stu-id="594b9-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="594b9-143">Istnieje wiele typów CLR, które można zamapować na jeden lub więcej typów programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="594b9-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="594b9-144">Mimo że mapowanie może być obsługiwana w składniku LINQ to SQL, nie oznacza to, że dwa typy, które są mapowane między CLR i programu SQL Server są doskonałe dopasowanie, dokładności, zakresu i semantyki.</span><span class="sxs-lookup"><span data-stu-id="594b9-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="594b9-145">Niektóre mapowania mogą obejmować różnice w wybranych lub wszystkich tych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="594b9-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="594b9-146">Można znaleźć szczegółowe informacje o tych różnic potencjalnych różne możliwości mapowania na [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="594b9-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="594b9-147">Typy zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="594b9-147">User-defined Types</span></span>

<span data-ttu-id="594b9-148">Typy CLR zdefiniowane przez użytkownika mają na celu pomóc wypełnić tę przerwę systemu typu.</span><span class="sxs-lookup"><span data-stu-id="594b9-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="594b9-149">Niemniej jednak ich powierzchni ciekawe problemy dotyczące wersji typu.</span><span class="sxs-lookup"><span data-stu-id="594b9-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="594b9-150">Zmiana wersji na komputerze klienckim nie może towarzyszyć zmiany w typie przechowywane na serwerze bazy danych.</span><span class="sxs-lookup"><span data-stu-id="594b9-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="594b9-151">Wszelkie takie zmiany powoduje, że inny niezgodność typów, gdzie semantyka typów mogą być niezgodne i przerwy w wersji może stanie się widoczna.</span><span class="sxs-lookup"><span data-stu-id="594b9-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="594b9-152">Dalsze komplikacji występują jako hierarchii dziedziczenia są przetwarzane w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="594b9-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="594b9-153">Semantyka wyrażeń</span><span class="sxs-lookup"><span data-stu-id="594b9-153">Expression Semantics</span></span>

<span data-ttu-id="594b9-154">Oprócz parowania niezgodność między typami CLR i bazy danych wyrażenia zwiększenia złożoności niezgodność.</span><span class="sxs-lookup"><span data-stu-id="594b9-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="594b9-155">Należy rozważyć niezgodności w semantyki operatora, semantykę funkcji, niejawna konwersja typu i reguły pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="594b9-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="594b9-156">Poniższe podsekcje ilustrują niezgodność między najwyraźniej podobne wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="594b9-157">Może być można wygenerować wyrażenia SQL, które są semantycznie równoważne z danego wyrażenia CLR.</span><span class="sxs-lookup"><span data-stu-id="594b9-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="594b9-158">Jednak nie jest jasne czy semantyczne różnice między najwyraźniej podobne wyrażenia są widoczne dla użytkownika CLR i w związku z tym tego, czy zmiany, które są wymagane dla semantyki równoważności mają czy nie.</span><span class="sxs-lookup"><span data-stu-id="594b9-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="594b9-159">Jest to problem szczególnie istotne, gdy wyrażenie jest obliczane dla zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="594b9-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="594b9-160">Wgląd w różnicy może zależeć od danych — i być trudne do zidentyfikowania się podczas kodowania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="594b9-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="594b9-161">Semantyka wartości Null</span><span class="sxs-lookup"><span data-stu-id="594b9-161">Null Semantics</span></span>

<span data-ttu-id="594b9-162">Wyrażenia SQL Podaj przechowywanymi w trzech logiki dla wyrażeń logicznych.</span><span class="sxs-lookup"><span data-stu-id="594b9-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="594b9-163">Wynik może być wartość true, false lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="594b9-163">The result can be true, false, or null.</span></span> <span data-ttu-id="594b9-164">Z drugiej strony CLR określa przechowywanymi w dwóch logiczną wynik porównania używające wartości null.</span><span class="sxs-lookup"><span data-stu-id="594b9-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="594b9-165">Rozważmy poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="594b9-165">Consider the following code:</span></span>

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

<span data-ttu-id="594b9-166">Podobny problem występuje, przy założeniu, o wynikach binarnego.</span><span class="sxs-lookup"><span data-stu-id="594b9-166">A similar problem occurs with the assumption about two-valued results.</span></span>

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

<span data-ttu-id="594b9-167">W poprzednim przypadku otrzymasz równoważne zachowanie w generowanie kodu SQL, ale tłumaczenia nie może być dokładnie odzwierciedlają zamiaru.</span><span class="sxs-lookup"><span data-stu-id="594b9-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="594b9-168">nie nakłada C# `null` lub Visual Basic `nothing` semantykę porównania w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="594b9-169">Operatory porównania składniowo są tłumaczone na ich odpowiedniki SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="594b9-170">Semantyka odzwierciedlają semantyki SQL, zgodnie z definicją ustawienia serwera lub połączenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="594b9-171">Dwie wartości null są uznawane za nierówne w obszarze domyślne ustawienia programu SQL Server, (mimo że można zmienić ustawienia, aby zmienić semantyki).</span><span class="sxs-lookup"><span data-stu-id="594b9-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="594b9-172">Niezależnie od tego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie należy wziąć pod uwagę ustawień serwera w translacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="594b9-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="594b9-173">Porównanie z literałem `null` (`nothing`) jest tłumaczona na odpowiednią wersję programu SQL (`is null` lub `is not null`).</span><span class="sxs-lookup"><span data-stu-id="594b9-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="594b9-174">Wartość `null` (`nothing`) w sortowaniu jest zdefiniowany przez program SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie powoduje zmiany sortowania.</span><span class="sxs-lookup"><span data-stu-id="594b9-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="594b9-175">Konwersja typu i promocji</span><span class="sxs-lookup"><span data-stu-id="594b9-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="594b9-176">SQL obsługuje bogatego zestawu konwersji niejawnych; w wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="594b9-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="594b9-177">Podobne wyrażenia w C# wymaga jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="594b9-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="594b9-178">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="594b9-178">For example:</span></span>

- <span data-ttu-id="594b9-179">`Nvarchar` i `DateTime` można porównać typów w języku SQL bez żadnych jawnych rzutowań; C# wymaga jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="594b9-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="594b9-180">`Decimal` jest niejawnie konwertowany na `DateTime` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="594b9-181">C#Nie zezwalaj na niejawną konwersję.</span><span class="sxs-lookup"><span data-stu-id="594b9-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="594b9-182">Podobnie, pierwszeństwo typ w języku Transact-SQL różni się od typu pierwszeństwo w C# ponieważ różni się podstawowy zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="594b9-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="594b9-183">W rzeczywistości nie ma wyczyść podzbioru/nadzbiór relacji między listami pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="594b9-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="594b9-184">Na przykład porównanie `nvarchar` z `varchar` powoduje, że niejawną konwersję `varchar` wyrażenie `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="594b9-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="594b9-185">Środowisko CLR oferuje nie równoważne podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="594b9-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="594b9-186">W prostych przypadkach te różnice spowodować wyrażenia CLR z rzutowania jako nadmiarowe dla odpowiedniego wyrażenia SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="594b9-187">Co ważniejsze, wyniki pośrednie wyrażenia SQL może być niejawnie promowane do typu, który nie ma odpowiednika dokładne w C#i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="594b9-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="594b9-188">Ogólne testowanie, debugowanie i sprawdzanie poprawności takich wyrażeń dodaje znaczne obciążenie na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="594b9-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="594b9-189">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="594b9-189">Collation</span></span>

<span data-ttu-id="594b9-190">Języka Transact-SQL obsługuje sortowanie jawne jako adnotacje do typu ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="594b9-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="594b9-191">Te sortowania sprawdzania poprawności pewne porównania.</span><span class="sxs-lookup"><span data-stu-id="594b9-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="594b9-192">Na przykład porównanie dwóch kolumn przy użyciu innego sortowania jawne, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="594b9-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="594b9-193">Użyj typu string znacznie uproszczone CTS nie powoduje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="594b9-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="594b9-194">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="594b9-194">Consider the following example:</span></span>

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

<span data-ttu-id="594b9-195">W efekcie powoduje utworzenie listy sortowania *z ograniczeniami typu* nie jest to zastępowalne.</span><span class="sxs-lookup"><span data-stu-id="594b9-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="594b9-196">Podobnie kolejność sortowania może być znacznie różnią się w systemach typu.</span><span class="sxs-lookup"><span data-stu-id="594b9-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="594b9-197">Różnica ta ma wpływ na sortowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="594b9-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="594b9-198"><xref:System.Guid> jest sortowany na wszystkich 16-bajtowy według porządku leksykograficznym (`IComparable()`), podczas gdy języka T-SQL porównuje identyfikatorów GUID w następującej kolejności: node(10-15) clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="594b9-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="594b9-199">Ta kolejność było to SQL w wersji 7.0, gdy generowane NT identyfikatorów GUID miał zamówienie octet.</span><span class="sxs-lookup"><span data-stu-id="594b9-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="594b9-200">Podejście zapewnia, że identyfikatory GUID generowany w tym samym klastrze węzła pochodzi ze sobą w kolejności sekwencyjnej, zgodnie z sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="594b9-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="594b9-201">To podejście było również przydatne w przypadku tworzenia indeksów (wstawia stają się dołącza zamiast losowego dla systemu IOs).</span><span class="sxs-lookup"><span data-stu-id="594b9-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="594b9-202">Kolejność zostało zaszyfrowane później w Windows ze względu na kwestie prywatności, ale SQL muszą zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="594b9-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="594b9-203">Obejście polega na użyciu <xref:System.Data.SqlTypes.SqlGuid> zamiast <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="594b9-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="594b9-204">Operator i różnice funkcji</span><span class="sxs-lookup"><span data-stu-id="594b9-204">Operator and Function Differences</span></span>

<span data-ttu-id="594b9-205">Operatory i funkcje, które są zasadniczo porównywalne ma semantykę różną kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="594b9-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="594b9-206">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="594b9-206">For example:</span></span>

- <span data-ttu-id="594b9-207">C#Określa semantyki zwarcia opartego na leksykalne Kolejność argumentów dla operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="594b9-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="594b9-208">SQL z drugiej strony jest przeznaczona dla zapytania oparte na zestawie i dlatego zapewnia większą swobodę w optymalizatorze podjęcie decyzji, kolejność wykonywania.</span><span class="sxs-lookup"><span data-stu-id="594b9-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="594b9-209">Implikacje między innymi następujące:</span><span class="sxs-lookup"><span data-stu-id="594b9-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="594b9-210">Tłumaczenie semantycznie równoważne wymagałoby "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="594b9-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="594b9-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="594b9-211">`WHEN` …</span></span> <span data-ttu-id="594b9-212">`THEN`"skonstruować w języku SQL, aby uniknąć zmianę kolejności wykonywania operand.</span><span class="sxs-lookup"><span data-stu-id="594b9-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="594b9-213">Luźne tłumaczenia do `AND` / `OR` operatorów może spowodować nieoczekiwane błędy, jeśli C# wyrażenia opiera się na ocenie drugi operand jest oparty na wynik oceny pierwszy operand.</span><span class="sxs-lookup"><span data-stu-id="594b9-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="594b9-214">`Round()` funkcja ma semantykę różną [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] i języka T-SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-214">`Round()` function has different semantics in [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] and in T-SQL.</span></span>

- <span data-ttu-id="594b9-215">Indeks początkowy dla ciągów jest 0 w CLR, ale 1 w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="594b9-216">W związku z tym każda funkcja, która ma indeks musi tłumaczenia indeksu.</span><span class="sxs-lookup"><span data-stu-id="594b9-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="594b9-217">Środowisko CLR obsługuje operator modulo (%) dla liczb zmiennoprzecinkowych, ale nie obsługuje programu SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="594b9-218">`Like` Operator skutecznie uzyskuje automatyczne przeciążenia oparte na niejawne konwersje.</span><span class="sxs-lookup"><span data-stu-id="594b9-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="594b9-219">Mimo że `Like` zdefiniowano operator może działać w typów ciągów znaków, niejawna konwersja z typów liczbowych lub `DateTime` typy umożliwia tych typów innych niż ciąg do użycia z `Like` równie dobrze.</span><span class="sxs-lookup"><span data-stu-id="594b9-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="594b9-220">W CTS porównywalnych niejawne konwersje nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="594b9-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="594b9-221">W związku z tym potrzebne są dodatkowe przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="594b9-222">To `Like` operator zachowanie dotyczy C# tylko Visual Basic `Like` — słowo kluczowe pozostaje niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="594b9-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="594b9-223">Przepełnienie zawsze ewidencjonowane SQL, ale musi on być jawnie określone w C# (nie w Visual Basic) w celu uniknięcia zapętlenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="594b9-224">Biorąc pod uwagę kolumn liczb całkowitych, C1, C2 i C3, jeśli C1 + C2 jest przechowywany w C3 (aktualizację T Ustaw C3 = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="594b9-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

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

- <span data-ttu-id="594b9-225">SQL wykonuje operacje arytmetyczne symetrycznego zaokrąglania podczas [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] banker używa przez zaokrąglenie.</span><span class="sxs-lookup"><span data-stu-id="594b9-225">SQL performs symmetric arithmetic rounding while [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] uses banker’s rounding.</span></span> <span data-ttu-id="594b9-226">Zobacz artykuł bazy wiedzy 196652, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="594b9-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="594b9-227">Porównywanie ciągów znaków są domyślnie dla typowych ustawień regionalnych, bez uwzględniania wielkości liter w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="594b9-228">W języku Visual Basic, a w C#, ich jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="594b9-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="594b9-229">Na przykład `s == "Food"` (`s = "Food"` w języku Visual Basic) i `s == "Food"` może przynieść różne wyniki, jeśli `s` jest `food`.</span><span class="sxs-lookup"><span data-stu-id="594b9-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

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

- <span data-ttu-id="594b9-230">Operatory / funkcje stosowane do argumentów typu znaków o stałej długości w języku SQL mają znacząco różną semantykę, niż te same operatory/funkcje stosowane do środowiska CLR <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="594b9-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="594b9-231">Może to także wyświetlane jako rozszerzenie Brak problemu odpowiednika omówione w sekcji o typach.</span><span class="sxs-lookup"><span data-stu-id="594b9-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

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

     <span data-ttu-id="594b9-232">Podobny problem występuje, za pomocą ciągów.</span><span class="sxs-lookup"><span data-stu-id="594b9-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="594b9-233">Podsumowując zawiłe tłumaczenia mogą być wymagane dla wyrażenia CLR i dodatkowe funkcje operatorów może być konieczne ujawniać funkcjonalność SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="594b9-234">Rzutowanie typów</span><span class="sxs-lookup"><span data-stu-id="594b9-234">Type Casting</span></span>

<span data-ttu-id="594b9-235">W C# a w bazach SQL, użytkownicy mogą przesłaniać semantyki domyślne wyrażeń przy użyciu typu jawnego rzutowania (`Cast` i `Convert`).</span><span class="sxs-lookup"><span data-stu-id="594b9-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="594b9-236">Jednak udostępnianie tej funkcji przez granicę systemu typu stanowi dilemma.</span><span class="sxs-lookup"><span data-stu-id="594b9-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="594b9-237">Rzutowanie SQL, który zapewnia semantykę, żądany nie można łatwo przekształcić na odpowiedni C# rzutowania.</span><span class="sxs-lookup"><span data-stu-id="594b9-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="594b9-238">Z drugiej strony C# cast nie można bezpośrednio przetłumaczyć równoważne SQL rzutowanie ze względu na niezgodność typu, brak odpowiedniki i hierarchie pierwszeństwo innego typu.</span><span class="sxs-lookup"><span data-stu-id="594b9-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="594b9-239">Istnieje zależność między Uwidacznianie typu niezgodność systemu i utraty zasilania znaczące wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="594b9-240">W innych przypadkach rzutowanie typów nie mogą być wymagane w domenie, albo do sprawdzania poprawności wyrażenia, ale mogą być wymagane, aby upewnić się, że mapowanie innych niż domyślne jest prawidłowo stosowane do wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

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

## <a name="performance-issues"></a><span data-ttu-id="594b9-241">Problemy z wydajnością</span><span class="sxs-lookup"><span data-stu-id="594b9-241">Performance Issues</span></span>

<span data-ttu-id="594b9-242">Ewidencjonowanie aktywności dla niektórych SQL Server CLR różnice typu może spowodować spadek wydajności przy przekraczaniu między CLR i programu SQL Server typu systemów.</span><span class="sxs-lookup"><span data-stu-id="594b9-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="594b9-243">Następujące przykładowe scenariusze wpływające na wydajność:</span><span class="sxs-lookup"><span data-stu-id="594b9-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="594b9-244">Wymusić kolejności oceny dla logicznej i/lub operatorów</span><span class="sxs-lookup"><span data-stu-id="594b9-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="594b9-245">Generowanie kodu SQL, aby wymusić kolejności oceny predykatu ogranicza możliwość Optymalizator SQL.</span><span class="sxs-lookup"><span data-stu-id="594b9-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="594b9-246">Konwersje typów czy wprowadzony przez kompilator CLR lub implementacja obiektowo-relacyjny kwerendy może ograniczać użycie indeksu.</span><span class="sxs-lookup"><span data-stu-id="594b9-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="594b9-247">Na przykład</span><span class="sxs-lookup"><span data-stu-id="594b9-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="594b9-248">Należy wziąć pod uwagę Translacja wyrażeń `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="594b9-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

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

<span data-ttu-id="594b9-249">Oprócz semantyczne różnice należy wziąć pod uwagę wpływ na wydajność przy przekraczaniu między programu SQL Server i systemów typu CLR.</span><span class="sxs-lookup"><span data-stu-id="594b9-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="594b9-250">Dla dużych zestawów danych takie problemy z wydajnością można określić, czy aplikacja ma do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="594b9-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="594b9-251">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="594b9-251">See also</span></span>

- [<span data-ttu-id="594b9-252">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="594b9-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
