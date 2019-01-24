---
title: '&lt; (Mniejsze niż) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 0c2185f824cfbe201b4138d0082e3edcf93e6a7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598319"
---
# <a name="lt-less-than-entity-sql"></a><span data-ttu-id="26ac0-102">&lt; (Mniejsze niż) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="26ac0-102">&lt; (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="26ac0-103">Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość mniejszą niż wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="26ac0-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ac0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26ac0-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="26ac0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26ac0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="26ac0-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="26ac0-106">Any valid expression.</span></span> <span data-ttu-id="26ac0-107">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="26ac0-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="26ac0-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="26ac0-108">Result Types</span></span>  
 <span data-ttu-id="26ac0-109">`true` Jeśli po lewej stronie wyrażenie ma wartość mniejszą niż wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="26ac0-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ac0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ac0-110">Example</span></span>  
 <span data-ttu-id="26ac0-111">Następujące zapytanie SQL jednostki używa < operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość mniejszą niż wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="26ac0-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="26ac0-112">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="26ac0-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="26ac0-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="26ac0-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="26ac0-114">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="26ac0-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="26ac0-115">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="26ac0-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="26ac0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26ac0-116">See also</span></span>
- [<span data-ttu-id="26ac0-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="26ac0-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
