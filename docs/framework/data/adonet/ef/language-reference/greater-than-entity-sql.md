---
title: '> (Większe niż) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e1d13fa863eb79982d239f4e2dc298f7fcd1346f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328559"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="bd6cc-102">> (Większe niż) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="bd6cc-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="bd6cc-103">Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="bd6cc-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd6cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd6cc-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd6cc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bd6cc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bd6cc-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="bd6cc-106">Any valid expression.</span></span> <span data-ttu-id="bd6cc-107">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="bd6cc-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="bd6cc-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="bd6cc-108">Result Types</span></span>  
 <span data-ttu-id="bd6cc-109">`true` Jeśli po lewej stronie wyrażenie ma wartość większą niż wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="bd6cc-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd6cc-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd6cc-110">Example</span></span>  
 <span data-ttu-id="bd6cc-111">Używa następującego zapytania SQL jednostki > operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość większą niż wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="bd6cc-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="bd6cc-112">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bd6cc-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bd6cc-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="bd6cc-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bd6cc-114">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bd6cc-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bd6cc-115">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="bd6cc-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="bd6cc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd6cc-116">See also</span></span>

- [<span data-ttu-id="bd6cc-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="bd6cc-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
