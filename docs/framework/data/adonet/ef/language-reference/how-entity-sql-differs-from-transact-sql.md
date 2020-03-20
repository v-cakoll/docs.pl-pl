---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150234"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="347cc-102">Czym język Entity SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="347cc-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="347cc-103">W tym temacie opisano [!INCLUDE[esql](../../../../../../includes/esql-md.md)] różnice między i Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="347cc-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="347cc-104">Obsługa dziedziczenia i relacji</span><span class="sxs-lookup"><span data-stu-id="347cc-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-105">współpracuje bezpośrednio ze schematami koncepcyjnych jednostek i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.</span><span class="sxs-lookup"><span data-stu-id="347cc-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="347cc-106">Podczas pracy z dziedziczenia, często jest przydatne do wybierania wystąpień podtypu z kolekcji wystąpień nadtypu.</span><span class="sxs-lookup"><span data-stu-id="347cc-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="347cc-107">[Oftype](oftype-entity-sql.md) operator [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w (podobnie jak `oftype` w sekwencje języka C#) zapewnia tę możliwość.</span><span class="sxs-lookup"><span data-stu-id="347cc-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="347cc-108">Obsługa kolekcji</span><span class="sxs-lookup"><span data-stu-id="347cc-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-109">traktuje kolekcje jako jednostki pierwszej klasy.</span><span class="sxs-lookup"><span data-stu-id="347cc-109">treats collections as first-class entities.</span></span> <span data-ttu-id="347cc-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="347cc-110">For example:</span></span>  
  
