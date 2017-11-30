---
title: CREATEREF (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9fe960d5b19f5119f2337ec410738a2df31f20c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="createref-entity-sql"></a><span data-ttu-id="27f5c-102">CREATEREF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="27f5c-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="27f5c-103">Fabricates odwołania do jednostki w obiekcie entityset.</span><span class="sxs-lookup"><span data-stu-id="27f5c-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27f5c-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="27f5c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="27f5c-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="27f5c-106">Identyfikator obiektu entityset nie literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="27f5c-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="27f5c-107">Wyrażenie typu wiersz odpowiada właściwości klucza typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="27f5c-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27f5c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27f5c-108">Remarks</span></span>  
 <span data-ttu-id="27f5c-109">`row_typed_expression`musi być równoważna strukturę do typu klucza dla jednostki.</span><span class="sxs-lookup"><span data-stu-id="27f5c-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="27f5c-110">Oznacza to musi mieć tego samego liczbę i typy pól w takiej samej kolejności jak kluczy jednostek.</span><span class="sxs-lookup"><span data-stu-id="27f5c-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="27f5c-111">W poniższym przykładzie zleceń i BadOrders są oba zestawy jednostek typu kolejności i identyfikator zakłada, że jedną właściwość klucza zlecenia.</span><span class="sxs-lookup"><span data-stu-id="27f5c-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="27f5c-112">Jak może utworzyć odwołania do jednostki w BadOrders pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="27f5c-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="27f5c-113">Należy pamiętać, że może być dangling odwołania.</span><span class="sxs-lookup"><span data-stu-id="27f5c-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="27f5c-114">Oznacza to, że odwołanie, nie może faktycznie zidentyfikować określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="27f5c-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="27f5c-115">W takich przypadkach `DEREF` operacji dla tego odwołania zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="27f5c-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="27f5c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="27f5c-116">Example</span></span>  
 <span data-ttu-id="27f5c-117">Następujące zapytanie SQL jednostki nawiązywał operatorze CREATEREF przeznaczeniem odwołania do jednostki w zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="27f5c-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="27f5c-118">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="27f5c-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="27f5c-119">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="27f5c-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="27f5c-120">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="27f5c-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="27f5c-121">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="27f5c-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="27f5c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27f5c-122">See Also</span></span>  
 [<span data-ttu-id="27f5c-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="27f5c-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="27f5c-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="27f5c-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="27f5c-125">KLUCZ</span><span class="sxs-lookup"><span data-stu-id="27f5c-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="27f5c-126">REF</span><span class="sxs-lookup"><span data-stu-id="27f5c-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
