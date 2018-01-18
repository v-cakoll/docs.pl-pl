---
title: (Modulo) (Jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e204612904aa55b4a0ae9aa65f2bbfd644bbc396
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="c1308-102">(Modulo) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c1308-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="c1308-103">Zwraca resztę z jednego wyrażenia podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="c1308-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1308-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1308-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1308-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c1308-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="c1308-106">Wyrażenie liczbowe do dzielenia.</span><span class="sxs-lookup"><span data-stu-id="c1308-106">The numeric expression to divide.</span></span> <span data-ttu-id="c1308-107">`dividend`jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="c1308-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="c1308-108">Wyrażenie liczbowe do dzielenia dzielna przez.</span><span class="sxs-lookup"><span data-stu-id="c1308-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="c1308-109">`divisor`jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="c1308-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c1308-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="c1308-110">Result Types</span></span>  
 <span data-ttu-id="c1308-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="c1308-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1308-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1308-112">Example</span></span>  
 <span data-ttu-id="c1308-113">Następujące zapytanie SQL jednostki użyto operatora arytmetycznego %, która zwraca pozostałej części jedno wyrażenie podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="c1308-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="c1308-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c1308-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c1308-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c1308-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c1308-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c1308-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="c1308-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c1308-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="c1308-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1308-118">See Also</span></span>  
 [<span data-ttu-id="c1308-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c1308-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
