---
title: "Literały null i wnioskowanie o typie (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eeea6a6b1674361a605d5236e203699d08724df3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="a8f43-102">Literały null i wnioskowanie o typie (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="a8f43-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="a8f43-103">Literały null są zgodne z dowolnego typu w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] system typów.</span><span class="sxs-lookup"><span data-stu-id="a8f43-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="a8f43-104">Niemniej jednak w przypadku typ literału null do można wywnioskować poprawnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada pewne ograniczenia, na której można użyć literału null.</span><span class="sxs-lookup"><span data-stu-id="a8f43-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="a8f43-105">Wartości null bez typu</span><span class="sxs-lookup"><span data-stu-id="a8f43-105">Typed Nulls</span></span>  
 <span data-ttu-id="a8f43-106">Wartości null bez typu może być używana w dowolnym.</span><span class="sxs-lookup"><span data-stu-id="a8f43-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="a8f43-107">Wnioskowanie o typie nie jest wymagana dla wartości null bez typu, ponieważ jest on znany typ.</span><span class="sxs-lookup"><span data-stu-id="a8f43-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="a8f43-108">Na przykład można utworzyć wartości null typu Int16 z następującymi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] utworzyć:</span><span class="sxs-lookup"><span data-stu-id="a8f43-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="a8f43-109">Swobodnego literałów wartości Null</span><span class="sxs-lookup"><span data-stu-id="a8f43-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="a8f43-110">Swobodnego literałów wartości null, mogą być używane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="a8f43-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="a8f43-111">Jako argument wyrażenia RZUTOWANIA lub TRAKTUJ.</span><span class="sxs-lookup"><span data-stu-id="a8f43-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="a8f43-112">Jest to zalecany sposób utworzyć wyrażenie typu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a8f43-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="a8f43-113">Jako argument do metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="a8f43-113">As an argument to a method or a function.</span></span> <span data-ttu-id="a8f43-114">Mają zastosowanie standardowe przeciążenia reguły.</span><span class="sxs-lookup"><span data-stu-id="a8f43-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="a8f43-115">Jako jeden z argumentów wyrażenia arytmetyczne, takie jak +, -, lub /.</span><span class="sxs-lookup"><span data-stu-id="a8f43-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="a8f43-116">Inne argumenty nie może być literałów wartości null, w przeciwnym razie wnioskowanie typu nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="a8f43-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="a8f43-117">Jako argumenty do wyrażenie logiczne (AND, OR lub nie).</span><span class="sxs-lookup"><span data-stu-id="a8f43-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="a8f43-118">Wszystkie argumenty są określane jako typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="a8f43-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="a8f43-119">Jako argumentu wyrażenia IS NULL i IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="a8f43-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="a8f43-120">Jako co najmniej jeden z argumentów do wyrażenia LIKE.</span><span class="sxs-lookup"><span data-stu-id="a8f43-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="a8f43-121">Wszystkie argumenty powinny być ciągami.</span><span class="sxs-lookup"><span data-stu-id="a8f43-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="a8f43-122">Jako jeden lub więcej argumentów konstruktora o nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="a8f43-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="a8f43-123">Jako jeden lub więcej argumentów konstruktora multiset —.</span><span class="sxs-lookup"><span data-stu-id="a8f43-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="a8f43-124">Co najmniej jeden argument multiset — Konstruktor musi być wyrażenie, które nie jest literałem wartości null.</span><span class="sxs-lookup"><span data-stu-id="a8f43-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="a8f43-125">Co najmniej jednego wyrażenia w wyrażeniu CASE następnie możesz też.</span><span class="sxs-lookup"><span data-stu-id="a8f43-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="a8f43-126">Przynajmniej jedno z wyrażeń w wyrażeniu CASE następnie możesz też musi być wyrażeniem innym niż null literału.</span><span class="sxs-lookup"><span data-stu-id="a8f43-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="a8f43-127">Swobodnego literałów wartości null nie można używać w innych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="a8f43-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="a8f43-128">Na przykład nie może być używane jako argumenty konstruktora wiersza.</span><span class="sxs-lookup"><span data-stu-id="a8f43-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f43-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8f43-129">See Also</span></span>  
 [<span data-ttu-id="a8f43-130">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a8f43-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
