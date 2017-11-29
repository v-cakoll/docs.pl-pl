---
title: '- (Dzielenie) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0f215e12f9f86ee08679bdb2e2638c0c8df35ea4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="81c1a-102">/ (Dzielenie) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="81c1a-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="81c1a-103">Dzieli jedną liczbę przez inny.</span><span class="sxs-lookup"><span data-stu-id="81c1a-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81c1a-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="81c1a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="81c1a-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="81c1a-106">Wyrażenie liczbowe do dzielenia.</span><span class="sxs-lookup"><span data-stu-id="81c1a-106">The numeric expression to divide.</span></span> <span data-ttu-id="81c1a-107">`dividend`jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="81c1a-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="81c1a-108">Wyrażenie liczbowe do dzielenia dzielna przez.</span><span class="sxs-lookup"><span data-stu-id="81c1a-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="81c1a-109">`divisor`jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="81c1a-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="81c1a-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="81c1a-110">Result Types</span></span>  
 <span data-ttu-id="81c1a-111">Typ danych, który powoduje z typem niejawnym promocji dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="81c1a-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="81c1a-112">Aby uzyskać więcej informacji na temat podwyższania poziomu typu niejawnego zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="81c1a-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81c1a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="81c1a-113">Example</span></span>  
 <span data-ttu-id="81c1a-114">Następujące zapytanie SQL jednostki używa / arytmetyczne operatora, aby podzielić jeden numer przez inny.</span><span class="sxs-lookup"><span data-stu-id="81c1a-114">The following Entity SQL query uses the / arithmetic operator to divide one numer by another.</span></span> <span data-ttu-id="81c1a-115">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="81c1a-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="81c1a-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="81c1a-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="81c1a-117">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="81c1a-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="81c1a-118">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="81c1a-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="81c1a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81c1a-119">See Also</span></span>  
 [<span data-ttu-id="81c1a-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="81c1a-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
