---
title: ANYELEMENT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 11d1dd4b09ff07519f3435d313de72c5b9a3edf4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761847"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="dea4b-102">ANYELEMENT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="dea4b-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="dea4b-103">Wyodrębnia element z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="dea4b-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dea4b-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="dea4b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dea4b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="dea4b-106">Wszystkie prawidłowe zapytanie zwracające można wyodrębnić elementu z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dea4b-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dea4b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dea4b-107">Return Value</span></span>  
 <span data-ttu-id="dea4b-108">Pojedynczy element w kolekcji lub dowolnego elementu, jeśli kolekcja zawiera więcej niż jeden; Jeśli kolekcja jest pusty, zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="dea4b-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="dea4b-109">Jeśli `collection` jest kolekcją typu `Collection<T>`, następnie `ANYELEMENT(collection)` jest prawidłowe wyrażenie zwracające wystąpienia typu `T`.</span><span class="sxs-lookup"><span data-stu-id="dea4b-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dea4b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dea4b-110">Remarks</span></span>  
 <span data-ttu-id="dea4b-111">ANYELEMENT wyodrębnia dowolnego elementu z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="dea4b-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="dea4b-112">Na przykład poniższy przykład próbuje wyodrębnić elementu pojedyncza ze zbioru `Customers`.</span><span class="sxs-lookup"><span data-stu-id="dea4b-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="dea4b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dea4b-113">Example</span></span>  
 <span data-ttu-id="dea4b-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ANYELEMENT można wyodrębnić elementu z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="dea4b-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="dea4b-115">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dea4b-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dea4b-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="dea4b-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="dea4b-117">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="dea4b-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="dea4b-118">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="dea4b-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="dea4b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dea4b-119">See Also</span></span>  
 [<span data-ttu-id="dea4b-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="dea4b-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="dea4b-121">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="dea4b-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
