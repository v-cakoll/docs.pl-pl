---
title: Z wyjątkiem (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 1e7ab2c29b6418e86fc1b6f0ed2aad92a18ee7e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671320"
---
# <a name="except-entity-sql"></a><span data-ttu-id="c353c-102">Z wyjątkiem (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c353c-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="c353c-103">Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu zapytania do lewego operandu EXCEPT, które nie są również zwracany z wyrażenia zapytania po prawej stronie operandu EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="c353c-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="c353c-104">Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="c353c-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c353c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c353c-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c353c-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c353c-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c353c-107">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję do porównania z tą kolekcją zwrócony z innego wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="c353c-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c353c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c353c-108">Return Value</span></span>  
 <span data-ttu-id="c353c-109">Kolekcji tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="c353c-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c353c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c353c-110">Remarks</span></span>  
 <span data-ttu-id="c353c-111">Z wyjątkiem jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="c353c-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="c353c-112">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="c353c-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="c353c-113">W poniższej tabeli przedstawiono pierwszeństwo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="c353c-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="c353c-114">Pierwszeństwo</span><span class="sxs-lookup"><span data-stu-id="c353c-114">Precedence</span></span>|<span data-ttu-id="c353c-115">Operatory</span><span class="sxs-lookup"><span data-stu-id="c353c-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="c353c-116">Najwyższy</span><span class="sxs-lookup"><span data-stu-id="c353c-116">Highest</span></span>|<span data-ttu-id="c353c-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="c353c-117">INTERSECT</span></span>|  
||<span data-ttu-id="c353c-118">UNION</span><span class="sxs-lookup"><span data-stu-id="c353c-118">UNION</span></span><br /><br /> <span data-ttu-id="c353c-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="c353c-119">UNION ALL</span></span>|  
||<span data-ttu-id="c353c-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="c353c-120">EXCEPT</span></span>|  
|<span data-ttu-id="c353c-121">Najniższy</span><span class="sxs-lookup"><span data-stu-id="c353c-121">Lowest</span></span>|<span data-ttu-id="c353c-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="c353c-122">EXISTS</span></span><br /><br /> <span data-ttu-id="c353c-123">NAKŁADA SIĘ NA</span><span class="sxs-lookup"><span data-stu-id="c353c-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="c353c-124">SPŁASZCZANIE</span><span class="sxs-lookup"><span data-stu-id="c353c-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="c353c-125">SET</span><span class="sxs-lookup"><span data-stu-id="c353c-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c353c-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c353c-126">Example</span></span>  
 <span data-ttu-id="c353c-127">Następujące zapytanie SQL jednostki używa operatora EXCEPT zwrócić kolekcję wszystkie unikatowe wartości z dwóch wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="c353c-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="c353c-128">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c353c-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c353c-129">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c353c-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c353c-130">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c353c-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="c353c-131">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c353c-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="c353c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c353c-132">See also</span></span>
- [<span data-ttu-id="c353c-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c353c-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
