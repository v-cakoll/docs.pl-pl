---
title: OD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 2334a30009d6bef9544d2ca1e0ab923a7441d6f2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833818"
---
# <a name="from-entity-sql"></a><span data-ttu-id="32c22-102">OD (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32c22-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="32c22-103">Określa kolekcję używaną w instrukcjach [SELECT](select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="32c22-103">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="32c22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32c22-104">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="32c22-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="32c22-105">Arguments</span></span>

`expression` \
<span data-ttu-id="32c22-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do użycia jako źródło w instrukcji `SELECT`.</span><span class="sxs-lookup"><span data-stu-id="32c22-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="32c22-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32c22-107">Remarks</span></span>

<span data-ttu-id="32c22-108">Klauzula `FROM` jest rozdzielaną przecinkami listą elementów klauzuli `FROM`.</span><span class="sxs-lookup"><span data-stu-id="32c22-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="32c22-109">Klauzula `FROM` może służyć do określenia jednego lub większej liczby źródeł dla instrukcji `SELECT`.</span><span class="sxs-lookup"><span data-stu-id="32c22-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="32c22-110">Najprostsza forma klauzuli `FROM` to pojedyncze wyrażenie zapytania, które identyfikuje kolekcję i alias używany jako źródło w instrukcji `SELECT`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32c22-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="32c22-111">Elementy klauzuli FROM</span><span class="sxs-lookup"><span data-stu-id="32c22-111">FROM Clause Items</span></span>

<span data-ttu-id="32c22-112">Każdy element klauzuli `FROM` odwołuje się do kolekcji źródłowej w zapytaniu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32c22-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="32c22-113">obsługuje następujące klasy elementów klauzuli `FROM`: proste elementy klauzuli `FROM`, elementy klauzuli `JOIN FROM` i elementy klauzul `APPLY FROM`.</span><span class="sxs-lookup"><span data-stu-id="32c22-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="32c22-114">Każdy z tych elementów klauzuli `FROM` został opisany bardziej szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="32c22-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="32c22-115">Prosty element klauzuli FROM</span><span class="sxs-lookup"><span data-stu-id="32c22-115">Simple FROM Clause Item</span></span>

<span data-ttu-id="32c22-116">Najprostszym elementem klauzuli `FROM` jest pojedyncze wyrażenie, które identyfikuje kolekcję i alias.</span><span class="sxs-lookup"><span data-stu-id="32c22-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="32c22-117">Wyrażenie może po prostu być zestawem jednostek lub podzapytaniem albo innym wyrażeniem, które jest typem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="32c22-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="32c22-118">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="32c22-118">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="32c22-119">Specyfikacja aliasu jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="32c22-119">The alias specification is optional.</span></span> <span data-ttu-id="32c22-120">Alternatywna Specyfikacja powyższego elementu klauzuli FROM może być następująca:</span><span class="sxs-lookup"><span data-stu-id="32c22-120">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="32c22-121">Jeśli alias nie zostanie określony, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias na podstawie wyrażenia kolekcji.</span><span class="sxs-lookup"><span data-stu-id="32c22-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="32c22-122">Element klauzuli JOIN</span><span class="sxs-lookup"><span data-stu-id="32c22-122">JOIN FROM Clause Item</span></span>

<span data-ttu-id="32c22-123">Element klauzuli `JOIN FROM` reprezentuje sprzężenie między dwoma elementami klauzuli `FROM`.</span><span class="sxs-lookup"><span data-stu-id="32c22-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="32c22-124">obsługuje sprzężenia krzyżowe, sprzężenia wewnętrzne, sprzężenia zewnętrzne w lewo i w prawo oraz pełne sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="32c22-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="32c22-125">Wszystkie te sprzężenia są obsługiwane podobne do sposobu, w jaki są obsługiwane w języku Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="32c22-125">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="32c22-126">Podobnie jak w języku Transact-SQL, dwa elementy klauzuli `FROM` w `JOIN` muszą być niezależne.</span><span class="sxs-lookup"><span data-stu-id="32c22-126">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="32c22-127">Oznacza to, że nie mogą być skorelowane.</span><span class="sxs-lookup"><span data-stu-id="32c22-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="32c22-128">W takich przypadkach można użyć `CROSS APPLY` lub `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="32c22-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="32c22-129">Sprzężenia krzyżowe</span><span class="sxs-lookup"><span data-stu-id="32c22-129">Cross Joins</span></span>

<span data-ttu-id="32c22-130">Wyrażenie zapytania `CROSS JOIN` generuje produkt kartezjańskiego dwóch kolekcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32c22-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="32c22-131">Sprzężenia wewnętrzne</span><span class="sxs-lookup"><span data-stu-id="32c22-131">Inner Joins</span></span>

