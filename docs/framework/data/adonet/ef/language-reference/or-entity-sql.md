---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: d089bcec56ff13ddcd5250a63aee6a00d0c3ef11
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297801"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="41b01-102">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="41b01-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="41b01-103">Łączy dwa `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="41b01-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41b01-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="41b01-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="41b01-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="41b01-106">Dowolne prawidłowe wyrażenie, które zwraca `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="41b01-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41b01-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="41b01-107">Return Value</span></span>  
 `true` <span data-ttu-id="41b01-108">gdy jeden z warunków jest `true`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="41b01-108">when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41b01-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41b01-109">Remarks</span></span>  
 <span data-ttu-id="41b01-110">LUB [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatora logicznego.</span><span class="sxs-lookup"><span data-stu-id="41b01-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="41b01-111">Służy do łączenia dwóch warunków.</span><span class="sxs-lookup"><span data-stu-id="41b01-111">It is used to combine two conditions.</span></span> <span data-ttu-id="41b01-112">Gdy więcej niż jeden operator jest używany w instrukcji, lub operatory są obliczane po operatorach i.</span><span class="sxs-lookup"><span data-stu-id="41b01-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="41b01-113">Można jednak zmienić kolejność obliczania, za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="41b01-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="41b01-114">Podwójne pionowych słupków (&#124;&#124;) mają taką samą funkcjonalność jak OR operator.</span><span class="sxs-lookup"><span data-stu-id="41b01-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="41b01-115">W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="41b01-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="41b01-116">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="41b01-116">TRUE</span></span>|<span data-ttu-id="41b01-117">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="41b01-117">TRUE</span></span>|<span data-ttu-id="41b01-118">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="41b01-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="41b01-119">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="41b01-119">TRUE</span></span>|<span data-ttu-id="41b01-120">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="41b01-120">FALSE</span></span>|<span data-ttu-id="41b01-121">NULL</span><span class="sxs-lookup"><span data-stu-id="41b01-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="41b01-122">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="41b01-122">TRUE</span></span>|<span data-ttu-id="41b01-123">NULL</span><span class="sxs-lookup"><span data-stu-id="41b01-123">NULL</span></span>|<span data-ttu-id="41b01-124">NULL</span><span class="sxs-lookup"><span data-stu-id="41b01-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="41b01-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="41b01-125">Example</span></span>  
 <span data-ttu-id="41b01-126">Następujące zapytanie SQL jednostki używa operatora OR połączyć dwa `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="41b01-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="41b01-127">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="41b01-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="41b01-128">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="41b01-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="41b01-129">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="41b01-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="41b01-130">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="41b01-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="41b01-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b01-131">See also</span></span>

- [<span data-ttu-id="41b01-132">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="41b01-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
