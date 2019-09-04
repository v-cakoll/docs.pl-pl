---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 10c5ecb2b44c85dccd758cc1cf63a152da045cc1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251080"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="60b5a-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="60b5a-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="60b5a-103">Odwołuje się do wartości odniesienia i tworzy wynik tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="60b5a-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60b5a-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="60b5a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="60b5a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="60b5a-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="60b5a-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60b5a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60b5a-107">Return Value</span></span>  
 <span data-ttu-id="60b5a-108">Wartość obiektu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="60b5a-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60b5a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60b5a-109">Remarks</span></span>  
 <span data-ttu-id="60b5a-110">Operator DEREF odwołuje się do wartości odniesienia i tworzy wynik tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="60b5a-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="60b5a-111">Na `r` przykład jeśli jest odwołaniem typu ref `Deref(r)` \<T >, jest wyrażeniem `r`typu `T` , które zwraca jednostkę, do której odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="60b5a-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="60b5a-112">Jeśli wartość odwołania ma wartość null lub jest zawieszonego (oznacza to, że obiekt docelowy odwołania nie istnieje), wynik operatora DEREF ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="60b5a-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b5a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="60b5a-113">Example</span></span>  
 <span data-ttu-id="60b5a-114">Poniższe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora DEREF, aby usunąć odwołanie do wartości odniesienia i utworzyć wynik tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="60b5a-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="60b5a-115">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="60b5a-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="60b5a-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="60b5a-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="60b5a-117">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="60b5a-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="60b5a-118">Przekaż następujące zapytanie jako argument do metody ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="60b5a-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="60b5a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60b5a-119">See also</span></span>

- [<span data-ttu-id="60b5a-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="60b5a-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="60b5a-121">REF</span><span class="sxs-lookup"><span data-stu-id="60b5a-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="60b5a-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="60b5a-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="60b5a-123">KEY</span><span class="sxs-lookup"><span data-stu-id="60b5a-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="60b5a-124">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="60b5a-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
