---
title: '>= (Większe lub równe) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833744"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="5b68e-102">> = (większe lub równe) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5b68e-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="5b68e-103">Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość większą lub równą prawemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5b68e-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b68e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b68e-104">Syntax</span></span>  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b68e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5b68e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5b68e-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5b68e-106">Any valid expression.</span></span> <span data-ttu-id="5b68e-107">Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.</span><span class="sxs-lookup"><span data-stu-id="5b68e-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5b68e-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="5b68e-108">Result Types</span></span>  
 <span data-ttu-id="5b68e-109">`true`, jeśli lewe wyrażenie ma wartość większą lub równą prawemu wyrażeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="5b68e-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b68e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b68e-110">Example</span></span>  
 <span data-ttu-id="5b68e-111">Poniższe zapytanie Entity SQL używa operatora porównania > = do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość większą lub równą prawemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5b68e-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="5b68e-112">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5b68e-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5b68e-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="5b68e-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5b68e-114">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5b68e-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5b68e-115">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="5b68e-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="5b68e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b68e-116">See also</span></span>

- [<span data-ttu-id="5b68e-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b68e-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
