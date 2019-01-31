---
title: '>= (Większe niż lub równe) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 4b7b2aa7be0b978fb6b1317393fb3c6e9a87c621
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289019"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="ac0e9-102">> = (większe niż lub równe) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ac0e9-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="ac0e9-103">Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac0e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac0e9-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac0e9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ac0e9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ac0e9-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-106">Any valid expression.</span></span> <span data-ttu-id="ac0e9-107">Oba wyrażenia muszą mieć niejawnej konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ac0e9-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="ac0e9-108">Result Types</span></span>  
 <span data-ttu-id="ac0e9-109">`true` Jeśli lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac0e9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac0e9-110">Example</span></span>  
 <span data-ttu-id="ac0e9-111">Używa następującego zapytania SQL jednostki > =, operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="ac0e9-112">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ac0e9-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ac0e9-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ac0e9-114">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ac0e9-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ac0e9-115">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ac0e9-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ac0e9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac0e9-116">See also</span></span>
- [<span data-ttu-id="ac0e9-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ac0e9-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
