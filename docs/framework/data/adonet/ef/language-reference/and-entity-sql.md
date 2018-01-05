---
title: '&amp;&amp;(A) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e7255110a9118c3a31c84e3262fd5b1490d546e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="17fff-102">&amp;&amp;(A) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="17fff-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="17fff-103">Zwraca `true` Jeśli oba wyrażenia są `true`; w przeciwnym razie `false` lub `NULL`.</span><span class="sxs-lookup"><span data-stu-id="17fff-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17fff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17fff-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="17fff-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="17fff-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="17fff-106">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="17fff-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17fff-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17fff-107">Remarks</span></span>  
 <span data-ttu-id="17fff-108">Podwójne ampersandu (& &) mają te same funkcje co AND operator.</span><span class="sxs-lookup"><span data-stu-id="17fff-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="17fff-109">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="17fff-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="17fff-110">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="17fff-110">TRUE</span></span>|<span data-ttu-id="17fff-111">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="17fff-111">FALSE</span></span>|<span data-ttu-id="17fff-112">NULL</span><span class="sxs-lookup"><span data-stu-id="17fff-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="17fff-113">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="17fff-113">FALSE</span></span>|<span data-ttu-id="17fff-114">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="17fff-114">FALSE</span></span>|<span data-ttu-id="17fff-115">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="17fff-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="17fff-116">NULL</span><span class="sxs-lookup"><span data-stu-id="17fff-116">NULL</span></span>|<span data-ttu-id="17fff-117">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="17fff-117">FALSE</span></span>|<span data-ttu-id="17fff-118">NULL</span><span class="sxs-lookup"><span data-stu-id="17fff-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17fff-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="17fff-119">Example</span></span>  
 <span data-ttu-id="17fff-120">Następujące zapytanie SQL jednostki pokazano, jak można użyć operatora AND.</span><span class="sxs-lookup"><span data-stu-id="17fff-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="17fff-121">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="17fff-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="17fff-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="17fff-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="17fff-123">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="17fff-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="17fff-124">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="17fff-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="17fff-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17fff-125">See Also</span></span>  
 [<span data-ttu-id="17fff-126">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="17fff-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
