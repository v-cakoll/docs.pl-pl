---
title: ORDER BY (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 5cffd7a696496f92ae83822faff2f08e325eea93
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="1d219-102">ORDER BY (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1d219-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="1d219-103">Określa porządek sortowania używane dla obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="1d219-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d219-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d219-104">Syntax</span></span>  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d219-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1d219-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="1d219-106">Dowolne wyrażenie prawidłowe zapytanie, określając właściwości do sortowania.</span><span class="sxs-lookup"><span data-stu-id="1d219-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="1d219-107">Można określić wiele wyrażeń sortowania.</span><span class="sxs-lookup"><span data-stu-id="1d219-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="1d219-108">Taką sekwencję wyrażeń sortowania w klauzuli ORDER BY definiuje organizacji zestawu wyników posortowane.</span><span class="sxs-lookup"><span data-stu-id="1d219-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="1d219-109">Instrukcji COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="1d219-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="1d219-110">Określa, czy można wykonać operacji ORDER BY, zgodnie z Sortowanie określone w `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="1d219-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="1d219-111">Instrukcji COLLATE ma zastosowanie tylko w przypadku wyrażenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="1d219-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="1d219-112">ASC</span><span class="sxs-lookup"><span data-stu-id="1d219-112">ASC</span></span>  
 <span data-ttu-id="1d219-113">Określa, że wartości w określonej właściwości mają być sortowane w kolejności rosnącej, od najniższej wartości do największej wartości.</span><span class="sxs-lookup"><span data-stu-id="1d219-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="1d219-114">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1d219-114">This is the default.</span></span>  
  
 <span data-ttu-id="1d219-115">DESC</span><span class="sxs-lookup"><span data-stu-id="1d219-115">DESC</span></span>  
 <span data-ttu-id="1d219-116">Określa, że wartości w określonej właściwości mają być sortowane w kolejności malejącej, z najwyższą wartością najniższą wartość.</span><span class="sxs-lookup"><span data-stu-id="1d219-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="1d219-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="1d219-117">LIMIT `n`</span></span>  
 <span data-ttu-id="1d219-118">Tylko pierwszy `n` zostaną wybrane elementy.</span><span class="sxs-lookup"><span data-stu-id="1d219-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="1d219-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="1d219-119">SKIP `n`</span></span>  
 <span data-ttu-id="1d219-120">Pomija pierwszy `n` elementów.</span><span class="sxs-lookup"><span data-stu-id="1d219-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d219-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d219-121">Remarks</span></span>  
 <span data-ttu-id="1d219-122">W klauzuli ORDER BY logicznie jest stosowany do wyniku klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="1d219-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="1d219-123">W klauzuli ORDER BY może odwoływać się elementy na liście wyboru przy użyciu ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="1d219-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="1d219-124">W klauzuli ORDER BY, można także odwoływać inne zmienne, które są obecnie w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1d219-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="1d219-125">Jednak jeśli określono w klauzuli SELECT DISTINCT modyfikatorem klauzuli ORDER BY może odwoływać się tylko aliasy w klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="1d219-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="1d219-126">Każde wyrażenie w klauzuli ORDER BY musi zwrócić pewien typ, który można porównywać pod kątem nierówności uporządkowanych, (mniejsze lub większe niż i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="1d219-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="1d219-127">Te typy są zazwyczaj skalarne w nim elementów podstawowych, takich jak liczby, ciągi i daty.</span><span class="sxs-lookup"><span data-stu-id="1d219-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="1d219-128">RowTypes typy można porównywać są również umożliwia porównywanie kolejności.</span><span class="sxs-lookup"><span data-stu-id="1d219-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="1d219-129">Jeśli kod przechodzi przez uporządkowany zestaw, innych niż dla projekcji najwyższego poziomu, dane wyjściowe nie jest gwarantowana mają ich kolejność zachowane.</span><span class="sxs-lookup"><span data-stu-id="1d219-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
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
  
 <span data-ttu-id="1d219-130">Aby mieć uporządkowanej UNION, UNION ALL, EXCEPT lub INTERSECT operację, należy użyć następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="1d219-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="1d219-131">Ograniczone słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1d219-131">Restricted keywords</span></span>  
 <span data-ttu-id="1d219-132">Poniższe słowa kluczowe muszą być ujęte w cudzysłów, gdy są używane w `ORDER BY` klauzuli:</span><span class="sxs-lookup"><span data-stu-id="1d219-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
-   <span data-ttu-id="1d219-133">CROSS</span><span class="sxs-lookup"><span data-stu-id="1d219-133">CROSS</span></span>  
  
-   <span data-ttu-id="1d219-134">PEŁNA</span><span class="sxs-lookup"><span data-stu-id="1d219-134">FULL</span></span>  
  
-   <span data-ttu-id="1d219-135">KLUCZ</span><span class="sxs-lookup"><span data-stu-id="1d219-135">KEY</span></span>  
  
-   <span data-ttu-id="1d219-136">PO LEWEJ</span><span class="sxs-lookup"><span data-stu-id="1d219-136">LEFT</span></span>  
  
-   <span data-ttu-id="1d219-137">KOLEJNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="1d219-137">ORDER</span></span>  
  
-   <span data-ttu-id="1d219-138">ZEWNĘTRZNE</span><span class="sxs-lookup"><span data-stu-id="1d219-138">OUTER</span></span>  
  
-   <span data-ttu-id="1d219-139">PRAWO</span><span class="sxs-lookup"><span data-stu-id="1d219-139">RIGHT</span></span>  
  
-   <span data-ttu-id="1d219-140">WIERSZ</span><span class="sxs-lookup"><span data-stu-id="1d219-140">ROW</span></span>  
  
-   <span data-ttu-id="1d219-141">WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="1d219-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="1d219-142">Porządkowanie zapytania zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="1d219-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="1d219-143">W ramach jednostki zagnieżdżone wyrażenia mogą umieszczać w dowolnym miejscu kwerendy; kolejność zapytanie zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="1d219-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="1d219-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d219-144">Example</span></span>  
 <span data-ttu-id="1d219-145">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ORDER BY, aby określić kolejność sortowania użyć obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="1d219-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="1d219-146">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1d219-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1d219-147">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1d219-147">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1d219-148">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1d219-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1d219-149">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1d219-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="1d219-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d219-150">See Also</span></span>  
 [<span data-ttu-id="1d219-151">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="1d219-151">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="1d219-152">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1d219-152">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1d219-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="1d219-153">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="1d219-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="1d219-154">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="1d219-155">TOP</span><span class="sxs-lookup"><span data-stu-id="1d219-155">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
