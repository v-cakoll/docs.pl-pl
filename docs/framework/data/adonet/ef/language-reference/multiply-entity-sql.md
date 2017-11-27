---
title: "* (Należy pomnożyć) (Jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47ccf810dde528af757f9c5698950198224b3118
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="97316-102">* (Mnożenia) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="97316-102">* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="97316-103">Mnoży dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="97316-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97316-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97316-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="97316-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="97316-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="97316-106">Dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="97316-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="97316-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="97316-107">Result Types</span></span>  
 <span data-ttu-id="97316-108">Typ danych, który powoduje z typem niejawnym promocji dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="97316-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="97316-109">Aby uzyskać więcej informacji na temat podwyższania poziomu typu niejawnego zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="97316-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97316-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="97316-110">Example</span></span>  
 <span data-ttu-id="97316-111">Następujące zapytanie SQL jednostki używa * operatora arytmetycznego Aby pomnożyć dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="97316-111">The following Entity SQL query uses the * arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="97316-112">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="97316-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="97316-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="97316-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="97316-114">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="97316-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="97316-115">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="97316-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="97316-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97316-116">See Also</span></span>  
 [<span data-ttu-id="97316-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="97316-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
