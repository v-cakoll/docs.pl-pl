---
title: '&amp;&amp; (I) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eab05f7454f8ebc88ed29030503bfa96d0c70756
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308435"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="43709-102">&amp;&amp; (I) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="43709-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="43709-103">Zwraca `true` Jeśli oba wyrażenia są `true`; w przeciwnym razie `false` lub `NULL`.</span><span class="sxs-lookup"><span data-stu-id="43709-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43709-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43709-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="43709-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="43709-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="43709-106">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="43709-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43709-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43709-107">Remarks</span></span>  
 <span data-ttu-id="43709-108">Podwójne ampersandu (& &) mają taką samą funkcjonalność jak operator i.</span><span class="sxs-lookup"><span data-stu-id="43709-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="43709-109">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="43709-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="43709-110">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="43709-110">TRUE</span></span>|<span data-ttu-id="43709-111">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="43709-111">FALSE</span></span>|<span data-ttu-id="43709-112">NULL</span><span class="sxs-lookup"><span data-stu-id="43709-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="43709-113">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="43709-113">FALSE</span></span>|<span data-ttu-id="43709-114">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="43709-114">FALSE</span></span>|<span data-ttu-id="43709-115">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="43709-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="43709-116">NULL</span><span class="sxs-lookup"><span data-stu-id="43709-116">NULL</span></span>|<span data-ttu-id="43709-117">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="43709-117">FALSE</span></span>|<span data-ttu-id="43709-118">NULL</span><span class="sxs-lookup"><span data-stu-id="43709-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43709-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="43709-119">Example</span></span>  
 <span data-ttu-id="43709-120">Następujące zapytanie SQL jednostki pokazuje sposób użycia operatora AND.</span><span class="sxs-lookup"><span data-stu-id="43709-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="43709-121">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="43709-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="43709-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="43709-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="43709-123">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="43709-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="43709-124">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="43709-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="43709-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43709-125">See also</span></span>

- [<span data-ttu-id="43709-126">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="43709-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
