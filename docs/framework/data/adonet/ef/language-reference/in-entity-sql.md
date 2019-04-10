---
title: W (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: d88f79dbfcd27f0ca0d1e26815d7d2bbee731bcf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331276"
---
# <a name="in-entity-sql"></a><span data-ttu-id="cd973-102">W (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cd973-102">IN (Entity SQL)</span></span>
<span data-ttu-id="cd973-103">Określa, czy wartość pasuje do dowolnej wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cd973-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd973-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd973-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd973-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cd973-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="cd973-106">Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="cd973-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="cd973-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="cd973-107">[ NOT ]</span></span>  
 <span data-ttu-id="cd973-108">Określa, że `Boolean` wynik w być ujemna.</span><span class="sxs-lookup"><span data-stu-id="cd973-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="cd973-109">Dowolne prawidłowe wyrażenie, które zwraca kolekcję do testowania pod kątem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="cd973-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="cd973-110">Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `value`.</span><span class="sxs-lookup"><span data-stu-id="cd973-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd973-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd973-111">Return Value</span></span>  
 `true` <span data-ttu-id="cd973-112">Jeśli wartość zostanie znaleziony w kolekcji; wartość null, jeśli ma wartość null lub kolekcji mają wartość null; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cd973-112">if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="cd973-113">Za pomocą NOT IN neguje wyniki cali</span><span class="sxs-lookup"><span data-stu-id="cd973-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd973-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd973-114">Example</span></span>  
 <span data-ttu-id="cd973-115">Następujące zapytanie SQL jednostki używa operatora w celu ustalenia, czy wartość pasuje do dowolnej wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cd973-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="cd973-116">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cd973-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cd973-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cd973-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cd973-118">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cd973-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="cd973-119">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cd973-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="cd973-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd973-120">See also</span></span>

- [<span data-ttu-id="cd973-121">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cd973-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
