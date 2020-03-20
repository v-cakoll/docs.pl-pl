---
title: '|| (LUB) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 8c93e68095a0e0ff63532f53152f166d6c3d047c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150096"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="99cbf-102">|| (LUB) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="99cbf-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="99cbf-103">Łączy dwa `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="99cbf-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cbf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99cbf-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="99cbf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="99cbf-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="99cbf-106">Dowolne prawidłowe `Boolean`wyrażenie, które zwraca wyraz .</span><span class="sxs-lookup"><span data-stu-id="99cbf-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99cbf-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99cbf-107">Return Value</span></span>  
 <span data-ttu-id="99cbf-108">`true`gdy którykolwiek z `true`warunków jest; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="99cbf-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cbf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99cbf-109">Remarks</span></span>  
 <span data-ttu-id="99cbf-110">OR jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorem logicznym.</span><span class="sxs-lookup"><span data-stu-id="99cbf-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="99cbf-111">Służy do łączenia dwóch warunków.</span><span class="sxs-lookup"><span data-stu-id="99cbf-111">It is used to combine two conditions.</span></span> <span data-ttu-id="99cbf-112">Gdy w instrukcji jest używany więcej niż jeden operator logiczny, operatory OR są oceniane po operatorach AND.</span><span class="sxs-lookup"><span data-stu-id="99cbf-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="99cbf-113">Można jednak zmienić kolejność oceny przy użyciu nawiasów.</span><span class="sxs-lookup"><span data-stu-id="99cbf-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="99cbf-114">Podwójne pionowe pręty (&#124;&#124;) mają taką samą funkcjonalność jak operator OR.</span><span class="sxs-lookup"><span data-stu-id="99cbf-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="99cbf-115">W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="99cbf-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="99cbf-116">Prawda</span><span class="sxs-lookup"><span data-stu-id="99cbf-116">TRUE</span></span>|<span data-ttu-id="99cbf-117">Prawda</span><span class="sxs-lookup"><span data-stu-id="99cbf-117">TRUE</span></span>|<span data-ttu-id="99cbf-118">Prawda</span><span class="sxs-lookup"><span data-stu-id="99cbf-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="99cbf-119">Prawda</span><span class="sxs-lookup"><span data-stu-id="99cbf-119">TRUE</span></span>|<span data-ttu-id="99cbf-120">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="99cbf-120">FALSE</span></span>|<span data-ttu-id="99cbf-121">NULL</span><span class="sxs-lookup"><span data-stu-id="99cbf-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="99cbf-122">Prawda</span><span class="sxs-lookup"><span data-stu-id="99cbf-122">TRUE</span></span>|<span data-ttu-id="99cbf-123">NULL</span><span class="sxs-lookup"><span data-stu-id="99cbf-123">NULL</span></span>|<span data-ttu-id="99cbf-124">NULL</span><span class="sxs-lookup"><span data-stu-id="99cbf-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="99cbf-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="99cbf-125">Example</span></span>  
 <span data-ttu-id="99cbf-126">Następująca kwerenda SQL jednostki używa `Boolean` operatora OR do łączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="99cbf-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="99cbf-127">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="99cbf-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="99cbf-128">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="99cbf-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="99cbf-129">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="99cbf-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="99cbf-130">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="99cbf-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="99cbf-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99cbf-131">See also</span></span>

- [<span data-ttu-id="99cbf-132">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="99cbf-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
