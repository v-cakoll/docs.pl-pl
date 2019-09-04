---
title: < (Mniejsze niż) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: c1d19c9017a4b789b40332e4eca522e9758dcdf2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250450"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="5d0d9-102">\<(Mniejsze niż) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5d0d9-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="5d0d9-103">Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość mniejszą niż prawo wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5d0d9-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d0d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d0d9-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d0d9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5d0d9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5d0d9-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5d0d9-106">Any valid expression.</span></span> <span data-ttu-id="5d0d9-107">Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.</span><span class="sxs-lookup"><span data-stu-id="5d0d9-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5d0d9-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="5d0d9-108">Result Types</span></span>  
 <span data-ttu-id="5d0d9-109">`true`Jeśli lewe wyrażenie ma wartość mniejszą niż prawe wyrażenie; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="5d0d9-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d0d9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d0d9-110">Example</span></span>  
 <span data-ttu-id="5d0d9-111">Poniższe zapytanie Entity SQL używa operatora porównania < do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość mniejszą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5d0d9-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="5d0d9-112">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5d0d9-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5d0d9-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="5d0d9-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5d0d9-114">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="5d0d9-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5d0d9-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="5d0d9-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="5d0d9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d0d9-116">See also</span></span>

- [<span data-ttu-id="5d0d9-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5d0d9-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
