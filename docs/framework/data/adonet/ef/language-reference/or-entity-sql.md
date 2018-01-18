---
title: '|| (LUB) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b44934aa0db73f872f0ab27a4c36c5c615855de1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="-or-entity-sql"></a><span data-ttu-id="a673d-102">|| (LUB) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="a673d-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="a673d-103">Łączy dwa `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a673d-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a673d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a673d-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a673d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a673d-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="a673d-106">Prawidłowe wyrażenie, które zwraca `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a673d-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a673d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a673d-107">Return Value</span></span>  
 <span data-ttu-id="a673d-108">`true`Jeśli jeden z warunków jest `true`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a673d-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a673d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a673d-109">Remarks</span></span>  
 <span data-ttu-id="a673d-110">LUB [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatora logicznego.</span><span class="sxs-lookup"><span data-stu-id="a673d-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="a673d-111">Służy do łączenia dwóch warunków.</span><span class="sxs-lookup"><span data-stu-id="a673d-111">It is used to combine two conditions.</span></span> <span data-ttu-id="a673d-112">W przypadku więcej niż jeden operator w instrukcji lub operatory są oceniane po operatorach i.</span><span class="sxs-lookup"><span data-stu-id="a673d-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="a673d-113">Można jednak zmienić kolejność obliczania za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="a673d-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="a673d-114">Podwójne pionowych słupków (&#124; &#124;) ma te same funkcje co operatora OR.</span><span class="sxs-lookup"><span data-stu-id="a673d-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="a673d-115">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="a673d-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="a673d-116">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="a673d-116">TRUE</span></span>|<span data-ttu-id="a673d-117">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="a673d-117">TRUE</span></span>|<span data-ttu-id="a673d-118">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="a673d-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="a673d-119">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="a673d-119">TRUE</span></span>|<span data-ttu-id="a673d-120">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="a673d-120">FALSE</span></span>|<span data-ttu-id="a673d-121">NULL</span><span class="sxs-lookup"><span data-stu-id="a673d-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="a673d-122">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="a673d-122">TRUE</span></span>|<span data-ttu-id="a673d-123">NULL</span><span class="sxs-lookup"><span data-stu-id="a673d-123">NULL</span></span>|<span data-ttu-id="a673d-124">NULL</span><span class="sxs-lookup"><span data-stu-id="a673d-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a673d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="a673d-125">Example</span></span>  
 <span data-ttu-id="a673d-126">Następujące zapytanie SQL jednostki używa operatora OR do łączenia dwóch `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a673d-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="a673d-127">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a673d-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a673d-128">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a673d-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a673d-129">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a673d-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a673d-130">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a673d-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="a673d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a673d-131">See Also</span></span>  
 [<span data-ttu-id="a673d-132">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a673d-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
