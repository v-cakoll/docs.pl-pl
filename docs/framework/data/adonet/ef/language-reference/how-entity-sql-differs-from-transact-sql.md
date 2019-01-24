---
title: Jak jednostka SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: f193a3f7441a8bf7efacf07d8a9eb18362d7f91d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635965"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="3a801-102">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3a801-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="3a801-103">W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a801-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="3a801-104">Dziedziczenie i relacje obsługi</span><span class="sxs-lookup"><span data-stu-id="3a801-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-105">współpracuje bezpośrednio ze schematami koncepcyjnymi encji i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.</span><span class="sxs-lookup"><span data-stu-id="3a801-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="3a801-106">Podczas pracy z dziedziczenia, często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu.</span><span class="sxs-lookup"><span data-stu-id="3a801-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="3a801-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobnie jak `oftype` w C# sekwencje) zapewnia tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="3a801-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="3a801-108">Obsługa kolekcji</span><span class="sxs-lookup"><span data-stu-id="3a801-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-109">traktuje kolekcji jako obiekty najwyższej jakości.</span><span class="sxs-lookup"><span data-stu-id="3a801-109">treats collections as first-class entities.</span></span> <span data-ttu-id="3a801-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3a801-110">For example:</span></span>  
  
-   <span data-ttu-id="3a801-111">Wyrażenia kolekcji są prawidłowe w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a801-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="3a801-112">`in` i `exists` podzapytań mają został uogólniony, aby zezwolić na wszystkie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="3a801-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="3a801-113">Podzapytania jest jeden rodzaj kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3a801-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="3a801-114">`e1 in e2` i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji wykonywać te operacje.</span><span class="sxs-lookup"><span data-stu-id="3a801-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="3a801-115">Ustawić operacje, takie jak `union`, `intersect`, i `except`, teraz działają w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="3a801-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="3a801-116">Sprzężenia działają w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="3a801-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="3a801-117">Obsługa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3a801-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="3a801-118">ma podzapytań (tabele) i wyrażenia (wiersze i kolumny).</span><span class="sxs-lookup"><span data-stu-id="3a801-118">has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="3a801-119">Do obsługi kolekcji i kolekcje zagnieżdżone [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawia, że wszystkie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3a801-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-120">jest bardziej konfigurowalna niż [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— każde wyrażenie może być używane w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="3a801-120">is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="3a801-121">Zapytanie wyrażenia zawsze powoduje kolekcji typów przewidywanych i mogą być używane wszędzie, gdzie jest dozwolona w wyrażeniu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3a801-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="3a801-122">Aby uzyskać informacje o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3a801-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3a801-123">Poniżej znajdują się wszystkie prawidłowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:</span><span class="sxs-lookup"><span data-stu-id="3a801-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="3a801-124">Jednolitego traktowania podzapytań</span><span class="sxs-lookup"><span data-stu-id="3a801-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="3a801-125">Biorąc pod uwagę jej nacisk na tabele, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wykonuje kontekstowych interpretacji podzapytania.</span><span class="sxs-lookup"><span data-stu-id="3a801-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="3a801-126">Na przykład podzapytania w `from` klauzula jest uważany za multiset (tabela).</span><span class="sxs-lookup"><span data-stu-id="3a801-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="3a801-127">Ale ten sam podzapytanie używane w `select` klauzula jest uważany za skalarne podzapytania.</span><span class="sxs-lookup"><span data-stu-id="3a801-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="3a801-128">Podobnie, podzapytania używane w lewej części `in` operator jest uważany za podzapytania skalarne, a po prawej stronie powinien być multiset — podzapytanie.</span><span class="sxs-lookup"><span data-stu-id="3a801-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-129">eliminuje te różnice.</span><span class="sxs-lookup"><span data-stu-id="3a801-129">eliminates these differences.</span></span> <span data-ttu-id="3a801-130">Wyrażenie zawiera jednolitej interpretacji, które nie są zależne od kontekstu, w którym jest używany.</span><span class="sxs-lookup"><span data-stu-id="3a801-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-131">uwzględnia wszystkich podzapytaniach to zestaw wielokrotny podzapytania.</span><span class="sxs-lookup"><span data-stu-id="3a801-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="3a801-132">Jeśli wartość skalarną z podzapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia `anyelement` operator, który działa w kolekcji (w tym przypadku podzapytanie) i wyodrębnia wartości pojedynczego wystąpienia z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3a801-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="3a801-133">Unikanie niejawne Coercions dla podzapytań</span><span class="sxs-lookup"><span data-stu-id="3a801-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="3a801-134">Powiązane efekt uboczny jednolitego traktowania podzapytań jest niejawnej konwersji wartości podzapytań wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="3a801-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="3a801-135">W szczególności w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multiset wierszy (z jednym polem) jest niejawnie konwertowana na wartość skalarną, której typem danych jest to, że pola.</span><span class="sxs-lookup"><span data-stu-id="3a801-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-136">nie obsługuje tego niejawne przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="3a801-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-137">zawiera operator ANYELEMENT do wyodrębnienia pojedyncze wartości z kolekcji, a `select value` klauzulę, aby uniknąć tworzenia otoki wiersza w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="3a801-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="3a801-138">Wybierz wartość: Unikanie otoki niejawne wiersza</span><span class="sxs-lookup"><span data-stu-id="3a801-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="3a801-139">Klauzuli select w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] podzapytania niejawnie tworzy otokę wierszy elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a801-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="3a801-140">Oznacza to, że nie można utworzyć kolekcji wartości skalarnych lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="3a801-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="3a801-141">zezwala na niejawne wymuszenia między rowtype z jednym polem i wartości pojedynczego wystąpienia typu danych.</span><span class="sxs-lookup"><span data-stu-id="3a801-141">allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-142">udostępnia `select value` klauzuli, aby pominąć konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="3a801-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="3a801-143">Można określić tylko jeden element w `select value` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a801-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="3a801-144">W przypadku takich klauzuli nie otoki wiersza została zbudowana w oparciu elementów w `select` klauzuli i kolekcji żądany kształt mogą powstać, na przykład: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="3a801-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-145">zapewnia także Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="3a801-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="3a801-146">`select` przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych przy użyciu pól, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3a801-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="3a801-147">Lewa Korelacja i aliasów</span><span class="sxs-lookup"><span data-stu-id="3a801-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="3a801-148">W [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], wyrażenia w danym zakresie (takie jak pojedyncza klauzula `select` lub `from`) nie może odwoływać się do wyrażenia zdefiniowany wcześniej w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="3a801-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="3a801-149">Niektóre dialekty programu SQL Server (w tym [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) obsługuje ograniczone formy w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a801-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-150">stanowi uogólnienie korelacji po lewej stronie w `from` klauzuli i traktować je równomiernie.</span><span class="sxs-lookup"><span data-stu-id="3a801-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="3a801-151">Wyrażenia w `from` klauzuli może odwoływać się definicje wcześniejsze (definicje po lewej stronie) w tej samej klauzuli bez konieczności stosowania dodatkowej składni.</span><span class="sxs-lookup"><span data-stu-id="3a801-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-152">również nakłada dodatkowe ograniczenia dotyczące zapytania obejmujące `group by` klauzul.</span><span class="sxs-lookup"><span data-stu-id="3a801-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="3a801-153">Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań może odwoływać się tylko do `group by` kluczy przy użyciu ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="3a801-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="3a801-154">Następująca konstrukcja jest prawidłowy w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nie znajdują się w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3a801-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="3a801-155">Aby to zrobić w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3a801-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="3a801-156">Odwoływanie się do kolumn (właściwości) tabel (kolekcji)</span><span class="sxs-lookup"><span data-stu-id="3a801-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="3a801-157">Wszystkie odwołania do kolumn w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być kwalifikowana za pomocą aliasu tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a801-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="3a801-158">Następująca konstrukcja (przy założeniu, że `a` jest prawidłową kolumną tabeli `T`) jest prawidłowa w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a801-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="3a801-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formularz</span><span class="sxs-lookup"><span data-stu-id="3a801-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="3a801-160">Aliasy tabeli są opcjonalne w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a801-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="3a801-161">Nazwa tabeli jest używany jako alias niejawne.</span><span class="sxs-lookup"><span data-stu-id="3a801-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-162">Umożliwia także następującą postać:</span><span class="sxs-lookup"><span data-stu-id="3a801-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="3a801-163">Nawigacja za pośrednictwem obiektów</span><span class="sxs-lookup"><span data-stu-id="3a801-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="3a801-164">używa "." Notacja do odwoływania się do kolumn (wiersz) tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a801-164">uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-165">Rozszerza ten zapis (pobierają z języków programowania) do obsługi nawigacji za pomocą właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a801-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="3a801-166">Na przykład jeśli `p` wyrażenia wpisz osobę, Oto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni do odwoływania się do miasta adres tej osoby.</span><span class="sxs-lookup"><span data-stu-id="3a801-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="3a801-167">Brak obsługi \*</span><span class="sxs-lookup"><span data-stu-id="3a801-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="3a801-168">obsługuje niekwalifikowanej \* składni jako alias dla całego wiersza i kwalifikowaną \* składni (t.\*) jako skrót dla pól tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a801-168">supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="3a801-169">Ponadto [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umożliwia specjalnych licznik (\*) wartość zagregowaną, która zawiera wartości null.</span><span class="sxs-lookup"><span data-stu-id="3a801-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-170">nie obsługuje \* konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="3a801-170">does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="3a801-171">zapytania w postaci `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3a801-171">queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="3a801-172">Ponadto te konstrukcje obsługi dziedziczenia (wartość podaży), podczas gdy `select *` wariantów są ograniczone do najwyższego poziomu właściwości zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="3a801-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-173">nie obsługuje `count(*)` agregacji.</span><span class="sxs-lookup"><span data-stu-id="3a801-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="3a801-174">Zamiast nich należy używać słów kluczowych `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="3a801-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="3a801-175">Zmiany Grupuj według</span><span class="sxs-lookup"><span data-stu-id="3a801-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-176">obsługuje tworzenie aliasów dla `group by` kluczy.</span><span class="sxs-lookup"><span data-stu-id="3a801-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="3a801-177">Wyrażenia w `select` klauzuli i `having` klauzuli musi odwoływać się do `group by` kluczy przy użyciu te aliasy.</span><span class="sxs-lookup"><span data-stu-id="3a801-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="3a801-178">Na przykład, to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni:</span><span class="sxs-lookup"><span data-stu-id="3a801-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="3a801-179">.. jest standardem odpowiednikiem następujące [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3a801-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="3a801-180">Wartości zagregowane z kolekcji</span><span class="sxs-lookup"><span data-stu-id="3a801-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-181">obsługuje dwa rodzaje wartości zagregowanych.</span><span class="sxs-lookup"><span data-stu-id="3a801-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="3a801-182">Agregacje związanych z kolekcjami działają w kolekcjach i tworzące zagregowany wynik.</span><span class="sxs-lookup"><span data-stu-id="3a801-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="3a801-183">Te mogą występować w dowolnym miejscu w zapytaniu i nie wymagają `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a801-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="3a801-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3a801-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-185">obsługuje również wartości zagregowanych SQL stylu.</span><span class="sxs-lookup"><span data-stu-id="3a801-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="3a801-186">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3a801-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="3a801-187">KOLEJNOŚĆ według użycia klauzuli</span><span class="sxs-lookup"><span data-stu-id="3a801-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="3a801-188">zezwala na klauzule w klauzuli ORDER BY, należy określić tylko w najwyższej wybierz...</span><span class="sxs-lookup"><span data-stu-id="3a801-188">allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="3a801-189">OD...</span><span class="sxs-lookup"><span data-stu-id="3a801-189">FROM ..</span></span> <span data-ttu-id="3a801-190">GDZIE zablokować.</span><span class="sxs-lookup"><span data-stu-id="3a801-190">WHERE block.</span></span> <span data-ttu-id="3a801-191">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można używać zagnieżdżonych wyrażeń klauzuli ORDER BY i można je umieścić w dowolnym miejscu w zapytaniu, ale szeregowaniem w zapytaniu zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="3a801-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="3a801-192">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="3a801-192">Identifiers</span></span>  
 <span data-ttu-id="3a801-193">W [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], porównanie identyfikatorów opiera się na sortowania bieżącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3a801-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="3a801-194">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identyfikatory są zawsze bez uwzględniania wielkości liter i akcent poufnych (czyli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozróżnia znaki akcentowane i nieakcentowane; na przykład, "" nie jest równa "ấ").</span><span class="sxs-lookup"><span data-stu-id="3a801-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-195">traktuje wersji liter, są wyświetlane takie same, które pochodzą z różne strony kodowe jako różne znaki.</span><span class="sxs-lookup"><span data-stu-id="3a801-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="3a801-196">Aby uzyskać więcej informacji, zobacz [zestaw znaków danych wejściowych](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3a801-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="3a801-197">Funkcje języka Transact-SQL nie jest dostępna w jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3a801-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="3a801-198">Następujące [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] funkcja nie jest dostępna w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a801-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="3a801-199">DML</span><span class="sxs-lookup"><span data-stu-id="3a801-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-200">obecnie nie obsługuje instrukcji DML (Wstawianie, aktualizowanie i usuwanie).</span><span class="sxs-lookup"><span data-stu-id="3a801-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="3a801-201">DDL</span><span class="sxs-lookup"><span data-stu-id="3a801-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-202">nie obsługuje języka DDL w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="3a801-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="3a801-203">Programowanie imperatywne</span><span class="sxs-lookup"><span data-stu-id="3a801-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-204">nie obsługuje programowanie imperatywne, w odróżnieniu od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a801-204">provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3a801-205">Zamiast tego użyj języka programowania.</span><span class="sxs-lookup"><span data-stu-id="3a801-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="3a801-206">Funkcje grupowania</span><span class="sxs-lookup"><span data-stu-id="3a801-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-207">nie jeszcze zapewniają obsługę grupowanie funkcji (na przykład moduł, pakiet ZBIORCZY i GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="3a801-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="3a801-208">Funkcje analityczne</span><span class="sxs-lookup"><span data-stu-id="3a801-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-209">nie (jeszcze) zapewnia obsługę funkcji analitycznych.</span><span class="sxs-lookup"><span data-stu-id="3a801-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="3a801-210">Funkcje wbudowane, operatory</span><span class="sxs-lookup"><span data-stu-id="3a801-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-211">obsługuje podzbiór [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]wbudowanego w funkcje i operatory.</span><span class="sxs-lookup"><span data-stu-id="3a801-211">supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="3a801-212">Te operatory i funkcje mogą być obsługiwane przez dostawców magazynu głównych.</span><span class="sxs-lookup"><span data-stu-id="3a801-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-213">korzysta z funkcji specyficznych dla magazynu zadeklarowane w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="3a801-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="3a801-214">Ponadto [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umożliwia deklarację wbudowanych oraz istniejącego użytkownika przechowywane funkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do użycia.</span><span class="sxs-lookup"><span data-stu-id="3a801-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="3a801-215">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="3a801-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-216">nie zapewnia mechanizmy wskazówki zapytania.</span><span class="sxs-lookup"><span data-stu-id="3a801-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="3a801-217">Przetwarzanie wsadowe wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="3a801-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-218">nie obsługuje przetwarzania wsadowego wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="3a801-218">does not support batching query results.</span></span> <span data-ttu-id="3a801-219">Na przykład poniżej przedstawiono prawidłowe [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (wysyłającym jako zadania wsadowego):</span><span class="sxs-lookup"><span data-stu-id="3a801-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="3a801-220">Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwane:</span><span class="sxs-lookup"><span data-stu-id="3a801-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3a801-221">obsługuje tylko jedną instrukcję zapytania zwracające wyniki dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3a801-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a801-222">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a801-222">See also</span></span>
- [<span data-ttu-id="3a801-223">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3a801-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="3a801-224">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="3a801-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
