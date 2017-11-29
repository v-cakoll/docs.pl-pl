---
title: OFTYPE (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd2660eb5fddd0c75b44d0796edce37c83865e81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="2a060-102">OFTYPE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="2a060-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="2a060-103">Zwraca kolekcję obiektów z wyrażenia zapytania, który jest określonego typu.</span><span class="sxs-lookup"><span data-stu-id="2a060-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a060-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a060-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2a060-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2a060-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2a060-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="2a060-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="2a060-107">Do przetestowania każdego obiektu zwróconego przez typ `expression` przed.</span><span class="sxs-lookup"><span data-stu-id="2a060-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="2a060-108">Typ musi być kwalifikowana przez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2a060-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a060-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2a060-109">Return Value</span></span>  
 <span data-ttu-id="2a060-110">Kolekcja obiektów typu `test_type`, lub typu podstawowego lub typu pochodnego `test_type`.</span><span class="sxs-lookup"><span data-stu-id="2a060-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="2a060-111">Jeśli jest określony tylko tylko wystąpienia o `test_type` lub pustej kolekcji zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="2a060-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a060-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a060-112">Remarks</span></span>  
 <span data-ttu-id="2a060-113">`OFTYPE` Wyrażenie określa wyrażenie typu, które wydaje się przeprowadzić test typu względem każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2a060-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="2a060-114">`OFTYPE` Wyrażenie zwraca nową kolekcję określonego typu zawierającego tylko elementy, które zostały odpowiednikiem tego typu lub podtyp go.</span><span class="sxs-lookup"><span data-stu-id="2a060-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="2a060-115">`OFTYPE` Wyrażenie stanowi skrót od następujących wyrażenia zapytania:</span><span class="sxs-lookup"><span data-stu-id="2a060-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="2a060-116">Biorąc pod uwagę, że Menedżer jest podtypem pracownika, poniższe wyrażenie tworzy kolekcję tylko menedżerów z kolekcji pracowników:</span><span class="sxs-lookup"><span data-stu-id="2a060-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="2a060-117">Istnieje również możliwość maksymalnie rzutowania kolekcji przy użyciu filtru typu:</span><span class="sxs-lookup"><span data-stu-id="2a060-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="2a060-118">Ponieważ wszystkich przedstawicieli kadry kierowniczej menedżerów, wynikowy kolekcji nadal zawiera wszystkie kierownicy oryginalnej, chociaż kolekcji jest teraz typu kolekcji menedżerów.</span><span class="sxs-lookup"><span data-stu-id="2a060-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="2a060-119">W poniższej tabeli przedstawiono zachowania `OFTYPE` operator przez niektóre wzorce.</span><span class="sxs-lookup"><span data-stu-id="2a060-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="2a060-120">Wszystkie wyjątki zostaną zgłoszone po stronie klienta, zanim dostawca jest wywoływany:</span><span class="sxs-lookup"><span data-stu-id="2a060-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="2a060-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="2a060-121">Pattern</span></span>|<span data-ttu-id="2a060-122">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="2a060-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="2a060-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="2a060-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="2a060-124">Elementem Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="2a060-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="2a060-125">OFTYPE(Collection(complexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="2a060-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="2a060-126">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="2a060-126">Throws</span></span>|  
|<span data-ttu-id="2a060-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="2a060-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="2a060-128">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="2a060-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a060-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a060-129">Example</span></span>  
 <span data-ttu-id="2a060-130">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora OFTYPE zwracać kolekcję OnsiteCourse obiektów z kolekcji oczywiście obiekty.</span><span class="sxs-lookup"><span data-stu-id="2a060-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="2a060-131">Zapytanie jest oparta na [modelu służbowe](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="2a060-131">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="2a060-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a060-132">See Also</span></span>  
 [<span data-ttu-id="2a060-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="2a060-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
