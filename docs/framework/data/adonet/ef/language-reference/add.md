---
title: + (Dodawanie)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 62bb4782f135309eed8efa7e182fd8b75f92e126
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040291"
---
# <a name="-add"></a><span data-ttu-id="fb4ea-102">+ (Dodaj)</span><span class="sxs-lookup"><span data-stu-id="fb4ea-102">+ (Add)</span></span>
<span data-ttu-id="fb4ea-103">Dodaje dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="fb4ea-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb4ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb4ea-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb4ea-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fb4ea-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fb4ea-106">Dowolne prawidłowe wyrażenie jednego z typów danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="fb4ea-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fb4ea-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="fb4ea-107">Result Types</span></span>  
 <span data-ttu-id="fb4ea-108">Typ danych, który wynika z promocji typu niejawnego dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="fb4ea-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fb4ea-109">Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fb4ea-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb4ea-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb4ea-110">Remarks</span></span>  
 <span data-ttu-id="fb4ea-111">Dla modelu EDM. Typy ciągów, Dodawanie to łączenie.</span><span class="sxs-lookup"><span data-stu-id="fb4ea-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb4ea-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb4ea-112">Example</span></span>  
 <span data-ttu-id="fb4ea-113">Poniższe zapytanie Entity SQL używa operatora arytmetycznego +, aby dodać dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="fb4ea-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="fb4ea-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fb4ea-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fb4ea-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="fb4ea-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fb4ea-116">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fb4ea-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fb4ea-117">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="fb4ea-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="fb4ea-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb4ea-118">See also</span></span>

- [<span data-ttu-id="fb4ea-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="fb4ea-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fb4ea-120">Typy modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="fb4ea-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
