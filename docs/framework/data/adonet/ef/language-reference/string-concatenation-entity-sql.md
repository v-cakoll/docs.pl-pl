---
title: "+ (Łączenie ciągów) (Jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24591b54af97eaad705e4914764c7b2c21e5ed0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="f5f41-102">+ (Ciągów) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f5f41-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="f5f41-103">Łączy dwa ciągi.</span><span class="sxs-lookup"><span data-stu-id="f5f41-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5f41-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5f41-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f5f41-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f5f41-106">Dowolne prawidłowe wyrażenie EDM. Ciąg typów danych.</span><span class="sxs-lookup"><span data-stu-id="f5f41-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="f5f41-107">Oba wyrażenia musi być tego samego typu danych lub jedno wyrażenie musi mieć możliwość można niejawnie przekonwertować na typ danych innych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f5f41-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f5f41-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="f5f41-108">Result Types</span></span>  
 <span data-ttu-id="f5f41-109">Typ danych, który powoduje z typem niejawnym promocji dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="f5f41-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f5f41-110">Aby uzyskać więcej informacji na temat podwyższania poziomu typu niejawnego zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f5f41-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5f41-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5f41-111">Example</span></span>  
 <span data-ttu-id="f5f41-112">Następujące zapytanie SQL jednostki używa + operatora łączy dwa ciągi.</span><span class="sxs-lookup"><span data-stu-id="f5f41-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="f5f41-113">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f5f41-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f5f41-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f5f41-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f5f41-115">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f5f41-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="f5f41-116">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="f5f41-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="f5f41-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5f41-117">See Also</span></span>  
 [<span data-ttu-id="f5f41-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f5f41-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f5f41-119">Typy modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="f5f41-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
