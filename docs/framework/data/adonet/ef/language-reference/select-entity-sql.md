---
title: Wybierz (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 93eea5d539e943c57ed7c6236caa854486ac238e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933856"
---
# <a name="select-entity-sql"></a><span data-ttu-id="eef71-102">Wybierz (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="eef71-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="eef71-103">Określa elementów zwróconych przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="eef71-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef71-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eef71-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="eef71-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="eef71-105">Arguments</span></span>  
 <span data-ttu-id="eef71-106">WSZYSTKIE</span><span class="sxs-lookup"><span data-stu-id="eef71-106">ALL</span></span>  
 <span data-ttu-id="eef71-107">Określa, czy duplikaty może znajdować się w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="eef71-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="eef71-108">WSZYSTKO jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="eef71-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="eef71-109">ODRĘBNE</span><span class="sxs-lookup"><span data-stu-id="eef71-109">DISTINCT</span></span>  
 <span data-ttu-id="eef71-110">Określa, że tylko unikatowe wyniki może znajdować się w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="eef71-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="eef71-111">WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="eef71-111">VALUE</span></span>  
 <span data-ttu-id="eef71-112">Zezwala na tylko jeden element ma być określony i nie powoduje dodania na otokę wiersza.</span><span class="sxs-lookup"><span data-stu-id="eef71-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="eef71-113">Dowolne prawidłowe wyrażenie, wskazującą liczbę pierwszych wyników do zwrócenia z zapytania w postaci `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="eef71-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="eef71-114">Parametr limitu [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator umożliwia także wybrać pierwsze n elementów zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="eef71-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="eef71-115">Wyrażenie formularza:</span><span class="sxs-lookup"><span data-stu-id="eef71-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="eef71-116">`expr` jako `identifier`&#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="eef71-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="eef71-117">Literał lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="eef71-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eef71-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eef71-118">Remarks</span></span>  
 <span data-ttu-id="eef71-119">Klauzula SELECT jest oceniane po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), i [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) klauzule zostały ocenione.</span><span class="sxs-lookup"><span data-stu-id="eef71-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="eef71-120">Klauzula SELECT może odwoływać się tylko do elementów aktualnie w zakresie (z klauzuli FROM lub zakresy zewnętrznych).</span><span class="sxs-lookup"><span data-stu-id="eef71-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="eef71-121">Jeśli określono klauzuli GROUP BY w klauzuli SELECT jest dozwolona tylko k odkazu aliasów dla kluczy GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="eef71-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="eef71-122">Odwołania do elementów Klauzula FROM jest dozwolona tylko w funkcjach agregujących.</span><span class="sxs-lookup"><span data-stu-id="eef71-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="eef71-123">Listę po słowie kluczowym wybierz co najmniej jednego wyrażenia kwerendy jest określany jako listy wyboru lub bardziej formalnie projekcji.</span><span class="sxs-lookup"><span data-stu-id="eef71-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="eef71-124">Najbardziej ogólną postaci projekcji jest wyrażeniem pojedynczego zapytania.</span><span class="sxs-lookup"><span data-stu-id="eef71-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="eef71-125">Jeśli wybierzesz członka `member1` z kolekcji `collection1`, generuje nowy zbiór wszystkich `member1` wartości dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="eef71-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="eef71-126">Na przykład jeśli `customers` jest kolekcją typów `Customer` zawierający właściwości `Name` jest typu `string`, wybierając opcję `Name` z `customers` przyniesie to zbiór ciągów, jak pokazano w poniższym przykładzie .</span><span class="sxs-lookup"><span data-stu-id="eef71-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="eef71-127">Użytkownik może również użyć składni klauzuli JOIN (pełnej, wewnętrzne, po lewej stronie, zewnętrzne, ON i po prawej stronie).</span><span class="sxs-lookup"><span data-stu-id="eef71-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="eef71-128">ON jest wymagana dla sprzężenia wewnętrzne i jest nAby dozwolone w przypadku wielu sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="eef71-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="eef71-129">Wiersz i klauzule wybierz wartość</span><span class="sxs-lookup"><span data-stu-id="eef71-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="eef71-130"> obsługuje dwa warianty klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="eef71-130"> supports two variants of the SELECT clause.</span></span> <span data-ttu-id="eef71-131">Pierwszy typ variant, wybierz wiersz jest identyfikowane za pomocą słowa kluczowego wybierz i może służyć do określenia co najmniej jednej wartości, które powinien być przekazywany się. Wynik wyrażenia zapytania, ponieważ wokół wartości zwracanych niejawnie dodaniu otoki wiersza jest zawsze multiset wierszy.</span><span class="sxs-lookup"><span data-stu-id="eef71-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="eef71-132">Każde wyrażenie zapytania, wybierz wiersz w należy określić alias.</span><span class="sxs-lookup"><span data-stu-id="eef71-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="eef71-133">Jeśli brak aliasu jest określony,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje go wygenerować aliasem, za pomocą reguł generowania aliasu.</span><span class="sxs-lookup"><span data-stu-id="eef71-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="eef71-134">Wariant klauzuli SELECT, wybierz wartość, jest identyfikowany przez SELECT VALUE — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="eef71-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="eef71-135">Umożliwia ona tylko jedną wartość, należy określić i nie powoduje dodania otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="eef71-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="eef71-136">Wybierz wiersz jest zawsze można wyrazić pod względem wybierz wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="eef71-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="eef71-137">Wszystkie i różne modyfikatorów</span><span class="sxs-lookup"><span data-stu-id="eef71-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="eef71-138">Oba warianty wybór w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] specyfikacji wszystkie lub modyfikator DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="eef71-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="eef71-139">Jeśli modyfikator DISTINCT jest określony, duplikaty są eliminowane z kolekcji, generowane przez wyrażenie zapytania (, w tym klauzula SELECT).</span><span class="sxs-lookup"><span data-stu-id="eef71-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="eef71-140">Jeśli wszystkie modyfikator jest określony, nie zduplikowane odbywa się eliminacji; WSZYSTKO jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="eef71-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="eef71-141">Różnice w języku Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eef71-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="eef71-142">W przeciwieństwie do języka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje korzystanie z \* argument w klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="eef71-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="eef71-143">Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia zapytania do projektu się całych rekordów, odwołując się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="eef71-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="eef71-144">Poprzedni [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażenie kwerendy jest będzie wyrażana [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="eef71-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="eef71-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="eef71-145">Example</span></span>  
 <span data-ttu-id="eef71-146">Następujące zapytanie SQL jednostki używa wybierz operator, określić elementy, które mają zostać zwrócone przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="eef71-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="eef71-147">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eef71-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eef71-148">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="eef71-148">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="eef71-149">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytania, że zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eef71-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="eef71-150">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="eef71-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="eef71-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eef71-151">See Also</span></span>  
 [<span data-ttu-id="eef71-152">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="eef71-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="eef71-153">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="eef71-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="eef71-154">TOP</span><span class="sxs-lookup"><span data-stu-id="eef71-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
