---
title: Istnieje (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 44f128a292b013fd3a3a80efdd2d10a63e3cfb07
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833834"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="bb1e1-102">Istnieje (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bb1e1-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="bb1e1-103">Określa, czy kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb1e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb1e1-104">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb1e1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bb1e1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bb1e1-106">Dowolne prawidłowe wyrażenie zwracające kolekcję.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="bb1e1-107">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="bb1e1-107">NOT</span></span>  
 <span data-ttu-id="bb1e1-108">Określa, że wynik istnieje jest negacją.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb1e1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb1e1-109">Return Value</span></span>  
 <span data-ttu-id="bb1e1-110">`true`, jeśli kolekcja nie jest pusta; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb1e1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb1e1-111">Remarks</span></span>  
 <span data-ttu-id="bb1e1-112">Istnieje jeden z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb1e1-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="bb1e1-113">Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="bb1e1-114">Aby uzyskać informacje o pierwszeństwie dla operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bb1e1-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb1e1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb1e1-115">Example</span></span>  
 <span data-ttu-id="bb1e1-116">Poniższe zapytanie Entity SQL używa operatora EXISTS, aby określić, czy kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="bb1e1-117">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bb1e1-118">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="bb1e1-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bb1e1-119">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bb1e1-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bb1e1-120">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="bb1e1-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="bb1e1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb1e1-121">See also</span></span>

- [<span data-ttu-id="bb1e1-122">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="bb1e1-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
