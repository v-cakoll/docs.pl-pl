---
title: "MIĘDZY (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 06008847a564d91d92a596978b90b040b6c508f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="between-entity-sql"></a><span data-ttu-id="ddd55-102">MIĘDZY (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ddd55-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="ddd55-103">Określa, czy wyrażenie wynikiem jest wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ddd55-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="ddd55-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Między wyrażenie ma tę samą funkcję co wyrażenia języka Transact-SQL między.</span><span class="sxs-lookup"><span data-stu-id="ddd55-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddd55-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddd55-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="ddd55-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ddd55-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ddd55-107">Dowolne prawidłowe wyrażenie do testowania w zakresie zdefiniowane przez `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="ddd55-108">`expression`musi być taki sam typ jak zarówno `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="ddd55-109">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="ddd55-109">Any valid expression.</span></span> <span data-ttu-id="ddd55-110">`begin_expression`musi być taki sam typ jak zarówno `expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="ddd55-111">`begin_expression`powinna być mniejsza niż `end_expression`, else będzie zanegowane wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="ddd55-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="ddd55-112">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="ddd55-112">Any valid expression.</span></span> <span data-ttu-id="ddd55-113">`end_expression`musi być taki sam typ jak zarówno `expression` i `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="ddd55-114">NIE</span><span class="sxs-lookup"><span data-stu-id="ddd55-114">NOT</span></span>  
 <span data-ttu-id="ddd55-115">Określa, czy wynik BETWEEN można zanegowane.</span><span class="sxs-lookup"><span data-stu-id="ddd55-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="ddd55-116">AND</span><span class="sxs-lookup"><span data-stu-id="ddd55-116">AND</span></span>  
 <span data-ttu-id="ddd55-117">Działa jako symbol zastępczy, który wskazuje `expression` powinien znajdować się w zakresie wskazywanym przez `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddd55-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ddd55-118">Return Value</span></span>  
 <span data-ttu-id="ddd55-119">`true`Jeśli `expression` między zakres wskazywany przez `begin_expression` i `end_expression`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="ddd55-120">`null`zostanie zwrócona w przypadku `expression` jest `null` lub, jeśli `begin_expression` lub `end_expression` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="ddd55-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddd55-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddd55-121">Remarks</span></span>  
 <span data-ttu-id="ddd55-122">Aby określić zakres wyłącznego, należy użyć większości (>) i mniejszości (<) operatory zamiast BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="ddd55-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd55-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddd55-123">Example</span></span>  
 <span data-ttu-id="ddd55-124">Następujące zapytanie SQL jednostki używa od operatora, aby określić, czy wyrażenie wynikiem jest wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ddd55-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="ddd55-125">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ddd55-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ddd55-126">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ddd55-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ddd55-127">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ddd55-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ddd55-128">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ddd55-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="ddd55-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddd55-129">See Also</span></span>  
 [<span data-ttu-id="ddd55-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ddd55-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
