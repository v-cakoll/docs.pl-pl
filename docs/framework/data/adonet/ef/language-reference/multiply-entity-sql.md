---
title: '* (Należy pomnożyć) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 308df758d59a7e12a8b5a19ae72fcbee2f168490
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329729"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="a506b-102">\* (Mnożenie) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="a506b-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="a506b-103">Mnoży dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a506b-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a506b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a506b-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a506b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a506b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a506b-106">Dowolne prawidłowe wyrażenie jeden z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a506b-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a506b-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="a506b-107">Result Types</span></span>  
 <span data-ttu-id="a506b-108">Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="a506b-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a506b-109">Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a506b-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a506b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a506b-110">Example</span></span>  
 <span data-ttu-id="a506b-111">Następujące zapytanie SQL jednostki używa \* operatora arytmetycznego na mnożenia dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="a506b-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="a506b-112">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a506b-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a506b-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a506b-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a506b-114">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a506b-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a506b-115">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a506b-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="a506b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a506b-116">See also</span></span>

- [<span data-ttu-id="a506b-117">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a506b-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
