---
title: Zestaw WIELOKROTNy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: eb676feeb168e1fb184f3869a18e138bff34211b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929347"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="a0456-102">Zestaw WIELOKROTNy (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a0456-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="a0456-103">Tworzy wystąpienie zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="a0456-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="a0456-104">Wszystkie wartości w konstruktorze zestawów wielokrotnych muszą być zgodne z typem `T`.</span><span class="sxs-lookup"><span data-stu-id="a0456-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="a0456-105">Puste konstruktory wielu zestawów są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="a0456-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0456-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0456-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0456-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a0456-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a0456-108">Dowolna prawidłowa lista wartości.</span><span class="sxs-lookup"><span data-stu-id="a0456-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0456-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0456-109">Return Value</span></span>  
 <span data-ttu-id="a0456-110">Kolekcja typu zestaw wielokrotny\<T >.</span><span class="sxs-lookup"><span data-stu-id="a0456-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0456-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0456-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a0456-112">oferuje trzy rodzaje konstruktorów: konstruktory wierszy, konstruktory obiektów i konstruktory wielokrotnego (lub kolekcji).</span><span class="sxs-lookup"><span data-stu-id="a0456-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="a0456-113">Aby uzyskać więcej informacji, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a0456-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="a0456-114">Konstruktor zestawów wielokrotnych tworzy wystąpienie zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="a0456-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="a0456-115">Wszystkie wartości w konstruktorze muszą być zgodnego typu.</span><span class="sxs-lookup"><span data-stu-id="a0456-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="a0456-116">Na przykład następujące wyrażenie tworzy zestaw wielokrotny dla liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="a0456-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="a0456-117">Zagnieżdżone literały zestawu wielokrotnego są obsługiwane tylko wtedy, gdy zestaw wielokrotny zawijania zawiera pojedynczy element wielokrotnego zestawu. na przykład `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="a0456-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="a0456-118">Gdy zestaw wielokrotny zawijania ma wiele elementów wielokrotnych ( `{{1, 2}, {3, 4}}`na przykład), zagnieżdżone literały zestawów wielokrotnych nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a0456-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0456-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0456-119">Example</span></span>  
 <span data-ttu-id="a0456-120">Poniższe zapytanie Entity SQL używa operatora WIELOKROTNego tworzenia wystąpienia zestawu wielokrotnego na podstawie listy wartości.</span><span class="sxs-lookup"><span data-stu-id="a0456-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="a0456-121">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a0456-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a0456-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a0456-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a0456-123">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="a0456-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a0456-124">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a0456-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="a0456-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0456-125">See also</span></span>

- [<span data-ttu-id="a0456-126">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="a0456-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="a0456-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a0456-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
