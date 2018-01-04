---
title: Unii (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5e8b3c28fa7b320b1bbf0f3d7621a587812a6e89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="union-entity-sql"></a><span data-ttu-id="b08ac-102">Unii (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="b08ac-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="b08ac-103">Łączy wyniki dwóch lub więcej kwerend w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b08ac-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b08ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b08ac-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b08ac-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b08ac-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b08ac-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję do łączenia z kolekcji wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="b08ac-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="b08ac-107">UNION</span><span class="sxs-lookup"><span data-stu-id="b08ac-107">UNION</span></span>  
 <span data-ttu-id="b08ac-108">Określa, że wiele kolekcji są łączone i zwracane w postaci jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b08ac-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="b08ac-109">WSZYSTKIE</span><span class="sxs-lookup"><span data-stu-id="b08ac-109">ALL</span></span>  
 <span data-ttu-id="b08ac-110">Określa, że wiele kolekcji są łączone i zwracane w postaci jednej kolekcji, w tym duplikaty.</span><span class="sxs-lookup"><span data-stu-id="b08ac-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="b08ac-111">Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wynik.</span><span class="sxs-lookup"><span data-stu-id="b08ac-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b08ac-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b08ac-112">Return Value</span></span>  
 <span data-ttu-id="b08ac-113">Kolekcji tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="b08ac-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b08ac-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b08ac-114">Remarks</span></span>  
 <span data-ttu-id="b08ac-115">Unii jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="b08ac-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="b08ac-116">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="b08ac-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="b08ac-117">Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b08ac-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b08ac-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b08ac-118">Example</span></span>  
 <span data-ttu-id="b08ac-119">Następujące zapytanie SQL jednostki używa operatora UNION ALL do łączenia wyniki dwa zapytania w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b08ac-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="b08ac-120">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b08ac-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b08ac-121">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b08ac-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b08ac-122">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b08ac-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b08ac-123">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b08ac-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="b08ac-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b08ac-124">See Also</span></span>  
 [<span data-ttu-id="b08ac-125">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b08ac-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
