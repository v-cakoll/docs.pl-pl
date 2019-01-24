---
title: ISNULL (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 1b728e170968e2fbeb67eef3f8f940c64816ff0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528735"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="06366-102">ISNULL (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="06366-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="06366-103">Określa, czy wyrażenie zapytania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="06366-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06366-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06366-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="06366-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="06366-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="06366-106">Dowolne wyrażenie prawidłowe zapytanie.</span><span class="sxs-lookup"><span data-stu-id="06366-106">Any valid query expression.</span></span> <span data-ttu-id="06366-107">Nie może być kolekcją, elementów członkowskich kolekcji lub typ rekordu w kolekcji właściwości typu.</span><span class="sxs-lookup"><span data-stu-id="06366-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="06366-108">NIE</span><span class="sxs-lookup"><span data-stu-id="06366-108">NOT</span></span>  
 <span data-ttu-id="06366-109">Neguje EDM. Wartość logiczna wynikiem jest wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="06366-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06366-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="06366-110">Return Value</span></span>  
 <span data-ttu-id="06366-111">`true` Jeśli `expression` zwraca wartość null; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="06366-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06366-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06366-112">Remarks</span></span>  
 <span data-ttu-id="06366-113">Użyj `IS NULL` do ustalenia, czy element sprzężenie zewnętrzne jest wartość null:</span><span class="sxs-lookup"><span data-stu-id="06366-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="06366-114">Użyj `IS NULL` można sprawdzić, czy członek jest rzeczywista wartość:</span><span class="sxs-lookup"><span data-stu-id="06366-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="06366-115">W poniższej tabeli przedstawiono zachowania `IS NULL` przez niektóre wzorce.</span><span class="sxs-lookup"><span data-stu-id="06366-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="06366-116">Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem pobiera dostawcy:</span><span class="sxs-lookup"><span data-stu-id="06366-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="06366-117">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="06366-117">Pattern</span></span>|<span data-ttu-id="06366-118">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="06366-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="06366-119">wartość null jest puste</span><span class="sxs-lookup"><span data-stu-id="06366-119">null IS NULL</span></span>|<span data-ttu-id="06366-120">Zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="06366-120">Returns `true`.</span></span>|  
|<span data-ttu-id="06366-121">TRAKTUJ (wartość null dla obiektu AS) IS NULL</span><span class="sxs-lookup"><span data-stu-id="06366-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="06366-122">Zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="06366-122">Returns `true`.</span></span>|  
|<span data-ttu-id="06366-123">TRAKTUJ (o wartości null ComplexType AS) IS NULL</span><span class="sxs-lookup"><span data-stu-id="06366-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="06366-124">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="06366-124">Throws an error.</span></span>|  
|<span data-ttu-id="06366-125">TRAKTUJ (o wartości null RowType AS) IS NULL</span><span class="sxs-lookup"><span data-stu-id="06366-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="06366-126">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="06366-126">Throws an error.</span></span>|  
|<span data-ttu-id="06366-127">Obiekt EntityType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="06366-127">EntityType IS NULL</span></span>|<span data-ttu-id="06366-128">Zwraca `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="06366-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="06366-129">ComplexType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="06366-129">ComplexType IS NULL</span></span>|<span data-ttu-id="06366-130">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="06366-130">Throws an error.</span></span>|  
|<span data-ttu-id="06366-131">RowType ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="06366-131">RowType IS NULL</span></span>|<span data-ttu-id="06366-132">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="06366-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06366-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="06366-133">Example</span></span>  
 <span data-ttu-id="06366-134">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora IS NOT NULL, aby określić, jeśli wyrażenie zapytania nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="06366-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="06366-135">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="06366-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="06366-136">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="06366-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="06366-137">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="06366-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="06366-138">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="06366-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="06366-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06366-139">See also</span></span>
- [<span data-ttu-id="06366-140">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="06366-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
