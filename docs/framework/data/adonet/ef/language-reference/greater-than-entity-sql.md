---
title: "&gt;(Więcej niż) (Jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9444aec821cd9ab6a6008989de83e929ba5f6baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gt-greater-than-entity-sql"></a><span data-ttu-id="58cb6-102">&gt;(Więcej niż) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="58cb6-102">&gt; (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="58cb6-103">Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="58cb6-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58cb6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58cb6-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="58cb6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="58cb6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="58cb6-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="58cb6-106">Any valid expression.</span></span> <span data-ttu-id="58cb6-107">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="58cb6-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="58cb6-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="58cb6-108">Result Types</span></span>  
 <span data-ttu-id="58cb6-109">`true`Jeśli wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="58cb6-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58cb6-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="58cb6-110">Example</span></span>  
 <span data-ttu-id="58cb6-111">Następujące zapytanie SQL jednostki używa > operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="58cb6-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="58cb6-112">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="58cb6-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="58cb6-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="58cb6-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="58cb6-114">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="58cb6-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="58cb6-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="58cb6-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="58cb6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58cb6-116">See Also</span></span>  
 [<span data-ttu-id="58cb6-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="58cb6-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
