---
title: '- Odjęt (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: fe9152100bddac86f3fb7fae1ab3c0b81ae58418
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319331"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="8bb5e-102">-(Odejmij) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8bb5e-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="8bb5e-103">Odejmuje dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="8bb5e-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bb5e-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8bb5e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8bb5e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8bb5e-106">Dowolne prawidłowe wyrażenie jednego z typów danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="8bb5e-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8bb5e-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="8bb5e-107">Result Types</span></span>  
 <span data-ttu-id="8bb5e-108">Typ danych, który wynika z promocji typu niejawnego dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="8bb5e-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="8bb5e-109">Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8bb5e-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bb5e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb5e-110">Example</span></span>  
 <span data-ttu-id="8bb5e-111">Poniższe zapytanie Entity SQL używa operatora-arytmetycznego do odejmowania dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="8bb5e-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="8bb5e-112">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8bb5e-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8bb5e-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="8bb5e-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8bb5e-114">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8bb5e-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8bb5e-115">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="8bb5e-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb5e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bb5e-116">See also</span></span>

- [<span data-ttu-id="8bb5e-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="8bb5e-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
