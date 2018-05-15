---
title: '&gt; (Więcej niż) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: b9cf4d5445060bbd013ae2d769c407e7f9ee9314
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="gt-greater-than-entity-sql"></a><span data-ttu-id="cabcd-102">&gt; (Więcej niż) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cabcd-102">&gt; (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="cabcd-103">Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cabcd-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabcd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cabcd-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cabcd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cabcd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cabcd-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cabcd-106">Any valid expression.</span></span> <span data-ttu-id="cabcd-107">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="cabcd-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="cabcd-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="cabcd-108">Result Types</span></span>  
 <span data-ttu-id="cabcd-109">`true` Jeśli wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cabcd-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cabcd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cabcd-110">Example</span></span>  
 <span data-ttu-id="cabcd-111">Następujące zapytanie SQL jednostki używa > operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cabcd-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="cabcd-112">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cabcd-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cabcd-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cabcd-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cabcd-114">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cabcd-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cabcd-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cabcd-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="cabcd-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cabcd-116">See Also</span></span>  
 [<span data-ttu-id="cabcd-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cabcd-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
