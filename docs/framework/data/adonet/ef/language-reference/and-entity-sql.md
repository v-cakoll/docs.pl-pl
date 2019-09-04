---
title: '&amp;&amp;LUB (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 02e404b73e5a9a9c3963e2d2b58ab7592afabc13
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251317"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="d9fb9-102">&amp;&amp;LUB (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d9fb9-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="d9fb9-103">Zwraca `true` Jeśli oba wyrażenia są `true`; w przeciwnym `false` razie `NULL`lub.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9fb9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9fb9-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9fb9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d9fb9-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="d9fb9-106">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9fb9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9fb9-107">Remarks</span></span>  
 <span data-ttu-id="d9fb9-108">Podwójne znaki "(& &) mają takie same funkcje jak operator i.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="d9fb9-109">W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="d9fb9-110">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="d9fb9-110">TRUE</span></span>|<span data-ttu-id="d9fb9-111">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="d9fb9-111">FALSE</span></span>|<span data-ttu-id="d9fb9-112">NULL</span><span class="sxs-lookup"><span data-stu-id="d9fb9-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="d9fb9-113">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="d9fb9-113">FALSE</span></span>|<span data-ttu-id="d9fb9-114">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="d9fb9-114">FALSE</span></span>|<span data-ttu-id="d9fb9-115">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="d9fb9-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="d9fb9-116">NULL</span><span class="sxs-lookup"><span data-stu-id="d9fb9-116">NULL</span></span>|<span data-ttu-id="d9fb9-117">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="d9fb9-117">FALSE</span></span>|<span data-ttu-id="d9fb9-118">NULL</span><span class="sxs-lookup"><span data-stu-id="d9fb9-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9fb9-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9fb9-119">Example</span></span>  
 <span data-ttu-id="d9fb9-120">W poniższym zapytaniu Entity SQL pokazano, jak używać operatora i.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="d9fb9-121">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d9fb9-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d9fb9-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d9fb9-123">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="d9fb9-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d9fb9-124">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d9fb9-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="d9fb9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9fb9-125">See also</span></span>

- [<span data-ttu-id="d9fb9-126">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d9fb9-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
