---
title: "Pobieranie obiektów z pamięci podręcznej tożsamości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8497f728019c97bb59162d39a9f77e34e4e6f3c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="ec1e2-102">Pobieranie obiektów z pamięci podręcznej tożsamości</span><span class="sxs-lookup"><span data-stu-id="ec1e2-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="ec1e2-103">W tym temacie opisano typy LINQ do zapytania SQL, które zwracają obiekt z pamięci podręcznej tożsamości zarządzanych przez <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="ec1e2-104">W składniku LINQ to SQL sposoby, w którym <xref:System.Data.Linq.DataContext> zarządza obiektów jest przez funkcję rejestrowania tożsamości obiektów w pamięci podręcznej tożsamości, jak są wykonywane zapytania.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="ec1e2-105">W niektórych przypadkach LINQ do SQL spróbuje pobrać obiekt z pamięci podręcznej tożsamości przed wykonaniem kwerendy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="ec1e2-106">Ogólnie rzecz biorąc dla zapytania składnika LINQ to SQL zwrócić obiekt z pamięci podręcznej tożsamości, zapytanie musi być oparta na kluczu podstawowym obiektu i musi zwracać pojedynczego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="ec1e2-107">W szczególności zapytania musi być w jednym z formularze ogólne, pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec1e2-108">Wstępnie skompilowane zapytania nie zwróci obiektów z pamięci podręcznej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="ec1e2-109">Aby uzyskać więcej informacji o wstępnie skompilowanym zapytań, zobacz <xref:System.Data.Linq.CompiledQuery> i [porady: Magazyn i ponowne użycie zapytania](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="ec1e2-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="ec1e2-110">Zapytanie musi mieć jedną z następujących postaci ogólne można pobrać obiektu z pamięci podręcznej tożsamości:</span><span class="sxs-lookup"><span data-stu-id="ec1e2-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
-   <span data-ttu-id="ec1e2-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="ec1e2-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
-   <span data-ttu-id="ec1e2-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="ec1e2-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="ec1e2-113">W tych formularze ogólne `Function1`, `Function2`, i `predicate` są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="ec1e2-114">`Function1`może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ec1e2-114">`Function1` can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="ec1e2-115">`Function2`może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ec1e2-115">`Function2` can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="ec1e2-116">`predicate`musi być wyrażeniem, w którym właściwości klucza podstawowego obiektu ma ustawioną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="ec1e2-117">Jeśli obiekt ma zdefiniowany przez więcej niż jedną właściwość klucza podstawowego, każda właściwość klucza podstawowego musi mieć ustawioną wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="ec1e2-118">Poniżej podano przykłady formularza `predicate` należy wykonać:</span><span class="sxs-lookup"><span data-stu-id="ec1e2-118">The following are examples of the form `predicate` must take:</span></span>  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="ec1e2-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec1e2-119">Example</span></span>  
 <span data-ttu-id="ec1e2-120">Poniższy kod zawiera przykłady typów LINQ do zapytań SQL, które pobrać obiekt z pamięci podręcznej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ec1e2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec1e2-121">See Also</span></span>  
 [<span data-ttu-id="ec1e2-122">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="ec1e2-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="ec1e2-123">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="ec1e2-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 [<span data-ttu-id="ec1e2-124">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="ec1e2-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="ec1e2-125">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="ec1e2-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
