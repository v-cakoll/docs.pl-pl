---
title: W (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 1f3be5717c27a691e073cee46df757d0166fe78a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="in-entity-sql"></a><span data-ttu-id="c34c6-102">W (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c34c6-102">IN (Entity SQL)</span></span>
<span data-ttu-id="c34c6-103">Określa, czy wartość odpowiada wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c34c6-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c34c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c34c6-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c34c6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c34c6-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="c34c6-106">Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="c34c6-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="c34c6-107">[NOT]</span><span class="sxs-lookup"><span data-stu-id="c34c6-107">[ NOT ]</span></span>  
 <span data-ttu-id="c34c6-108">Określa, że `Boolean` wynik w można zanegowane.</span><span class="sxs-lookup"><span data-stu-id="c34c6-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="c34c6-109">Dowolne prawidłowe wyrażenie zwracające kolekcji do testowania pod kątem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="c34c6-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="c34c6-110">Wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `value`.</span><span class="sxs-lookup"><span data-stu-id="c34c6-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c34c6-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c34c6-111">Return Value</span></span>  
 <span data-ttu-id="c34c6-112">`true` Jeśli wartość zostanie znaleziony w kolekcji; wartość null, jeśli ma wartość null lub kolekcja ma wartość null; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c34c6-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="c34c6-113">Przy użyciu NOT IN Negacja wyniki cali</span><span class="sxs-lookup"><span data-stu-id="c34c6-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c34c6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c34c6-114">Example</span></span>  
 <span data-ttu-id="c34c6-115">Następujące zapytanie SQL jednostki używa operatora IN ustalenie, czy wartość odpowiada wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c34c6-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="c34c6-116">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c34c6-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c34c6-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c34c6-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c34c6-118">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c34c6-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="c34c6-119">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c34c6-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="c34c6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c34c6-120">See Also</span></span>  
 [<span data-ttu-id="c34c6-121">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c34c6-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
