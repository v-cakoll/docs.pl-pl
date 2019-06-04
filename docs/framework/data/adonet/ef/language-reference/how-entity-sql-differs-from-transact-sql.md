---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 54d7a3fa8ce6e8a0aba6194bfc034eb4d47dbf60
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489926"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="00b74-102">Czym język Entity SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="00b74-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="00b74-103">W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oraz języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="00b74-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="00b74-104">Dziedziczenie i relacje obsługi</span><span class="sxs-lookup"><span data-stu-id="00b74-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-105">współpracuje bezpośrednio ze schematami koncepcyjnymi encji i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.</span><span class="sxs-lookup"><span data-stu-id="00b74-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="00b74-106">Podczas pracy z dziedziczenia, często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu.</span><span class="sxs-lookup"><span data-stu-id="00b74-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="00b74-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobnie jak `oftype` w C# sekwencje) zapewnia tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="00b74-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="00b74-108">Obsługa kolekcji</span><span class="sxs-lookup"><span data-stu-id="00b74-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-109">traktuje kolekcji jako obiekty najwyższej jakości.</span><span class="sxs-lookup"><span data-stu-id="00b74-109">treats collections as first-class entities.</span></span> <span data-ttu-id="00b74-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="00b74-110">For example:</span></span>  
  
