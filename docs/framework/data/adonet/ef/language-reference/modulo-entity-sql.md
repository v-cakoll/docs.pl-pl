---
title: Operator (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250086"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="c638c-102">Operator (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c638c-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="c638c-103">Zwraca resztę jednego wyrażenia podzieloną przez inny.</span><span class="sxs-lookup"><span data-stu-id="c638c-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c638c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c638c-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="c638c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c638c-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="c638c-106">Wyrażenie liczbowe do podzielenia.</span><span class="sxs-lookup"><span data-stu-id="c638c-106">The numeric expression to divide.</span></span> <span data-ttu-id="c638c-107">`dividend`jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="c638c-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="c638c-108">Wyrażenie liczbowe dzielące dywidendę przez.</span><span class="sxs-lookup"><span data-stu-id="c638c-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="c638c-109">`divisor`jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="c638c-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c638c-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="c638c-110">Result Types</span></span>  
 <span data-ttu-id="c638c-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="c638c-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="c638c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c638c-112">Example</span></span>  
 <span data-ttu-id="c638c-113">Poniższe zapytanie Entity SQL używa operatora arytmetycznego% do zwrócenia reszty jednego wyrażenia podzielonego przez inny.</span><span class="sxs-lookup"><span data-stu-id="c638c-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="c638c-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c638c-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c638c-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c638c-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c638c-116">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="c638c-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c638c-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c638c-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="c638c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c638c-118">See also</span></span>

- [<span data-ttu-id="c638c-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c638c-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
