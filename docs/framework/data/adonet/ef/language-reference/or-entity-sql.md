---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 3ceaf33d8baba9776008cddcbe2e2d70f13fe089
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141287"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="d22e3-102">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d22e3-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="d22e3-103">Łączy dwa `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d22e3-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d22e3-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d22e3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d22e3-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="d22e3-106">Dowolne prawidłowe wyrażenie, które zwraca `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d22e3-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d22e3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d22e3-107">Return Value</span></span>  
 `true` <span data-ttu-id="d22e3-108">gdy jeden z warunków jest `true`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d22e3-108">when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d22e3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d22e3-109">Remarks</span></span>  
 <span data-ttu-id="d22e3-110">LUB [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatora logicznego.</span><span class="sxs-lookup"><span data-stu-id="d22e3-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="d22e3-111">Służy do łączenia dwóch warunków.</span><span class="sxs-lookup"><span data-stu-id="d22e3-111">It is used to combine two conditions.</span></span> <span data-ttu-id="d22e3-112">Gdy więcej niż jeden operator jest używany w instrukcji, lub operatory są obliczane po operatorach i.</span><span class="sxs-lookup"><span data-stu-id="d22e3-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="d22e3-113">Można jednak zmienić kolejność obliczania, za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="d22e3-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="d22e3-114">Podwójne pionowych słupków (&#124;&#124;) mają taką samą funkcjonalność jak OR operator.</span><span class="sxs-lookup"><span data-stu-id="d22e3-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="d22e3-115">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="d22e3-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="d22e3-116">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="d22e3-116">TRUE</span></span>|<span data-ttu-id="d22e3-117">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="d22e3-117">TRUE</span></span>|<span data-ttu-id="d22e3-118">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="d22e3-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="d22e3-119">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="d22e3-119">TRUE</span></span>|<span data-ttu-id="d22e3-120">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="d22e3-120">FALSE</span></span>|<span data-ttu-id="d22e3-121">NULL</span><span class="sxs-lookup"><span data-stu-id="d22e3-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="d22e3-122">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="d22e3-122">TRUE</span></span>|<span data-ttu-id="d22e3-123">NULL</span><span class="sxs-lookup"><span data-stu-id="d22e3-123">NULL</span></span>|<span data-ttu-id="d22e3-124">NULL</span><span class="sxs-lookup"><span data-stu-id="d22e3-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d22e3-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="d22e3-125">Example</span></span>  
 <span data-ttu-id="d22e3-126">Następujące zapytanie SQL jednostki używa operatora OR połączyć dwa `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d22e3-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="d22e3-127">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d22e3-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d22e3-128">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d22e3-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d22e3-129">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d22e3-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d22e3-130">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d22e3-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="d22e3-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d22e3-131">See also</span></span>

- [<span data-ttu-id="d22e3-132">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d22e3-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
