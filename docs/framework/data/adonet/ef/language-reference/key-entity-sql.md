---
title: KLUCZ (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ccc13599889eb91755c775600f2386d1812880b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="key-entity-sql"></a><span data-ttu-id="d5604-102">KLUCZ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="d5604-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="d5604-103">Wyodrębnia klucza referencyjnego lub wyrażenie jednostki.</span><span class="sxs-lookup"><span data-stu-id="d5604-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5604-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5604-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="d5604-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5604-105">Remarks</span></span>  
 <span data-ttu-id="d5604-106">Klucz jednostki zawiera wartości klucza w odpowiedniej kolejności określonej jednostki lub odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="d5604-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="d5604-107">Ponieważ wiele zestawów jednostek może opierać się na ten sam typ, ten sam klucz może wyglądać w każdym zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="d5604-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="d5604-108">Aby odwołać unikatowy, należy użyć `REF`.</span><span class="sxs-lookup"><span data-stu-id="d5604-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="d5604-109">Typ zwracany operatora klucza jest typ wiersza, który zawiera jedno pole dla każdego klucza jednostki, w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d5604-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="d5604-110">W poniższym przykładzie operator klucza jest przekazywany odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="d5604-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="d5604-111">W takim przypadku rekord wpisz dokładnie jedno pole odpowiadającego `Id` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5604-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="d5604-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5604-112">Example</span></span>  
 <span data-ttu-id="d5604-113">Następujące zapytanie SQL jednostki używa operatora klucza można wyodrębnić klucza część wyrażenia z odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="d5604-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="d5604-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d5604-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d5604-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d5604-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d5604-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d5604-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d5604-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d5604-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="d5604-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5604-118">See Also</span></span>  
 [<span data-ttu-id="d5604-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d5604-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d5604-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="d5604-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="d5604-121">REF</span><span class="sxs-lookup"><span data-stu-id="d5604-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="d5604-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="d5604-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
