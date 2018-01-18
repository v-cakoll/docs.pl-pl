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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f2bd509de0db92d4b33791ab3d83947ac36ad3c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="gt-greater-than-entity-sql"></a><span data-ttu-id="8cf8d-102">&gt;(Więcej niż) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="8cf8d-102">&gt; (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="8cf8d-103">Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8cf8d-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cf8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cf8d-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8cf8d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8cf8d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8cf8d-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8cf8d-106">Any valid expression.</span></span> <span data-ttu-id="8cf8d-107">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="8cf8d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8cf8d-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="8cf8d-108">Result Types</span></span>  
 <span data-ttu-id="8cf8d-109">`true`Jeśli wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8cf8d-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cf8d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cf8d-110">Example</span></span>  
 <span data-ttu-id="8cf8d-111">Następujące zapytanie SQL jednostki używa > operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8cf8d-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="8cf8d-112">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8cf8d-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8cf8d-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="8cf8d-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8cf8d-114">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8cf8d-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8cf8d-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="8cf8d-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="8cf8d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cf8d-116">See Also</span></span>  
 [<span data-ttu-id="8cf8d-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="8cf8d-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
