---
title: = (Equals) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: ec87ec682e1773c001c225567a35b3cedc9c5aba
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251006"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="cb7ef-102">= (Equals) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cb7ef-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="cb7ef-103">Porównuje równość dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb7ef-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cb7ef-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cb7ef-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cb7ef-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-106">Any valid expression.</span></span> <span data-ttu-id="cb7ef-107">Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="cb7ef-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="cb7ef-108">Result Types</span></span>  
 <span data-ttu-id="cb7ef-109">`true`Jeśli wyrażenie po lewej stronie jest równe wyrażeniu z prawej strony; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="cb7ef-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb7ef-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb7ef-110">Remarks</span></span>  
 <span data-ttu-id="cb7ef-111">Operator = = jest równoważny z =.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb7ef-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb7ef-112">Example</span></span>  
 <span data-ttu-id="cb7ef-113">Poniższy Entity SQL Query używa operatora porównania, aby porównać równość dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="cb7ef-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cb7ef-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cb7ef-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cb7ef-116">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="cb7ef-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="cb7ef-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cb7ef-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="cb7ef-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb7ef-118">See also</span></span>

- [<span data-ttu-id="cb7ef-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cb7ef-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
