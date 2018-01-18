---
title: W (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d32e5012b4acbf0ecd6830f549de5dccf79bb38b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="in-entity-sql"></a><span data-ttu-id="566ef-102">W (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="566ef-102">IN (Entity SQL)</span></span>
<span data-ttu-id="566ef-103">Określa, czy wartość odpowiada wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="566ef-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="566ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="566ef-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="566ef-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="566ef-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="566ef-106">Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="566ef-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="566ef-107">[NOT]</span><span class="sxs-lookup"><span data-stu-id="566ef-107">[ NOT ]</span></span>  
 <span data-ttu-id="566ef-108">Określa, że `Boolean` wynik w można zanegowane.</span><span class="sxs-lookup"><span data-stu-id="566ef-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="566ef-109">Dowolne prawidłowe wyrażenie zwracające kolekcji do testowania pod kątem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="566ef-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="566ef-110">Wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `value`.</span><span class="sxs-lookup"><span data-stu-id="566ef-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="566ef-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="566ef-111">Return Value</span></span>  
 <span data-ttu-id="566ef-112">`true`Jeśli wartość zostanie znaleziony w kolekcji; wartość null, jeśli ma wartość null lub kolekcja ma wartość null; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="566ef-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="566ef-113">Przy użyciu NOT IN Negacja wyniki cali</span><span class="sxs-lookup"><span data-stu-id="566ef-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="566ef-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="566ef-114">Example</span></span>  
 <span data-ttu-id="566ef-115">Następujące zapytanie SQL jednostki używa operatora IN ustalenie, czy wartość odpowiada wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="566ef-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="566ef-116">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="566ef-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="566ef-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="566ef-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="566ef-118">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="566ef-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="566ef-119">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="566ef-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="566ef-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="566ef-120">See Also</span></span>  
 [<span data-ttu-id="566ef-121">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="566ef-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
