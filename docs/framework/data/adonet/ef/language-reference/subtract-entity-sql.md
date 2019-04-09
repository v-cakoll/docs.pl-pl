---
title: '- (Odjąć) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: d7eee2fdb8e61711b453f4f444cc8dc8d5a43558
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128833"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="fc34e-102">-(Odejmowanie) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="fc34e-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="fc34e-103">Odejmuje dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="fc34e-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc34e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc34e-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc34e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fc34e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fc34e-106">Dowolne prawidłowe wyrażenie jeden z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="fc34e-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fc34e-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="fc34e-107">Result Types</span></span>  
 <span data-ttu-id="fc34e-108">Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="fc34e-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fc34e-109">Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fc34e-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc34e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc34e-110">Example</span></span>  
 <span data-ttu-id="fc34e-111">Następujące zapytanie SQL jednostki używa operatora arytmetycznego na potrzeby odejmowania dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="fc34e-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="fc34e-112">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fc34e-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fc34e-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="fc34e-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fc34e-114">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fc34e-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fc34e-115">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="fc34e-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="fc34e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc34e-116">See also</span></span>

- [<span data-ttu-id="fc34e-117">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fc34e-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
