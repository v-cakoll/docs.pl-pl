---
title: '&amp;&amp; (A) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 649b805c1d728c45120adf85f02533d36f7bcdff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763790"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="09de7-102">&amp;&amp; (A) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="09de7-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="09de7-103">Zwraca `true` Jeśli oba wyrażenia są `true`; w przeciwnym razie `false` lub `NULL`.</span><span class="sxs-lookup"><span data-stu-id="09de7-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09de7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09de7-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="09de7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="09de7-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="09de7-106">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="09de7-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09de7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09de7-107">Remarks</span></span>  
 <span data-ttu-id="09de7-108">Podwójne ampersandu (& &) mają te same funkcje co AND operator.</span><span class="sxs-lookup"><span data-stu-id="09de7-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="09de7-109">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="09de7-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="09de7-110">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="09de7-110">TRUE</span></span>|<span data-ttu-id="09de7-111">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="09de7-111">FALSE</span></span>|<span data-ttu-id="09de7-112">NULL</span><span class="sxs-lookup"><span data-stu-id="09de7-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="09de7-113">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="09de7-113">FALSE</span></span>|<span data-ttu-id="09de7-114">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="09de7-114">FALSE</span></span>|<span data-ttu-id="09de7-115">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="09de7-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="09de7-116">NULL</span><span class="sxs-lookup"><span data-stu-id="09de7-116">NULL</span></span>|<span data-ttu-id="09de7-117">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="09de7-117">FALSE</span></span>|<span data-ttu-id="09de7-118">NULL</span><span class="sxs-lookup"><span data-stu-id="09de7-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09de7-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="09de7-119">Example</span></span>  
 <span data-ttu-id="09de7-120">Następujące zapytanie SQL jednostki pokazano, jak można użyć operatora AND.</span><span class="sxs-lookup"><span data-stu-id="09de7-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="09de7-121">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="09de7-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="09de7-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="09de7-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="09de7-123">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="09de7-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="09de7-124">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="09de7-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="09de7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09de7-125">See Also</span></span>  
 [<span data-ttu-id="09de7-126">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="09de7-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
