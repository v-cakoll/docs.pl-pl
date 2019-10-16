---
title: Zestaw WIELOKROTNy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 222be86db434b5d41c7b0536d271a3750b6afbe8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319580"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="37e62-102">Zestaw WIELOKROTNy (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="37e62-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="37e62-103">Tworzy wystąpienie zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="37e62-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="37e62-104">Wszystkie wartości w konstruktorze zestawów wielokrotnych muszą być zgodne z typem `T`.</span><span class="sxs-lookup"><span data-stu-id="37e62-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="37e62-105">Puste konstruktory wielu zestawów są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="37e62-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e62-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="37e62-106">Syntax</span></span>  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="37e62-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37e62-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="37e62-108">Dowolna prawidłowa lista wartości.</span><span class="sxs-lookup"><span data-stu-id="37e62-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37e62-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37e62-109">Return Value</span></span>  
 <span data-ttu-id="37e62-110">Kolekcja typu zestaw WIELOKROTNy @ no__t-0T >.</span><span class="sxs-lookup"><span data-stu-id="37e62-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37e62-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37e62-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="37e62-112">zawiera trzy rodzaje konstruktorów: konstruktory wierszy, konstruktory obiektów oraz konstruktory wielu zestawów (lub kolekcji).</span><span class="sxs-lookup"><span data-stu-id="37e62-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="37e62-113">Aby uzyskać więcej informacji, zobacz [konstruowanie typów](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="37e62-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="37e62-114">Konstruktor zestawów wielokrotnych tworzy wystąpienie zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="37e62-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="37e62-115">Wszystkie wartości w konstruktorze muszą być zgodnego typu.</span><span class="sxs-lookup"><span data-stu-id="37e62-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="37e62-116">Na przykład następujące wyrażenie tworzy zestaw wielokrotny dla liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="37e62-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="37e62-117">Zagnieżdżone literały zestawu wielokrotnego są obsługiwane tylko wtedy, gdy zestaw wielokrotny zawijania zawiera pojedynczy element wielokrotnego zestawu. na przykład `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="37e62-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="37e62-118">Gdy zestaw wielokrotny zawijania ma wiele elementów zestawów wielokrotnych (na przykład `{{1, 2}, {3, 4}}`), zagnieżdżone literały zestawów wielokrotnych nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="37e62-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37e62-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="37e62-119">Example</span></span>  
 <span data-ttu-id="37e62-120">Poniższe zapytanie Entity SQL używa operatora WIELOKROTNego tworzenia wystąpienia zestawu wielokrotnego na podstawie listy wartości.</span><span class="sxs-lookup"><span data-stu-id="37e62-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="37e62-121">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="37e62-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="37e62-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="37e62-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="37e62-123">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="37e62-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="37e62-124">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="37e62-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="37e62-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37e62-125">See also</span></span>

- [<span data-ttu-id="37e62-126">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="37e62-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="37e62-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="37e62-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
