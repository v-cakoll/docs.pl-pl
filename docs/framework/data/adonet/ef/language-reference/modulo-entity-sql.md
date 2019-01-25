---
title: (Modulo) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 543c35c56955fb0a9909fced23357444bc78197a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732599"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="de36f-102">(Modulo) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="de36f-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="de36f-103">Zwraca resztę z dzielenia jednego wyrażenia podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="de36f-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de36f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de36f-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="de36f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="de36f-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="de36f-106">Wyrażenie liczbowe, aby podzielić.</span><span class="sxs-lookup"><span data-stu-id="de36f-106">The numeric expression to divide.</span></span> <span data-ttu-id="de36f-107">`dividend` jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="de36f-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="de36f-108">Wyrażenie liczbowe do dzielenia dzielnej przez.</span><span class="sxs-lookup"><span data-stu-id="de36f-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="de36f-109">`divisor` jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="de36f-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="de36f-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="de36f-110">Result Types</span></span>  
 <span data-ttu-id="de36f-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="de36f-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="de36f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="de36f-112">Example</span></span>  
 <span data-ttu-id="de36f-113">Następujące zapytanie SQL jednostki używa operatora arytmetycznego % do zwracania końca jedno wyrażenie podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="de36f-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="de36f-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="de36f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="de36f-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="de36f-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="de36f-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="de36f-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="de36f-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="de36f-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="de36f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de36f-118">See also</span></span>
- [<span data-ttu-id="de36f-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="de36f-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
