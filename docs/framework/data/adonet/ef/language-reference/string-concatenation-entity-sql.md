---
title: + (Łączenie ciągów) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: e53bd0a2607deb67d45edc44e51cf4ad283b21c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633935"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="49b32-102">+ (Łączenie ciągów) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="49b32-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="49b32-103">Łączy dwa ciągi.</span><span class="sxs-lookup"><span data-stu-id="49b32-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b32-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49b32-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="49b32-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="49b32-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="49b32-106">Dowolne prawidłowe wyrażenie EDM. Ciąg typów danych.</span><span class="sxs-lookup"><span data-stu-id="49b32-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="49b32-107">Oba wyrażenia muszą być tego samego typu danych lub jedno wyrażenie musi umożliwiać można niejawnie przekonwertować na typ danych, inne wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49b32-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="49b32-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="49b32-108">Result Types</span></span>  
 <span data-ttu-id="49b32-109">Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="49b32-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="49b32-110">Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="49b32-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b32-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="49b32-111">Example</span></span>  
 <span data-ttu-id="49b32-112">Następujące zapytanie SQL jednostki używa + operatora łączy dwa ciągi.</span><span class="sxs-lookup"><span data-stu-id="49b32-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="49b32-113">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="49b32-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="49b32-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="49b32-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="49b32-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="49b32-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="49b32-116">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="49b32-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="49b32-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49b32-117">See also</span></span>
- [<span data-ttu-id="49b32-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="49b32-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="49b32-119">Model koncepcyjny typów (CSDL)</span><span class="sxs-lookup"><span data-stu-id="49b32-119">Conceptual Model Types (CSDL)</span></span>](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