- <span data-ttu-id="347cc-111">Wyrażenia kolekcji są `from` prawidłowe w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="347cc-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="347cc-112">`in`i `exists` podksycje zostały uogólnione, aby umożliwić wszelkie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="347cc-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="347cc-113">Podkwerenda jest jednym z rodzajów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="347cc-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="347cc-114">`e1 in e2`i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcje do wykonywania tych operacji.</span><span class="sxs-lookup"><span data-stu-id="347cc-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="347cc-115">Ustaw operacje, `union`takie `intersect`jak `except`, i , teraz działają na kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="347cc-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="347cc-116">Sprzężenia działają na kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="347cc-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="347cc-117">Obsługa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="347cc-117">Support for Expressions</span></span>  
 <span data-ttu-id="347cc-118">Transact-SQL zawiera podquerie (tabele) i wyrażenia (wiersze i kolumny).</span><span class="sxs-lookup"><span data-stu-id="347cc-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="347cc-119">Do obsługi kolekcji i zagnieżdżonych kolekcji, sprawia, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] że wszystko wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="347cc-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-120">jest bardziej komponowalna niż Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="347cc-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="347cc-121">Wyrażenia kwerendy zawsze powodują kolekcje typów przewidywanych i mogą być używane wszędzie tam, gdzie wyrażenie kolekcji jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="347cc-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="347cc-122">Aby uzyskać informacje o wyrażeniach Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie , zobacz [Nieobsługiwalone wyrażenia](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="347cc-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="347cc-123">Oto wszystkie prawidłowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:</span><span class="sxs-lookup"><span data-stu-id="347cc-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="347cc-124">Jednolite traktowanie podkemietów</span><span class="sxs-lookup"><span data-stu-id="347cc-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="347cc-125">Biorąc pod uwagę nacisk na tabele, Transact-SQL wykonuje kontekstową interpretację podkemiewa.</span><span class="sxs-lookup"><span data-stu-id="347cc-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="347cc-126">Na przykład podkwerendy `from` w klauzuli jest uważany za multiset (tabela).</span><span class="sxs-lookup"><span data-stu-id="347cc-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="347cc-127">Ale ta sama podkwerenda używana w `select` klauzuli jest uważana za podkwerendę skalarną.</span><span class="sxs-lookup"><span data-stu-id="347cc-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="347cc-128">Podobnie podkwerenda używane po lewej `in` stronie operatora jest uważany za podkwerendę skalarną, podczas gdy po prawej stronie oczekuje się, że jest podkwerendą wielozestawową.</span><span class="sxs-lookup"><span data-stu-id="347cc-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-129">eliminuje te różnice.</span><span class="sxs-lookup"><span data-stu-id="347cc-129">eliminates these differences.</span></span> <span data-ttu-id="347cc-130">Wyrażenie ma jednolitą interpretację, która nie zależy od kontekstu, w którym jest używany.</span><span class="sxs-lookup"><span data-stu-id="347cc-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-131">uważa, że wszystkie podksy podksyrii są podksygną wielozespołowe.</span><span class="sxs-lookup"><span data-stu-id="347cc-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="347cc-132">Jeśli wartość skalarna jest pożądana [!INCLUDE[esql](../../../../../../includes/esql-md.md)] z `anyelement` podzapytania, zapewnia operator, który działa na kolekcji (w tym przypadku podkwerendy) i wyodrębnia wartość singleton z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="347cc-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="347cc-133">Unikanie ukrytych przymusów dla podkemietów</span><span class="sxs-lookup"><span data-stu-id="347cc-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="347cc-134">Powiązanym skutkiem ubocznym jednolitego traktowania podkwery jest niejawna konwersja podkwererów do wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="347cc-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="347cc-135">W szczególności w transact-SQL, zestaw wielu wierszy (z jednym polem) jest niejawnie konwertowane na wartość skalarną, której typem danych jest to, że w polu.</span><span class="sxs-lookup"><span data-stu-id="347cc-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-136">nie obsługuje tego ukrytego przymusu.</span><span class="sxs-lookup"><span data-stu-id="347cc-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-137">zapewnia ANYELEMENT operator wyodrębnić wartość singleton z `select value` kolekcji i klauzuli, aby uniknąć tworzenia otoki wiersza podczas wyrażenia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="347cc-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="347cc-138">Wybierz wartość: Unikanie niejawnego otoki wiersza</span><span class="sxs-lookup"><span data-stu-id="347cc-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="347cc-139">Klauzula select w podkwercie Transact-SQL niejawnie tworzy otokę wiersza wokół elementów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="347cc-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="347cc-140">Oznacza to, że nie możemy tworzyć kolekcji skalarnych lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="347cc-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="347cc-141">Transact-SQL umożliwia niejawne przymusu między typem wiersza z jednym polem i wartością singleton tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="347cc-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-142">zawiera `select value` klauzulę, aby pominąć konstrukcję niejawnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="347cc-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="347cc-143">W `select value` klauzuli można określić tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="347cc-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="347cc-144">Gdy taka klauzula jest używana, wokół elementów w `select` klauzuli nie jest skonstruowane żadne otoki wierszy, a kolekcja żądanego kształtu może być wyprodukowana, na przykład: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="347cc-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-145">udostępnia również konstruktora wierszy do konstruowania dowolnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="347cc-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="347cc-146">`select`przyjmuje jeden lub więcej elementów projekcji i powoduje, że rekord danych z polami jest następujący:</span><span class="sxs-lookup"><span data-stu-id="347cc-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="347cc-147">Lewa korelacja i aliasowanie</span><span class="sxs-lookup"><span data-stu-id="347cc-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="347cc-148">W Transact-SQL wyrażenia w danym zakresie (pojedyncza klauzula jak `select` lub `from`) nie mogą odwoływać się do wyrażeń zdefiniowanych wcześniej w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="347cc-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="347cc-149">Niektóre dialekty SQL (w tym Transact-SQL) obsługują `from` ograniczone formy tych w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="347cc-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-150">uogólnia lewe korelacje w klauzuli `from` i traktuje je jednolicie.</span><span class="sxs-lookup"><span data-stu-id="347cc-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="347cc-151">Wyrażenia w `from` klauzuli można odwoływać się do wcześniejszych definicji (definicje po lewej) w tej samej klauzuli bez konieczności dodatkowej składni.</span><span class="sxs-lookup"><span data-stu-id="347cc-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-152">nakłada również dodatkowe ograniczenia na zapytania `group by` dotyczące klauzul.</span><span class="sxs-lookup"><span data-stu-id="347cc-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="347cc-153">Wyrażenia w `select` klauzuli `having` i klauzuli takich zapytań `group by` mogą odwoływać się do kluczy tylko za pośrednictwem ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="347cc-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="347cc-154">Następująca konstrukcja jest prawidłowa w Transact-SQL, ale nie ma w: [!INCLUDE[esql](../../../../../../includes/esql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="347cc-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="347cc-155">Aby to [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zrobić w:</span><span class="sxs-lookup"><span data-stu-id="347cc-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="347cc-156">Odwoływanie się do kolumn (właściwości) tabel (kolekcje)</span><span class="sxs-lookup"><span data-stu-id="347cc-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="347cc-157">Wszystkie odwołania do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolumn muszą być kwalifikowane za pomocą aliasu tabeli.</span><span class="sxs-lookup"><span data-stu-id="347cc-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="347cc-158">Następująca konstrukcja (przy założeniu, `a` `T`że jest prawidłową kolumną tabeli) jest prawidłowa w transact-SQL, ale nie w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="347cc-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="347cc-159">Formularz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest</span><span class="sxs-lookup"><span data-stu-id="347cc-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="347cc-160">Aliasy tabeli są `from` opcjonalne w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="347cc-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="347cc-161">Nazwa tabeli jest używana jako alias niejawny.</span><span class="sxs-lookup"><span data-stu-id="347cc-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-162">pozwala również na następującą formę:</span><span class="sxs-lookup"><span data-stu-id="347cc-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="347cc-163">Nawigacja po obiektach</span><span class="sxs-lookup"><span data-stu-id="347cc-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="347cc-164">Transact-SQL używa notacji "." do odwoływania się do kolumn (wiersza) tabeli.</span><span class="sxs-lookup"><span data-stu-id="347cc-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-165">rozszerza tę notację (zapożyczoną z języków programowania) do obsługi nawigacji za pośrednictwem właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="347cc-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="347cc-166">Na przykład `p` jeśli jest wyrażeniem typu Osoba, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poniżej znajduje się składnia odwoływania się do miasta adresu tej osoby.</span><span class="sxs-lookup"><span data-stu-id="347cc-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="347cc-167">Brak wsparcia dla \*</span><span class="sxs-lookup"><span data-stu-id="347cc-167">No Support for \*</span></span>  
 <span data-ttu-id="347cc-168">Transact-SQL obsługuje składnię niekwalifikowaną \* jako alias dla \* całego wiersza\*i składnię kwalifikowaną (t. ) jako skrót dla pól tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="347cc-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="347cc-169">Ponadto Transact-SQL pozwala na specjalną\*liczbę( ) agregacji, która zawiera wartości null.</span><span class="sxs-lookup"><span data-stu-id="347cc-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-170">nie obsługuje konstrukcji \*.</span><span class="sxs-lookup"><span data-stu-id="347cc-170">does not support the \* construct.</span></span> <span data-ttu-id="347cc-171">Zapytania transact-SQL `select * from T` formularza i `select T1.* from T1, T2...` mogą być [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażone w as `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="347cc-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="347cc-172">Ponadto te konstrukcje obsługi dziedziczenia (substytucyjność wartości), podczas gdy `select *` warianty są ograniczone do właściwości najwyższego poziomu zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="347cc-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-173">nie obsługuje `count(*)` agregacji.</span><span class="sxs-lookup"><span data-stu-id="347cc-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="347cc-174">Zamiast tego użyj polecenia cmdlet `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="347cc-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="347cc-175">Zmiany w grupie według</span><span class="sxs-lookup"><span data-stu-id="347cc-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-176">obsługuje aliasing `group by` klawiszy.</span><span class="sxs-lookup"><span data-stu-id="347cc-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="347cc-177">Wyrażenia w `select` klauzuli `having` i klauzuli `group by` musi odwoływać się do kluczy za pośrednictwem tych aliasów.</span><span class="sxs-lookup"><span data-stu-id="347cc-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="347cc-178">Na przykład [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ta składnia:</span><span class="sxs-lookup"><span data-stu-id="347cc-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="347cc-179">... odpowiada następującemu transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="347cc-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="347cc-180">Agregaty oparte na kolekcji</span><span class="sxs-lookup"><span data-stu-id="347cc-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-181">obsługuje dwa rodzaje agregatów.</span><span class="sxs-lookup"><span data-stu-id="347cc-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="347cc-182">Agregaty oparte na kolekcji działają na kolekcjach i generują zagregowany wynik.</span><span class="sxs-lookup"><span data-stu-id="347cc-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="347cc-183">Mogą one pojawić się w dowolnym miejscu `group by` w kwerendzie i nie wymagają klauzuli.</span><span class="sxs-lookup"><span data-stu-id="347cc-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="347cc-184">Przykład:</span><span class="sxs-lookup"><span data-stu-id="347cc-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-185">obsługuje również agregacje w stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="347cc-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="347cc-186">Przykład:</span><span class="sxs-lookup"><span data-stu-id="347cc-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="347cc-187">ORDER BY Użycie klauzuli</span><span class="sxs-lookup"><span data-stu-id="347cc-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="347cc-188">Transact-SQL `ORDER BY` umożliwia klauzule, które mają `SELECT .. FROM .. WHERE` być określone tylko w głównym bloku.</span><span class="sxs-lookup"><span data-stu-id="347cc-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="347cc-189">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można użyć wyrażenia `ORDER BY` zagnieżdżonego i może być umieszczony w dowolnym miejscu w kwerendzie, ale kolejność w kwerendzie zagnieżdżonej nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="347cc-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="347cc-190">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="347cc-190">Identifiers</span></span>  
 <span data-ttu-id="347cc-191">W Transact-SQL porównanie identyfikatorów opiera się na sortowanie bieżącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="347cc-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="347cc-192">W [!INCLUDE[esql](../../../../../../includes/esql-md.md)]identyfikatorach zawsze są niewrażliwe na wielkość liter [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i akcenty (to oznacza, że rozróżnia znaki akcentowane i bez akcentu; na przykład "a" nie jest równe "ѕ").</span><span class="sxs-lookup"><span data-stu-id="347cc-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-193">traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych, jak różne znaki.</span><span class="sxs-lookup"><span data-stu-id="347cc-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="347cc-194">Aby uzyskać więcej informacji, zobacz [Input Character Set](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="347cc-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="347cc-195">Funkcja Transact-SQL niedostępna w programie Entity SQL</span><span class="sxs-lookup"><span data-stu-id="347cc-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="347cc-196">Następująca funkcja Transact-SQL nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest dostępna w programie .</span><span class="sxs-lookup"><span data-stu-id="347cc-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="347cc-197">Dml</span><span class="sxs-lookup"><span data-stu-id="347cc-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-198">obecnie nie zapewnia obsługi instrukcji DML (wstaw, aktualizacja, usuwanie).</span><span class="sxs-lookup"><span data-stu-id="347cc-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="347cc-199">Ddl</span><span class="sxs-lookup"><span data-stu-id="347cc-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-200">nie zapewnia obsługi DDL w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="347cc-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="347cc-201">programowanie imperatywne</span><span class="sxs-lookup"><span data-stu-id="347cc-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-202">nie zapewnia obsługi programowania imperatywowego, w przeciwieństwie do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="347cc-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="347cc-203">Zamiast tego użyj języka programowania.</span><span class="sxs-lookup"><span data-stu-id="347cc-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="347cc-204">Funkcje grupowania</span><span class="sxs-lookup"><span data-stu-id="347cc-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-205">nie zapewnia jeszcze obsługi funkcji grupowania (na przykład CUBE, ROLLUP i GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="347cc-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="347cc-206">Funkcje analityczne</span><span class="sxs-lookup"><span data-stu-id="347cc-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-207">nie zapewnia (jeszcze) wsparcia dla funkcji analitycznych.</span><span class="sxs-lookup"><span data-stu-id="347cc-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="347cc-208">Wbudowane funkcje, operatorzy</span><span class="sxs-lookup"><span data-stu-id="347cc-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-209">obsługuje podzbiór wbudowanych funkcji i operatorów Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="347cc-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="347cc-210">Te operatory i funkcje mogą być obsługiwane przez głównych dostawców sklepu.</span><span class="sxs-lookup"><span data-stu-id="347cc-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-211">używa funkcji specyficznych dla magazynu zadeklarowanych w manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="347cc-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="347cc-212">Ponadto entity framework umożliwia zadeklarowanie wbudowanych i zdefiniowanych przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] użytkownika istniejących funkcji magazynu, do użycia.</span><span class="sxs-lookup"><span data-stu-id="347cc-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="347cc-213">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="347cc-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-214">nie zapewnia mechanizmów dla wskazówek dotyczących zapytań.</span><span class="sxs-lookup"><span data-stu-id="347cc-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="347cc-215">Przetwarzanie wsadowe wyniki kwerendy</span><span class="sxs-lookup"><span data-stu-id="347cc-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-216">nie obsługuje wyników kwerendy wsadowe.</span><span class="sxs-lookup"><span data-stu-id="347cc-216">does not support batching query results.</span></span> <span data-ttu-id="347cc-217">Na przykład następujące jest prawidłowe Transact-SQL (wysyłanie jako partia):</span><span class="sxs-lookup"><span data-stu-id="347cc-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="347cc-218">Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwany:</span><span class="sxs-lookup"><span data-stu-id="347cc-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="347cc-219">obsługuje tylko jedną instrukcję kwerendy powodującą wynik na polecenie.</span><span class="sxs-lookup"><span data-stu-id="347cc-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347cc-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="347cc-220">See also</span></span>

- [<span data-ttu-id="347cc-221">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="347cc-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="347cc-222">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="347cc-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
