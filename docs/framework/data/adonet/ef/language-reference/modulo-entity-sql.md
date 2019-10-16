---
title: Operator (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 4bbdbe53403cfec2568cfac320fc7ab1ad2725b0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319603"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="3f922-102">Operator (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3f922-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="3f922-103">Zwraca resztę jednego wyrażenia podzieloną przez inny.</span><span class="sxs-lookup"><span data-stu-id="3f922-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f922-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f922-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f922-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3f922-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="3f922-106">Wyrażenie liczbowe do podzielenia.</span><span class="sxs-lookup"><span data-stu-id="3f922-106">The numeric expression to divide.</span></span> <span data-ttu-id="3f922-107">`dividend` jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="3f922-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="3f922-108">Wyrażenie liczbowe dzielące dywidendę przez.</span><span class="sxs-lookup"><span data-stu-id="3f922-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="3f922-109">`divisor` jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="3f922-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3f922-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="3f922-110">Result Types</span></span>  
 <span data-ttu-id="3f922-111">EDM. Int32</span><span class="sxs-lookup"><span data-stu-id="3f922-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f922-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f922-112">Example</span></span>  
 <span data-ttu-id="3f922-113">Poniższe zapytanie Entity SQL używa operatora arytmetycznego% do zwrócenia reszty jednego wyrażenia podzielonego przez inny.</span><span class="sxs-lookup"><span data-stu-id="3f922-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="3f922-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3f922-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3f922-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3f922-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3f922-116">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3f922-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3f922-117">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="3f922-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="3f922-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f922-118">See also</span></span>

- [<span data-ttu-id="3f922-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3f922-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
