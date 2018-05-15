---
title: Z wyjątkiem (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fb7f8040e9e310798b003ad02614cd464e996389
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="except-entity-sql"></a><span data-ttu-id="4e043-102">Z wyjątkiem (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4e043-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="4e043-103">Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu kwerendy do lewego operandu EXCEPT, które nie są również zwracane w wyrażeniu zapytania z prawej strony argument EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="4e043-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="4e043-104">Wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="4e043-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e043-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e043-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e043-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4e043-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4e043-107">Wszystkie prawidłowe zapytanie zwracające kolekcja do porównania z kolekcji zwrócony z innym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="4e043-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e043-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e043-108">Return Value</span></span>  
 <span data-ttu-id="4e043-109">Kolekcji tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="4e043-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e043-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e043-110">Remarks</span></span>  
 <span data-ttu-id="4e043-111">Z wyjątkiem jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="4e043-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4e043-112">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="4e043-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4e043-113">W poniższej tabeli przedstawiono pierwszeństwo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="4e043-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="4e043-114">Pierwszeństwo</span><span class="sxs-lookup"><span data-stu-id="4e043-114">Precedence</span></span>|<span data-ttu-id="4e043-115">Operatory</span><span class="sxs-lookup"><span data-stu-id="4e043-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="4e043-116">Najwyższy</span><span class="sxs-lookup"><span data-stu-id="4e043-116">Highest</span></span>|<span data-ttu-id="4e043-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="4e043-117">INTERSECT</span></span>|  
||<span data-ttu-id="4e043-118">UNION</span><span class="sxs-lookup"><span data-stu-id="4e043-118">UNION</span></span><br /><br /> <span data-ttu-id="4e043-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="4e043-119">UNION ALL</span></span>|  
||<span data-ttu-id="4e043-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="4e043-120">EXCEPT</span></span>|  
|<span data-ttu-id="4e043-121">Najniższa</span><span class="sxs-lookup"><span data-stu-id="4e043-121">Lowest</span></span>|<span data-ttu-id="4e043-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="4e043-122">EXISTS</span></span><br /><br /> <span data-ttu-id="4e043-123">POKRYWA SIĘ</span><span class="sxs-lookup"><span data-stu-id="4e043-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="4e043-124">SPŁASZCZANIE</span><span class="sxs-lookup"><span data-stu-id="4e043-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="4e043-125">SET</span><span class="sxs-lookup"><span data-stu-id="4e043-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4e043-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e043-126">Example</span></span>  
 <span data-ttu-id="4e043-127">Następujące zapytanie SQL jednostki używa operatora EXCEPT do zwracać kolekcji wartości różne od dwóch wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="4e043-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="4e043-128">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4e043-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4e043-129">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4e043-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4e043-130">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4e043-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4e043-131">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="4e043-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="4e043-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e043-132">See Also</span></span>  
 [<span data-ttu-id="4e043-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4e043-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
