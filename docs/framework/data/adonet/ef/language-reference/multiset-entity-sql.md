---
title: Zestaw WIELOKROTNY (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e72605225d214ccd2283aaae3f0c2071ceb92d91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="cb91b-102">Zestaw WIELOKROTNY (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cb91b-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="cb91b-103">Tworzy wystąpienie zestaw wielokrotny na podstawie listy wartości.</span><span class="sxs-lookup"><span data-stu-id="cb91b-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="cb91b-104">Wszystkie wartości w Konstruktorze multiset — muszą być zgodne z typem `T`.</span><span class="sxs-lookup"><span data-stu-id="cb91b-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="cb91b-105">Pusty konstruktorów zestawów wielokrotnych są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="cb91b-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb91b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb91b-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="cb91b-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cb91b-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cb91b-108">Wszelkie prawidłową listę wartości.</span><span class="sxs-lookup"><span data-stu-id="cb91b-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb91b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cb91b-109">Return Value</span></span>  
 <span data-ttu-id="cb91b-110">Kolekcja typu MULTISET\<T >.</span><span class="sxs-lookup"><span data-stu-id="cb91b-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb91b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb91b-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cb91b-112">udostępnia trzy rodzaje konstruktory: wiersz konstruktorów, obiekt konstruktorów i konstruktorów multiset (lub kolekcji).</span><span class="sxs-lookup"><span data-stu-id="cb91b-112"> provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="cb91b-113">Aby uzyskać więcej informacji, zobacz [konstruowania typy](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cb91b-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="cb91b-114">Multiset — Konstruktor tworzy wystąpienie zestaw wielokrotny na podstawie listy wartości.</span><span class="sxs-lookup"><span data-stu-id="cb91b-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="cb91b-115">Wszystkie wartości w Konstruktorze musi być zgodne z typem.</span><span class="sxs-lookup"><span data-stu-id="cb91b-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="cb91b-116">Na przykład poniższe wyrażenie tworzy zestaw wielokrotny liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="cb91b-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="cb91b-117">Zagnieżdżone literały zestawów wielokrotnych są obsługiwane tylko podczas mutiset zawijania ma jeden elementów zestawów wielokrotnych; na przykład `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="cb91b-117">Nested multiset literals are only supported when a wrapping mutiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="cb91b-118">Gdy multiset zawijania ma wiele elementów zestawów wielokrotnych (na przykład `{{1, 2}, {3, 4}}`), zagnieżdżonych zestawów wielokrotnych literały nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="cb91b-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb91b-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb91b-119">Example</span></span>  
 <span data-ttu-id="cb91b-120">Następujące zapytanie SQL jednostki używa operatora MULTISET do utworzenia wystąpienia zestaw wielokrotny z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="cb91b-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="cb91b-121">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cb91b-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cb91b-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cb91b-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cb91b-123">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cb91b-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cb91b-124">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cb91b-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="cb91b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb91b-125">See Also</span></span>  
 [<span data-ttu-id="cb91b-126">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="cb91b-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="cb91b-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cb91b-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
