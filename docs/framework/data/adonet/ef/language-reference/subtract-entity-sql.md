---
title: "- Odejmuje (wartość) (Jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5ca2bc8cb34d99421962289930c26de84eaa68e2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="eddc8-102">-(Odejmowanie) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="eddc8-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="eddc8-103">Odejmuje dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="eddc8-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eddc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eddc8-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="eddc8-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="eddc8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="eddc8-106">Dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="eddc8-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="eddc8-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="eddc8-107">Result Types</span></span>  
 <span data-ttu-id="eddc8-108">Typ danych, który powoduje z typem niejawnym promocji dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="eddc8-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="eddc8-109">Aby uzyskać więcej informacji na temat podwyższania poziomu typu niejawnego zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eddc8-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eddc8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="eddc8-110">Example</span></span>  
 <span data-ttu-id="eddc8-111">Następujące zapytanie SQL jednostki używa operator arytmetyczny do odjęcia dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="eddc8-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="eddc8-112">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eddc8-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eddc8-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="eddc8-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="eddc8-114">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eddc8-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="eddc8-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="eddc8-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="eddc8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eddc8-116">See Also</span></span>  
 [<span data-ttu-id="eddc8-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="eddc8-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
