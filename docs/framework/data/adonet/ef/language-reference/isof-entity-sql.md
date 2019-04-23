---
title: ISOF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 097d6e7d452ee62a2c8934d2c5fcfdddbeaffc73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195751"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="e6af1-102">ISOF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="e6af1-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="e6af1-103">Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypy.</span><span class="sxs-lookup"><span data-stu-id="e6af1-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6af1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6af1-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6af1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e6af1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e6af1-106">Dowolne wyrażenie prawidłowe zapytanie w celu określenia rodzaju.</span><span class="sxs-lookup"><span data-stu-id="e6af1-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="e6af1-107">NIE</span><span class="sxs-lookup"><span data-stu-id="e6af1-107">NOT</span></span>  
 <span data-ttu-id="e6af1-108">Neguje EDM. Wartość logiczną wyniku jest programu.</span><span class="sxs-lookup"><span data-stu-id="e6af1-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="e6af1-109">TYLKO</span><span class="sxs-lookup"><span data-stu-id="e6af1-109">ONLY</span></span>  
 <span data-ttu-id="e6af1-110">Określa, że jest z zwraca `true` tylko wtedy, gdy `expression` typu `type` i nie wszystkie z jedną jego podtypy.</span><span class="sxs-lookup"><span data-stu-id="e6af1-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="e6af1-111">Typ do przetestowania `expression` względem.</span><span class="sxs-lookup"><span data-stu-id="e6af1-111">The type to test `expression` against.</span></span> <span data-ttu-id="e6af1-112">Typ musi być kwalifikowana przez obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="e6af1-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6af1-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e6af1-113">Return Value</span></span>  
 <span data-ttu-id="e6af1-114">`true` Jeśli `expression` jest typu T i T jest typu podstawowego lub typem pochodnym `type`; wartość null, jeśli `expression` jest wartość null w czasie wykonywania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e6af1-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6af1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6af1-115">Remarks</span></span>  
 <span data-ttu-id="e6af1-116">Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` są składniowo równoważne `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e6af1-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="e6af1-117">W poniższej tabeli przedstawiono zachowania `IS OF` operatora przez niektóre typowe i rogu wzorce.</span><span class="sxs-lookup"><span data-stu-id="e6af1-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="e6af1-118">Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem pobiera dostawcy:</span><span class="sxs-lookup"><span data-stu-id="e6af1-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e6af1-119">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="e6af1-119">Pattern</span></span>|<span data-ttu-id="e6af1-120">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="e6af1-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="e6af1-121">wartość null jest z (typu jednostki)</span><span class="sxs-lookup"><span data-stu-id="e6af1-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="e6af1-122">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-122">Throws</span></span>|  
|<span data-ttu-id="e6af1-123">wartość null jest z (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="e6af1-124">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-124">Throws</span></span>|  
|<span data-ttu-id="e6af1-125">wartość null jest z (RowType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-125">null IS OF (RowType)</span></span>|<span data-ttu-id="e6af1-126">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-126">Throws</span></span>|  
|<span data-ttu-id="e6af1-127">TRAKTUJ (wartość null dla obiektu AS) jest typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="e6af1-128">Zwraca wartość DBNull</span><span class="sxs-lookup"><span data-stu-id="e6af1-128">Returns DBNull</span></span>|  
|<span data-ttu-id="e6af1-129">TRAKTUJ (o wartości null ComplexType AS) jest z (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="e6af1-130">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-130">Throws</span></span>|  
|<span data-ttu-id="e6af1-131">TRAKTUJ (o wartości null RowType AS) jest z (RowType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="e6af1-132">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-132">Throws</span></span>|  
|<span data-ttu-id="e6af1-133">Obiekt EntityType jest z typu (jednostki)</span><span class="sxs-lookup"><span data-stu-id="e6af1-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="e6af1-134">Zwraca wartość PRAWDA/FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="e6af1-134">Returns true/false</span></span>|  
|<span data-ttu-id="e6af1-135">JEST ComplexType z (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="e6af1-136">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-136">Throws</span></span>|  
|<span data-ttu-id="e6af1-137">JEST RowType z (RowType)</span><span class="sxs-lookup"><span data-stu-id="e6af1-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="e6af1-138">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6af1-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6af1-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6af1-139">Example</span></span>  
 <span data-ttu-id="e6af1-140">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora jest OF można określić typu wyrażenia zapytania, a następnie używa operatora TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="e6af1-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="e6af1-141">Zapytanie jest oparty na [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e6af1-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="e6af1-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6af1-142">See also</span></span>

- [<span data-ttu-id="e6af1-143">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e6af1-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
