---
title: + (Łączenie ciągów) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: ef482a1206dea98cfb5a0ba5071acc130ef0cd18
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249032"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="c224c-102">+ (Łączenie ciągów) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c224c-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="c224c-103">Łączy dwa ciągi.</span><span class="sxs-lookup"><span data-stu-id="c224c-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c224c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c224c-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c224c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c224c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c224c-106">Dowolne prawidłowe wyrażenie modelu EDM. Typy danych ciągu.</span><span class="sxs-lookup"><span data-stu-id="c224c-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="c224c-107">Oba wyrażenia muszą być tego samego typu danych lub jedno wyrażenie musi być możliwe do niejawnego przekonwertowania na typ danych innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c224c-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c224c-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="c224c-108">Result Types</span></span>  
 <span data-ttu-id="c224c-109">Typ danych, który wynika z promocji typu niejawnego dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="c224c-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="c224c-110">Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c224c-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c224c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c224c-111">Example</span></span>  
 <span data-ttu-id="c224c-112">Poniższe zapytanie Entity SQL używa operatora + do łączenia dwóch ciągów.</span><span class="sxs-lookup"><span data-stu-id="c224c-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="c224c-113">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c224c-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c224c-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c224c-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c224c-115">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="c224c-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="c224c-116">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c224c-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="c224c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c224c-117">See also</span></span>

- [<span data-ttu-id="c224c-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c224c-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c224c-119">Typy modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="c224c-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
