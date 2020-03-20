---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149912"
---
# <a name="select-entity-sql"></a><span data-ttu-id="cc351-102">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cc351-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="cc351-103">Określa elementy zwracane przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="cc351-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc351-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc351-104">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc351-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cc351-105">Arguments</span></span>  
 <span data-ttu-id="cc351-106">ALL</span><span class="sxs-lookup"><span data-stu-id="cc351-106">ALL</span></span>  
 <span data-ttu-id="cc351-107">Określa, że duplikaty mogą pojawiać się w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="cc351-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="cc351-108">ALL jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="cc351-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="cc351-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="cc351-109">DISTINCT</span></span>  
 <span data-ttu-id="cc351-110">Określa, że w zestawie wyników mogą pojawić się tylko unikatowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="cc351-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="cc351-111">WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="cc351-111">VALUE</span></span>  
 <span data-ttu-id="cc351-112">Umożliwia określenie tylko jednego elementu i nie dodaje się do otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="cc351-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="cc351-113">Każde prawidłowe wyrażenie wskazujące liczbę pierwszych wyników do zwrócenia `top(expr)`z kwerendy formularza .</span><span class="sxs-lookup"><span data-stu-id="cc351-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="cc351-114">Parametr LIMIT operatora [ORDER BY](order-by-entity-sql.md) umożliwia również wybranie pierwszych n elementów w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="cc351-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="cc351-115">Wyrażenie formularza:</span><span class="sxs-lookup"><span data-stu-id="cc351-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="cc351-116">`expr`jak `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="cc351-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="cc351-117">Literał lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cc351-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc351-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc351-118">Remarks</span></span>  
 <span data-ttu-id="cc351-119">Klauzula SELECT jest oceniana po ocenie [klauzul FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)i [HAVING.](having-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="cc351-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="cc351-120">Klauzula SELECT może odwoływać się tylko do elementów aktualnie w zakresie (z klauzuli FROM lub z zakresów zewnętrznych).</span><span class="sxs-lookup"><span data-stu-id="cc351-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="cc351-121">Jeśli klauzula GROUP BY została określona, klauzula SELECT może odwoływać się tylko do aliasów dla kluczy GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="cc351-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="cc351-122">Odwoływanie się do elementów klauzuli FROM jest dozwolone tylko w funkcjach zagregowanych.</span><span class="sxs-lookup"><span data-stu-id="cc351-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="cc351-123">Lista co najmniej jednego wyrażenia kwerendy po słowie kluczowym SELECT jest znana jako lista select lub bardziej formalnie jako projekcja.</span><span class="sxs-lookup"><span data-stu-id="cc351-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="cc351-124">Najbardziej ogólną formą projekcji jest wyrażenie pojedynczego zapytania.</span><span class="sxs-lookup"><span data-stu-id="cc351-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="cc351-125">Jeśli wybierzesz `member1` element `collection1`członkowski z kolekcji, zostanie `member1` wyprodukowana nowa `collection1`kolekcja wszystkich wartości dla każdego obiektu w , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc351-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="cc351-126">Na przykład `customers` jeśli jest kolekcją `Customer` typu, `Name` który ma `string`właściwość, która jest typu, wybierając `Name` z `customers` przyniesie kolekcję ciągów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc351-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="cc351-127">Możliwe jest również użycie składni JOIN (FULL, INNER, LEFT, OUTER, ON i RIGHT).</span><span class="sxs-lookup"><span data-stu-id="cc351-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="cc351-128">ON jest wymagane dla sprzężeń wewnętrznych i jest nto dozwolone dla sprzężeń krzyżowych.</span><span class="sxs-lookup"><span data-stu-id="cc351-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="cc351-129">Klauzule wyboru wierszy i wartości</span><span class="sxs-lookup"><span data-stu-id="cc351-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cc351-130">obsługuje dwa warianty klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="cc351-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="cc351-131">Pierwszy wariant, wybierz wiersz, jest identyfikowany przez select słowa kluczowego i może służyć do określenia jednej lub więcej wartości, które powinny być rzutowane. Ponieważ otoka wiersza jest niejawnie dodawany wokół zwracanych wartości, wynik wyrażenia kwerendy jest zawsze wielokrotny zestaw wierszy.</span><span class="sxs-lookup"><span data-stu-id="cc351-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="cc351-132">Każde wyrażenie kwerendy w wierszu wybierające musi określać alias.</span><span class="sxs-lookup"><span data-stu-id="cc351-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="cc351-133">Jeśli nie określono aliasu,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias przy użyciu reguł generowania aliasu.</span><span class="sxs-lookup"><span data-stu-id="cc351-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="cc351-134">Inny wariant select klauzuli, wartość select, jest identyfikowany przez SELECT VALUE słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cc351-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="cc351-135">Umożliwia tylko jedną wartość, która ma być określona i nie dodaje otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="cc351-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="cc351-136">Wybór wiersza jest zawsze wyrażony w kategoriach WARTOŚĆ SELECT, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc351-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="cc351-137">Wszystkie i różne modyfikatory</span><span class="sxs-lookup"><span data-stu-id="cc351-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="cc351-138">Oba warianty SELECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwiają specyfikację modyfikatora ALL lub DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="cc351-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="cc351-139">Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji produkowanej przez wyrażenie kwerendy (do klauzuli SELECT włącznie).</span><span class="sxs-lookup"><span data-stu-id="cc351-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="cc351-140">Jeśli określono modyfikator ALL, nie jest wykonywana żadna eliminacja duplikatów; ALL jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="cc351-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="cc351-141">Różnice w stosunku do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc351-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="cc351-142">W przeciwieństwie do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL, nie obsługuje użycia \* argument w SELECT klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cc351-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="cc351-143">Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia kwerendom rzutowanie całych rekordów przez odwoływanie się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc351-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="cc351-144">Poprzednie wyrażenie zapytania Transact-SQL jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażone w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cc351-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="cc351-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc351-145">Example</span></span>  
 <span data-ttu-id="cc351-146">Następująca kwerenda SQL jednostki używa select operatora, aby określić elementy, które mają być zwracane przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="cc351-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="cc351-147">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cc351-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cc351-148">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cc351-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cc351-149">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cc351-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="cc351-150">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="cc351-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="cc351-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc351-151">See also</span></span>

- [<span data-ttu-id="cc351-152">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="cc351-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="cc351-153">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cc351-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="cc351-154">Do góry</span><span class="sxs-lookup"><span data-stu-id="cc351-154">TOP</span></span>](top-entity-sql.md)
