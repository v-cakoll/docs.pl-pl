---
title: Z wyjątkiem (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32b5148e43a38e5cf8dcce0ae16260d7a6b6a018
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341221"
---
# <a name="except-entity-sql"></a><span data-ttu-id="1a230-102">Z wyjątkiem (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1a230-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="1a230-103">Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu zapytania do lewego operandu EXCEPT, które nie są również zwracany z wyrażenia zapytania po prawej stronie operandu EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="1a230-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="1a230-104">Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="1a230-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a230-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a230-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a230-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1a230-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1a230-107">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję do porównania z tą kolekcją zwrócony z innego wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="1a230-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a230-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a230-108">Return Value</span></span>  
 <span data-ttu-id="1a230-109">Kolekcji tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="1a230-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a230-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a230-110">Remarks</span></span>  
 <span data-ttu-id="1a230-111">Z wyjątkiem jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="1a230-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1a230-112">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="1a230-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1a230-113">W poniższej tabeli przedstawiono pierwszeństwo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="1a230-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="1a230-114">Pierwszeństwo</span><span class="sxs-lookup"><span data-stu-id="1a230-114">Precedence</span></span>|<span data-ttu-id="1a230-115">Operatory</span><span class="sxs-lookup"><span data-stu-id="1a230-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="1a230-116">Najwyższy</span><span class="sxs-lookup"><span data-stu-id="1a230-116">Highest</span></span>|<span data-ttu-id="1a230-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="1a230-117">INTERSECT</span></span>|  
||<span data-ttu-id="1a230-118">UNION</span><span class="sxs-lookup"><span data-stu-id="1a230-118">UNION</span></span><br /><br /> <span data-ttu-id="1a230-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="1a230-119">UNION ALL</span></span>|  
||<span data-ttu-id="1a230-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="1a230-120">EXCEPT</span></span>|  
|<span data-ttu-id="1a230-121">Najniższy</span><span class="sxs-lookup"><span data-stu-id="1a230-121">Lowest</span></span>|<span data-ttu-id="1a230-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="1a230-122">EXISTS</span></span><br /><br /> <span data-ttu-id="1a230-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="1a230-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="1a230-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="1a230-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="1a230-125">SET</span><span class="sxs-lookup"><span data-stu-id="1a230-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a230-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a230-126">Example</span></span>  
 <span data-ttu-id="1a230-127">Następujące zapytanie SQL jednostki używa operatora EXCEPT zwrócić kolekcję wszystkie unikatowe wartości z dwóch wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="1a230-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="1a230-128">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1a230-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1a230-129">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1a230-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1a230-130">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1a230-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1a230-131">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1a230-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="1a230-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a230-132">See also</span></span>

- [<span data-ttu-id="1a230-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1a230-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
