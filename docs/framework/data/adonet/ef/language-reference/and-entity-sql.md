---
title: '&amp;&amp;(I) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150517"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="ec74f-102">&amp;&amp;(I) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ec74f-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="ec74f-103">Zwraca, `true` jeśli oba `true`wyrażenia są ; w `false` inny `NULL`sposób, lub .</span><span class="sxs-lookup"><span data-stu-id="ec74f-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec74f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec74f-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="ec74f-105">lub</span><span class="sxs-lookup"><span data-stu-id="ec74f-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec74f-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ec74f-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="ec74f-107">Dowolne prawidłowe wyrażenie, które zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="ec74f-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec74f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec74f-108">Remarks</span></span>  
 <span data-ttu-id="ec74f-109">Podwójne ampersandy (&&) mają taką samą funkcjonalność jak operator AND.</span><span class="sxs-lookup"><span data-stu-id="ec74f-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="ec74f-110">W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="ec74f-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="ec74f-111">Prawda</span><span class="sxs-lookup"><span data-stu-id="ec74f-111">TRUE</span></span>|<span data-ttu-id="ec74f-112">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="ec74f-112">FALSE</span></span>|<span data-ttu-id="ec74f-113">NULL</span><span class="sxs-lookup"><span data-stu-id="ec74f-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="ec74f-114">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="ec74f-114">FALSE</span></span>|<span data-ttu-id="ec74f-115">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="ec74f-115">FALSE</span></span>|<span data-ttu-id="ec74f-116">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="ec74f-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="ec74f-117">NULL</span><span class="sxs-lookup"><span data-stu-id="ec74f-117">NULL</span></span>|<span data-ttu-id="ec74f-118">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="ec74f-118">FALSE</span></span>|<span data-ttu-id="ec74f-119">NULL</span><span class="sxs-lookup"><span data-stu-id="ec74f-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ec74f-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec74f-120">Example</span></span>  
 <span data-ttu-id="ec74f-121">Następujące zapytanie SQL jednostki pokazuje, jak używać operatora AND.</span><span class="sxs-lookup"><span data-stu-id="ec74f-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="ec74f-122">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ec74f-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ec74f-123">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ec74f-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ec74f-124">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ec74f-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ec74f-125">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="ec74f-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="ec74f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec74f-126">See also</span></span>

- [<span data-ttu-id="ec74f-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ec74f-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
