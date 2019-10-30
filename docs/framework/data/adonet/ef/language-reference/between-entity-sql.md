---
title: MIĘDZY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 611e90f362bbc0eac521e1e1998fb85200169c19
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039948"
---
# <a name="between-entity-sql"></a><span data-ttu-id="9522a-102">MIĘDZY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9522a-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="9522a-103">Określa, czy wynikiem wyrażenia jest wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9522a-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="9522a-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] między wyrażeniem ma takie same funkcje jak wyrażenie Transact-SQL między wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="9522a-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9522a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9522a-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="9522a-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9522a-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9522a-107">Dowolne prawidłowe wyrażenie do przetestowania w zakresie zdefiniowanym przez `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="9522a-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="9522a-108">`expression` muszą być tego samego typu co `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="9522a-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="9522a-109">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="9522a-109">Any valid expression.</span></span> <span data-ttu-id="9522a-110">`begin_expression` muszą być tego samego typu co `expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="9522a-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="9522a-111">`begin_expression` powinna być mniejsza niż `end_expression`, w przeciwnym razie wartość zwracana zostanie Negacja.</span><span class="sxs-lookup"><span data-stu-id="9522a-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="9522a-112">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="9522a-112">Any valid expression.</span></span> <span data-ttu-id="9522a-113">`end_expression` muszą być tego samego typu co `expression` i `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="9522a-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="9522a-114">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="9522a-114">NOT</span></span>  
 <span data-ttu-id="9522a-115">Określa, że wynik między jest negacją.</span><span class="sxs-lookup"><span data-stu-id="9522a-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="9522a-116">AND</span><span class="sxs-lookup"><span data-stu-id="9522a-116">AND</span></span>  
 <span data-ttu-id="9522a-117">Działa jako symbol zastępczy, który wskazuje, `expression` powinien znajdować się w zakresie wskazanym przez `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="9522a-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9522a-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9522a-118">Return Value</span></span>  
 <span data-ttu-id="9522a-119">`true`, jeśli `expression` jest między zakresem wskazanym przez `begin_expression` i `end_expression`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="9522a-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="9522a-120">`null` będzie zwracana, jeśli `expression` jest `null` lub jeśli `begin_expression` lub `end_expression` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="9522a-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9522a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9522a-121">Remarks</span></span>  
 <span data-ttu-id="9522a-122">Aby określić zakres wyłącznych, użyj operatorów większe niż (>) i mniejsze niż (<), a nie między.</span><span class="sxs-lookup"><span data-stu-id="9522a-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9522a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="9522a-123">Example</span></span>  
 <span data-ttu-id="9522a-124">Poniższe zapytanie Entity SQL używa operatora, aby określić, czy wynikiem wyrażenia jest wartość w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9522a-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="9522a-125">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9522a-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9522a-126">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9522a-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9522a-127">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9522a-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9522a-128">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="9522a-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="9522a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9522a-129">See also</span></span>

- [<span data-ttu-id="9522a-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="9522a-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
