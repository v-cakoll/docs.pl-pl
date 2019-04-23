---
title: = (Równa się) (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: d50ede1964f6d6b9025a7214efe90e878aa55a0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333161"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="2b02f-102">= (Równa się) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="2b02f-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="2b02f-103">Porównanie równości dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="2b02f-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b02f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b02f-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b02f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2b02f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2b02f-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="2b02f-106">Any valid expression.</span></span> <span data-ttu-id="2b02f-107">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="2b02f-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2b02f-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="2b02f-108">Result Types</span></span>  
 <span data-ttu-id="2b02f-109">`true` Jeśli po lewej stronie wyrażenia jest równy wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2b02f-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b02f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b02f-110">Remarks</span></span>  
 <span data-ttu-id="2b02f-111">== — Operator jest odpowiednikiem =.</span><span class="sxs-lookup"><span data-stu-id="2b02f-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b02f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b02f-112">Example</span></span>  
 <span data-ttu-id="2b02f-113">Następujące zapytanie SQL jednostki używa =, operator porównania do porównania równości dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="2b02f-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="2b02f-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2b02f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b02f-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="2b02f-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b02f-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2b02f-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2b02f-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="2b02f-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="2b02f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b02f-118">See also</span></span>

- [<span data-ttu-id="2b02f-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="2b02f-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
