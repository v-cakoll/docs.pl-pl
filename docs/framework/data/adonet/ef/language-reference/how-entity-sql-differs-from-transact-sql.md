---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615634"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="bc2cd-102">Jak Entity SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bc2cd-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="bc2cd-103">W tym artykule opisano różnice między Entity SQL i Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="bc2cd-104">Obsługa dziedziczenia i relacji</span><span class="sxs-lookup"><span data-stu-id="bc2cd-104">Inheritance and Relationships Support</span></span>  
 <span data-ttu-id="bc2cd-105">Entity SQL działa bezpośrednio ze schematami jednostki koncepcyjnej i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="bc2cd-106">Podczas pracy z dziedziczeniem często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="bc2cd-107">Ta możliwość zapewnia operator [OfType](oftype-entity-sql.md) w Entity SQL (podobnie jak `oftype` w sekwencjach C#).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="bc2cd-108">Obsługa kolekcji</span><span class="sxs-lookup"><span data-stu-id="bc2cd-108">Support for Collections</span></span>  
 <span data-ttu-id="bc2cd-109">Entity SQL traktuje kolekcje jako jednostki pierwszej klasy.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="bc2cd-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-110">For example:</span></span>  
  
- <span data-ttu-id="bc2cd-111">Wyrażenia kolekcji są prawidłowe w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="bc2cd-112">`in`i `exists` podzapytania zostały uogólnione w celu zezwolenia na jakiekolwiek kolekcje.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="bc2cd-113">Podzapytanie jest jednym rodzajem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="bc2cd-114">`e1 in e2`i `exists(e)` są konstrukcjami Entity SQL do wykonywania tych operacji.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="bc2cd-115">Ustaw operacje, takie jak `union` , `intersect` , i `except` teraz działają na kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="bc2cd-116">Sprzężenia działają na kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="bc2cd-117">Obsługa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="bc2cd-117">Support for Expressions</span></span>  
 <span data-ttu-id="bc2cd-118">Transact-SQL ma podzapytania (tabele) i wyrażenia (wiersze i kolumny).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="bc2cd-119">Aby zapewnić obsługę kolekcji i kolekcji zagnieżdżonych, Entity SQL wykonuje wszystkie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="bc2cd-120">Entity SQL jest większa niż Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="bc2cd-121">Wyrażenia zapytania zawsze powodują kolekcje typów rzutowanych i mogą być używane wszędzie tam, gdzie wyrażenie kolekcji jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="bc2cd-122">Aby uzyskać informacje o wyrażeniach języka Transact-SQL, które nie są obsługiwane w Entity SQL, zobacz [nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="bc2cd-123">Wszystkie prawidłowe kwerendy Entity SQL są następujące:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="bc2cd-124">Ujednolicone traktowanie podkwerend</span><span class="sxs-lookup"><span data-stu-id="bc2cd-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="bc2cd-125">Uwzględniając podkreślenie w tabelach, Transact-SQL wykonuje kontekstową interpretację podzapytań.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="bc2cd-126">Na przykład podzapytanie w `from` klauzuli jest uznawane za zestaw wielokrotny (tabelę).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="bc2cd-127">Ale to samo podzapytanie użyte w `select` klauzuli jest uznawane za podzapytanie skalarne.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="bc2cd-128">Podobnie podzapytanie użyte po lewej stronie `in` operatora jest uznawane za podzapytanie skalarne, podczas gdy po prawej stronie oczekiwana jest podzapytanie zestawu wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="bc2cd-129">Entity SQL eliminuje te różnice.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="bc2cd-130">Wyrażenie ma jednolitą interpretację, która nie zależy od kontekstu, w którym jest używana.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="bc2cd-131">Entity SQL traktuje wszystkie podzapytania jako podzapytania zestawu wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="bc2cd-132">Jeśli jest wymagana wartość skalarna z podzapytania, Entity SQL udostępnia `anyelement` operator, który działa w kolekcji (w tym przypadku podzapytania) i wyodrębnia wartość singleton z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="bc2cd-133">Unikanie niejawnych zarzutów dla podkwerend</span><span class="sxs-lookup"><span data-stu-id="bc2cd-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="bc2cd-134">Powiązane skutki uboczne jednolitego traktowania podzapytań są niejawną konwersją podzapytań na wartości skalarne.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="bc2cd-135">W języku Transact-SQL zestaw wielokrotny wierszy (z pojedynczym polem) jest niejawnie konwertowany na wartość skalarną, której typem danych jest pole.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="bc2cd-136">Entity SQL nie obsługuje tego niejawnego przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="bc2cd-137">Entity SQL zapewnia `ANYELEMENT` operatorowi wyodrębnienie wartości pojedynczej z kolekcji oraz `select value` klauzulę, aby uniknąć tworzenia otoki wiersza podczas wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="bc2cd-138">Wybierz wartość: unikanie niejawnej otoki wiersza</span><span class="sxs-lookup"><span data-stu-id="bc2cd-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="bc2cd-139">Klauzula SELECT w podzapytaniu Transact-SQL niejawnie tworzy otokę wiersza wokół elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="bc2cd-140">Oznacza to, że nie możemy utworzyć kolekcji skalarnych lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="bc2cd-141">Język Transact-SQL umożliwia niejawne przekształcenie między wartością `rowtype` z jednego pola a wartością singleton tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="bc2cd-142">Entity SQL udostępnia `select value` klauzulę do pomijania konstrukcji niejawnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="bc2cd-143">W klauzuli może być określony tylko jeden element `select value` .</span><span class="sxs-lookup"><span data-stu-id="bc2cd-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="bc2cd-144">Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w `select` klauzuli i można utworzyć kolekcję żądanego kształtu, na przykład `select value a` .</span><span class="sxs-lookup"><span data-stu-id="bc2cd-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="bc2cd-145">Entity SQL udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="bc2cd-146">`select`przyjmuje co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="bc2cd-147">Lewa korelacja i aliasowanie</span><span class="sxs-lookup"><span data-stu-id="bc2cd-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="bc2cd-148">W języku Transact-SQL wyrażenia w danym zakresie (pojedyncza klauzula LIKE `select` lub `from` ) nie mogą odwoływać się do wyrażeń zdefiniowanych wcześniej w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="bc2cd-149">Niektóre dialekty SQL (w tym Transact-SQL) obsługują ograniczone formy tych w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="bc2cd-150">Entity SQL uogólnia lewe korelacje w `from` klauzuli i traktuje je równomiernie.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="bc2cd-151">Wyrażenia w `from` klauzuli mogą odwoływać się do wcześniejszych definicji (definicje po lewej) w tej samej klauzuli bez potrzeby dodatkowej składni.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="bc2cd-152">Entity SQL również nakłada dodatkowe ograniczenia dotyczące zapytań obejmujących `group by` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="bc2cd-153">Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań mogą odwoływać się tylko do `group by` kluczy za pośrednictwem ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="bc2cd-154">Następująca konstrukcja jest prawidłowa w języku Transact-SQL, ale nie znajduje się w Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="bc2cd-155">W tym celu w Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="bc2cd-156">Odwoływanie się do kolumn (właściwości) tabel (Kolekcje)</span><span class="sxs-lookup"><span data-stu-id="bc2cd-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="bc2cd-157">Wszystkie odwołania do kolumn w Entity SQL muszą być kwalifikowane z aliasem tabeli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="bc2cd-158">Następująca konstrukcja (przy założeniu, że `a` jest to prawidłowa kolumna tabeli `T` ) jest prawidłowa w języku Transact-SQL, ale nie w Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="bc2cd-159">Formularz Entity SQL jest</span><span class="sxs-lookup"><span data-stu-id="bc2cd-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="bc2cd-160">Aliasy tabeli są opcjonalne w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="bc2cd-161">Nazwa tabeli jest używana jako alias niejawny.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="bc2cd-162">Entity SQL również zezwala na następujący formularz:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="bc2cd-163">Nawigacja za poorednictwem obiektów</span><span class="sxs-lookup"><span data-stu-id="bc2cd-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="bc2cd-164">Język Transact-SQL używa notacji "." w celu odwoływania się do kolumn (wierszy) tabeli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="bc2cd-165">Entity SQL rozszerza tę notację (zapożyczone z języków programowania) do obsługi nawigacji za pośrednictwem właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="bc2cd-166">Na przykład jeśli `p` jest wyrażeniem typu Person, poniżej przedstawiono składnię Entity SQL do odwoływania się do miasta adresu tej osoby.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="bc2cd-167">Brak obsługi dla\*</span><span class="sxs-lookup"><span data-stu-id="bc2cd-167">No Support for \*</span></span>  
 <span data-ttu-id="bc2cd-168">Język Transact-SQL obsługuje niekwalifikowaną \* składnię jako alias dla całego wiersza oraz kwalifikowaną \* składnią (t. \* ) jako skrót dla pól tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="bc2cd-169">Ponadto język Transact-SQL zezwala na \* agregację specjalna (), która zawiera wartości null.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="bc2cd-170">Entity SQL nie obsługuje konstrukcji \*.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="bc2cd-171">Zapytania Transact-SQL formularza `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w Entity SQL `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` odpowiednio i.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="bc2cd-172">Ponadto te konstrukcje obsługują dziedziczenie (podstawienie wartości), podczas gdy `select *` warianty są ograniczone do właściwości najwyższego poziomu zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="bc2cd-173">Entity SQL nie obsługuje `count(*)` agregacji.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="bc2cd-174">Zamiast tego użyj polecenia cmdlet `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="bc2cd-175">Zmiany w grupie według</span><span class="sxs-lookup"><span data-stu-id="bc2cd-175">Changes to Group By</span></span>  
 <span data-ttu-id="bc2cd-176">Entity SQL obsługuje aliasowanie `group by` kluczy.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="bc2cd-177">Wyrażenia w `select` klauzuli i `having` klauzuli muszą odwoływać się do `group by` kluczy za pośrednictwem tych aliasów.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="bc2cd-178">Na przykład następująca składnia Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="bc2cd-179">... jest odpowiednikiem następującego języka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="bc2cd-180">Agregacje oparte na kolekcjach</span><span class="sxs-lookup"><span data-stu-id="bc2cd-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="bc2cd-181">Entity SQL obsługuje dwa rodzaje agregacji.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="bc2cd-182">Agregacje oparte na kolekcji działają na kolekcjach i tworzą zagregowany wynik.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="bc2cd-183">Mogą one występować w dowolnym miejscu zapytania i nie wymagają `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="bc2cd-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="bc2cd-185">Entity SQL obsługuje również agregacje w stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="bc2cd-186">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="bc2cd-187">Użycie klauzuli ORDER BY</span><span class="sxs-lookup"><span data-stu-id="bc2cd-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="bc2cd-188">Język Transact-SQL zezwala `ORDER BY` na określenie klauzul tylko w bloku najwyższego poziomu `SELECT .. FROM .. WHERE` .</span><span class="sxs-lookup"><span data-stu-id="bc2cd-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="bc2cd-189">W Entity SQL można użyć wyrażenia zagnieżdżonego, które `ORDER BY` można umieścić w dowolnym miejscu zapytania, ale porządkowanie w zagnieżdżonych zapytaniach nie jest zachowywane.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="bc2cd-190">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="bc2cd-190">Identifiers</span></span>  
 <span data-ttu-id="bc2cd-191">W języku Transact-SQL porównanie identyfikatorów jest oparte na sortowaniu bieżącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="bc2cd-192">W Entity SQL w identyfikatorach zawsze jest rozróżniana wielkość liter i znaki akcentu (oznacza to, że Entity SQL rozróżnia znaków akcentowane i nieakcentowane, na przykład "a" nie jest równe "ấ").</span><span class="sxs-lookup"><span data-stu-id="bc2cd-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="bc2cd-193">Entity SQL traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych jako różne znaki.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="bc2cd-194">Aby uzyskać więcej informacji, zobacz [wejściowy zestaw znaków](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="bc2cd-195">Funkcja Transact-SQL nie jest dostępna w Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bc2cd-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="bc2cd-196">Poniższe funkcje języka Transact-SQL nie są dostępne w Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="bc2cd-197">DML</span><span class="sxs-lookup"><span data-stu-id="bc2cd-197">DML</span></span>  
 <span data-ttu-id="bc2cd-198">Entity SQL obecnie nie obsługuje instrukcji DML (INSERT, Update i Delete).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="bc2cd-199">JĘZYKA</span><span class="sxs-lookup"><span data-stu-id="bc2cd-199">DDL</span></span>  
 <span data-ttu-id="bc2cd-200">Entity SQL nie obsługuje języka DDL w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="bc2cd-201">programowanie imperatywne</span><span class="sxs-lookup"><span data-stu-id="bc2cd-201">Imperative Programming</span></span>  
 <span data-ttu-id="bc2cd-202">Entity SQL nie zapewnia obsługi bezwzględnego programowania, w przeciwieństwie do języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="bc2cd-203">Zamiast tego użyj języka programowania.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="bc2cd-204">Funkcje grupowania</span><span class="sxs-lookup"><span data-stu-id="bc2cd-204">Grouping Functions</span></span>  
 <span data-ttu-id="bc2cd-205">Entity SQL nie zapewnia jeszcze obsługi funkcji grupowania (na przykład CUBE, ROLLUP i GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="bc2cd-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="bc2cd-206">Funkcje analityczne</span><span class="sxs-lookup"><span data-stu-id="bc2cd-206">Analytic Functions</span></span>  
 <span data-ttu-id="bc2cd-207">Entity SQL nie (jeszcze) zapewnia obsługę funkcji analitycznych.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="bc2cd-208">Wbudowane funkcje, operatory</span><span class="sxs-lookup"><span data-stu-id="bc2cd-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="bc2cd-209">Entity SQL obsługuje podzestaw wbudowanych funkcji i operatorów języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="bc2cd-210">Te operatory i funkcje mogą być obsługiwane przez dostawców głównych magazynów.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="bc2cd-211">Entity SQL używa funkcji specyficznych dla magazynu zadeklarowanych w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="bc2cd-212">Ponadto Entity Framework umożliwia zadeklarować wbudowane i zdefiniowane przez użytkownika funkcje magazynu, aby Entity SQL do użycia.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="bc2cd-213">Wskazówek</span><span class="sxs-lookup"><span data-stu-id="bc2cd-213">Hints</span></span>  
 <span data-ttu-id="bc2cd-214">Entity SQL nie oferuje mechanizmów dla wskazówek dotyczących zapytań.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="bc2cd-215">Wsadowe wyniki zapytania</span><span class="sxs-lookup"><span data-stu-id="bc2cd-215">Batching Query Results</span></span>  
 <span data-ttu-id="bc2cd-216">Entity SQL nie obsługuje wsadowych wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="bc2cd-217">Na przykład następujące są prawidłowe w języku Transact-SQL (wysyłanie jako partia):</span><span class="sxs-lookup"><span data-stu-id="bc2cd-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="bc2cd-218">Jednak odpowiednik Entity SQL nie jest obsługiwany:</span><span class="sxs-lookup"><span data-stu-id="bc2cd-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="bc2cd-219">Entity SQL obsługuje tylko jedną instrukcję zapytania wytwarzającą wynik na polecenie.</span><span class="sxs-lookup"><span data-stu-id="bc2cd-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2cd-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc2cd-220">See also</span></span>

- [<span data-ttu-id="bc2cd-221">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="bc2cd-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="bc2cd-222">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="bc2cd-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
