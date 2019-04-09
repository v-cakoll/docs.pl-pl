---
title: '! = (Nie równa się) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3d6e391e708b81c45af82280f200aebdaef41421
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130975"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="ad552-102">! = (Nie równa się) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ad552-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="ad552-103">Porównuje dwa wyrażenia w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="ad552-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="ad552-104">! = — Operator (nie równa się) jest funkcjonalnym odpowiednikiem < > — operator.</span><span class="sxs-lookup"><span data-stu-id="ad552-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad552-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad552-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad552-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ad552-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ad552-107">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="ad552-107">Any valid expression.</span></span> <span data-ttu-id="ad552-108">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="ad552-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ad552-109">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="ad552-109">Result Types</span></span>  
 `true` <span data-ttu-id="ad552-110">Jeśli po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ad552-110">if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad552-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad552-111">Example</span></span>  
 <span data-ttu-id="ad552-112">Następujące zapytanie SQL jednostki używa! = — operator do porównywania dwóch wyrażeń w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="ad552-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="ad552-113">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ad552-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ad552-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ad552-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ad552-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ad552-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ad552-116">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ad552-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ad552-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad552-117">See also</span></span>

- [<span data-ttu-id="ad552-118">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ad552-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
