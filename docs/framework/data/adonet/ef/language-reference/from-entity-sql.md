---
title: Z (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: de2ad24e5c6399ed1ca91e3907da4a66c056e337
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765818"
---
# <a name="from-entity-sql"></a><span data-ttu-id="522fe-102">Z (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="522fe-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="522fe-103">Określa kolekcję używane w [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="522fe-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="522fe-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="522fe-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="522fe-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="522fe-106">Dowolne wyrażenie prawidłowe zapytanie zwracające kolekcji do użycia jako źródło w `SELECT` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="522fe-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="522fe-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="522fe-107">Remarks</span></span>  
 <span data-ttu-id="522fe-108">A `FROM` klauzula jest rozdzielaną przecinkami listę co najmniej jeden `FROM` klauzuli elementów.</span><span class="sxs-lookup"><span data-stu-id="522fe-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="522fe-109">`FROM` Klauzuli może służyć do określenia co najmniej jedno źródło dla `SELECT` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="522fe-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="522fe-110">Najprostsza forma `FROM` klauzula jest wyrażenie pojedynczego zapytania, które identyfikuje kolekcji i alias używany jako źródło w `SELECT` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="522fe-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="522fe-111">W klauzuli elementów</span><span class="sxs-lookup"><span data-stu-id="522fe-111">FROM Clause Items</span></span>  
 <span data-ttu-id="522fe-112">Każdy `FROM` element klauzuli odwołuje się do kolekcji źródła w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="522fe-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="522fe-113"> obsługuje następujące rodzaje `FROM` elementów klauzuli: prosty `FROM` elementów klauzuli `JOIN FROM` elementów klauzuli i `APPLY FROM` klauzuli elementów.</span><span class="sxs-lookup"><span data-stu-id="522fe-113"> supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="522fe-114">Każdy z tych `FROM` elementy klauzuli jest opisane bardziej szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="522fe-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="522fe-115">Prosty z klauzuli elementu</span><span class="sxs-lookup"><span data-stu-id="522fe-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="522fe-116">Najprostszą `FROM` element klauzuli jest jedno wyrażenie identyfikujące kolekcji i alias.</span><span class="sxs-lookup"><span data-stu-id="522fe-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="522fe-117">Wyrażenie, które można po prostu zestaw jednostek lub podzapytaniu lub innego wyrażenia, który jest typem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="522fe-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="522fe-118">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="522fe-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="522fe-119">Specyfikacja alias jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="522fe-119">The alias specification is optional.</span></span> <span data-ttu-id="522fe-120">Alternatywne specyfikacji powyższe z elementu klauzuli może być następująca:</span><span class="sxs-lookup"><span data-stu-id="522fe-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="522fe-121">Jeśli jest określony żaden alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prób wygenerowania alias oparte na wyrażeniu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="522fe-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="522fe-122">Dołączanie z klauzuli elementu</span><span class="sxs-lookup"><span data-stu-id="522fe-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="522fe-123">A `JOIN FROM` element klauzuli reprezentuje sprzężenia między dwiema `FROM` klauzuli elementów.</span><span class="sxs-lookup"><span data-stu-id="522fe-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="522fe-124"> Obsługa wielu sprzężeń, sprzężenia wewnętrzne po lewej stronie i prawe sprzężenia zewnętrzne i pełne sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="522fe-124"> supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="522fe-125">Wszystkie te sprzężeń są obsługiwane w podobny sposób, że są one obsługiwane w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="522fe-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="522fe-126">Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], dwa `FROM` klauzuli elementy objęte `JOIN` musi być niezależna.</span><span class="sxs-lookup"><span data-stu-id="522fe-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="522fe-127">Oznacza to, że nie zostanie skorelowana.</span><span class="sxs-lookup"><span data-stu-id="522fe-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="522fe-128">A `CROSS APPLY` lub `OUTER APPLY` może służyć do tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="522fe-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="522fe-129">Sprzężenia krzyżowe</span><span class="sxs-lookup"><span data-stu-id="522fe-129">Cross Joins</span></span>  
 <span data-ttu-id="522fe-130">A `CROSS JOIN` zapytania wyrażenie zwraca iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="522fe-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="522fe-131">Sprzężenia wewnętrzne</span><span class="sxs-lookup"><span data-stu-id="522fe-131">Inner Joins</span></span>  
 <span data-ttu-id="522fe-132">`INNER JOIN` Tworzy ograniczonego iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="522fe-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="522fe-133">Każdy element kolekcji po lewej stronie łączyć się z każdym elementem kolekcji w prawo, gdzie kombinacji przetwarza poprzedniego wyrażenia zapytania `ON` warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="522fe-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="522fe-134">Jeśli nie `ON` jest określony warunek, `INNER JOIN` jest degenerowana do `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="522fe-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="522fe-135">Lewe sprzężenia zewnętrzne i prawe sprzężenia zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="522fe-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="522fe-136">`OUTER JOIN` Zapytania wyrażenie zwraca iloczyn kartezjański ograniczonego dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="522fe-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="522fe-137">Każdy element kolekcji po lewej stronie łączyć się z każdym elementem kolekcji w prawo, gdzie kombinacji przetwarza poprzedniego wyrażenia zapytania `ON` warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="522fe-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="522fe-138">Jeśli `ON` jest spełniony warunek, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie łączyć się względem elementu po prawej stronie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="522fe-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="522fe-139">A `RIGHT OUTER JOIN` mogą być sformułowane w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="522fe-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="522fe-140">Tworzy sprzężenie zewnętrzne pełne</span><span class="sxs-lookup"><span data-stu-id="522fe-140">Full Outer Joins</span></span>  
 <span data-ttu-id="522fe-141">Jawne `FULL OUTER JOIN` tworzy ograniczonego iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="522fe-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="522fe-142">Każdy element kolekcji po lewej stronie łączyć się z każdym elementem kolekcji w prawo, gdzie kombinacji przetwarza poprzedniego wyrażenia zapytania `ON` warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="522fe-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="522fe-143">Jeśli `ON` jest spełniony warunek, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie łączyć się względem elementu po prawej stronie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="522fe-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="522fe-144">Przetwarza jedno wystąpienie elementu po prawej stronie łączyć się względem elementu po lewej stronie z wartość null.</span><span class="sxs-lookup"><span data-stu-id="522fe-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="522fe-145">W celu zachowania zgodności z SQL 92, w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] zewnętrzne — słowo kluczowe jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="522fe-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="522fe-146">W związku z tym `LEFT JOIN`, `RIGHT JOIN`, i `FULL JOIN` są synonimy `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, i `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="522fe-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="522fe-147">Zastosuj element klauzuli</span><span class="sxs-lookup"><span data-stu-id="522fe-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="522fe-148"> obsługuje dwa rodzaje z `APPLY`: `CROSS APPLY` i `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="522fe-148"> supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="522fe-149">A `CROSS APPLY` tworzy unikatowy parowanie każdego elementu w kolekcji po lewej stronie z elementem kolekcji utworzonej przez obliczenie wyrażenia po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="522fe-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="522fe-150">Z `CROSS APPLY`, wyrażenie po prawej stronie jest funkcjonalnie zależny od elementu po lewej stronie, jak pokazano w poniższym przykładzie skojarzonej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="522fe-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="522fe-151">Zachowanie `CROSS APPLY` jest podobna do listy sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="522fe-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="522fe-152">Jeśli po prawej stronie wyrażenie ma pustą kolekcję, `CROSS APPLY` tworzy nie skojarzenie tego wystąpienia elementu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="522fe-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="522fe-153">`OUTER APPLY` Podobny `CROSS APPLY`, z wyjątkiem sparowania nadal jest generowany nawet wtedy, gdy po prawej stronie wyrażenie ma pustą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="522fe-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="522fe-154">Poniżej przedstawiono przykład `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="522fe-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="522fe-155">W odróżnieniu od w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], nie istnieje potrzeba jawnego unnest kroku w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="522fe-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="522fe-156">`CROSS` i `OUTER APPLY` operatory zostały wprowadzone w systemie [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="522fe-156">`CROSS` and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="522fe-157">W niektórych przypadkach potoku zapytanie może wygenerować języka Transact-SQL, który zawiera `CROSS APPLY` i/lub `OUTER APPLY` operatorów.</span><span class="sxs-lookup"><span data-stu-id="522fe-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="522fe-158">Ponieważ niektórzy dostawcy wewnętrznej bazy danych, w tym wersje programu SQL Server starszych niż [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nie obsługują tych operatorów, przetwarzanie takich zapytań nie można wykonać na tych dostawców wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="522fe-158">Because some backend providers, including versions of SQL Server earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="522fe-159">Niektóre typowe scenariusze, które mogą prowadzić do obecności `CROSS APPLY` i/lub `OUTER APPLY` operatory w zapytaniu dane wyjściowe są następujące: podzapytania skorelowane z stronicowania; AnyElement w podzapytaniu skorelowane lub za pośrednictwem kolekcji utworzonej przez nawigacji; Używające grupowanie metod, które akceptują selektorem elementu; zapytań LINQ zapytanie, w którym `CROSS APPLY` lub `OUTER APPLY` zostały jawnie określone; kwerendę, która ma `DEREF` skonstruować za pośrednictwem `REF` utworzenia.</span><span class="sxs-lookup"><span data-stu-id="522fe-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="522fe-160">Wiele kolekcji w polu od klauzuli</span><span class="sxs-lookup"><span data-stu-id="522fe-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="522fe-161">`FROM` Klauzula może zawierać więcej niż jednej kolekcji, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="522fe-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="522fe-162">W takich przypadkach kolekcje uznaje, że mają zostać połączone ze sobą.</span><span class="sxs-lookup"><span data-stu-id="522fe-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="522fe-163">Potraktować je jako n sposób sprzężenia KRZYŻOWEGO.</span><span class="sxs-lookup"><span data-stu-id="522fe-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="522fe-164">W poniższym przykładzie `C` i `D` są niezależne kolekcji, ale `c.Names` jest zależna od `C`.</span><span class="sxs-lookup"><span data-stu-id="522fe-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="522fe-165">Poprzedni przykład logicznie odpowiada do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="522fe-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="522fe-166">Lewa korelacja</span><span class="sxs-lookup"><span data-stu-id="522fe-166">Left Correlation</span></span>  
 <span data-ttu-id="522fe-167">Elementy w `FROM` klauzuli mogą odwoływać się do określonych w klauzulach starszych elementów.</span><span class="sxs-lookup"><span data-stu-id="522fe-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="522fe-168">W poniższym przykładzie `C` i `D` są niezależne kolekcji, ale `c.Names` jest zależna od `C`:</span><span class="sxs-lookup"><span data-stu-id="522fe-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="522fe-169">Jest to równoważne logicznie:</span><span class="sxs-lookup"><span data-stu-id="522fe-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="522fe-170">Semantyka</span><span class="sxs-lookup"><span data-stu-id="522fe-170">Semantics</span></span>  
 <span data-ttu-id="522fe-171">Logicznie, kolekcje w `FROM` klauzuli będą traktowani jako część `n`-sprzężenia krzyżowego sposób (z wyjątkiem w przypadku 1-sposób sprzężenie krzyżowe).</span><span class="sxs-lookup"><span data-stu-id="522fe-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="522fe-172">Aliasy w `FROM` klauzul są przetwarzane po lewej do prawej i są dodawane do bieżącego zakresu do wykorzystania w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="522fe-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="522fe-173">`FROM` Przyjęto, że klauzula utworzyć zestaw wielokrotny wierszy.</span><span class="sxs-lookup"><span data-stu-id="522fe-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="522fe-174">Będzie jedno pole dla każdego elementu w `FROM` klauzuli, która reprezentuje jeden element z elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="522fe-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="522fe-175">`FROM` Klauzuli logicznie tworzy zestaw wielokrotny, który wiersze typu wiersza (c, d, e) gdzie pól c, d i e są rozpatrywane typu elementu `C`, `D`, i `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="522fe-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="522fe-176"> wprowadzono alias dla każdego prosty `FROM` element klauzuli w zakresie.</span><span class="sxs-lookup"><span data-stu-id="522fe-176"> introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="522fe-177">Na przykład poniższa z klauzuli fragment nazwy wprowadzane do zakresu są c, d i e.</span><span class="sxs-lookup"><span data-stu-id="522fe-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="522fe-178">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (w przeciwieństwie do [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` klauzuli wprowadza tylko aliasów do zakresu.</span><span class="sxs-lookup"><span data-stu-id="522fe-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="522fe-179">Wszystkie odwołania do tych kolekcji kolumn (właściwości) musi być kwalifikowana za alias.</span><span class="sxs-lookup"><span data-stu-id="522fe-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="522fe-180">Ściąganie zapasową kluczy z zapytania zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="522fe-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="522fe-181">Niektóre rodzaje zapytania wymagające ściąganie zapasową kluczy z zapytanie zagnieżdżone nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="522fe-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="522fe-182">Na przykład następujące kwerendy jest nieprawidłowa:</span><span class="sxs-lookup"><span data-stu-id="522fe-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="522fe-183">Jednak poniższe zapytanie jest nieprawidłowe, ponieważ zapytanie zagnieżdżone nie ma żadnych kluczy:</span><span class="sxs-lookup"><span data-stu-id="522fe-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="522fe-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="522fe-184">See Also</span></span>  
 [<span data-ttu-id="522fe-185">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="522fe-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="522fe-186">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="522fe-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="522fe-187">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="522fe-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
