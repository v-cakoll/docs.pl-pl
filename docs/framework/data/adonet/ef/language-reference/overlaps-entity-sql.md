---
title: Nakładania się (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 9b67e6824317b032f420501ffba385ec6fd651b9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762679"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="59393-102">Nakładania się (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="59393-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="59393-103">Określa, czy dwie kolekcje mają wspólne elementy.</span><span class="sxs-lookup"><span data-stu-id="59393-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59393-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59393-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="59393-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="59393-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="59393-106">Wszystkie prawidłowe zapytanie zwracające kolekcja do porównania z kolekcji zwrócony z innym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="59393-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="59393-107">Wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="59393-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59393-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59393-108">Return Value</span></span>  
 <span data-ttu-id="59393-109">`true` Jeśli dwie kolekcje mają wspólne elementy; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="59393-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59393-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59393-110">Remarks</span></span>  
 <span data-ttu-id="59393-111">Nakładania się funkcjonalnie udostępnia odpowiednik do następującego:</span><span class="sxs-lookup"><span data-stu-id="59393-111">OVERLAPS provides functionally equivalent tothe following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="59393-112">Nakładania się jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="59393-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="59393-113">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="59393-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="59393-114">Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="59393-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59393-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="59393-115">Example</span></span>  
 <span data-ttu-id="59393-116">Następujące zapytanie SQL jednostki używa operatora nakładania się do Określa, czy dwie kolekcje mają wspólną wartość.</span><span class="sxs-lookup"><span data-stu-id="59393-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="59393-117">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="59393-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="59393-118">Aby skompilować i uruchomić to, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="59393-118">To compile and run this, follow these steps:</span></span>  
  
1.  <span data-ttu-id="59393-119">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="59393-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="59393-120">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="59393-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="59393-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59393-121">See Also</span></span>  
 [<span data-ttu-id="59393-122">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="59393-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
