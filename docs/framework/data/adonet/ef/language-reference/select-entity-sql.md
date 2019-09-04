---
title: Wybierz (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249211"
---
# <a name="select-entity-sql"></a><span data-ttu-id="b52f3-102">Wybierz (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b52f3-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="b52f3-103">Określa elementy zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="b52f3-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b52f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b52f3-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="b52f3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b52f3-105">Arguments</span></span>  
 <span data-ttu-id="b52f3-106">CAŁĄ</span><span class="sxs-lookup"><span data-stu-id="b52f3-106">ALL</span></span>  
 <span data-ttu-id="b52f3-107">Określa, czy duplikaty mogą występować w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="b52f3-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="b52f3-108">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="b52f3-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="b52f3-109">ITP</span><span class="sxs-lookup"><span data-stu-id="b52f3-109">DISTINCT</span></span>  
 <span data-ttu-id="b52f3-110">Określa, że w zestawie wyników mogą występować tylko unikatowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="b52f3-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="b52f3-111">WARTOŚCIAMI</span><span class="sxs-lookup"><span data-stu-id="b52f3-111">VALUE</span></span>  
 <span data-ttu-id="b52f3-112">Zezwala na określenie tylko jednego elementu i nie dodaje go do otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="b52f3-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="b52f3-113">Dowolne prawidłowe wyrażenie określające liczbę pierwszych wyników do zwrócenia z zapytania w formularzu `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="b52f3-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="b52f3-114">Parametr LIMIT operatora [order by](order-by-entity-sql.md) umożliwia również wybranie pierwszych n elementów w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="b52f3-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="b52f3-115">Wyrażenie formularza:</span><span class="sxs-lookup"><span data-stu-id="b52f3-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="b52f3-116">`expr`jako `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="b52f3-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="b52f3-117">Literał lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b52f3-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b52f3-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b52f3-118">Remarks</span></span>  
 <span data-ttu-id="b52f3-119">Klauzula SELECT jest obliczana po obliczeniu klauzul [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)i [HAVING](having-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="b52f3-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="b52f3-120">Klauzula SELECT może odwoływać się tylko do elementów aktualnie znajdujących się w zakresie (z klauzuli FROM lub z zewnętrznych zakresów).</span><span class="sxs-lookup"><span data-stu-id="b52f3-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="b52f3-121">Jeśli określono klauzulę GROUP BY, klauzula SELECT może odwoływać się tylko do aliasów dla kluczy Grupuj według.</span><span class="sxs-lookup"><span data-stu-id="b52f3-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="b52f3-122">Odwołania do elementów klauzuli FROM są dozwolone tylko w funkcjach agregujących.</span><span class="sxs-lookup"><span data-stu-id="b52f3-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="b52f3-123">Lista co najmniej jednego wyrażenia zapytania po słowie kluczowym SELECT jest znana jako lista wyboru lub bardziej formalnie jako projekcja.</span><span class="sxs-lookup"><span data-stu-id="b52f3-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="b52f3-124">Najbardziej ogólną formą projekcji jest pojedyncze wyrażenie zapytania.</span><span class="sxs-lookup"><span data-stu-id="b52f3-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="b52f3-125">Wybranie elementu członkowskiego `member1` z kolekcji `collection1`spowoduje utworzenie `member1` nowej kolekcji wszystkich wartości dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b52f3-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="b52f3-126">Na przykład `customers` jeśli jest kolekcją typu `Customer` , który ma właściwość `Name` typu `string`, wybranie `Name` z `customers` spowoduje przekazanie kolekcji ciągów, jak pokazano w poniższym przykładzie. .</span><span class="sxs-lookup"><span data-stu-id="b52f3-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="b52f3-127">Istnieje również możliwość użycia składni JOIN (pełna, wewnętrzna, LEFT, OUTER, ON i RIGHT).</span><span class="sxs-lookup"><span data-stu-id="b52f3-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="b52f3-128">WŁĄCZONA jest wymagana dla sprzężeń wewnętrznych i jest to nAby możliwe dla sprzężeń krzyżowych.</span><span class="sxs-lookup"><span data-stu-id="b52f3-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="b52f3-129">Klauzule Select z wierszami i wartościami</span><span class="sxs-lookup"><span data-stu-id="b52f3-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b52f3-130">obsługuje dwa warianty klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="b52f3-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="b52f3-131">Pierwszy wariant, wybór wiersza, jest identyfikowany za pomocą słowa kluczowego SELECT i może służyć do określenia co najmniej jednej wartości, która ma zostać wyznaczony. Ponieważ otoka wierszy jest niejawnie dodawana wokół zwracanych wartości, wynik wyrażenia zapytania jest zawsze zestawem wielokrotnym wierszy.</span><span class="sxs-lookup"><span data-stu-id="b52f3-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="b52f3-132">Każde wyrażenie zapytania w wierszu wybierz musi określać alias.</span><span class="sxs-lookup"><span data-stu-id="b52f3-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="b52f3-133">Jeśli alias nie zostanie określony,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] program podejmie próbę wygenerowania aliasu przy użyciu reguł generowania aliasów.</span><span class="sxs-lookup"><span data-stu-id="b52f3-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="b52f3-134">Inny wariant klauzuli SELECT, select value jest identyfikowany za pomocą słowa kluczowego SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="b52f3-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="b52f3-135">Umożliwia określenie tylko jednej wartości i nie powoduje dodania otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="b52f3-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="b52f3-136">Wybór wiersza jest zawsze można wyrazić elementu w zakresie ZAZNACZania wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b52f3-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="b52f3-137">Modyfikatory All i DISTINCT</span><span class="sxs-lookup"><span data-stu-id="b52f3-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="b52f3-138">Oba warianty instrukcji SELECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w zezwalają na specyfikację modyfikatora All lub DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="b52f3-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="b52f3-139">Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji utworzonej przez wyrażenie zapytania (do i włącznie z klauzulą SELECT).</span><span class="sxs-lookup"><span data-stu-id="b52f3-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="b52f3-140">Jeśli modyfikator ALL jest określony, nie jest wykonywane duplikowanie eliminacji; Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="b52f3-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="b52f3-141">Różnice w języku Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b52f3-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="b52f3-142">W przeciwieństwie do języka Transact [!INCLUDE[esql](../../../../../../includes/esql-md.md)] -SQL, program nie obsługuje użycia argumentu \* w klauzuli select.</span><span class="sxs-lookup"><span data-stu-id="b52f3-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="b52f3-143">Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , program umożliwia zaprojektowanie całych rekordów, odwołując się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b52f3-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="b52f3-144">Poprzednie wyrażenie zapytania Transact-SQL jest wyrażone [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b52f3-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="b52f3-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="b52f3-145">Example</span></span>  
 <span data-ttu-id="b52f3-146">Poniższe zapytanie Entity SQL używa operatora SELECT, aby określić elementy do zwrócenia przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="b52f3-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="b52f3-147">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b52f3-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b52f3-148">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b52f3-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b52f3-149">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="b52f3-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b52f3-150">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b52f3-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="b52f3-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b52f3-151">See also</span></span>

- [<span data-ttu-id="b52f3-152">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="b52f3-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="b52f3-153">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b52f3-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b52f3-154">TOP</span><span class="sxs-lookup"><span data-stu-id="b52f3-154">TOP</span></span>](top-entity-sql.md)
