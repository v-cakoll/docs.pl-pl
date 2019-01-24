---
title: CREATEREF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: bdf1c34f8a050764e8f8766da25076a7c1c361ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505084"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="ac040-102">CREATEREF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ac040-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="ac040-103">Fabricates odwołania do jednostki w obiekcie entityset.</span><span class="sxs-lookup"><span data-stu-id="ac040-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac040-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac040-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac040-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ac040-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="ac040-106">Identyfikator obiektu entityset nie literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="ac040-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="ac040-107">Wpisane wiersza wyrażenie, które odnosi się do właściwości kluczy tego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="ac040-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac040-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac040-108">Remarks</span></span>  
 <span data-ttu-id="ac040-109">`row_typed_expression` musi być strukturalnie odpowiednikiem typu klucza jednostki.</span><span class="sxs-lookup"><span data-stu-id="ac040-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="ac040-110">Oznacza to musi on mieć tej samej liczby i typy pól w tej samej kolejności, jak klucze jednostek.</span><span class="sxs-lookup"><span data-stu-id="ac040-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="ac040-111">W poniższym przykładzie zamówień i BadOrders są oba zestawy jednostek typu zamówienia, a identyfikator zakłada, że jedną właściwość klucza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="ac040-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="ac040-112">W przykładzie pokazano, jak firma Microsoft może zwrócić odwołanie do jednostki w BadOrders.</span><span class="sxs-lookup"><span data-stu-id="ac040-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="ac040-113">Należy zauważyć, że odwołanie może dangling.</span><span class="sxs-lookup"><span data-stu-id="ac040-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="ac040-114">Oznacza to odwołanie, nie może faktycznie zidentyfikować określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="ac040-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="ac040-115">W takich przypadkach `DEREF` operacji dla tego odwołania zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="ac040-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="ac040-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac040-116">Example</span></span>  
 <span data-ttu-id="ac040-117">Następujące zapytanie SQL jednostki używa operatorze CREATEREF do przeznaczeniem odwołania do jednostki w zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="ac040-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="ac040-118">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ac040-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ac040-119">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ac040-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ac040-120">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ac040-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ac040-121">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ac040-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="ac040-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac040-122">See also</span></span>
- [<span data-ttu-id="ac040-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ac040-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="ac040-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="ac040-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [<span data-ttu-id="ac040-125">KEY</span><span class="sxs-lookup"><span data-stu-id="ac040-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="ac040-126">REF</span><span class="sxs-lookup"><span data-stu-id="ac040-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
