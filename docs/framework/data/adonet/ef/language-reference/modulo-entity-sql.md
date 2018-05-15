---
title: (Modulo) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: ad7b76c1479906e9dcd875407e75475b55d5ae16
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="476d6-102">(Modulo) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="476d6-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="476d6-103">Zwraca resztę z jednego wyrażenia podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="476d6-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="476d6-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="476d6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="476d6-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="476d6-106">Wyrażenie liczbowe do dzielenia.</span><span class="sxs-lookup"><span data-stu-id="476d6-106">The numeric expression to divide.</span></span> <span data-ttu-id="476d6-107">`dividend` jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="476d6-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="476d6-108">Wyrażenie liczbowe do dzielenia dzielna przez.</span><span class="sxs-lookup"><span data-stu-id="476d6-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="476d6-109">`divisor` jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="476d6-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="476d6-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="476d6-110">Result Types</span></span>  
 <span data-ttu-id="476d6-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="476d6-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="476d6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="476d6-112">Example</span></span>  
 <span data-ttu-id="476d6-113">Następujące zapytanie SQL jednostki użyto operatora arytmetycznego %, która zwraca pozostałej części jedno wyrażenie podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="476d6-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="476d6-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="476d6-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="476d6-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="476d6-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="476d6-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="476d6-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="476d6-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="476d6-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="476d6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="476d6-118">See Also</span></span>  
 [<span data-ttu-id="476d6-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="476d6-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
