---
title: Istnieje (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 20e18bf536f2b89eca9515b3c5dca7ca7fbd6fe5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250987"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="66bfd-102">Istnieje (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="66bfd-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="66bfd-103">Określa, czy kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="66bfd-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66bfd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66bfd-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="66bfd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="66bfd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="66bfd-106">Dowolne prawidłowe wyrażenie zwracające kolekcję.</span><span class="sxs-lookup"><span data-stu-id="66bfd-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="66bfd-107">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="66bfd-107">NOT</span></span>  
 <span data-ttu-id="66bfd-108">Określa, że wynik istnieje jest negacją.</span><span class="sxs-lookup"><span data-stu-id="66bfd-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66bfd-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66bfd-109">Return Value</span></span>  
 <span data-ttu-id="66bfd-110">`true`Jeśli kolekcja nie jest pusta; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="66bfd-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66bfd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66bfd-111">Remarks</span></span>  
 <span data-ttu-id="66bfd-112">Istnieje, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest jednym z operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="66bfd-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="66bfd-113">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="66bfd-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="66bfd-114">Aby uzyskać informacje o pierwszeństwie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu, zobacz [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="66bfd-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66bfd-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="66bfd-115">Example</span></span>  
 <span data-ttu-id="66bfd-116">Poniższe zapytanie Entity SQL używa operatora EXISTS, aby określić, czy kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="66bfd-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="66bfd-117">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="66bfd-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="66bfd-118">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="66bfd-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="66bfd-119">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="66bfd-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="66bfd-120">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="66bfd-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="66bfd-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66bfd-121">See also</span></span>

- [<span data-ttu-id="66bfd-122">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="66bfd-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
