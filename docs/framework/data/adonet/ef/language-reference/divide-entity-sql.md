---
title: '- Mieszczon (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 79fdbebc648daac4f695387d52d2a915383f99ca
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833887"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="00856-102">/(Dzielenie) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="00856-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="00856-103">Dzieli jedną liczbę przez inną.</span><span class="sxs-lookup"><span data-stu-id="00856-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00856-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00856-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="00856-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="00856-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="00856-106">Wyrażenie liczbowe do podzielenia.</span><span class="sxs-lookup"><span data-stu-id="00856-106">The numeric expression to divide.</span></span> <span data-ttu-id="00856-107">`dividend` jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="00856-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="00856-108">Wyrażenie liczbowe dzielące dywidendę przez.</span><span class="sxs-lookup"><span data-stu-id="00856-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="00856-109">`divisor` jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="00856-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="00856-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="00856-110">Result Types</span></span>  
 <span data-ttu-id="00856-111">Typ danych, który wynika z promocji typu niejawnego dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="00856-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="00856-112">Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="00856-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00856-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="00856-113">Example</span></span>  
 <span data-ttu-id="00856-114">Poniższe zapytanie Entity SQL używa operatora arytmetycznego w celu podzielenia jednej liczby przez inną.</span><span class="sxs-lookup"><span data-stu-id="00856-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="00856-115">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="00856-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="00856-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="00856-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="00856-117">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="00856-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="00856-118">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="00856-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="00856-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00856-119">See also</span></span>

- [<span data-ttu-id="00856-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="00856-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
