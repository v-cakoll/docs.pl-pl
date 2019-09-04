---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251103"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="984fa-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="984fa-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="984fa-103">W obiekcie EntitySet są przywoływane odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="984fa-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="984fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="984fa-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="984fa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="984fa-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="984fa-106">Identyfikator obiektu EntitySet, a nie literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="984fa-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="984fa-107">Wyrażenie z określonym wierszem, które odnosi się do właściwości klucza typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="984fa-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="984fa-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="984fa-108">Remarks</span></span>  
 <span data-ttu-id="984fa-109">`row_typed_expression`muszą być strukturalnie równoważne z typem klucza dla jednostki.</span><span class="sxs-lookup"><span data-stu-id="984fa-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="984fa-110">Oznacza to, że musi mieć taką samą liczbę i typy pól w tej samej kolejności co klucze jednostek.</span><span class="sxs-lookup"><span data-stu-id="984fa-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="984fa-111">W poniższym przykładzie zamówienia i BadOrders są zarówno obiektem EntitySet typu Order, jak i przyjmuje się, że są one właściwością Single Key kolejności.</span><span class="sxs-lookup"><span data-stu-id="984fa-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="984fa-112">W przykładzie pokazano, jak możemy utworzyć odwołanie do jednostki w BadOrders.</span><span class="sxs-lookup"><span data-stu-id="984fa-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="984fa-113">Należy zauważyć, że odwołanie może być zawieszonego.</span><span class="sxs-lookup"><span data-stu-id="984fa-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="984fa-114">Oznacza to, że odwołanie może nie identyfikować określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="984fa-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="984fa-115">W takich przypadkach `DEREF` operacja na tym odwołaniu zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="984fa-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="984fa-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="984fa-116">Example</span></span>  
 <span data-ttu-id="984fa-117">Poniższe zapytanie Entity SQL używa operatora CREATEREF do tworzenia odwołań do jednostki w zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="984fa-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="984fa-118">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="984fa-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="984fa-119">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="984fa-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="984fa-120">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="984fa-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="984fa-121">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="984fa-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="984fa-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="984fa-122">See also</span></span>

- [<span data-ttu-id="984fa-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="984fa-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="984fa-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="984fa-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="984fa-125">KEY</span><span class="sxs-lookup"><span data-stu-id="984fa-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="984fa-126">REF</span><span class="sxs-lookup"><span data-stu-id="984fa-126">REF</span></span>](ref-entity-sql.md)
