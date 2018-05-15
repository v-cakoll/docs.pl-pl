---
title: Literały null i wnioskowanie o typie (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 74ff2b459488f896c5ea6af4f7d1e045da5a7983
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="497e1-102">Literały null i wnioskowanie o typie (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="497e1-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="497e1-103">Literały null są zgodne z dowolnego typu w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] system typów.</span><span class="sxs-lookup"><span data-stu-id="497e1-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="497e1-104">Niemniej jednak w przypadku typ literału null do można wywnioskować poprawnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada pewne ograniczenia, na której można użyć literału null.</span><span class="sxs-lookup"><span data-stu-id="497e1-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="497e1-105">Wartości null bez typu</span><span class="sxs-lookup"><span data-stu-id="497e1-105">Typed Nulls</span></span>  
 <span data-ttu-id="497e1-106">Wartości null bez typu może być używana w dowolnym.</span><span class="sxs-lookup"><span data-stu-id="497e1-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="497e1-107">Wnioskowanie o typie nie jest wymagana dla wartości null bez typu, ponieważ jest on znany typ.</span><span class="sxs-lookup"><span data-stu-id="497e1-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="497e1-108">Na przykład można utworzyć wartości null typu Int16 z następującymi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] utworzyć:</span><span class="sxs-lookup"><span data-stu-id="497e1-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="497e1-109">Swobodnego literałów wartości Null</span><span class="sxs-lookup"><span data-stu-id="497e1-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="497e1-110">Swobodnego literałów wartości null, mogą być używane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="497e1-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="497e1-111">Jako argument wyrażenia RZUTOWANIA lub TRAKTUJ.</span><span class="sxs-lookup"><span data-stu-id="497e1-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="497e1-112">Jest to zalecany sposób utworzyć wyrażenie typu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="497e1-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="497e1-113">Jako argument do metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="497e1-113">As an argument to a method or a function.</span></span> <span data-ttu-id="497e1-114">Mają zastosowanie standardowe przeciążenia reguły.</span><span class="sxs-lookup"><span data-stu-id="497e1-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="497e1-115">Jako jeden z argumentów wyrażenia arytmetyczne, takie jak +, -, lub /.</span><span class="sxs-lookup"><span data-stu-id="497e1-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="497e1-116">Inne argumenty nie może być literałów wartości null, w przeciwnym razie wnioskowanie typu nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="497e1-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="497e1-117">Jako argumenty do wyrażenie logiczne (AND, OR lub nie).</span><span class="sxs-lookup"><span data-stu-id="497e1-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="497e1-118">Wszystkie argumenty są określane jako typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="497e1-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="497e1-119">Jako argumentu wyrażenia IS NULL i IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="497e1-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="497e1-120">Jako co najmniej jeden z argumentów do wyrażenia LIKE.</span><span class="sxs-lookup"><span data-stu-id="497e1-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="497e1-121">Wszystkie argumenty powinny być ciągami.</span><span class="sxs-lookup"><span data-stu-id="497e1-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="497e1-122">Jako jeden lub więcej argumentów konstruktora o nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="497e1-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="497e1-123">Jako jeden lub więcej argumentów konstruktora multiset —.</span><span class="sxs-lookup"><span data-stu-id="497e1-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="497e1-124">Co najmniej jeden argument multiset — Konstruktor musi być wyrażenie, które nie jest literałem wartości null.</span><span class="sxs-lookup"><span data-stu-id="497e1-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="497e1-125">Co najmniej jednego wyrażenia w wyrażeniu CASE następnie możesz też.</span><span class="sxs-lookup"><span data-stu-id="497e1-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="497e1-126">Przynajmniej jedno z wyrażeń w wyrażeniu CASE następnie możesz też musi być wyrażeniem innym niż null literału.</span><span class="sxs-lookup"><span data-stu-id="497e1-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="497e1-127">Swobodnego literałów wartości null nie można używać w innych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="497e1-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="497e1-128">Na przykład nie może być używane jako argumenty konstruktora wiersza.</span><span class="sxs-lookup"><span data-stu-id="497e1-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497e1-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="497e1-129">See Also</span></span>  
 [<span data-ttu-id="497e1-130">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="497e1-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
