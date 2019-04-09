---
title: '>= (Większe niż lub równe) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 1e2eef7c98aefd93c6ef388888661ac758fd8e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166117"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="9a02d-102">> = (większe niż lub równe) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="9a02d-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="9a02d-103">Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="9a02d-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a02d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a02d-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a02d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a02d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9a02d-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="9a02d-106">Any valid expression.</span></span> <span data-ttu-id="9a02d-107">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="9a02d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9a02d-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="9a02d-108">Result Types</span></span>  
 `true` <span data-ttu-id="9a02d-109">Jeśli lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="9a02d-109">if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a02d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a02d-110">Example</span></span>  
 <span data-ttu-id="9a02d-111">Używa następującego zapytania SQL jednostki > =, operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="9a02d-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="9a02d-112">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9a02d-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a02d-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9a02d-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9a02d-114">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9a02d-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9a02d-115">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="9a02d-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="9a02d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a02d-116">See also</span></span>

- [<span data-ttu-id="9a02d-117">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9a02d-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
