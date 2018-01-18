---
title: "= (Równa) (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 27faf6c59afd4de2481f474053812b12182e3f58
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="3e84d-102">= (Równa) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="3e84d-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="3e84d-103">Porównuje równość dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3e84d-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e84d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e84d-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e84d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3e84d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3e84d-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="3e84d-106">Any valid expression.</span></span> <span data-ttu-id="3e84d-107">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="3e84d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3e84d-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="3e84d-108">Result Types</span></span>  
 <span data-ttu-id="3e84d-109">`true`Jeśli po lewej stronie wyrażenia jest taki sam, jak prawo wyrażenia. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3e84d-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e84d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e84d-110">Remarks</span></span>  
 <span data-ttu-id="3e84d-111">== — Operator jest odpowiednikiem =.</span><span class="sxs-lookup"><span data-stu-id="3e84d-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e84d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e84d-112">Example</span></span>  
 <span data-ttu-id="3e84d-113">Następujące zapytanie SQL jednostki używa = — operator porównania do porównania równości dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3e84d-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="3e84d-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3e84d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3e84d-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3e84d-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3e84d-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3e84d-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3e84d-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="3e84d-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="3e84d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e84d-118">See Also</span></span>  
 [<span data-ttu-id="3e84d-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3e84d-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
