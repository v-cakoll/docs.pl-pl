---
title: Pobieranie obiektów z pamięci podręcznej tożsamości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033478"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="805c9-102">Pobieranie obiektów z pamięci podręcznej tożsamości</span><span class="sxs-lookup"><span data-stu-id="805c9-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="805c9-103">W tym temacie opisano rodzaje LINQ do zapytań SQL, które zwracają obiekt z pamięci podręcznej tożsamości zarządzanych przez <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="805c9-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="805c9-104">W składniku LINQ to SQL jednym ze sposobów, w którym <xref:System.Data.Linq.DataContext> zarządza obiektami polega rejestrowanie tożsamości obiektów w pamięci podręcznej tożsamości, gdy zapytania są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="805c9-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="805c9-105">W niektórych przypadkach LINQ to SQL będzie próbował pobrać obiekt z pamięci podręcznej tożsamości przed wykonaniem kwerendy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="805c9-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="805c9-106">Ogólnie rzecz biorąc dla programu LINQ do kwerendy SQL zwrócić obiekt z pamięci podręcznej tożsamości zapytania muszą być oparte na kluczu podstawowym obiektu i musi zwracać pojedynczy obiekt.</span><span class="sxs-lookup"><span data-stu-id="805c9-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="805c9-107">W szczególności zapytanie musi być w jednym z formularzy ogólne, pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="805c9-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="805c9-108">Wstępnie skompilowanym zapytania nie będzie zwracać obiekty z pamięci podręcznej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="805c9-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="805c9-109">Aby dowiedzieć się więcej o wstępnie skompilowanym zapytań, zobacz <xref:System.Data.Linq.CompiledQuery> i [jak: Store i ponowne użycie zapytań](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="805c9-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="805c9-110">Zapytanie musi mieć jedną z następujących form ogólne, aby pobrać obiekt z pamięci podręcznej tożsamości:</span><span class="sxs-lookup"><span data-stu-id="805c9-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="805c9-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="805c9-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="805c9-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="805c9-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="805c9-113">W tych formularzach ogólne `Function1`, `Function2`, i `predicate` są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="805c9-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="805c9-114">`Function1` może być dowolny z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="805c9-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="805c9-115">`Function2` może być dowolny z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="805c9-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="805c9-116">`predicate` musi być wyrażeniem, w której właściwość klucza podstawowego obiektu jest ustawiony na wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="805c9-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="805c9-117">Jeśli obiekt ma zdefiniowany przez więcej niż jedną właściwość klucza podstawowego, każda właściwość klucza podstawowego musi być równa wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="805c9-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="805c9-118">Poniżej przedstawiono przykłady formularza `predicate` należy wykonać:</span><span class="sxs-lookup"><span data-stu-id="805c9-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="805c9-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="805c9-119">Example</span></span>  
 <span data-ttu-id="805c9-120">Poniższy kod zawiera przykłady typów LINQ do zapytań SQL, które pobierają obiekt z pamięci podręcznej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="805c9-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="805c9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="805c9-121">See also</span></span>

- [<span data-ttu-id="805c9-122">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="805c9-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="805c9-123">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="805c9-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [<span data-ttu-id="805c9-124">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="805c9-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="805c9-125">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="805c9-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
