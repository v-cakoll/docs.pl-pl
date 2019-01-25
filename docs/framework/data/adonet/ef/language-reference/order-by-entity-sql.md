---
title: ORDER BY (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: ac888a26f906d8439b51c9c56d966440d7a25b7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670202"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="b4d21-102">ORDER BY (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="b4d21-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="b4d21-103">Określa porządek sortowania na obiekty zwrócone w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4d21-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4d21-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="b4d21-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b4d21-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="b4d21-106">Dowolne wyrażenie prawidłowe zapytanie, określając właściwość do sortowania.</span><span class="sxs-lookup"><span data-stu-id="b4d21-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="b4d21-107">Można określić wiele wyrażeń sortowania.</span><span class="sxs-lookup"><span data-stu-id="b4d21-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="b4d21-108">Taką sekwencję wyrażeń sortowania w klauzuli ORDER BY określa organizacji zestawu posortowanego wyników.</span><span class="sxs-lookup"><span data-stu-id="b4d21-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="b4d21-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="b4d21-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="b4d21-110">Określa, czy można wykonać operacji klauzuli ORDER BY, zgodnie z sortowania określonego w `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="b4d21-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="b4d21-111">COLLATE ma zastosowanie tylko w przypadku wyrażenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="b4d21-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="b4d21-112">ASC</span><span class="sxs-lookup"><span data-stu-id="b4d21-112">ASC</span></span>  
 <span data-ttu-id="b4d21-113">Określa, że wartości w określonej właściwości powinny być sortowane w kolejności rosnącej, od wartości najniższej do najwyższej wartości.</span><span class="sxs-lookup"><span data-stu-id="b4d21-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="b4d21-114">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b4d21-114">This is the default.</span></span>  
  
 <span data-ttu-id="b4d21-115">DESC</span><span class="sxs-lookup"><span data-stu-id="b4d21-115">DESC</span></span>  
 <span data-ttu-id="b4d21-116">Określa, że wartości w określonej właściwości powinny być sortowane w kolejności malejącej, z najwyższą wartość do najmniejszej wartości.</span><span class="sxs-lookup"><span data-stu-id="b4d21-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="b4d21-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="b4d21-117">LIMIT `n`</span></span>  
 <span data-ttu-id="b4d21-118">Tylko pierwszy `n` zostaną wybrane elementy.</span><span class="sxs-lookup"><span data-stu-id="b4d21-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="b4d21-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="b4d21-119">SKIP `n`</span></span>  
 <span data-ttu-id="b4d21-120">Pominie pierwszy `n` elementów.</span><span class="sxs-lookup"><span data-stu-id="b4d21-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4d21-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4d21-121">Remarks</span></span>  
 <span data-ttu-id="b4d21-122">Klauzula ORDER BY logicznie jest stosowany do wyniku klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4d21-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="b4d21-123">Klauzuli ORDER BY może odwoływać się do elementów na liście wyboru przy użyciu ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="b4d21-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="b4d21-124">Klauzula ORDER BY może także odwoływać się inne zmienne, które są obecnie w zakresie.</span><span class="sxs-lookup"><span data-stu-id="b4d21-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="b4d21-125">Jednakże jeśli określono klauzuli SELECT DISTINCT modyfikatorem klauzuli ORDER BY może odwoływać się tylko aliasów w klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4d21-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="b4d21-126">Każde wyrażenie w klauzuli ORDER BY muszą być pewnego typu, który można porównać pod kątem nierówności uporządkowanym, (mniejsze lub większe niż, i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="b4d21-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="b4d21-127">Te typy są zazwyczaj skalarną w nim elementów podstawowych, takich jak liczby, ciągi i daty.</span><span class="sxs-lookup"><span data-stu-id="b4d21-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="b4d21-128">RowTypes porównywalnych typów są również porównywanie kolejności.</span><span class="sxs-lookup"><span data-stu-id="b4d21-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="b4d21-129">Jeśli Twój kod wykonuje iterację na uporządkowany zestaw, innego niż projekcji najwyższego poziomu, dane wyjściowe nie gwarantuje jego zamówienia zachowywane są.</span><span class="sxs-lookup"><span data-stu-id="b4d21-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
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
  
 <span data-ttu-id="b4d21-130">Aby zostały uporządkowane UNION, UNION ALL, EXCEPT lub INTERSECT operację, należy użyć następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="b4d21-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="b4d21-131">Ograniczone słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="b4d21-131">Restricted keywords</span></span>  
 <span data-ttu-id="b4d21-132">Następujące słowa kluczowe muszą być ujęte w znaki cudzysłowu, gdy są używane w `ORDER BY` klauzuli:</span><span class="sxs-lookup"><span data-stu-id="b4d21-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
-   <span data-ttu-id="b4d21-133">CROSS</span><span class="sxs-lookup"><span data-stu-id="b4d21-133">CROSS</span></span>  
  
-   <span data-ttu-id="b4d21-134">FULL</span><span class="sxs-lookup"><span data-stu-id="b4d21-134">FULL</span></span>  
  
-   <span data-ttu-id="b4d21-135">KLUCZ</span><span class="sxs-lookup"><span data-stu-id="b4d21-135">KEY</span></span>  
  
-   <span data-ttu-id="b4d21-136">PO LEWEJ STRONIE</span><span class="sxs-lookup"><span data-stu-id="b4d21-136">LEFT</span></span>  
  
-   <span data-ttu-id="b4d21-137">KOLEJNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b4d21-137">ORDER</span></span>  
  
-   <span data-ttu-id="b4d21-138">ZEWNĘTRZNE</span><span class="sxs-lookup"><span data-stu-id="b4d21-138">OUTER</span></span>  
  
-   <span data-ttu-id="b4d21-139">PO PRAWEJ STRONIE</span><span class="sxs-lookup"><span data-stu-id="b4d21-139">RIGHT</span></span>  
  
-   <span data-ttu-id="b4d21-140">WIERSZ</span><span class="sxs-lookup"><span data-stu-id="b4d21-140">ROW</span></span>  
  
-   <span data-ttu-id="b4d21-141">WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b4d21-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="b4d21-142">Określanie kolejności zapytań zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="b4d21-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="b4d21-143">Platformy Entity Framework zagnieżdżone wyrażenie można umieścić w dowolnym miejscu w zapytania. kolejność zapytanie zagnieżdżone nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="b4d21-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b4d21-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4d21-144">Example</span></span>  
 <span data-ttu-id="b4d21-145">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora w klauzuli ORDER BY, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4d21-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="b4d21-146">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b4d21-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b4d21-147">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b4d21-147">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b4d21-148">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b4d21-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b4d21-149">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b4d21-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="b4d21-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4d21-150">See also</span></span>
- [<span data-ttu-id="b4d21-151">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="b4d21-151">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="b4d21-152">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b4d21-152">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="b4d21-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="b4d21-153">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [<span data-ttu-id="b4d21-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="b4d21-154">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [<span data-ttu-id="b4d21-155">TOP</span><span class="sxs-lookup"><span data-stu-id="b4d21-155">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
