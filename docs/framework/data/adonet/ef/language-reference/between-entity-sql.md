---
title: MIĘDZY (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 2c411fd7fcac9d98323d5fcfb1874f98bc664991
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225264"
---
# <a name="between-entity-sql"></a><span data-ttu-id="0e38c-102">MIĘDZY (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="0e38c-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="0e38c-103">Określa, czy wynikiem wyrażenia wartości w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="0e38c-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="0e38c-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Wyrażenie BETWEEN ma taką samą funkcjonalność jak wyrażenia języka Transact-SQL między.</span><span class="sxs-lookup"><span data-stu-id="0e38c-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e38c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e38c-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="0e38c-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0e38c-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0e38c-107">Dowolne prawidłowe wyrażenie do testowania w zakres zdefiniowany przez `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> `expression` <span data-ttu-id="0e38c-108">musi być taki sam jak zarówno `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-108">must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="0e38c-109">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="0e38c-109">Any valid expression.</span></span> `begin_expression` <span data-ttu-id="0e38c-110">musi być taki sam jak zarówno `expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-110">must be the same type as both `expression` and `end_expression`.</span></span> `begin_expression` <span data-ttu-id="0e38c-111">powinna być mniejsza niż `end_expression`, przeciwnym wypadku zwracana wartość będzie ujemna.</span><span class="sxs-lookup"><span data-stu-id="0e38c-111">should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="0e38c-112">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="0e38c-112">Any valid expression.</span></span> `end_expression` <span data-ttu-id="0e38c-113">musi być taki sam jak zarówno `expression` i `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-113">must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="0e38c-114">NIE</span><span class="sxs-lookup"><span data-stu-id="0e38c-114">NOT</span></span>  
 <span data-ttu-id="0e38c-115">Określa, że wynik BETWEEN być ujemna.</span><span class="sxs-lookup"><span data-stu-id="0e38c-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="0e38c-116">AND</span><span class="sxs-lookup"><span data-stu-id="0e38c-116">AND</span></span>  
 <span data-ttu-id="0e38c-117">Działa jako symbol zastępczy, który wskazuje `expression` powinien być z zakresu wskazywanym przez `begin_expression` i `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e38c-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0e38c-118">Return Value</span></span>  
 `true` <span data-ttu-id="0e38c-119">Jeśli `expression` między zakres wskazywany przez `begin_expression` i `end_expression`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-119">if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> `null` <span data-ttu-id="0e38c-120">zostanie zwrócona, jeśli `expression` jest `null` lub jeśli `begin_expression` lub `end_expression` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0e38c-120">will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e38c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e38c-121">Remarks</span></span>  
 <span data-ttu-id="0e38c-122">Aby określić zakres wyłączny, użyj większe niż (>) i mniejszości (<) operatory zamiast BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="0e38c-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e38c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e38c-123">Example</span></span>  
 <span data-ttu-id="0e38c-124">Następujące zapytanie SQL jednostki używa od operatora w celu określenia, czy wynikiem wyrażenia wartości w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="0e38c-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="0e38c-125">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0e38c-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0e38c-126">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="0e38c-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0e38c-127">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0e38c-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0e38c-128">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0e38c-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="0e38c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e38c-129">See also</span></span>

- [<span data-ttu-id="0e38c-130">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0e38c-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
