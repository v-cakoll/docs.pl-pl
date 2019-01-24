---
title: '! = (Nie równa się) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: d5e59fe61dbc05a48e98f5720dca446482b9968e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568139"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="377e3-102">! = (Nie równa się) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="377e3-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="377e3-103">Porównuje dwa wyrażenia w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="377e3-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="377e3-104">! = — Operator (nie równa się) jest funkcjonalnym odpowiednikiem < > — operator.</span><span class="sxs-lookup"><span data-stu-id="377e3-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377e3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="377e3-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="377e3-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="377e3-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="377e3-107">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="377e3-107">Any valid expression.</span></span> <span data-ttu-id="377e3-108">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="377e3-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="377e3-109">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="377e3-109">Result Types</span></span>  
 <span data-ttu-id="377e3-110">`true` Jeśli po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="377e3-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="377e3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="377e3-111">Example</span></span>  
 <span data-ttu-id="377e3-112">Następujące zapytanie SQL jednostki używa! = — operator do porównywania dwóch wyrażeń w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="377e3-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="377e3-113">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="377e3-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="377e3-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="377e3-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="377e3-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="377e3-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="377e3-116">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="377e3-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="377e3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="377e3-117">See also</span></span>
- [<span data-ttu-id="377e3-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="377e3-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
