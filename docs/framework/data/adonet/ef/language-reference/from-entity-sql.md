---
title: OD (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 3cc02b4c51b32d0faace4d89d0c6c1f6923dd138
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119837"
---
# <a name="from-entity-sql"></a><span data-ttu-id="39ad0-102">OD (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="39ad0-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="39ad0-103">Określa kolekcję używane w [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="39ad0-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ad0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39ad0-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="39ad0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="39ad0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="39ad0-106">Dowolne wyrażenie prawidłowe zapytanie, które daje kolekcję do użycia jako źródło w `SELECT` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="39ad0-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39ad0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39ad0-107">Remarks</span></span>  
 <span data-ttu-id="39ad0-108">A `FROM` klauzula jest rozdzielaną przecinkami listę co najmniej jeden `FROM` elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="39ad0-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="39ad0-109">`FROM` Klauzuli może służyć do określania jednego lub kilku źródeł dla `SELECT` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="39ad0-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="39ad0-110">Najprostsza forma `FROM` klauzula jest wyrażenie jednego zapytania, które identyfikuje kolekcję i alias używany jako źródło w `SELECT` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39ad0-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="39ad0-111">Z elementów — klauzula</span><span class="sxs-lookup"><span data-stu-id="39ad0-111">FROM Clause Items</span></span>  
 <span data-ttu-id="39ad0-112">Każdy `FROM` element klauzuli odwołuje się do kolekcji źródłowej, w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="39ad0-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="39ad0-113">obsługuje następujące klasy `FROM` elementy klauzuli: proste `FROM` elementy klauzuli `JOIN FROM` elementy klauzuli i `APPLY FROM` elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="39ad0-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="39ad0-114">Każda z tych `FROM` elementy klauzula jest opisany bardziej szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="39ad0-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="39ad0-115">Prosty element klauzuli FROM</span><span class="sxs-lookup"><span data-stu-id="39ad0-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="39ad0-116">Najprostsze `FROM` element klauzuli jest pojedyncze wyrażenie określające kolekcji i alias.</span><span class="sxs-lookup"><span data-stu-id="39ad0-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="39ad0-117">Wyrażenie można po prostu zestaw jednostek lub podzapytania lub innego wyrażenia, który jest typem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="39ad0-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="39ad0-118">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="39ad0-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="39ad0-119">Specyfikacja aliasu jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="39ad0-119">The alias specification is optional.</span></span> <span data-ttu-id="39ad0-120">Alternatywne specyfikacji powyżej element klauzuli from może być następująca:</span><span class="sxs-lookup"><span data-stu-id="39ad0-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="39ad0-121">Jeśli brak aliasu jest określony, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje go wygenerować alias oparte na wyrażeniu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="39ad0-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="39ad0-122">Dołącz element klauzuli FROM</span><span class="sxs-lookup"><span data-stu-id="39ad0-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="39ad0-123">A `JOIN FROM` element klauzuli reprezentuje sprzężenia między dwoma `FROM` elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="39ad0-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="39ad0-124">Obsługa wielu sprzężeń wewnętrznych, po lewej stronie i prawe sprzężenia zewnętrzne, filtrami czasowymi i klauzule full outer JOIN.</span><span class="sxs-lookup"><span data-stu-id="39ad0-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="39ad0-125">Wszystkie te sprzężeń są obsługiwane w podobny sposób, że są one obsługiwane w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="39ad0-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="39ad0-126">Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], dwa `FROM` klauzuli elementy zaangażowany w `JOIN` muszą być niezależne.</span><span class="sxs-lookup"><span data-stu-id="39ad0-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="39ad0-127">Oznacza to nie może zostać skorelowane.</span><span class="sxs-lookup"><span data-stu-id="39ad0-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="39ad0-128">A `CROSS APPLY` lub `OUTER APPLY` może służyć w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="39ad0-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="39ad0-129">Sprzężenia krzyżowe</span><span class="sxs-lookup"><span data-stu-id="39ad0-129">Cross Joins</span></span>  
 <span data-ttu-id="39ad0-130">A `CROSS JOIN` zapytania wyrażenie powoduje formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39ad0-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="39ad0-131">Sprzężenia wewnętrzne</span><span class="sxs-lookup"><span data-stu-id="39ad0-131">Inner Joins</span></span>  
 <span data-ttu-id="39ad0-132">`INNER JOIN` Tworzy ograniczone formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39ad0-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="39ad0-133">Poprzednie wyrażenie zapytania przetwarza kombinacji każdy element kolekcji po lewej stronie porównywane każdy element kolekcji o tym, gdzie po prawej stronie `ON` warunek jest prawdziwy.</span><span class="sxs-lookup"><span data-stu-id="39ad0-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="39ad0-134">Jeśli nie `ON` jest określony warunek, `INNER JOIN` jest degenerowana do `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="39ad0-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="39ad0-135">LEFT lewych sprzężeń zewnętrznych i prawe sprzężenia zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="39ad0-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="39ad0-136">`OUTER JOIN` Zapytania wyrażenie powoduje ograniczone formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39ad0-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="39ad0-137">Poprzednie wyrażenie zapytania przetwarza kombinacji każdy element kolekcji po lewej stronie porównywane każdy element kolekcji o tym, gdzie po prawej stronie `ON` warunek jest prawdziwy.</span><span class="sxs-lookup"><span data-stu-id="39ad0-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="39ad0-138">Jeśli `ON` warunek jest fałszywy, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie porównywane elementu po prawej stronie przy użyciu wartość null.</span><span class="sxs-lookup"><span data-stu-id="39ad0-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="39ad0-139">A `RIGHT OUTER JOIN` mogą być wyrażone w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="39ad0-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="39ad0-140">Sprzężenia pełne zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="39ad0-140">Full Outer Joins</span></span>  
 <span data-ttu-id="39ad0-141">Jawnie `FULL OUTER JOIN` tworzy ograniczone formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39ad0-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="39ad0-142">Poprzednie wyrażenie zapytania przetwarza kombinacji każdy element kolekcji po lewej stronie porównywane każdy element kolekcji o tym, gdzie po prawej stronie `ON` warunek jest prawdziwy.</span><span class="sxs-lookup"><span data-stu-id="39ad0-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="39ad0-143">Jeśli `ON` warunek jest fałszywy, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie porównywane elementu po prawej stronie przy użyciu wartość null.</span><span class="sxs-lookup"><span data-stu-id="39ad0-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="39ad0-144">Przetwarza jedno wystąpienie elementu po prawej stronie porównywane elementu po lewej stronie, za pomocą wartość null.</span><span class="sxs-lookup"><span data-stu-id="39ad0-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39ad0-145">W celu zachowania zgodności z SQL-92 w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] zewnętrzne — słowo kluczowe jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="39ad0-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="39ad0-146">W związku z tym `LEFT JOIN`, `RIGHT JOIN`, i `FULL JOIN` są synonimy `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, i `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="39ad0-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="39ad0-147">Zastosuj element klauzuli</span><span class="sxs-lookup"><span data-stu-id="39ad0-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="39ad0-148">obsługuje dwa rodzaje z `APPLY`: `CROSS APPLY` i `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="39ad0-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="39ad0-149">A `CROSS APPLY` generuje unikatowy parowanie każdego elementu kolekcji po lewej stronie, z elementem kolekcji utworzone przez obliczenie wyrażenia po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="39ad0-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="39ad0-150">Za pomocą `CROSS APPLY`, wyrażenie po prawej stronie jest funkcjonalnie zależny od elementu po lewej stronie, jak pokazano w poniższym przykładzie skojarzonej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="39ad0-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="39ad0-151">Zachowanie `CROSS APPLY` jest podobna do listy dołączania.</span><span class="sxs-lookup"><span data-stu-id="39ad0-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="39ad0-152">Jeśli po prawej stronie wyrażenie ma pustą kolekcję, `CROSS APPLY` tworzy nie skojarzenie tego wystąpienia elementu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="39ad0-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="39ad0-153">`OUTER APPLY` Przypomina `CROSS APPLY`, z wyjątkiem parowanie nadal jest generowany, nawet wtedy, gdy po prawej stronie wyrażenie ma pustą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="39ad0-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="39ad0-154">Oto przykład `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="39ad0-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="39ad0-155">W odróżnieniu od w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], nie istnieje potrzeba jawnego unnest etapem [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="39ad0-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39ad0-156">`CROSS` i `OUTER APPLY` operatory zostały wprowadzone w [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="39ad0-156">`CROSS` and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="39ad0-157">W niektórych przypadkach potoku zapytania może powodować generowanie języka Transact-SQL, który zawiera `CROSS APPLY` i/lub `OUTER APPLY` operatorów.</span><span class="sxs-lookup"><span data-stu-id="39ad0-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="39ad0-158">Ponieważ niektórzy dostawcy wewnętrznej bazy danych, w tym wersje programu SQL Server starszych niż [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nie obsługuje tych operatorów, takich zapytań nie można wykonać na tych dostawców wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="39ad0-158">Because some backend providers, including versions of SQL Server earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="39ad0-159">Niektóre typowe scenariusze, które mogą prowadzić do występowania `CROSS APPLY` i/lub `OUTER APPLY` operatory w zapytaniu dane wyjściowe są następujące: skorelowane podzapytanie za pomocą stronicowania; AnyElement za pośrednictwem skorelowane podzapytanie lub kolekcję produkowane przez nawigacji; LINQ zapytania używające grupowanie metod, które akceptują selektor elementu; zapytanie, w którym `CROSS APPLY` lub `OUTER APPLY` są jawnie określone, zapytania, które zawiera `DEREF` skonstruować za pośrednictwem `REF` konstruowania.</span><span class="sxs-lookup"><span data-stu-id="39ad0-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="39ad0-160">Wieloma kolekcjami w FROM — klauzula</span><span class="sxs-lookup"><span data-stu-id="39ad0-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="39ad0-161">`FROM` Klauzula może zawierać więcej niż jedną kolekcję, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="39ad0-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="39ad0-162">W takich przypadkach kolekcje są uznawane za mają zostać połączone ze sobą.</span><span class="sxs-lookup"><span data-stu-id="39ad0-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="39ad0-163">Należy traktować je jako sposób n sprzężenia KRZYŻOWEGO.</span><span class="sxs-lookup"><span data-stu-id="39ad0-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="39ad0-164">W poniższym przykładzie `C` i `D` są kolekcjami niezależne, ale `c.Names` jest zależny od `C`.</span><span class="sxs-lookup"><span data-stu-id="39ad0-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="39ad0-165">Poprzedni przykład jest logicznie równoważne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="39ad0-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="39ad0-166">Lewa korelacja</span><span class="sxs-lookup"><span data-stu-id="39ad0-166">Left Correlation</span></span>  
 <span data-ttu-id="39ad0-167">Elementy w `FROM` klauzuli mogą odwoływać się do elementów określone w klauzulach wcześniej.</span><span class="sxs-lookup"><span data-stu-id="39ad0-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="39ad0-168">W poniższym przykładzie `C` i `D` są kolekcjami niezależne, ale `c.Names` jest zależny od `C`:</span><span class="sxs-lookup"><span data-stu-id="39ad0-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="39ad0-169">To jest logicznie równoważne:</span><span class="sxs-lookup"><span data-stu-id="39ad0-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="39ad0-170">Semantyka</span><span class="sxs-lookup"><span data-stu-id="39ad0-170">Semantics</span></span>  
 <span data-ttu-id="39ad0-171">Logicznie kolekcji w `FROM` klauzuli będą traktowani jako część `n`— sprzężenie sposób krzyżowe (z wyjątkiem w przypadku 1-sposób cross join).</span><span class="sxs-lookup"><span data-stu-id="39ad0-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="39ad0-172">Aliasy w `FROM` klauzuli są przetwarzane od lewej do prawej i są dodawane do bieżącego zakresu do późniejszego wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="39ad0-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="39ad0-173">`FROM` Klauzuli założono, że generuje multiset wierszy.</span><span class="sxs-lookup"><span data-stu-id="39ad0-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="39ad0-174">Będzie istniało jedno pole dla każdego elementu w `FROM` klauzula, która reprezentuje pojedynczy element z tego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="39ad0-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="39ad0-175">`FROM` Klauzuli logicznie tworzy zestaw wielokrotny wiersze typu wiersza (c, d, e) gdzie pola c, d i e są rozpatrywane typu elementu `C`, `D`, i `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="39ad0-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="39ad0-176">wprowadzono alias dla każdego prostej `FROM` element klauzuli w zakresie.</span><span class="sxs-lookup"><span data-stu-id="39ad0-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="39ad0-177">Na przykład w następujących poleceń w klauzuli fragment, nazwy wprowadzone do zakresu są c, d i e.</span><span class="sxs-lookup"><span data-stu-id="39ad0-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="39ad0-178">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (w przeciwieństwie do [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` klauzuli tylko wprowadza aliasów do zakresu.</span><span class="sxs-lookup"><span data-stu-id="39ad0-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="39ad0-179">Wszystkie odwołania do tych kolekcji kolumn (właściwości) musi być kwalifikowana z aliasem.</span><span class="sxs-lookup"><span data-stu-id="39ad0-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="39ad0-180">Ściąganie klucze z zapytań zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="39ad0-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="39ad0-181">Niektórych rodzajów zapytań, które wymagają ściąganie klucze z zapytań zagnieżdżonej nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="39ad0-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="39ad0-182">Na przykład następujące zapytanie jest prawidłowy:</span><span class="sxs-lookup"><span data-stu-id="39ad0-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="39ad0-183">Jednakże następujące zapytanie jest nieprawidłowe, ponieważ zapytanie zagnieżdżone nie ma żadnych kluczy:</span><span class="sxs-lookup"><span data-stu-id="39ad0-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="39ad0-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39ad0-184">See also</span></span>

- [<span data-ttu-id="39ad0-185">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="39ad0-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="39ad0-186">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="39ad0-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="39ad0-187">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="39ad0-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
