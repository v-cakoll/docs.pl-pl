---
title: + (Dodaj)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: a3c41ef8cf393a4d1b1deb362d6a3614558a34ba
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326140"
---
# <a name="-add"></a><span data-ttu-id="9d01b-102">+ (Dodaj)</span><span class="sxs-lookup"><span data-stu-id="9d01b-102">+ (Add)</span></span>
<span data-ttu-id="9d01b-103">Dodaje dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="9d01b-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d01b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d01b-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d01b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9d01b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9d01b-106">Dowolne prawidłowe wyrażenie jeden z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="9d01b-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9d01b-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="9d01b-107">Result Types</span></span>  
 <span data-ttu-id="9d01b-108">Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="9d01b-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9d01b-109">Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9d01b-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d01b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d01b-110">Remarks</span></span>  
 <span data-ttu-id="9d01b-111">Aby uzyskać EDM. Typy ciągu, dodanie jest łączenia.</span><span class="sxs-lookup"><span data-stu-id="9d01b-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d01b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d01b-112">Example</span></span>  
 <span data-ttu-id="9d01b-113">Następujące zapytanie SQL jednostki używa + operatora arytmetycznego na dodanie dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="9d01b-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="9d01b-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9d01b-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9d01b-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9d01b-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9d01b-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytania, że zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9d01b-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9d01b-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="9d01b-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="9d01b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d01b-118">See Also</span></span>  
 [<span data-ttu-id="9d01b-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="9d01b-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="9d01b-120">Model koncepcyjny typów (CSDL)</span><span class="sxs-lookup"><span data-stu-id="9d01b-120">Conceptual Model Types (CSDL)</span></span>](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
