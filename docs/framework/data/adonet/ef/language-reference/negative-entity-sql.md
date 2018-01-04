---
title: '- (Ujemne) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 78d5ccbcfe23acd1a8b9b285d865452e7ccad00f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="bcd5c-102">-(Ujemna) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="bcd5c-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="bcd5c-103">Zwraca wartość ujemną wartość wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcd5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcd5c-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="bcd5c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bcd5c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bcd5c-106">Dowolne prawidłowe wyrażenie jednego z typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="bcd5c-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="bcd5c-107">Result Types</span></span>  
 <span data-ttu-id="bcd5c-108">Typ danych miary `expression`.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcd5c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bcd5c-109">Remarks</span></span>  
 <span data-ttu-id="bcd5c-110">Jeśli `expression` jest typu unsigned, typ wynik będzie podpisany typ, który najlepiej odnosi się do typu `expression`.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="bcd5c-111">Na przykład jeśli `expression` była typu Byte, wartości typu Int16 zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcd5c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="bcd5c-112">Example</span></span>  
 <span data-ttu-id="bcd5c-113">Następujące zapytanie SQL jednostki używa operator arytmetyczny, aby zwrócić wartość ujemną wartość wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="bcd5c-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bcd5c-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bcd5c-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="bcd5c-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bcd5c-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bcd5c-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="bcd5c-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="bcd5c-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="bcd5c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcd5c-118">See Also</span></span>  
 [<span data-ttu-id="bcd5c-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="bcd5c-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
