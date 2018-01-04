---
title: + (Dodaj)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: abd5921653e65c69da99a1aff60506aafd814278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="-add"></a><span data-ttu-id="1d7a0-102">+ (Dodaj)</span><span class="sxs-lookup"><span data-stu-id="1d7a0-102">+ (Add)</span></span>
<span data-ttu-id="1d7a0-103">Dodaje dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="1d7a0-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d7a0-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d7a0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1d7a0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1d7a0-106">Dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="1d7a0-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1d7a0-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="1d7a0-107">Result Types</span></span>  
 <span data-ttu-id="1d7a0-108">Typ danych, który powoduje z typem niejawnym promocji dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="1d7a0-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="1d7a0-109">Aby uzyskać więcej informacji na temat podwyższania poziomu typu niejawnego zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1d7a0-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d7a0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d7a0-110">Remarks</span></span>  
 <span data-ttu-id="1d7a0-111">Dla EDM. Parametry typów, dodanie jest łączenia.</span><span class="sxs-lookup"><span data-stu-id="1d7a0-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d7a0-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d7a0-112">Example</span></span>  
 <span data-ttu-id="1d7a0-113">Następujące zapytanie SQL jednostki używa + operatora arytmetycznego można dodać dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="1d7a0-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="1d7a0-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1d7a0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1d7a0-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1d7a0-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1d7a0-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1d7a0-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1d7a0-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1d7a0-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="1d7a0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d7a0-118">See Also</span></span>  
 [<span data-ttu-id="1d7a0-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1d7a0-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1d7a0-120">Typy modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="1d7a0-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)
