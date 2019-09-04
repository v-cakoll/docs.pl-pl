---
title: MIĘDZY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251283"
---
# <a name="between-entity-sql"></a><span data-ttu-id="b6566-102">MIĘDZY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6566-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="b6566-103">Określa, czy wynikiem wyrażenia jest wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b6566-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="b6566-104">Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between ma takie same funkcje jak wyrażenie Transact-SQL między wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="b6566-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6566-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6566-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="b6566-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b6566-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b6566-107">Dowolne prawidłowe wyrażenie do przetestowania w zakresie zdefiniowanym `begin_expression` przez `end_expression`i.</span><span class="sxs-lookup"><span data-stu-id="b6566-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="b6566-108">`expression`musi być tego samego typu co `begin_expression` i. `end_expression`</span><span class="sxs-lookup"><span data-stu-id="b6566-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="b6566-109">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b6566-109">Any valid expression.</span></span> <span data-ttu-id="b6566-110">`begin_expression`musi być tego samego typu co `expression` i. `end_expression`</span><span class="sxs-lookup"><span data-stu-id="b6566-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="b6566-111">`begin_expression`wartość nie może być `end_expression`mniejsza niż, w przeciwnym razie zwracana jest Negacja.</span><span class="sxs-lookup"><span data-stu-id="b6566-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="b6566-112">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b6566-112">Any valid expression.</span></span> <span data-ttu-id="b6566-113">`end_expression`musi być tego samego typu co `expression` i. `begin_expression`</span><span class="sxs-lookup"><span data-stu-id="b6566-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="b6566-114">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="b6566-114">NOT</span></span>  
 <span data-ttu-id="b6566-115">Określa, że wynik między jest negacją.</span><span class="sxs-lookup"><span data-stu-id="b6566-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="b6566-116">AND</span><span class="sxs-lookup"><span data-stu-id="b6566-116">AND</span></span>  
 <span data-ttu-id="b6566-117">Działa jako symbol zastępczy, `expression` który wskazuje, że powinien znajdować `begin_expression` się `end_expression`w zakresie wskazanym przez i.</span><span class="sxs-lookup"><span data-stu-id="b6566-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6566-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b6566-118">Return Value</span></span>  
 <span data-ttu-id="b6566-119">`true`Jeśli `expression` jest między zakresem wskazanym `begin_expression` przez `end_expression`i; w `false`przeciwnym razie,.</span><span class="sxs-lookup"><span data-stu-id="b6566-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="b6566-120">`null`zostanie zwrócona, `expression` Jeśli `null` jest lub `begin_expression` Jeśli `end_expression` lub `null`jest.</span><span class="sxs-lookup"><span data-stu-id="b6566-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6566-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6566-121">Remarks</span></span>  
 <span data-ttu-id="b6566-122">Aby określić zakres wyłącznych, użyj operatorów większe niż (>) i mniejsze niż (<), a nie między.</span><span class="sxs-lookup"><span data-stu-id="b6566-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6566-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6566-123">Example</span></span>  
 <span data-ttu-id="b6566-124">Poniższe zapytanie Entity SQL używa operatora, aby określić, czy wynikiem wyrażenia jest wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b6566-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="b6566-125">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b6566-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b6566-126">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b6566-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b6566-127">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="b6566-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b6566-128">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b6566-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="b6566-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6566-129">See also</span></span>

- [<span data-ttu-id="b6566-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b6566-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