<span data-ttu-id="32c22-132">@No__t-0 tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32c22-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="32c22-133">Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie warunek `ON` ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="32c22-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="32c22-134">Jeśli nie określono żadnego warunku `ON`, `INNER JOIN` degeneruje do `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="32c22-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="32c22-135">Lewe sprzężenia zewnętrzne i prawe sprzężenia zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="32c22-135">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="32c22-136">Wyrażenie zapytania `OUTER JOIN` tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32c22-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="32c22-137">Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie warunek `ON` ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="32c22-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="32c22-138">Jeśli warunek `ON` ma wartość false, wyrażenie nadal przetwarza pojedyncze wystąpienie elementu w lewej parze względem elementu po prawej stronie z wartością null.</span><span class="sxs-lookup"><span data-stu-id="32c22-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="32c22-139">@No__t-0 może być wyrażona w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="32c22-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="32c22-140">Pełne sprzężenia zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="32c22-140">Full Outer Joins</span></span>

<span data-ttu-id="32c22-141">Jawny `FULL OUTER JOIN` tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32c22-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="32c22-142">Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie warunek `ON` ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="32c22-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="32c22-143">Jeśli warunek `ON` ma wartość false, wyrażenie nadal przetwarza jedno wystąpienie elementu w lewej parze względem elementu po prawej stronie z wartością null.</span><span class="sxs-lookup"><span data-stu-id="32c22-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="32c22-144">Przetwarza także jedno wystąpienie elementu w prawej parze względem elementu po lewej stronie, z wartością null.</span><span class="sxs-lookup"><span data-stu-id="32c22-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="32c22-145">Aby zachować zgodność z SQL-92, w języku Transact-SQL słowo kluczowe OUTER jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="32c22-145">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="32c22-146">W związku z tym `LEFT JOIN`, `RIGHT JOIN` i `FULL JOIN` są synonimami dla `LEFT OUTER JOIN`, `RIGHT OUTER JOIN` i `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="32c22-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="32c22-147">APPLY — element klauzuli</span><span class="sxs-lookup"><span data-stu-id="32c22-147">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="32c22-148">obsługuje dwa rodzaje `APPLY`: `CROSS APPLY` i `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="32c22-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="32c22-149">@No__t-0 generuje unikatową parowanie każdego elementu kolekcji po lewej stronie z elementem kolekcji utworzonej przez obliczenie wyrażenia po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="32c22-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="32c22-150">W przypadku `CROSS APPLY` wyrażenie po prawej stronie jest funkcjonalnie zależne od elementu po lewej stronie, jak pokazano w następującym przykładzie skojarzonej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="32c22-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="32c22-151">Zachowanie `CROSS APPLY` jest podobne do listy sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="32c22-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="32c22-152">Jeśli wyrażenie po prawej stronie zwróci pustą kolekcję, `CROSS APPLY` nie tworzy par dla tego wystąpienia elementu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="32c22-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="32c22-153">@No__t-0 przypomina `CROSS APPLY`, z wyjątkiem tego, że parowanie jest nadal generowane nawet wtedy, gdy wyrażenie po prawej stronie oblicza pustą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="32c22-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="32c22-154">Poniżej znajduje się przykład `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="32c22-154">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="32c22-155">W przeciwieństwie do języka Transact-SQL nie ma potrzeby jawnego kroku unnesting w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32c22-155">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="32c22-156">Operatory `CROSS` i `OUTER APPLY` zostały wprowadzone w SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="32c22-156">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="32c22-157">W niektórych przypadkach potok zapytania może generować Transact-SQL, który zawiera `CROSS APPLY` i/lub operatory `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="32c22-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="32c22-158">Ponieważ niektórzy dostawcy zaplecza, w tym wersje SQL Server wcześniejsze niż SQL Server 2005, nie obsługują tych operatorów, takie zapytania nie mogą być wykonywane w tych dostawcach zaplecza.</span><span class="sxs-lookup"><span data-stu-id="32c22-158">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="32c22-159">Niektóre typowe scenariusze, które mogą prowadzić do obecności operatorów `CROSS APPLY` i/lub `OUTER APPLY` w zapytaniu wyjściowym są następujące: skorelowane podzapytanie ze stronicowaniem; AnyElement za pomocą skorelowanego podzapytania lub kolekcji utworzonej przez nawigację; Zapytania LINQ używające metod grupowania, które akceptują selektor elementu; zapytanie, w którym jawnie określono `CROSS APPLY` lub `OUTER APPLY`; zapytanie, które ma konstrukcję `DEREF` dla konstrukcji `REF`.</span><span class="sxs-lookup"><span data-stu-id="32c22-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="32c22-160">Wiele kolekcji w klauzuli FROM</span><span class="sxs-lookup"><span data-stu-id="32c22-160">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="32c22-161">Klauzula `FROM` może zawierać więcej niż jedną kolekcję rozdzieloną przecinkami.</span><span class="sxs-lookup"><span data-stu-id="32c22-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="32c22-162">W takich przypadkach przyjmuje się, że kolekcje są połączone ze sobą.</span><span class="sxs-lookup"><span data-stu-id="32c22-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="32c22-163">Zastanów się nad nimi jako SPRZĘŻENIem KRZYŻowym.</span><span class="sxs-lookup"><span data-stu-id="32c22-163">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="32c22-164">W poniższym przykładzie `C` i `D` są kolekcjami niezależnymi, ale `c.Names` zależy od `C`.</span><span class="sxs-lookup"><span data-stu-id="32c22-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="32c22-165">Poprzedni przykład jest logicznym odpowiednikiem poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="32c22-165">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="32c22-166">Lewa korelacja</span><span class="sxs-lookup"><span data-stu-id="32c22-166">Left Correlation</span></span>
 <span data-ttu-id="32c22-167">Elementy w klauzuli `FROM` mogą odwoływać się do elementów określonych w klauzulach wcześniejszych.</span><span class="sxs-lookup"><span data-stu-id="32c22-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="32c22-168">W poniższym przykładzie `C` i `D` są kolekcjami niezależnymi, ale `c.Names` zależy od `C`:</span><span class="sxs-lookup"><span data-stu-id="32c22-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="32c22-169">Jest to logicznie równoważne z:</span><span class="sxs-lookup"><span data-stu-id="32c22-169">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="32c22-170">Semantyki</span><span class="sxs-lookup"><span data-stu-id="32c22-170">Semantics</span></span>

