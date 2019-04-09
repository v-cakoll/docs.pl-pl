---
title: '&amp;&amp; (I) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: f0b20a8c1960bd6191a35c426dbea45c30ccc1c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084072"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="e1316-102">&amp;&amp; (I) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="e1316-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="e1316-103">Zwraca `true` Jeśli oba wyrażenia są `true`; w przeciwnym razie `false` lub `NULL`.</span><span class="sxs-lookup"><span data-stu-id="e1316-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1316-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1316-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1316-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e1316-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="e1316-106">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="e1316-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1316-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1316-107">Remarks</span></span>  
 <span data-ttu-id="e1316-108">Podwójne ampersandu (& &) mają taką samą funkcjonalność jak operator i.</span><span class="sxs-lookup"><span data-stu-id="e1316-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="e1316-109">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="e1316-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="e1316-110">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="e1316-110">TRUE</span></span>|<span data-ttu-id="e1316-111">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="e1316-111">FALSE</span></span>|<span data-ttu-id="e1316-112">NULL</span><span class="sxs-lookup"><span data-stu-id="e1316-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="e1316-113">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="e1316-113">FALSE</span></span>|<span data-ttu-id="e1316-114">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="e1316-114">FALSE</span></span>|<span data-ttu-id="e1316-115">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="e1316-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="e1316-116">NULL</span><span class="sxs-lookup"><span data-stu-id="e1316-116">NULL</span></span>|<span data-ttu-id="e1316-117">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="e1316-117">FALSE</span></span>|<span data-ttu-id="e1316-118">NULL</span><span class="sxs-lookup"><span data-stu-id="e1316-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1316-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1316-119">Example</span></span>  
 <span data-ttu-id="e1316-120">Następujące zapytanie SQL jednostki pokazuje sposób użycia operatora AND.</span><span class="sxs-lookup"><span data-stu-id="e1316-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="e1316-121">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e1316-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e1316-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e1316-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e1316-123">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e1316-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e1316-124">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e1316-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="e1316-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1316-125">See also</span></span>

- [<span data-ttu-id="e1316-126">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e1316-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
