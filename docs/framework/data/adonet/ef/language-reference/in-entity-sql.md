---
title: W (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833694"
---
# <a name="in-entity-sql"></a><span data-ttu-id="23f60-102">W (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="23f60-102">IN (Entity SQL)</span></span>
<span data-ttu-id="23f60-103">Określa, czy wartość jest zgodna z dowolną wartością w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23f60-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23f60-104">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="23f60-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="23f60-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="23f60-106">Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="23f60-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="23f60-107">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="23f60-107">[ NOT ]</span></span>  
 <span data-ttu-id="23f60-108">Określa, że wynik `Boolean` jest negacji.</span><span class="sxs-lookup"><span data-stu-id="23f60-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="23f60-109">Dowolne prawidłowe wyrażenie zwracające kolekcję do przetestowania w celu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="23f60-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="23f60-110">Wszystkie wyrażenia muszą być tego samego typu lub wspólnego typu podstawowego lub pochodnego jako `value`.</span><span class="sxs-lookup"><span data-stu-id="23f60-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23f60-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23f60-111">Return Value</span></span>  
 <span data-ttu-id="23f60-112">`true`, jeśli wartość zostanie znaleziona w kolekcji; wartość null, jeśli wartość jest równa null lub kolekcja ma wartość null; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="23f60-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="23f60-113">Użycie nie jest w wyniku negacji wyników w.</span><span class="sxs-lookup"><span data-stu-id="23f60-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23f60-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="23f60-114">Example</span></span>  
 <span data-ttu-id="23f60-115">Poniższe zapytanie Entity SQL używa operatora IN, aby określić, czy wartość pasuje do dowolnej wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23f60-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="23f60-116">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="23f60-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="23f60-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="23f60-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="23f60-118">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="23f60-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="23f60-119">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="23f60-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="23f60-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23f60-120">See also</span></span>

- [<span data-ttu-id="23f60-121">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="23f60-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
