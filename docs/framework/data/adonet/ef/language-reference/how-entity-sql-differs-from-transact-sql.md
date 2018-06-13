---
title: Jak jednostki SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: d34c6933e0f19c73b954446fdf18cea7243eae0d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766299"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="7dd17-102">Jak jednostki SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7dd17-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="7dd17-103">W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7dd17-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="7dd17-104">Dziedziczenie i relacje obsługi</span><span class="sxs-lookup"><span data-stu-id="7dd17-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-105"> współpracuje bezpośrednio z Schematy koncepcyjne jednostki i obsługuje model koncepcyjny funkcje, takie jak dziedziczenia i relacje.</span><span class="sxs-lookup"><span data-stu-id="7dd17-105"> works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="7dd17-106">Podczas pracy z dziedziczenia, często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu.</span><span class="sxs-lookup"><span data-stu-id="7dd17-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="7dd17-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobnie jak `oftype` w sekwencjach C#) zapewnia tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="7dd17-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="7dd17-108">Obsługa kolekcji</span><span class="sxs-lookup"><span data-stu-id="7dd17-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-109"> traktuje kolekcji jako najwyższej jakości jednostek.</span><span class="sxs-lookup"><span data-stu-id="7dd17-109"> treats collections as first-class entities.</span></span> <span data-ttu-id="7dd17-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7dd17-110">For example:</span></span>  
  
