---
title: MULTISET (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: ad54450b8f987da9a7a502d6561a58794a24b207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655182"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="72578-102">MULTISET (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="72578-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="72578-103">Tworzy wystąpienie zestawu wielokrotnego na podstawie listy wartości.</span><span class="sxs-lookup"><span data-stu-id="72578-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="72578-104">Wszystkie wartości w Konstruktor MULTISET musi być zgodne z typem `T`.</span><span class="sxs-lookup"><span data-stu-id="72578-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="72578-105">Pusty zestaw wielokrotny konstruktory nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="72578-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72578-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="72578-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="72578-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="72578-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="72578-108">Wszystkie prawidłowe listy wartości.</span><span class="sxs-lookup"><span data-stu-id="72578-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72578-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="72578-109">Return Value</span></span>  
 <span data-ttu-id="72578-110">Kolekcja typu MULTISET\<T >.</span><span class="sxs-lookup"><span data-stu-id="72578-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72578-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72578-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="72578-112">zawiera trzy rodzaje konstruktorów: wiersz konstruktorów, obiektu konstruktorów i konstruktorów multiset (lub kolekcji).</span><span class="sxs-lookup"><span data-stu-id="72578-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="72578-113">Aby uzyskać więcej informacji, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="72578-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="72578-114">Konstruktor multiset tworzy wystąpienie zestawu wielokrotnego na podstawie listy wartości.</span><span class="sxs-lookup"><span data-stu-id="72578-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="72578-115">Wszystkie wartości w Konstruktorze musi być zgodne z typem.</span><span class="sxs-lookup"><span data-stu-id="72578-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="72578-116">Na przykład poniższe wyrażenie tworzy zestaw wielokrotny liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="72578-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="72578-117">Zagnieżdżone literały zestawów wielokrotnych są obsługiwana tylko w przypadku multiset zawijania ma jeden element multiset; na przykład `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="72578-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="72578-118">Gdy multiset zawijania ma wiele elementów zestawów wielokrotnych (na przykład `{{1, 2}, {3, 4}}`), zagnieżdżone literały multiset — nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="72578-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72578-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="72578-119">Example</span></span>  
 <span data-ttu-id="72578-120">Następujące zapytanie SQL jednostki używa operatora MULTISET do utworzenia wystąpienia zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="72578-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="72578-121">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="72578-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="72578-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="72578-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="72578-123">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="72578-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="72578-124">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="72578-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="72578-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72578-125">See also</span></span>
- [<span data-ttu-id="72578-126">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="72578-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="72578-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="72578-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
