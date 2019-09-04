---
title: Z wyjątkiem (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: d00fdeed01de80e441d28e2bcd5da084571b0361
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251045"
---
# <a name="except-entity-sql"></a><span data-ttu-id="e7455-102">Z wyjątkiem (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e7455-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="e7455-103">Zwraca kolekcję wszystkich odrębnych wartości z wyrażenia zapytania na lewo od operandu EXCEPT, które nie są zwracane z wyrażenia zapytania z prawej strony operandu EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="e7455-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="e7455-104">Wszystkie wyrażenia muszą być tego samego typu lub według `expression`wspólnego typu podstawowego lub pochodnego.</span><span class="sxs-lookup"><span data-stu-id="e7455-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7455-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7455-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7455-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e7455-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e7455-107">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="e7455-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7455-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e7455-108">Return Value</span></span>  
 <span data-ttu-id="e7455-109">Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="e7455-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7455-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7455-110">Remarks</span></span>  
 <span data-ttu-id="e7455-111">Oprócz tego jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="e7455-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e7455-112">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e7455-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e7455-113">W poniższej tabeli przedstawiono pierwszeństwo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="e7455-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="e7455-114">Pierwszeństwo</span><span class="sxs-lookup"><span data-stu-id="e7455-114">Precedence</span></span>|<span data-ttu-id="e7455-115">Operatory</span><span class="sxs-lookup"><span data-stu-id="e7455-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="e7455-116">Najwyższy</span><span class="sxs-lookup"><span data-stu-id="e7455-116">Highest</span></span>|<span data-ttu-id="e7455-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="e7455-117">INTERSECT</span></span>|  
||<span data-ttu-id="e7455-118">UNION</span><span class="sxs-lookup"><span data-stu-id="e7455-118">UNION</span></span><br /><br /> <span data-ttu-id="e7455-119">UNION WSZYSTKO</span><span class="sxs-lookup"><span data-stu-id="e7455-119">UNION ALL</span></span>|  
||<span data-ttu-id="e7455-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="e7455-120">EXCEPT</span></span>|  
|<span data-ttu-id="e7455-121">Okreolon</span><span class="sxs-lookup"><span data-stu-id="e7455-121">Lowest</span></span>|<span data-ttu-id="e7455-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="e7455-122">EXISTS</span></span><br /><br /> <span data-ttu-id="e7455-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="e7455-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="e7455-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="e7455-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="e7455-125">SET</span><span class="sxs-lookup"><span data-stu-id="e7455-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7455-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7455-126">Example</span></span>  
 <span data-ttu-id="e7455-127">Poniższe zapytanie Entity SQL używa operatora EXCEPT do zwrócenia kolekcji wszelkich odrębnych wartości z dwóch wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="e7455-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="e7455-128">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e7455-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e7455-129">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e7455-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e7455-130">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="e7455-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e7455-131">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e7455-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="e7455-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7455-132">See also</span></span>

- [<span data-ttu-id="e7455-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e7455-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