<span data-ttu-id="32c22-171">Logicznie kolekcje w klauzuli `FROM` są założono, że jest częścią @no__t -1 sprzężenia krzyżowego (z wyjątkiem w przypadku 1-kierunkowego sprzężenia krzyżowego).</span><span class="sxs-lookup"><span data-stu-id="32c22-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="32c22-172">Aliasy w klauzuli `FROM` są przetwarzane od lewej do prawej i są dodawane do bieżącego zakresu w celu późniejszego odwołania.</span><span class="sxs-lookup"><span data-stu-id="32c22-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="32c22-173">Przyjęto klauzulę `FROM`, aby utworzyć zestaw wielokrotny wierszy.</span><span class="sxs-lookup"><span data-stu-id="32c22-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="32c22-174">Dla każdego elementu w klauzuli `FROM` będzie dostępne jedno pole, które reprezentuje pojedynczy element z tego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="32c22-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="32c22-175">Klauzula `FROM` logicznie tworzy zestaw wielokrotny wierszy typu Row (c, d, e), gdzie pola c, d i e są zakładane jako typ elementu `C`, `D` i `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="32c22-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="32c22-176">wprowadza alias dla każdego prostego elementu klauzuli `FROM` w zakresie.</span><span class="sxs-lookup"><span data-stu-id="32c22-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="32c22-177">Na przykład, w poniższym fragmencie kodu klauzuli, nazwy wprowadzone do zakresu to c, d i e.</span><span class="sxs-lookup"><span data-stu-id="32c22-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="32c22-178">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (w przeciwieństwie do języka Transact-SQL) klauzula `FROM` wprowadza tylko aliasy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="32c22-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="32c22-179">Wszystkie odwołania do kolumn (właściwości) tych kolekcji muszą być kwalifikowane przy użyciu aliasu.</span><span class="sxs-lookup"><span data-stu-id="32c22-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="32c22-180">Ściąganie kluczy z zagnieżdżonych zapytań</span><span class="sxs-lookup"><span data-stu-id="32c22-180">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="32c22-181">Niektóre typy zapytań, które wymagają ściągania kluczy z zapytania zagnieżdżonego, nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="32c22-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="32c22-182">Na przykład następujące zapytanie jest prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="32c22-182">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="32c22-183">Jednak następujące zapytanie jest nieprawidłowe, ponieważ zapytanie zagnieżdżone nie ma żadnych kluczy:</span><span class="sxs-lookup"><span data-stu-id="32c22-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="32c22-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32c22-184">See also</span></span>

- [<span data-ttu-id="32c22-185">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="32c22-185">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="32c22-186">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="32c22-186">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="32c22-187">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="32c22-187">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
