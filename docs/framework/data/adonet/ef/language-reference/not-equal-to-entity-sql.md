---
title: "! = (Nie jest równa) (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 237dae641c272260e37fa7757792247700784d17
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="d7640-102">! = (Nie jest równa) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="d7640-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="d7640-103">Porównuje dwa wyrażenia, aby określić, czy po lewej stronie wyrażenia nie jest równa prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d7640-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="d7640-104">! = (Nie) operator równe jest funkcjonalnym odpowiednikiem < > — operator.</span><span class="sxs-lookup"><span data-stu-id="d7640-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7640-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7640-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7640-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7640-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d7640-107">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d7640-107">Any valid expression.</span></span> <span data-ttu-id="d7640-108">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="d7640-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d7640-109">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="d7640-109">Result Types</span></span>  
 <span data-ttu-id="d7640-110">`true`Jeśli po lewej stronie wyrażenia nie jest równa prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d7640-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7640-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7640-111">Example</span></span>  
 <span data-ttu-id="d7640-112">Następujące zapytanie SQL jednostki używa! = — operator do porównania dwóch wyrażeń w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d7640-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="d7640-113">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d7640-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7640-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d7640-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d7640-115">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d7640-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d7640-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d7640-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="d7640-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7640-117">See Also</span></span>  
 [<span data-ttu-id="d7640-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d7640-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
