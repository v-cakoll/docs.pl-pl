---
title: '- (Dzielenie) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: c3b477a63adf3c3d51f28449e94c2b716422296c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330860"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="a3213-102">/ (Dzielenie) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="a3213-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="a3213-103">Dzieli liczbę przez inny.</span><span class="sxs-lookup"><span data-stu-id="a3213-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3213-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3213-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3213-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a3213-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="a3213-106">Wyrażenie liczbowe, aby podzielić.</span><span class="sxs-lookup"><span data-stu-id="a3213-106">The numeric expression to divide.</span></span> `dividend` <span data-ttu-id="a3213-107">jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a3213-107">is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="a3213-108">Wyrażenie liczbowe do dzielenia dzielnej przez.</span><span class="sxs-lookup"><span data-stu-id="a3213-108">The numeric expression to divide the dividend by.</span></span> `divisor` <span data-ttu-id="a3213-109">jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a3213-109">is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a3213-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="a3213-110">Result Types</span></span>  
 <span data-ttu-id="a3213-111">Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="a3213-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a3213-112">Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a3213-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3213-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3213-113">Example</span></span>  
 <span data-ttu-id="a3213-114">Następujące zapytanie SQL jednostki używa / arytmetyczne operator dzielnikiem jeden numer innego.</span><span class="sxs-lookup"><span data-stu-id="a3213-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="a3213-115">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a3213-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a3213-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a3213-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a3213-117">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a3213-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a3213-118">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a3213-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="a3213-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3213-119">See also</span></span>

- [<span data-ttu-id="a3213-120">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a3213-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
