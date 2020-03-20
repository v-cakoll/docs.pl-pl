---
title: ZAMÓWIENIE WEDŁUG (ENTITY SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150072"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="637f7-102">ZAMÓWIENIE WEDŁUG (ENTITY SQL)</span><span class="sxs-lookup"><span data-stu-id="637f7-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="637f7-103">Określa kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="637f7-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="637f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="637f7-104">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="637f7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="637f7-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="637f7-106">Dowolne prawidłowe wyrażenie kwerendy określające właściwość, na której ma być sortowane.</span><span class="sxs-lookup"><span data-stu-id="637f7-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="637f7-107">Można określić wiele wyrażeń sortowania.</span><span class="sxs-lookup"><span data-stu-id="637f7-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="637f7-108">Sekwencja wyrażeń sortowania w klauzuli ORDER BY definiuje organizację posortowanego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="637f7-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="637f7-109">SORTOWANIE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="637f7-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="637f7-110">Określa, że operacja ORDER BY powinna być wykonywana `collation_name`zgodnie z sortowaniem określonym w .</span><span class="sxs-lookup"><span data-stu-id="637f7-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="637f7-111">COLLATE ma zastosowanie tylko do wyrażeń ciągu.</span><span class="sxs-lookup"><span data-stu-id="637f7-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="637f7-112">ASC</span><span class="sxs-lookup"><span data-stu-id="637f7-112">ASC</span></span>  
 <span data-ttu-id="637f7-113">Określa, że wartości w określonej właściwości powinny być sortowane w porządku rosnącym, od najniższej wartości do najwyższej wartości.</span><span class="sxs-lookup"><span data-stu-id="637f7-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="637f7-114">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="637f7-114">This is the default.</span></span>  
  
 <span data-ttu-id="637f7-115">DESC</span><span class="sxs-lookup"><span data-stu-id="637f7-115">DESC</span></span>  
 <span data-ttu-id="637f7-116">Określa, że wartości w określonej właściwości powinny być sortowane w porządku malejącym, od najwyższej wartości do najniższej wartości.</span><span class="sxs-lookup"><span data-stu-id="637f7-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="637f7-117">Limit`n`</span><span class="sxs-lookup"><span data-stu-id="637f7-117">LIMIT `n`</span></span>  
 <span data-ttu-id="637f7-118">Zostaną wybrane `n` tylko pierwsze elementy.</span><span class="sxs-lookup"><span data-stu-id="637f7-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="637f7-119">Pominąć`n`</span><span class="sxs-lookup"><span data-stu-id="637f7-119">SKIP `n`</span></span>  
 <span data-ttu-id="637f7-120">Pomija pierwsze `n` elementy.</span><span class="sxs-lookup"><span data-stu-id="637f7-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="637f7-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="637f7-121">Remarks</span></span>  
 <span data-ttu-id="637f7-122">Klauzula ORDER BY jest logicznie stosowana do wyniku select klauzuli.</span><span class="sxs-lookup"><span data-stu-id="637f7-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="637f7-123">Klauzula ORDER BY może odwoływać się do elementów na liście select przy użyciu ich aliasów.</span><span class="sxs-lookup"><span data-stu-id="637f7-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="637f7-124">Order BY klauzula może również odwoływać się do innych zmiennych, które są obecnie w zakresie.</span><span class="sxs-lookup"><span data-stu-id="637f7-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="637f7-125">Jednak jeśli SELECT klauzuli został określony z distinct modyfikatora, ORDER BY klauzuli może odwoływać się tylko aliasy z SELECT klauzuli.</span><span class="sxs-lookup"><span data-stu-id="637f7-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="637f7-126">Każde wyrażenie w klauzuli ORDER BY musi ocenić do pewnego typu, które można porównać dla uporządkowanej nierówności (mniejszej lub większej niż itd.).</span><span class="sxs-lookup"><span data-stu-id="637f7-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="637f7-127">Te typy są zazwyczaj skalarne prymitywów, takich jak liczby, ciągi i daty.</span><span class="sxs-lookup"><span data-stu-id="637f7-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="637f7-128">RowTypes porównywalnych typów są również kolejność porównywalne.</span><span class="sxs-lookup"><span data-stu-id="637f7-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="637f7-129">Jeśli kod iteruje za pomocą uporządkowanego zestawu, innego niż dla projekcji najwyższego poziomu, dane wyjściowe nie jest gwarantowana, aby jego kolejność została zachowana.</span><span class="sxs-lookup"><span data-stu-id="637f7-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="637f7-130">W poniższej próbce kolejność jest gwarantowana do zachowania:</span><span class="sxs-lookup"><span data-stu-id="637f7-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="637f7-131">W następującej kwerendzie kolejność zagnieżdżonej kwerendy jest ignorowana:</span><span class="sxs-lookup"><span data-stu-id="637f7-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="637f7-132">Aby mieć uporządkowaną operację UNION, UNION ALL, EXCEPT lub INTERSECT, użyj następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="637f7-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="637f7-133">Słowa kluczowe z ograniczeniami</span><span class="sxs-lookup"><span data-stu-id="637f7-133">Restricted keywords</span></span>  
 <span data-ttu-id="637f7-134">Następujące słowa kluczowe muszą być ujęte w `ORDER BY` cudzysłów, gdy są używane w klauzuli:</span><span class="sxs-lookup"><span data-stu-id="637f7-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="637f7-135">Krzyż</span><span class="sxs-lookup"><span data-stu-id="637f7-135">CROSS</span></span>  
  
- <span data-ttu-id="637f7-136">Pełne</span><span class="sxs-lookup"><span data-stu-id="637f7-136">FULL</span></span>  
  
- <span data-ttu-id="637f7-137">KEY</span><span class="sxs-lookup"><span data-stu-id="637f7-137">KEY</span></span>  
  
- <span data-ttu-id="637f7-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="637f7-138">LEFT</span></span>  
  
- <span data-ttu-id="637f7-139">Zamówienia</span><span class="sxs-lookup"><span data-stu-id="637f7-139">ORDER</span></span>  
  
- <span data-ttu-id="637f7-140">Zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="637f7-140">OUTER</span></span>  
  
- <span data-ttu-id="637f7-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="637f7-141">RIGHT</span></span>  
  
- <span data-ttu-id="637f7-142">ROW</span><span class="sxs-lookup"><span data-stu-id="637f7-142">ROW</span></span>  
  
- <span data-ttu-id="637f7-143">WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="637f7-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="637f7-144">Zamawianie zapytań zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="637f7-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="637f7-145">W ramach encji zagnieżdżone wyrażenie można umieścić w dowolnym miejscu w kwerendzie; kolejność kwerendy zagnieżdżonej nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="637f7-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="637f7-146">Następująca kwerenda zamówi wyniki według nazwiska:</span><span class="sxs-lookup"><span data-stu-id="637f7-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="637f7-147">W następującej kwerendzie kolejność zagnieżdżonej kwerendy jest ignorowana:</span><span class="sxs-lookup"><span data-stu-id="637f7-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="637f7-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="637f7-148">Example</span></span>  
 <span data-ttu-id="637f7-149">Następująca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kwerenda używa operatora ORDER BY do określenia kolejności sortowania używanej dla obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="637f7-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="637f7-150">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="637f7-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="637f7-151">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="637f7-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="637f7-152">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="637f7-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="637f7-153">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="637f7-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="637f7-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="637f7-154">See also</span></span>

- [<span data-ttu-id="637f7-155">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="637f7-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="637f7-156">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="637f7-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="637f7-157">Pominąć</span><span class="sxs-lookup"><span data-stu-id="637f7-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="637f7-158">Limit</span><span class="sxs-lookup"><span data-stu-id="637f7-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="637f7-159">Do góry</span><span class="sxs-lookup"><span data-stu-id="637f7-159">TOP</span></span>](top-entity-sql.md)
