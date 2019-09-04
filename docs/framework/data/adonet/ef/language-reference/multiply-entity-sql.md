---
title: '* Mnożenia (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 19fb73d327f91303de938a5f49866339413b9698
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250060"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="a595f-102">\* (Pomnóż) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a595f-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="a595f-103">Mnoży dwa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a595f-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a595f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a595f-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a595f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a595f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a595f-106">Dowolne prawidłowe wyrażenie jednego z typów danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a595f-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a595f-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="a595f-107">Result Types</span></span>  
 <span data-ttu-id="a595f-108">Typ danych, który wynika z promocji typu niejawnego dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="a595f-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a595f-109">Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a595f-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a595f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a595f-110">Example</span></span>  
 <span data-ttu-id="a595f-111">Poniższe zapytanie Entity SQL używa operatora \* arytmetycznego, aby pomnożyć dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="a595f-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="a595f-112">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a595f-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a595f-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a595f-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a595f-114">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="a595f-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a595f-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a595f-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="a595f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a595f-116">See also</span></span>

- [<span data-ttu-id="a595f-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a595f-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
