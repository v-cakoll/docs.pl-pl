---
title: + (Dodawanie)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 8ecbb7a8b38625f248dbfb5974bb8c64eb482ca2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328273"
---
# <a name="-add"></a><span data-ttu-id="34ce2-102">+ (Dodaj)</span><span class="sxs-lookup"><span data-stu-id="34ce2-102">+ (Add)</span></span>
<span data-ttu-id="34ce2-103">Dodaje dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="34ce2-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34ce2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34ce2-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="34ce2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="34ce2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="34ce2-106">Dowolne prawidłowe wyrażenie jeden z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="34ce2-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="34ce2-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="34ce2-107">Result Types</span></span>  
 <span data-ttu-id="34ce2-108">Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="34ce2-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="34ce2-109">Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="34ce2-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34ce2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34ce2-110">Remarks</span></span>  
 <span data-ttu-id="34ce2-111">Aby uzyskać EDM. Typy ciągu, dodanie jest łączenia.</span><span class="sxs-lookup"><span data-stu-id="34ce2-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34ce2-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="34ce2-112">Example</span></span>  
 <span data-ttu-id="34ce2-113">Następujące zapytanie SQL jednostki używa + operatora arytmetycznego na dodanie dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="34ce2-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="34ce2-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="34ce2-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="34ce2-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="34ce2-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="34ce2-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="34ce2-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="34ce2-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="34ce2-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="34ce2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34ce2-118">See also</span></span>

- [<span data-ttu-id="34ce2-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="34ce2-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="34ce2-120">Model koncepcyjny typów (CSDL)</span><span class="sxs-lookup"><span data-stu-id="34ce2-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