-   <span data-ttu-id="7dd17-111">Wyrażenia kolekcji są prawidłowe w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="7dd17-112">`in` i `exists` podzapytania ma został uogólniony zezwalająca na wszystkie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="7dd17-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="7dd17-113">Podzapytania jest jednego rodzaju kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="7dd17-114">`e1 in e2` i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji, aby wykonać te operacje.</span><span class="sxs-lookup"><span data-stu-id="7dd17-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="7dd17-115">Ustaw operacje, takie jak `union`, `intersect`, i `except`, działał w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="7dd17-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="7dd17-116">Sprzężenia działają w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="7dd17-117">Obsługę wyrażeń</span><span class="sxs-lookup"><span data-stu-id="7dd17-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="7dd17-118"> ma podzapytania (tabele) i wyrażenia (wierszy i kolumn).</span><span class="sxs-lookup"><span data-stu-id="7dd17-118"> has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="7dd17-119">Do obsługi kolekcji i zagnieżdżonych kolekcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawia, że wszystkie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7dd17-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-120"> więcej zezwala na składanie niż [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— co wyrażenia można używać w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="7dd17-120"> is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="7dd17-121">Zapytanie wyrażenia zawsze powoduje kolekcji planowanego typów i mogą być używane wszędzie, gdzie jest dozwolona w wyrażeniu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="7dd17-122">Aby uzyskać informacje o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7dd17-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="7dd17-123">Poniżej znajdują się wszystkie ważne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:</span><span class="sxs-lookup"><span data-stu-id="7dd17-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="7dd17-124">Jednolitego traktowania podzapytania</span><span class="sxs-lookup"><span data-stu-id="7dd17-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="7dd17-125">Podane jego wyróżnienia w tabelach, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wykonuje kontekstowe interpretacja podzapytania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="7dd17-126">Na przykład podzapytania w `from` klauzuli jest traktowany jako zestaw wielokrotny (tabeli).</span><span class="sxs-lookup"><span data-stu-id="7dd17-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="7dd17-127">Ale tego samego podzapytania, używane w `select` klauzuli jest traktowany jako skalarna podzapytania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="7dd17-128">Podobnie, podzapytania używane po lewej stronie `in` operator jest uznawane za podzapytania skalarne, gdy po prawej stronie powinien być podzapytania multiset —.</span><span class="sxs-lookup"><span data-stu-id="7dd17-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-129"> eliminuje tych różnic.</span><span class="sxs-lookup"><span data-stu-id="7dd17-129"> eliminates these differences.</span></span> <span data-ttu-id="7dd17-130">Wyrażenie zawiera jednolitej interpretacji, które nie są zależne od kontekstu, w którym jest używana.</span><span class="sxs-lookup"><span data-stu-id="7dd17-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-131"> uwzględnia wszystkich podzapytaniach jako zestaw wielokrotny podzapytania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-131"> considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="7dd17-132">Jeśli wartość skalarną z podzapytania, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia `anyelement` operator, który operuje na kolekcji (w tym przypadku podzapytanie) i wyodrębnianie pojedyncze wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="7dd17-133">Unikanie niejawne Wymuszeniami dla zapytania podrzędne</span><span class="sxs-lookup"><span data-stu-id="7dd17-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="7dd17-134">Efekt uboczny pokrewne jednolitego traktowania podzapytania jest niejawnej konwersji wartości podzapytania wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="7dd17-135">W szczególności w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multiset wierszy (z jednym polem) jest niejawnie konwertowane na wartość skalarną, której typ danych jest to, że pola.</span><span class="sxs-lookup"><span data-stu-id="7dd17-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-136"> nie obsługuje tego niejawne przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="7dd17-136"> does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-137"> zawiera operator ANYELEMENT można wyodrębnić pojedynczą wartość z kolekcji, a `select value` klauzuli, aby uniknąć tworzenia otoka wiersza w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-137"> provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="7dd17-138">Wybierz wartość: Unikanie otoki niejawne wiersza</span><span class="sxs-lookup"><span data-stu-id="7dd17-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="7dd17-139">Klauzuli select w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] podzapytania niejawnie tworzy otokę wiersza elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="7dd17-140">Oznacza to, że nie można utworzyć kolekcji wartości skalarne lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="7dd17-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="7dd17-141"> zezwala na niejawne koercja między rowtype z jednego pola i wartość singleton tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-141"> allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-142"> udostępnia `select value` klauzuli, aby pominąć konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="7dd17-142"> provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="7dd17-143">Można określić tylko jeden element w `select value` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="7dd17-144">W przypadku takich klauzuli nie otoki wiersza jest tworzony wokół elementów w `select` klauzul i kolekcji żądanego kształtu mogą powstać, na przykład: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="7dd17-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-145"> udostępnia również Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="7dd17-145"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="7dd17-146">`select` przyjmuje jeden lub więcej elementów w projekcji i wyników w rekordzie danych z polami, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7dd17-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="7dd17-147">Lewa Korelacja i aliasów</span><span class="sxs-lookup"><span data-stu-id="7dd17-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="7dd17-148">W [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], wyrażenia w danym zakresie (takich jak jedną klauzulę `select` lub `from`) nie może odwoływać się wyrażenia zdefiniowanego wcześniej w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7dd17-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="7dd17-149">Niektóre dialekty języka SQL (w tym [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) obsługuje ograniczone form w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-150"> stanowi uogólnienie po lewej stronie korelacji w `from` klauzuli i traktuje je jednakowo.</span><span class="sxs-lookup"><span data-stu-id="7dd17-150"> generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="7dd17-151">Wyrażenia w `from` klauzuli może odwoływać się wcześniej definicje (definicje z lewej strony) w tej samej klauzuli bez konieczności stosowania dodatkowych składni.</span><span class="sxs-lookup"><span data-stu-id="7dd17-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-152"> nakłada także dodatkowe ograniczenia dotyczące zapytań `group by` klauzul.</span><span class="sxs-lookup"><span data-stu-id="7dd17-152"> also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="7dd17-153">Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań może odwoływać się tylko do `group by` klucze za pomocą ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="7dd17-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="7dd17-154">Poniższa konstrukcja jest prawidłowa w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nie znajdują się w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7dd17-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="7dd17-155">Aby to zrobić w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7dd17-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="7dd17-156">Odwoływanie się do kolumn (właściwości) tabele (kolekcji)</span><span class="sxs-lookup"><span data-stu-id="7dd17-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="7dd17-157">Wszystkie odwołania do kolumn w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być kwalifikowany za pomocą aliasu tabeli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="7dd17-158">Poniższa konstrukcja (przy założeniu, że `a` jest prawidłową kolumnę tabeli `T`) jest nieprawidłowy w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7dd17-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="7dd17-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formularz</span><span class="sxs-lookup"><span data-stu-id="7dd17-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="7dd17-160">Aliasy tabeli są opcjonalne w `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="7dd17-161">Nazwa tabeli jest używana jako alias niejawnej.</span><span class="sxs-lookup"><span data-stu-id="7dd17-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-162"> Umożliwia również następującą postać:</span><span class="sxs-lookup"><span data-stu-id="7dd17-162"> allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="7dd17-163">Nawigację obiektów</span><span class="sxs-lookup"><span data-stu-id="7dd17-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="7dd17-164"> używa "." notation dla odwołania do kolumny (wiersz) tabeli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-164"> uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-165"> Rozszerza ten element notation (pobierają z języków programowania) do obsługi nawigacji za pomocą właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="7dd17-165"> extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="7dd17-166">Na przykład jeśli `p` jest wyrażenie wpisz osobę, Oto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składnię odwołujące się do miasta adres tej osoby.</span><span class="sxs-lookup"><span data-stu-id="7dd17-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="7dd17-167">Brak obsługi \*</span><span class="sxs-lookup"><span data-stu-id="7dd17-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="7dd17-168"> obsługuje niekwalifikowane \* składni jako alias dla całego wiersza i kwalifikowaną \* składni (t.\*) jako skrót do pól w tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-168"> supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="7dd17-169">Ponadto [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umożliwia specjalne Count (\*) wartość zagregowaną, która zawiera wartości null.</span><span class="sxs-lookup"><span data-stu-id="7dd17-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-170"> nie obsługuje \* konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-170"> does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="7dd17-171"> zapytania w postaci `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7dd17-171"> queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="7dd17-172">Ponadto tych konstrukcji obsługi dziedziczenia (wartość podaży), podczas gdy `select *` wariantów są ograniczone do najwyższego poziomu właściwości deklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="7dd17-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-173"> nie obsługuje `count(*)` agregacji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-173"> does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="7dd17-174">Zamiast nich należy używać słów kluczowych `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="7dd17-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="7dd17-175">Zmiany Grupuj według</span><span class="sxs-lookup"><span data-stu-id="7dd17-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-176"> obsługuje aliasów z `group by` kluczy.</span><span class="sxs-lookup"><span data-stu-id="7dd17-176"> supports aliasing of `group by` keys.</span></span> <span data-ttu-id="7dd17-177">Wyrażenia w `select` klauzuli i `having` klauzuli musi odwoływać się do `group by` klucze za pomocą tych aliasów.</span><span class="sxs-lookup"><span data-stu-id="7dd17-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="7dd17-178">Na przykład to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni:</span><span class="sxs-lookup"><span data-stu-id="7dd17-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="7dd17-179">.. jest standardem odpowiednikiem następujące [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7dd17-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="7dd17-180">Agreguje opartego na kolekcji</span><span class="sxs-lookup"><span data-stu-id="7dd17-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-181"> obsługuje dwa rodzaje wartości zagregowanych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-181"> supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="7dd17-182">Agregacje opartego na kolekcji działać na kolekcje i utworzenia wyniku zagregowanych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="7dd17-183">Te mogą występować w dowolnym miejscu w zapytaniu i nie wymagają `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd17-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="7dd17-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7dd17-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-185"> obsługuje również wartości zagregowanych SQL stylu.</span><span class="sxs-lookup"><span data-stu-id="7dd17-185"> also supports SQL-style aggregates.</span></span> <span data-ttu-id="7dd17-186">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7dd17-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="7dd17-187">ORDER BY — klauzula użycia</span><span class="sxs-lookup"><span data-stu-id="7dd17-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="7dd17-188"> zezwala na klauzule ORDER BY określić tylko w najwyższej wybierz...</span><span class="sxs-lookup"><span data-stu-id="7dd17-188"> allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="7dd17-189">Z...</span><span class="sxs-lookup"><span data-stu-id="7dd17-189">FROM ..</span></span> <span data-ttu-id="7dd17-190">GDZIE bloku.</span><span class="sxs-lookup"><span data-stu-id="7dd17-190">WHERE block.</span></span> <span data-ttu-id="7dd17-191">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można używać zagnieżdżonych Wyrażenie ORDER BY i można je umieścić w dowolnym miejscu w zapytaniu, ale szeregowaniem w zapytaniu zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="7dd17-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="7dd17-192">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="7dd17-192">Identifiers</span></span>  
 <span data-ttu-id="7dd17-193">W [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identyfikator porównania jest oparta na sortowanie bieżącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="7dd17-194">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identyfikatory są zawsze bez uwzględniania wielkości liter i akcent poufnych (to znaczy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozróżnia znaki akcentowane i formami; na przykład "" nie jest równa "ấ").</span><span class="sxs-lookup"><span data-stu-id="7dd17-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-195"> traktuje wersji liter wyglądają tak samo, które pochodzą z różnych kodowe jako różne znaki.</span><span class="sxs-lookup"><span data-stu-id="7dd17-195"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="7dd17-196">Aby uzyskać więcej informacji, zobacz [zestaw znaków wprowadzania](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7dd17-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="7dd17-197">Funkcje języka Transact-SQL nie jest dostępna w jednostce SQL</span><span class="sxs-lookup"><span data-stu-id="7dd17-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="7dd17-198">Następujące [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] funkcja nie jest dostępna w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7dd17-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="7dd17-199">DML</span><span class="sxs-lookup"><span data-stu-id="7dd17-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-200"> obecnie nie zapewnia obsługi dla instrukcji DML (Wstawianie, aktualizowanie i usuwanie).</span><span class="sxs-lookup"><span data-stu-id="7dd17-200"> currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="7dd17-201">DDL</span><span class="sxs-lookup"><span data-stu-id="7dd17-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-202"> nie zapewnia obsługi dla języka DDL w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="7dd17-202"> provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="7dd17-203">Programowanie imperatywne</span><span class="sxs-lookup"><span data-stu-id="7dd17-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-204"> nie zapewnia obsługi imperatywnych programowania, w odróżnieniu od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7dd17-204"> provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7dd17-205">Zamiast tego użyj języka programowania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="7dd17-206">Grupowanie funkcji</span><span class="sxs-lookup"><span data-stu-id="7dd17-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-207"> nie jeszcze zapewnia obsługę do grupowania funkcji (na przykład, CUBE, ROLLUP i GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="7dd17-207"> does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="7dd17-208">Funkcje analityczne</span><span class="sxs-lookup"><span data-stu-id="7dd17-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-209"> nie (jeszcze) zapewniają obsługę funkcji analitycznych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-209"> does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="7dd17-210">Funkcje wbudowane operatory</span><span class="sxs-lookup"><span data-stu-id="7dd17-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-211"> obsługuje podzbiór [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]przez wbudowane funkcje i operatory.</span><span class="sxs-lookup"><span data-stu-id="7dd17-211"> supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="7dd17-212">Te operatory i funkcje są mogą być obsługiwane przez dostawców magazynu głównych.</span><span class="sxs-lookup"><span data-stu-id="7dd17-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-213"> korzysta z funkcji specyficznych dla magazynu zadeklarowane w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="7dd17-213"> uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="7dd17-214">Ponadto [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umożliwia zadeklarować wbudowanych i zdefiniowanych przez użytkownika istniejących magazynu funkcji, dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do użycia.</span><span class="sxs-lookup"><span data-stu-id="7dd17-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="7dd17-215">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="7dd17-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-216"> nie zapewnia mechanizmy wskazówki zapytania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-216"> does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="7dd17-217">Przetwarzanie wsadowe wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="7dd17-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-218"> nie obsługuje przetwarzanie wsadowe wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="7dd17-218"> does not support batching query results.</span></span> <span data-ttu-id="7dd17-219">Na przykład poniżej przedstawiono prawidłowe [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (wysyłania jako plik wsadowy):</span><span class="sxs-lookup"><span data-stu-id="7dd17-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="7dd17-220">Jednak odpowiednikiem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwana:</span><span class="sxs-lookup"><span data-stu-id="7dd17-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7dd17-221"> obsługuje tylko jedną instrukcję zapytanie zwracające w wyniku na polecenie.</span><span class="sxs-lookup"><span data-stu-id="7dd17-221"> only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd17-222">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7dd17-222">See Also</span></span>  
 [<span data-ttu-id="7dd17-223">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="7dd17-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="7dd17-224">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7dd17-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
