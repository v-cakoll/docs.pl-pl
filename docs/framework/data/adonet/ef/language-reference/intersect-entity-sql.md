---
title: CZĘŚĆ wspólna (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: a943de89de37d00cc2a643b443da7ef1fd3380b9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250601"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="1d616-102">CZĘŚĆ wspólna (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1d616-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="1d616-103">Zwraca kolekcję wszelkich unikatowych wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i po prawej stronie operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="1d616-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="1d616-104">Wszystkie wyrażenia muszą być tego samego typu lub według `expression`wspólnego typu podstawowego lub pochodnego.</span><span class="sxs-lookup"><span data-stu-id="1d616-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d616-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d616-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d616-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1d616-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1d616-107">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="1d616-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d616-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d616-108">Return Value</span></span>  
 <span data-ttu-id="1d616-109">Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="1d616-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d616-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d616-110">Remarks</span></span>  
 <span data-ttu-id="1d616-111">Część wspólna jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d616-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1d616-112">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="1d616-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1d616-113">Aby uzyskać informacje o pierwszeństwie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu, zobacz [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1d616-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d616-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d616-114">Example</span></span>  
 <span data-ttu-id="1d616-115">Poniższe zapytanie Entity SQL używa operatora INTERSECT do zwrócenia kolekcji wszelkich unikatowych wartości, które są zwracane przez wyrażenia zapytania po lewej i prawej stronie operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="1d616-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="1d616-116">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1d616-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1d616-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1d616-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1d616-118">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="1d616-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1d616-119">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1d616-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="1d616-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d616-120">See also</span></span>

- [<span data-ttu-id="1d616-121">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1d616-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
