---
title: ISNULL (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7d880328c1006f418d50c02083e92f97b67627e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="ae4c2-102">ISNULL (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ae4c2-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="ae4c2-103">Określa, czy wyrażenie kwerendy jest null.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae4c2-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae4c2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ae4c2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ae4c2-106">Dowolne wyrażenie prawidłowe zapytanie.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-106">Any valid query expression.</span></span> <span data-ttu-id="ae4c2-107">Nie może być kolekcją, mieć elementów członkowskich kolekcji lub typ rekordu z kolekcji właściwości typu.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="ae4c2-108">NIE</span><span class="sxs-lookup"><span data-stu-id="ae4c2-108">NOT</span></span>  
 <span data-ttu-id="ae4c2-109">Negacja EDM. Wartość logiczna wynik jest NULL.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae4c2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae4c2-110">Return Value</span></span>  
 <span data-ttu-id="ae4c2-111">`true`Jeśli `expression` zwraca wartość null; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae4c2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae4c2-112">Remarks</span></span>  
 <span data-ttu-id="ae4c2-113">Użyj `IS NULL` do ustalenia, czy element sprzężenie zewnętrzne jest pusty:</span><span class="sxs-lookup"><span data-stu-id="ae4c2-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="ae4c2-114">Użyj `IS NULL` ustalenie, jeśli element członkowski ma wartość rzeczywista:</span><span class="sxs-lookup"><span data-stu-id="ae4c2-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="ae4c2-115">W poniższej tabeli przedstawiono zachowania `IS NULL` przez niektóre wzorce.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="ae4c2-116">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem pobiera dostawcy:</span><span class="sxs-lookup"><span data-stu-id="ae4c2-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="ae4c2-117">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ae4c2-117">Pattern</span></span>|<span data-ttu-id="ae4c2-118">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="ae4c2-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="ae4c2-119">wartość null jest puste</span><span class="sxs-lookup"><span data-stu-id="ae4c2-119">null IS NULL</span></span>|<span data-ttu-id="ae4c2-120">Zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-120">Returns `true`.</span></span>|  
|<span data-ttu-id="ae4c2-121">TRAKTUJ (wartość null dla obiektu AS) IS NULL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="ae4c2-122">Zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-122">Returns `true`.</span></span>|  
|<span data-ttu-id="ae4c2-123">TRAKTUJ (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="ae4c2-124">Zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-124">Throws an error.</span></span>|  
|<span data-ttu-id="ae4c2-125">TRAKTUJ (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="ae4c2-126">Zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-126">Throws an error.</span></span>|  
|<span data-ttu-id="ae4c2-127">Obiekt EntityType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-127">EntityType IS NULL</span></span>|<span data-ttu-id="ae4c2-128">Zwraca `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="ae4c2-129">Element ComplexType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-129">ComplexType IS NULL</span></span>|<span data-ttu-id="ae4c2-130">Zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-130">Throws an error.</span></span>|  
|<span data-ttu-id="ae4c2-131">RowType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-131">RowType IS NULL</span></span>|<span data-ttu-id="ae4c2-132">Zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae4c2-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae4c2-133">Example</span></span>  
 <span data-ttu-id="ae4c2-134">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora IS NOT NULL, aby określić, czy wyrażenie zapytania nie jest zerowa.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="ae4c2-135">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ae4c2-136">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ae4c2-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ae4c2-137">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ae4c2-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ae4c2-138">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ae4c2-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="ae4c2-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae4c2-139">See Also</span></span>  
 [<span data-ttu-id="ae4c2-140">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ae4c2-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
