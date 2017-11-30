---
title: ANYELEMENT (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 518ac4bc1ba6842a4b5e5f3b1f0771495752859c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="a7519-102">ANYELEMENT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="a7519-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="a7519-103">Wyodrębnia element z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="a7519-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7519-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7519-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7519-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a7519-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a7519-106">Wszystkie prawidłowe zapytanie zwracające można wyodrębnić elementu z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a7519-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7519-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7519-107">Return Value</span></span>  
 <span data-ttu-id="a7519-108">Pojedynczy element w kolekcji lub dowolnego elementu, jeśli kolekcja zawiera więcej niż jeden; Jeśli kolekcja jest pusty, zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="a7519-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="a7519-109">Jeśli `collection` jest kolekcją typu `Collection<T>`, następnie `ANYELEMENT(collection)` jest prawidłowe wyrażenie zwracające wystąpienia typu `T`.</span><span class="sxs-lookup"><span data-stu-id="a7519-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7519-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7519-110">Remarks</span></span>  
 <span data-ttu-id="a7519-111">ANYELEMENT wyodrębnia dowolnego elementu z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="a7519-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="a7519-112">Na przykład poniższy przykład próbuje wyodrębnić elementu pojedyncza ze zbioru `Customers`.</span><span class="sxs-lookup"><span data-stu-id="a7519-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="a7519-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7519-113">Example</span></span>  
 <span data-ttu-id="a7519-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ANYELEMENT można wyodrębnić elementu z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="a7519-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="a7519-115">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a7519-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a7519-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a7519-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a7519-117">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a7519-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a7519-118">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a7519-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="a7519-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7519-119">See Also</span></span>  
 [<span data-ttu-id="a7519-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a7519-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a7519-121">Typy dopuszczające wartości zerowe strukturalnych</span><span class="sxs-lookup"><span data-stu-id="a7519-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
