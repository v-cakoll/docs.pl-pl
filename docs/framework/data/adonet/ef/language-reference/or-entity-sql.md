---
title: '|| ORAZ (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319467"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="62ea1-102">|| ORAZ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="62ea1-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="62ea1-103">Łączy dwa wyrażenia `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="62ea1-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ea1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62ea1-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="62ea1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="62ea1-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="62ea1-106">Dowolne prawidłowe wyrażenie zwracające wartość `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="62ea1-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62ea1-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62ea1-107">Return Value</span></span>  
 <span data-ttu-id="62ea1-108">`true`, gdy jeden z warunków jest `true`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="62ea1-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62ea1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62ea1-109">Remarks</span></span>  
 <span data-ttu-id="62ea1-110">LUB jest operatorem logicznym [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62ea1-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="62ea1-111">Służy do łączenia dwóch warunków.</span><span class="sxs-lookup"><span data-stu-id="62ea1-111">It is used to combine two conditions.</span></span> <span data-ttu-id="62ea1-112">Gdy w instrukcji użyto więcej niż jednego operatora logicznego, operatory są oceniane po operatorze i.</span><span class="sxs-lookup"><span data-stu-id="62ea1-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="62ea1-113">Można jednak zmienić kolejność obliczeń przy użyciu nawiasów.</span><span class="sxs-lookup"><span data-stu-id="62ea1-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="62ea1-114">Podwójne pionowe słupki&#124;&#124;() mają takie same funkcje jak operator or.</span><span class="sxs-lookup"><span data-stu-id="62ea1-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="62ea1-115">W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="62ea1-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="62ea1-116">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="62ea1-116">TRUE</span></span>|<span data-ttu-id="62ea1-117">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="62ea1-117">TRUE</span></span>|<span data-ttu-id="62ea1-118">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="62ea1-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="62ea1-119">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="62ea1-119">TRUE</span></span>|<span data-ttu-id="62ea1-120">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="62ea1-120">FALSE</span></span>|<span data-ttu-id="62ea1-121">NULL</span><span class="sxs-lookup"><span data-stu-id="62ea1-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="62ea1-122">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="62ea1-122">TRUE</span></span>|<span data-ttu-id="62ea1-123">NULL</span><span class="sxs-lookup"><span data-stu-id="62ea1-123">NULL</span></span>|<span data-ttu-id="62ea1-124">NULL</span><span class="sxs-lookup"><span data-stu-id="62ea1-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="62ea1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="62ea1-125">Example</span></span>  
 <span data-ttu-id="62ea1-126">Poniższe zapytanie Entity SQL używa operatora OR do łączenia dwóch wyrażeń `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="62ea1-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="62ea1-127">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="62ea1-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="62ea1-128">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="62ea1-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="62ea1-129">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="62ea1-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="62ea1-130">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="62ea1-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="62ea1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62ea1-131">See also</span></span>

- [<span data-ttu-id="62ea1-132">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="62ea1-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
