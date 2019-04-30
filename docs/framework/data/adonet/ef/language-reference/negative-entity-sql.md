---
title: '- (Negatywna) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 6e5512546faeaa9760dcf135165a999a6f95322b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760392"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="2f9dc-102">-(Ujemnej) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="2f9dc-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="2f9dc-103">Zwraca wartość ujemną wartość wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f9dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f9dc-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f9dc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2f9dc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2f9dc-106">Dowolne prawidłowe wyrażenie jeden z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2f9dc-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="2f9dc-107">Result Types</span></span>  
 <span data-ttu-id="2f9dc-108">Typ danych `expression`.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f9dc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f9dc-109">Remarks</span></span>  
 <span data-ttu-id="2f9dc-110">Jeśli `expression` jest typ bez znaku typu wyniku będzie typ ze znakiem, który najlepiej odnosi się do typu `expression`.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="2f9dc-111">Na przykład jeśli `expression` typu Byte, wartości typu Int16 zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f9dc-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f9dc-112">Example</span></span>  
 <span data-ttu-id="2f9dc-113">Następujące zapytanie SQL jednostki używa operator arytmetyczny, aby zwrócić wartość ujemną wartość wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="2f9dc-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2f9dc-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2f9dc-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="2f9dc-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2f9dc-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2f9dc-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2f9dc-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="2f9dc-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="2f9dc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f9dc-118">See also</span></span>

- [<span data-ttu-id="2f9dc-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="2f9dc-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
