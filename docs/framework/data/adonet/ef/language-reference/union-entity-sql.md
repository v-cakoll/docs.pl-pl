---
title: Unii (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: ea74cb77df059556876364237887d6dfa21e5609
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165857"
---
# <a name="union-entity-sql"></a><span data-ttu-id="d90d3-102">Unii (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="d90d3-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="d90d3-103">Scala wyniki dwóch lub więcej zapytań w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d90d3-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d90d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d90d3-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d90d3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d90d3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d90d3-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję, aby połączyć się z tą kolekcją wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="d90d3-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="d90d3-107">UNION</span><span class="sxs-lookup"><span data-stu-id="d90d3-107">UNION</span></span>  
 <span data-ttu-id="d90d3-108">Określa, że wiele kolekcji są połączone i zwracane jako jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="d90d3-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="d90d3-109">ALL</span><span class="sxs-lookup"><span data-stu-id="d90d3-109">ALL</span></span>  
 <span data-ttu-id="d90d3-110">Określa, że wiele kolekcji są połączone i zwracany jako jedną kolekcję, w tym duplikaty.</span><span class="sxs-lookup"><span data-stu-id="d90d3-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="d90d3-111">Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wynik.</span><span class="sxs-lookup"><span data-stu-id="d90d3-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d90d3-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d90d3-112">Return Value</span></span>  
 <span data-ttu-id="d90d3-113">Kolekcji tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="d90d3-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d90d3-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d90d3-114">Remarks</span></span>  
 <span data-ttu-id="d90d3-115">UNION jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="d90d3-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="d90d3-116">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="d90d3-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="d90d3-117">Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zestaw operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d90d3-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d90d3-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d90d3-118">Example</span></span>  
 <span data-ttu-id="d90d3-119">Następujące zapytanie SQL jednostki używa operatora UNION ALL połączyć dwa wyniki zapytań w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="d90d3-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="d90d3-120">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d90d3-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d90d3-121">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d90d3-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d90d3-122">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d90d3-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d90d3-123">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d90d3-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="d90d3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d90d3-124">See also</span></span>

- [<span data-ttu-id="d90d3-125">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d90d3-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
