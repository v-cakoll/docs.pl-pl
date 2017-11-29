---
title: "SPŁASZCZANIE (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 226f7fa14331ee8e2500ac91a665e86928e37f8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="cf8b1-102">SPŁASZCZANIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cf8b1-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="cf8b1-103">Konwertuje kolekcję spłaszczonych kolekcją kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="cf8b1-104">Nowa kolekcja te same zawiera elementy, co stary kolekcji, ale bez struktury zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf8b1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf8b1-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf8b1-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cf8b1-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="cf8b1-107">Dowolne prawidłowe wyrażenie zwracające kolekcją wartość kolekcji do spłaszczenia do jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf8b1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf8b1-108">Remarks</span></span>  
 <span data-ttu-id="cf8b1-109">`FLATTEN`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="cf8b1-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="cf8b1-111">Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8b1-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf8b1-112">Example</span></span>  
 <span data-ttu-id="cf8b1-113">Następujące zapytanie SQL jednostki używa `FLATTEN` operator można przekonwertować na kolekcję spłaszczonych kolekcją kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cf8b1-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="cf8b1-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cf8b1-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cf8b1-115">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cf8b1-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cf8b1-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cf8b1-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="cf8b1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf8b1-117">See Also</span></span>  
 [<span data-ttu-id="cf8b1-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cf8b1-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
