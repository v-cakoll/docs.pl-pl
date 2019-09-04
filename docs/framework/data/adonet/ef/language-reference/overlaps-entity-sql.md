---
title: NAKŁADAją się (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: fef90beebf1c2723c767eaf5155542ad40d5fcb8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249735"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="e732f-102">NAKŁADAją się (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e732f-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="e732f-103">Określa, czy dwie kolekcje mają wspólne elementy.</span><span class="sxs-lookup"><span data-stu-id="e732f-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e732f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e732f-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e732f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e732f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e732f-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="e732f-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="e732f-107">Wszystkie wyrażenia muszą być tego samego typu lub według `expression`wspólnego typu podstawowego lub pochodnego.</span><span class="sxs-lookup"><span data-stu-id="e732f-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e732f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e732f-108">Return Value</span></span>  
 <span data-ttu-id="e732f-109">`true`Jeśli dwie kolekcje mają wspólne elementy; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="e732f-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e732f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e732f-110">Remarks</span></span>  
 <span data-ttu-id="e732f-111">NAKŁADAjące się funkcje zapewniają funkcję równoważną z następującymi:</span><span class="sxs-lookup"><span data-stu-id="e732f-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="e732f-112">Nakładanie się jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="e732f-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e732f-113">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e732f-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e732f-114">Aby uzyskać informacje o pierwszeństwie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu, zobacz [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e732f-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e732f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="e732f-115">Example</span></span>  
 <span data-ttu-id="e732f-116">Poniższe zapytanie Entity SQL używa operatora NAKŁADAnia się, aby określić, czy dwie kolekcje mają wspólną wartość.</span><span class="sxs-lookup"><span data-stu-id="e732f-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="e732f-117">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e732f-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e732f-118">Aby skompilować i uruchomić, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e732f-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="e732f-119">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="e732f-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e732f-120">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e732f-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="e732f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e732f-121">See also</span></span>

- [<span data-ttu-id="e732f-122">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e732f-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
