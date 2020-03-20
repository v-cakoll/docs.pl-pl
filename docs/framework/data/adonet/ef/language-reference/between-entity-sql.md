---
title: MIĘDZY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150496"
---
# <a name="between-entity-sql"></a><span data-ttu-id="5f415-102">MIĘDZY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5f415-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="5f415-103">Określa, czy wyrażenie powoduje wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5f415-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="5f415-104">Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ma taką samą funkcjonalność jak wyrażenie Transact-SQL BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="5f415-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f415-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f415-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="5f415-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5f415-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5f415-107">Dowolne prawidłowe wyrażenie do `begin_expression` przetestowania w zakresie zdefiniowanym przez i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="5f415-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="5f415-108">`expression`musi być tego samego `begin_expression` `end_expression`typu co oba i .</span><span class="sxs-lookup"><span data-stu-id="5f415-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="5f415-109">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5f415-109">Any valid expression.</span></span> <span data-ttu-id="5f415-110">`begin_expression`musi być tego samego `expression` `end_expression`typu co oba i .</span><span class="sxs-lookup"><span data-stu-id="5f415-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="5f415-111">`begin_expression`powinna być `end_expression`mniejsza niż wartość zwracana, w przeciwnym razie wartość zwracana zostanie zanegowana.</span><span class="sxs-lookup"><span data-stu-id="5f415-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="5f415-112">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5f415-112">Any valid expression.</span></span> <span data-ttu-id="5f415-113">`end_expression`musi być tego samego `expression` `begin_expression`typu co oba i .</span><span class="sxs-lookup"><span data-stu-id="5f415-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="5f415-114">NOT</span><span class="sxs-lookup"><span data-stu-id="5f415-114">NOT</span></span>  
 <span data-ttu-id="5f415-115">Określa, że wynik BETWEEN zostać zanegowany.</span><span class="sxs-lookup"><span data-stu-id="5f415-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="5f415-116">AND</span><span class="sxs-lookup"><span data-stu-id="5f415-116">AND</span></span>  
 <span data-ttu-id="5f415-117">Działa jako symbol zastępczy, który wskazuje, `expression` powinien `begin_expression` `end_expression`mieszcząć się w zakresie wskazanym przez i .</span><span class="sxs-lookup"><span data-stu-id="5f415-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f415-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5f415-118">Return Value</span></span>  
 <span data-ttu-id="5f415-119">`true`jeżeli `expression` znajduje się między `begin_expression` zakresem wskazanym przez i `end_expression`; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="5f415-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="5f415-120">`null`zostanie zwrócona, `null` jeśli `begin_expression` `end_expression` `null` `expression` jest lub jeśli lub jest .</span><span class="sxs-lookup"><span data-stu-id="5f415-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f415-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f415-121">Remarks</span></span>  
 <span data-ttu-id="5f415-122">Aby określić zakres wyłączności, należy użyć operatorów większych niż (>) i mniejszych niż (<) zamiast between.</span><span class="sxs-lookup"><span data-stu-id="5f415-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f415-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f415-123">Example</span></span>  
 <span data-ttu-id="5f415-124">Następująca kwerenda SQL jednostki używa operatora BETWEEN, aby ustalić, czy wyrażenie powoduje wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5f415-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="5f415-125">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5f415-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5f415-126">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="5f415-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5f415-127">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5f415-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5f415-128">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="5f415-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="5f415-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f415-129">See also</span></span>

- [<span data-ttu-id="5f415-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5f415-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
