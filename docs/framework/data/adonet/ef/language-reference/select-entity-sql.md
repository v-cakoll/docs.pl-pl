---
title: Wybierz (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 26d62b4ccab71d1d21a8f65f7feacb8cec727a94
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="select-entity-sql"></a><span data-ttu-id="594e2-102">Wybierz (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="594e2-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="594e2-103">Określa elementów zwróconych przez kwerendę.</span><span class="sxs-lookup"><span data-stu-id="594e2-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="594e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="594e2-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="594e2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="594e2-105">Arguments</span></span>  
 <span data-ttu-id="594e2-106">WSZYSTKIE</span><span class="sxs-lookup"><span data-stu-id="594e2-106">ALL</span></span>  
 <span data-ttu-id="594e2-107">Określa, czy duplikaty może występować w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="594e2-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="594e2-108">WSZYSTKO to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="594e2-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="594e2-109">RÓŻNE</span><span class="sxs-lookup"><span data-stu-id="594e2-109">DISTINCT</span></span>  
 <span data-ttu-id="594e2-110">Określa, że wyniki tylko unikatowe może występować w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="594e2-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="594e2-111">WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="594e2-111">VALUE</span></span>  
 <span data-ttu-id="594e2-112">Zezwala na tylko jeden element, aby określić, a nie dodać otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="594e2-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="594e2-113">Prawidłowe wyrażenie, wskazującą liczbę pierwszy wyników do zwrócenia z kwerendy w postaci `top (``expr``)`.</span><span class="sxs-lookup"><span data-stu-id="594e2-113">Any valid expression that indicates the number of first results to return from the query, of the form `top (``expr``)`.</span></span>  
  
 <span data-ttu-id="594e2-114">Parametr limitu [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator umożliwia również wybrać pierwsze n elementów zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="594e2-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="594e2-115">Wyrażenie w postaci:</span><span class="sxs-lookup"><span data-stu-id="594e2-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="594e2-116">`expr`jako `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="594e2-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="594e2-117">Literał lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="594e2-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="594e2-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="594e2-118">Remarks</span></span>  
 <span data-ttu-id="594e2-119">W klauzuli SELECT jest oceniane po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), i [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) klauzule zostały ocenione.</span><span class="sxs-lookup"><span data-stu-id="594e2-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="594e2-120">Klauzula SELECT może odwoływać się tylko do elementów aktualnie w zakresie (z klauzuli FROM lub zakresy zewnętrzne).</span><span class="sxs-lookup"><span data-stu-id="594e2-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="594e2-121">Jeśli określono klauzuli GROUP BY klauzuli SELECT jest dozwolona tylko do odwołania aliasów dla kluczy GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="594e2-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="594e2-122">Odwołania do elementów Klauzula FROM jest dozwolony tylko w funkcjach agregujących.</span><span class="sxs-lookup"><span data-stu-id="594e2-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="594e2-123">Lista po słowie kluczowym wybierz co najmniej jednego wyrażenia zapytania jest znany jako lista wyboru lub więcej formalnie projekcji.</span><span class="sxs-lookup"><span data-stu-id="594e2-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="594e2-124">Najbardziej ogólnym postaci projekcji to wyrażenie pojedynczego zapytania.</span><span class="sxs-lookup"><span data-stu-id="594e2-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="594e2-125">W przypadku wybrania członka `member1` z kolekcji `collection1`, utworzy nową kolekcję wszystkich `member1` wartości dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="594e2-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="594e2-126">Na przykład jeśli `customers` jest kolekcją typu `Customer` mający właściwość `Name` jest typu `string`, wybierając żądane `Name` z `customers` umożliwia uzyskanie kolekcji ciągów, jak pokazano w poniższym przykładzie .</span><span class="sxs-lookup"><span data-stu-id="594e2-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="594e2-127">Istnieje również możliwość użycia składni klauzuli JOIN (FULL, wewnętrzny, po lewej, zewnętrzne, ON i po prawej).</span><span class="sxs-lookup"><span data-stu-id="594e2-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="594e2-128">ON jest wymagana do sprzężenia wewnętrzne i jest nAby dozwolone w przypadku wielu sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="594e2-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="594e2-129">Wiersz i wartość klauzule Select</span><span class="sxs-lookup"><span data-stu-id="594e2-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="594e2-130">obsługuje dwa rodzaje klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="594e2-130"> supports two variants of the SELECT clause.</span></span> <span data-ttu-id="594e2-131">Pierwszy variant, wybierz wiersz, jest identyfikowany przez wybierz — słowo kluczowe i może służyć do określenia jednego lub więcej wartości, które należy utworzyć projekcji limit. Wynik wyrażenia zapytania, ponieważ otoki wiersza jest niejawnie dodane wokół wartości zwracane, jest zawsze multiset wierszy.</span><span class="sxs-lookup"><span data-stu-id="594e2-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="594e2-132">Każde wyrażenie zapytania w klauzuli select wiersz należy określić alias.</span><span class="sxs-lookup"><span data-stu-id="594e2-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="594e2-133">Jeśli jest określony żaden alias[!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować za pomocą reguł generowania aliasu alias.</span><span class="sxs-lookup"><span data-stu-id="594e2-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="594e2-134">Wariant klauzuli SELECT, wybierz wartość jest identyfikowany przez SELECT VALUE — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="594e2-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="594e2-135">Zezwala na tylko jedną wartość, należy określić i dodaje otoki wiersza.</span><span class="sxs-lookup"><span data-stu-id="594e2-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="594e2-136">Wybierz wiersz jest zawsze można wyrazić pod względem wartości wybierz, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="594e2-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="594e2-137">Wszystkie i różne modyfikatorów</span><span class="sxs-lookup"><span data-stu-id="594e2-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="594e2-138">Oba rodzaje wybierz w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zezwalaj specyfikację ALL lub modyfikator DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="594e2-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="594e2-139">Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji utworzonej przez wyrażenie kwerendy (, w tym klauzula SELECT).</span><span class="sxs-lookup"><span data-stu-id="594e2-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="594e2-140">Jeśli wszystkie modyfikator jest określony, nie zduplikowane eliminacji jest wykonywane; WSZYSTKO to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="594e2-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="594e2-141">Różnice języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="594e2-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="594e2-142">W przeciwieństwie do języka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje użycia \* argument w klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="594e2-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="594e2-143">Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia kwerendy projektu limit całych rekordów odwołując aliasy kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="594e2-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="594e2-144">Poprzedni [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażenie kwerendy jest wyrażona w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="594e2-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="594e2-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="594e2-145">Example</span></span>  
 <span data-ttu-id="594e2-146">Następujące zapytanie SQL jednostki użyto operatora SELECT do określenia elementy będą zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="594e2-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="594e2-147">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="594e2-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="594e2-148">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="594e2-148">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="594e2-149">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="594e2-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="594e2-150">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="594e2-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="594e2-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="594e2-151">See Also</span></span>  
 [<span data-ttu-id="594e2-152">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="594e2-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="594e2-153">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="594e2-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="594e2-154">TOP</span><span class="sxs-lookup"><span data-stu-id="594e2-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
