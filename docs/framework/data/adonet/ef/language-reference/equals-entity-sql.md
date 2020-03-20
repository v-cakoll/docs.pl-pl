---
title: = (Równa się) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150315"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="58135-102">= (Równa się) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="58135-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="58135-103">Porównuje równość dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="58135-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58135-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58135-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="58135-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="58135-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="58135-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="58135-106">Any valid expression.</span></span> <span data-ttu-id="58135-107">Oba wyrażenia muszą mieć niejawnie konwertowane typy danych.</span><span class="sxs-lookup"><span data-stu-id="58135-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="58135-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="58135-108">Result Types</span></span>  
 <span data-ttu-id="58135-109">`true`jeśli wyrażenie lewe jest równe prawemu wyrażeniu; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="58135-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58135-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58135-110">Remarks</span></span>  
 <span data-ttu-id="58135-111">Operator == jest odpowiednikiem =.</span><span class="sxs-lookup"><span data-stu-id="58135-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58135-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="58135-112">Example</span></span>  
 <span data-ttu-id="58135-113">Następująca kwerenda SQL jednostki używa = operator porównania, aby porównać równość dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="58135-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="58135-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="58135-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="58135-115">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="58135-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="58135-116">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="58135-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="58135-117">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="58135-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="58135-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58135-118">See also</span></span>

- [<span data-ttu-id="58135-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="58135-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
