---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 4eea3d43ef6ae9ea91432ea277326526e5e91fbc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251329"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="3c38e-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3c38e-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="3c38e-103">Wyodrębnia element z kolekcji wielowartościowej.</span><span class="sxs-lookup"><span data-stu-id="3c38e-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c38e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c38e-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c38e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3c38e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3c38e-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję w celu wyodrębnienia elementu z.</span><span class="sxs-lookup"><span data-stu-id="3c38e-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c38e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c38e-107">Return Value</span></span>  
 <span data-ttu-id="3c38e-108">Pojedynczy element w kolekcji lub dowolny element, jeśli kolekcja zawiera więcej niż jeden; Jeśli kolekcja jest pusta, zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="3c38e-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="3c38e-109">Jeśli `collection` jest kolekcją typu `Collection<T>`, `ANYELEMENT(collection)` jest prawidłowym wyrażeniem, które zwraca wystąpienie typu `T`.</span><span class="sxs-lookup"><span data-stu-id="3c38e-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c38e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c38e-110">Remarks</span></span>  
 <span data-ttu-id="3c38e-111">ANYELEMENT wyodrębnia dowolny element z kolekcji wielowartościowej.</span><span class="sxs-lookup"><span data-stu-id="3c38e-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="3c38e-112">Na przykład poniższy przykład próbuje wyodrębnić element singleton z zestawu `Customers`.</span><span class="sxs-lookup"><span data-stu-id="3c38e-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="3c38e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c38e-113">Example</span></span>  
 <span data-ttu-id="3c38e-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora AnyElement do wyodrębnienia elementu z kolekcji wielowartościowej.</span><span class="sxs-lookup"><span data-stu-id="3c38e-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="3c38e-115">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3c38e-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3c38e-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3c38e-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3c38e-117">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="3c38e-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3c38e-118">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="3c38e-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="3c38e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c38e-119">See also</span></span>

- [<span data-ttu-id="3c38e-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3c38e-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3c38e-121">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="3c38e-121">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
