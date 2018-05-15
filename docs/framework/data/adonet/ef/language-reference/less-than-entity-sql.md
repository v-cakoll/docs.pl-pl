---
title: '&lt; (Poniżej) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: e11f28fd05cb49524b5a0ff854f951385603602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lt-less-than-entity-sql"></a><span data-ttu-id="07d18-102">&lt; (Poniżej) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="07d18-102">&lt; (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="07d18-103">Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość mniejszą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="07d18-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07d18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07d18-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="07d18-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="07d18-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="07d18-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="07d18-106">Any valid expression.</span></span> <span data-ttu-id="07d18-107">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="07d18-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="07d18-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="07d18-108">Result Types</span></span>  
 <span data-ttu-id="07d18-109">`true` Jeśli wyrażenie po lewej stronie ma wartość mniejszą niż prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="07d18-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07d18-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="07d18-110">Example</span></span>  
 <span data-ttu-id="07d18-111">Następujące zapytanie SQL jednostki używa < operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy wyrażenie po lewej stronie ma wartość mniejszą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="07d18-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="07d18-112">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="07d18-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="07d18-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="07d18-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="07d18-114">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="07d18-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="07d18-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="07d18-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="07d18-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07d18-116">See Also</span></span>  
 [<span data-ttu-id="07d18-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="07d18-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
