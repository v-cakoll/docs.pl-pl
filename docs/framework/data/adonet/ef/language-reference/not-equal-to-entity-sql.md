---
title: '! = (Nie równa się) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: f5fdbbf2892781ce44dfe73e8cd80fbe0f74cf1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310970"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="b69d2-102">! = (Nie równa się) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="b69d2-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="b69d2-103">Porównuje dwa wyrażenia w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="b69d2-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="b69d2-104">! = — Operator (nie równa się) jest funkcjonalnym odpowiednikiem < > — operator.</span><span class="sxs-lookup"><span data-stu-id="b69d2-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b69d2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b69d2-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b69d2-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b69d2-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b69d2-107">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b69d2-107">Any valid expression.</span></span> <span data-ttu-id="b69d2-108">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="b69d2-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b69d2-109">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="b69d2-109">Result Types</span></span>  
 <span data-ttu-id="b69d2-110">`true` Jeśli po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b69d2-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b69d2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b69d2-111">Example</span></span>  
 <span data-ttu-id="b69d2-112">Następujące zapytanie SQL jednostki używa! = — operator do porównywania dwóch wyrażeń w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="b69d2-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="b69d2-113">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b69d2-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b69d2-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b69d2-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b69d2-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b69d2-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b69d2-116">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b69d2-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="b69d2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b69d2-117">See also</span></span>

- [<span data-ttu-id="b69d2-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b69d2-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
