---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250558"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="13878-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="13878-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="13878-103">Określa, czy wyrażenie zapytania ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="13878-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13878-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13878-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="13878-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13878-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="13878-106">Dowolne prawidłowe wyrażenie zapytania.</span><span class="sxs-lookup"><span data-stu-id="13878-106">Any valid query expression.</span></span> <span data-ttu-id="13878-107">Nie może być kolekcją, mieć składowe kolekcji lub typem rekordu z właściwościami typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="13878-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="13878-108">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="13878-108">NOT</span></span>  
 <span data-ttu-id="13878-109">Negacja modelu EDM. Wynik wartości logicznej jest równy NULL.</span><span class="sxs-lookup"><span data-stu-id="13878-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13878-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13878-110">Return Value</span></span>  
 <span data-ttu-id="13878-111">`true`Jeśli `expression` zwraca wartość null; `false`w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="13878-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13878-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13878-112">Remarks</span></span>  
 <span data-ttu-id="13878-113">Użyj `IS NULL` , aby określić, czy element sprzężenia zewnętrznego ma wartość null:</span><span class="sxs-lookup"><span data-stu-id="13878-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="13878-114">Użyj `IS NULL` , aby określić, czy element członkowski ma rzeczywistą wartość:</span><span class="sxs-lookup"><span data-stu-id="13878-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="13878-115">W poniższej tabeli przedstawiono zachowanie `IS NULL` niektórych wzorców.</span><span class="sxs-lookup"><span data-stu-id="13878-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="13878-116">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:</span><span class="sxs-lookup"><span data-stu-id="13878-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="13878-117">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="13878-117">Pattern</span></span>|<span data-ttu-id="13878-118">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="13878-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="13878-119">wartość zerowa ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-119">null IS NULL</span></span>|<span data-ttu-id="13878-120">Zwraca `true`wartość.</span><span class="sxs-lookup"><span data-stu-id="13878-120">Returns `true`.</span></span>|  
|<span data-ttu-id="13878-121">TRAKTOWANIe (null jako EntityType) ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="13878-122">Zwraca `true`wartość.</span><span class="sxs-lookup"><span data-stu-id="13878-122">Returns `true`.</span></span>|  
|<span data-ttu-id="13878-123">TRAKTOWANIe (null jako ComplexType) ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="13878-124">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="13878-124">Throws an error.</span></span>|  
|<span data-ttu-id="13878-125">TRAKTOWANIe (null AS RowType) ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="13878-126">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="13878-126">Throws an error.</span></span>|  
|<span data-ttu-id="13878-127">Obiekt EntityType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-127">EntityType IS NULL</span></span>|<span data-ttu-id="13878-128">Zwraca `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="13878-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="13878-129">ComplexType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-129">ComplexType IS NULL</span></span>|<span data-ttu-id="13878-130">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="13878-130">Throws an error.</span></span>|  
|<span data-ttu-id="13878-131">RowType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="13878-131">RowType IS NULL</span></span>|<span data-ttu-id="13878-132">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="13878-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="13878-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="13878-133">Example</span></span>  
 <span data-ttu-id="13878-134">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora is not null, aby określić, czy wyrażenie zapytania nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="13878-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="13878-135">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="13878-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="13878-136">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="13878-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="13878-137">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="13878-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="13878-138">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="13878-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="13878-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13878-139">See also</span></span>

- [<span data-ttu-id="13878-140">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="13878-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
