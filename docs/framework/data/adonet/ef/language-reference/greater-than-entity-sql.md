---
title: '> (Większe niż) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 0b57f36681575ccbe3239220e89804c804f13f39
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250882"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="13e18-102">> (Większe niż) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="13e18-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="13e18-103">Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość większą niż prawo wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="13e18-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13e18-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="13e18-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13e18-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="13e18-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="13e18-106">Any valid expression.</span></span> <span data-ttu-id="13e18-107">Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.</span><span class="sxs-lookup"><span data-stu-id="13e18-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="13e18-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="13e18-108">Result Types</span></span>  
 <span data-ttu-id="13e18-109">`true`Jeśli lewe wyrażenie ma wartość większą niż wyrażenie Right; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="13e18-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13e18-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="13e18-110">Example</span></span>  
 <span data-ttu-id="13e18-111">Poniższe zapytanie Entity SQL używa operatora porównania > do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość większą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="13e18-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="13e18-112">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="13e18-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="13e18-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="13e18-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="13e18-114">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="13e18-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="13e18-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="13e18-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="13e18-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13e18-116">See also</span></span>

- [<span data-ttu-id="13e18-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="13e18-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