- <span data-ttu-id="00b74-111">Wyrażenia kolekcji są prawidłowe w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="00b74-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="00b74-112">`in` i `exists` podzapytań mają został uogólniony, aby zezwolić na wszystkie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="00b74-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="00b74-113">Podzapytania jest jeden rodzaj kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00b74-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="00b74-114">`e1 in e2` i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji wykonywać te operacje.</span><span class="sxs-lookup"><span data-stu-id="00b74-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="00b74-115">Ustawić operacje, takie jak `union`, `intersect`, i `except`, teraz działają w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="00b74-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="00b74-116">Sprzężenia działają w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="00b74-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="00b74-117">Obsługa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="00b74-117">Support for Expressions</span></span>  
 <span data-ttu-id="00b74-118">Języka Transact-SQL ma podzapytań (tabele) i wyrażenia (wiersze i kolumny).</span><span class="sxs-lookup"><span data-stu-id="00b74-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="00b74-119">Do obsługi kolekcji i kolekcje zagnieżdżone [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawia, że wszystkie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="00b74-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-120">jest bardziej konfigurowalna niż języka Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="00b74-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="00b74-121">Zapytanie wyrażenia zawsze powoduje kolekcji typów przewidywanych i mogą być używane wszędzie, gdzie jest dozwolona w wyrażeniu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00b74-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="00b74-122">Aby uzyskać informacje o wyrażeniach języka Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="00b74-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="00b74-123">Poniżej znajdują się wszystkie prawidłowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:</span><span class="sxs-lookup"><span data-stu-id="00b74-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="00b74-124">Jednolitego traktowania podzapytań</span><span class="sxs-lookup"><span data-stu-id="00b74-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="00b74-125">Biorąc pod uwagę jej nacisk na tabele, języka Transact-SQL wykonuje kontekstowych interpretacji podzapytania.</span><span class="sxs-lookup"><span data-stu-id="00b74-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="00b74-126">Na przykład podzapytania w `from` klauzula jest uważany za multiset (tabela).</span><span class="sxs-lookup"><span data-stu-id="00b74-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="00b74-127">Ale ten sam podzapytanie używane w `select` klauzula jest uważany za skalarne podzapytania.</span><span class="sxs-lookup"><span data-stu-id="00b74-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="00b74-128">Podobnie, podzapytania używane w lewej części `in` operator jest uważany za podzapytania skalarne, a po prawej stronie powinien być multiset — podzapytanie.</span><span class="sxs-lookup"><span data-stu-id="00b74-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-129">eliminuje te różnice.</span><span class="sxs-lookup"><span data-stu-id="00b74-129">eliminates these differences.</span></span> <span data-ttu-id="00b74-130">Wyrażenie zawiera jednolitej interpretacji, które nie są zależne od kontekstu, w którym jest używany.</span><span class="sxs-lookup"><span data-stu-id="00b74-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-131">uwzględnia wszystkich podzapytaniach to zestaw wielokrotny podzapytania.</span><span class="sxs-lookup"><span data-stu-id="00b74-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="00b74-132">Jeśli wartość skalarną z podzapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia `anyelement` operator, który działa w kolekcji (w tym przypadku podzapytanie) i wyodrębnia wartości pojedynczego wystąpienia z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00b74-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="00b74-133">Unikanie niejawne Coercions dla podzapytań</span><span class="sxs-lookup"><span data-stu-id="00b74-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="00b74-134">Powiązane efekt uboczny jednolitego traktowania podzapytań jest niejawnej konwersji wartości podzapytań wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="00b74-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="00b74-135">W szczególności w języku Transact-SQL, multiset wierszy (z jednym polem) jest niejawnie konwertowany na wartość skalarną, której typem danych jest to, że pola.</span><span class="sxs-lookup"><span data-stu-id="00b74-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-136">nie obsługuje tego niejawne przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="00b74-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-137">zawiera operator ANYELEMENT do wyodrębnienia pojedyncze wartości z kolekcji, a `select value` klauzulę, aby uniknąć tworzenia otoki wiersza w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="00b74-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="00b74-138">Wybierz wartość: Unikanie otoki niejawne wiersza</span><span class="sxs-lookup"><span data-stu-id="00b74-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="00b74-139">Klauzula select w podzapytaniu języka Transact-SQL niejawnie tworzy otokę wierszy elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="00b74-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="00b74-140">Oznacza to, że nie można utworzyć kolekcji wartości skalarnych lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="00b74-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="00b74-141">Języka Transact-SQL umożliwia niejawne wymuszenia między rowtype z jednym polem i wartości pojedynczego wystąpienia typu danych.</span><span class="sxs-lookup"><span data-stu-id="00b74-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-142">udostępnia `select value` klauzuli, aby pominąć konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="00b74-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="00b74-143">Można określić tylko jeden element w `select value` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="00b74-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="00b74-144">W przypadku takich klauzuli nie otoki wiersza została zbudowana w oparciu elementów w `select` klauzuli i kolekcji żądany kształt mogą powstać, na przykład: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="00b74-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-145">zapewnia także Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="00b74-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="00b74-146">`select` przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych przy użyciu pól, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="00b74-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="00b74-147">Lewa Korelacja i aliasów</span><span class="sxs-lookup"><span data-stu-id="00b74-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="00b74-148">W języku Transact-SQL, wyrażenia w danym zakresie (takie jak pojedyncza klauzula `select` lub `from`) nie może odwoływać się do wyrażenia zdefiniowany wcześniej w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="00b74-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="00b74-149">Niektóre dialekty programu SQL Server (w tym języka Transact-SQL) obsługuje ograniczone formy w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="00b74-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-150">stanowi uogólnienie korelacji po lewej stronie w `from` klauzuli i traktować je równomiernie.</span><span class="sxs-lookup"><span data-stu-id="00b74-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="00b74-151">Wyrażenia w `from` klauzuli może odwoływać się definicje wcześniejsze (definicje po lewej stronie) w tej samej klauzuli bez konieczności stosowania dodatkowej składni.</span><span class="sxs-lookup"><span data-stu-id="00b74-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-152">również nakłada dodatkowe ograniczenia dotyczące zapytania obejmujące `group by` klauzul.</span><span class="sxs-lookup"><span data-stu-id="00b74-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="00b74-153">Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań może odwoływać się tylko do `group by` kluczy przy użyciu ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="00b74-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="00b74-154">Następujące konstrukcja jest nieprawidłowy w instrukcji Transact-SQL, ale nie są [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="00b74-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="00b74-155">Aby to zrobić w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="00b74-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="00b74-156">Odwoływanie się do kolumn (właściwości) tabel (kolekcji)</span><span class="sxs-lookup"><span data-stu-id="00b74-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="00b74-157">Wszystkie odwołania do kolumn w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być kwalifikowana za pomocą aliasu tabeli.</span><span class="sxs-lookup"><span data-stu-id="00b74-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="00b74-158">Następująca konstrukcja (przy założeniu, że `a` jest prawidłową kolumną tabeli `T`) jest prawidłowa w języku Transact-SQL, ale nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00b74-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="00b74-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formularz</span><span class="sxs-lookup"><span data-stu-id="00b74-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="00b74-160">Aliasy tabeli są opcjonalne w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="00b74-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="00b74-161">Nazwa tabeli jest używany jako alias niejawne.</span><span class="sxs-lookup"><span data-stu-id="00b74-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-162">Umożliwia także następującą postać:</span><span class="sxs-lookup"><span data-stu-id="00b74-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="00b74-163">Nawigacja za pośrednictwem obiektów</span><span class="sxs-lookup"><span data-stu-id="00b74-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="00b74-164">Używa języka Transact-SQL "." Notacja do odwoływania się do kolumn (wiersz) tabeli.</span><span class="sxs-lookup"><span data-stu-id="00b74-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-165">Rozszerza ten zapis (pobierają z języków programowania) do obsługi nawigacji za pomocą właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="00b74-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="00b74-166">Na przykład jeśli `p` wyrażenia wpisz osobę, Oto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni do odwoływania się do miasta adres tej osoby.</span><span class="sxs-lookup"><span data-stu-id="00b74-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="00b74-167">Brak obsługi \*</span><span class="sxs-lookup"><span data-stu-id="00b74-167">No Support for \*</span></span>  
 <span data-ttu-id="00b74-168">Języka Transact-SQL obsługuje niekwalifikowanej \* składni jako alias dla całego wiersza i kwalifikowaną \* składni (t.\*) jako skrót dla pól tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="00b74-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="00b74-169">Ponadto języka Transact-SQL umożliwia specjalnych licznik (\*) wartość zagregowaną, która zawiera wartości null.</span><span class="sxs-lookup"><span data-stu-id="00b74-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-170">nie obsługuje \* konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="00b74-170">does not support the \* construct.</span></span> <span data-ttu-id="00b74-171">Zapytania Transact-SQL w postaci `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="00b74-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="00b74-172">Ponadto te konstrukcje obsługi dziedziczenia (wartość podaży), podczas gdy `select *` wariantów są ograniczone do najwyższego poziomu właściwości zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="00b74-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-173">nie obsługuje `count(*)` agregacji.</span><span class="sxs-lookup"><span data-stu-id="00b74-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="00b74-174">Zamiast nich należy używać słów kluczowych `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="00b74-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="00b74-175">Zmiany Grupuj według</span><span class="sxs-lookup"><span data-stu-id="00b74-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-176">obsługuje tworzenie aliasów dla `group by` kluczy.</span><span class="sxs-lookup"><span data-stu-id="00b74-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="00b74-177">Wyrażenia w `select` klauzuli i `having` klauzuli musi odwoływać się do `group by` kluczy przy użyciu te aliasy.</span><span class="sxs-lookup"><span data-stu-id="00b74-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="00b74-178">Na przykład, to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni:</span><span class="sxs-lookup"><span data-stu-id="00b74-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="00b74-179">... jest równoważne z instrukcji Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="00b74-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="00b74-180">Wartości zagregowane z kolekcji</span><span class="sxs-lookup"><span data-stu-id="00b74-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-181">obsługuje dwa rodzaje wartości zagregowanych.</span><span class="sxs-lookup"><span data-stu-id="00b74-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="00b74-182">Agregacje związanych z kolekcjami działają w kolekcjach i tworzące zagregowany wynik.</span><span class="sxs-lookup"><span data-stu-id="00b74-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="00b74-183">Te mogą występować w dowolnym miejscu w zapytaniu i nie wymagają `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="00b74-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="00b74-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="00b74-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-185">obsługuje również wartości zagregowanych SQL stylu.</span><span class="sxs-lookup"><span data-stu-id="00b74-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="00b74-186">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="00b74-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="00b74-187">KOLEJNOŚĆ według użycia klauzuli</span><span class="sxs-lookup"><span data-stu-id="00b74-187">ORDER BY Clause Usage</span></span>  
 <span data-ttu-id="00b74-188">Języka Transact-SQL umożliwia klauzule w klauzuli ORDER BY, należy określić tylko w najwyższej wybierz...</span><span class="sxs-lookup"><span data-stu-id="00b74-188">Transact-SQL allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="00b74-189">OD...</span><span class="sxs-lookup"><span data-stu-id="00b74-189">FROM ..</span></span> <span data-ttu-id="00b74-190">GDZIE zablokować.</span><span class="sxs-lookup"><span data-stu-id="00b74-190">WHERE block.</span></span> <span data-ttu-id="00b74-191">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można używać zagnieżdżonych wyrażeń klauzuli ORDER BY i można je umieścić w dowolnym miejscu w zapytaniu, ale szeregowaniem w zapytaniu zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="00b74-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="00b74-192">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="00b74-192">Identifiers</span></span>  
 <span data-ttu-id="00b74-193">W języku Transact-SQL porównanie identyfikatorów opiera się na sortowania bieżącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="00b74-193">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="00b74-194">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identyfikatory są zawsze bez uwzględniania wielkości liter i akcent poufnych (czyli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozróżnia znaki akcentowane i nieakcentowane; na przykład, "" nie jest równa "ấ").</span><span class="sxs-lookup"><span data-stu-id="00b74-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-195">traktuje wersji liter, są wyświetlane takie same, które pochodzą z różne strony kodowe jako różne znaki.</span><span class="sxs-lookup"><span data-stu-id="00b74-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="00b74-196">Aby uzyskać więcej informacji, zobacz [zestaw znaków danych wejściowych](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="00b74-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="00b74-197">Funkcje języka Transact-SQL nie jest dostępna w jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="00b74-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="00b74-198">Następujące funkcje języka Transact-SQL nie jest dostępna w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00b74-198">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="00b74-199">DML</span><span class="sxs-lookup"><span data-stu-id="00b74-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-200">obecnie nie obsługuje instrukcji DML (Wstawianie, aktualizowanie i usuwanie).</span><span class="sxs-lookup"><span data-stu-id="00b74-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="00b74-201">DDL</span><span class="sxs-lookup"><span data-stu-id="00b74-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-202">nie obsługuje języka DDL w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="00b74-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="00b74-203">programowanie imperatywne</span><span class="sxs-lookup"><span data-stu-id="00b74-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-204">nie obsługuje programowanie imperatywne, w przeciwieństwie do języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="00b74-204">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="00b74-205">Zamiast tego użyj języka programowania.</span><span class="sxs-lookup"><span data-stu-id="00b74-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="00b74-206">Funkcje grupowania</span><span class="sxs-lookup"><span data-stu-id="00b74-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-207">nie jeszcze zapewniają obsługę grupowanie funkcji (na przykład moduł, pakiet ZBIORCZY i GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="00b74-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="00b74-208">Funkcje analityczne</span><span class="sxs-lookup"><span data-stu-id="00b74-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-209">nie (jeszcze) zapewnia obsługę funkcji analitycznych.</span><span class="sxs-lookup"><span data-stu-id="00b74-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="00b74-210">Funkcje wbudowane, operatory</span><span class="sxs-lookup"><span data-stu-id="00b74-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-211">obsługuje podzbiór języka Transact-SQL zawiera wbudowane funkcje i operatory.</span><span class="sxs-lookup"><span data-stu-id="00b74-211">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="00b74-212">Te operatory i funkcje mogą być obsługiwane przez dostawców magazynu głównych.</span><span class="sxs-lookup"><span data-stu-id="00b74-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-213">korzysta z funkcji specyficznych dla magazynu zadeklarowane w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="00b74-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="00b74-214">Ponadto [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umożliwia deklarację wbudowanych oraz istniejącego użytkownika przechowywane funkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do użycia.</span><span class="sxs-lookup"><span data-stu-id="00b74-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="00b74-215">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="00b74-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-216">nie zapewnia mechanizmy wskazówki zapytania.</span><span class="sxs-lookup"><span data-stu-id="00b74-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="00b74-217">Przetwarzanie wsadowe wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="00b74-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-218">nie obsługuje przetwarzania wsadowego wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="00b74-218">does not support batching query results.</span></span> <span data-ttu-id="00b74-219">Na przykład Oto prawidłowe języka Transact-SQL (wysyłającym jako zadania wsadowego):</span><span class="sxs-lookup"><span data-stu-id="00b74-219">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="00b74-220">Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwane:</span><span class="sxs-lookup"><span data-stu-id="00b74-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="00b74-221">obsługuje tylko jedną instrukcję zapytania zwracające wyniki dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="00b74-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b74-222">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00b74-222">See also</span></span>

- [<span data-ttu-id="00b74-223">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="00b74-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="00b74-224">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="00b74-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
