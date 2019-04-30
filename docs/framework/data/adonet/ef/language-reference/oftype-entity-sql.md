---
title: OFTYPE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: bbc3ffd4902fe8c1c41aebe88317d0e3c32f7771
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760366"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="acde4-102">OFTYPE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="acde4-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="acde4-103">Zwraca kolekcję obiektów z wyrażenie zapytania, które jest określonego typu.</span><span class="sxs-lookup"><span data-stu-id="acde4-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acde4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="acde4-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="acde4-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="acde4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="acde4-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="acde4-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="acde4-107">Typ do przetestowania każdego obiektu zwróconego przez `expression` względem.</span><span class="sxs-lookup"><span data-stu-id="acde4-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="acde4-108">Typ musi być kwalifikowana przez obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="acde4-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acde4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="acde4-109">Return Value</span></span>  
 <span data-ttu-id="acde4-110">Kolekcja obiektów typu `test_type`, lub typu podstawowego lub typ pochodny `test_type`.</span><span class="sxs-lookup"><span data-stu-id="acde4-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="acde4-111">Jeśli jest określony, tylko tylko wystąpienia z `test_type` lub pusta Kolekcja zostanie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="acde4-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acde4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acde4-112">Remarks</span></span>  
 <span data-ttu-id="acde4-113">`OFTYPE` Wyrażenie określa wyrażenie typu, który jest wystawiony dla wykonywania testu typu dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="acde4-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="acde4-114">`OFTYPE` Wyrażenie tworzy nową kolekcję określonego typu, zawierający tylko te elementy, które zostały odpowiednikiem tego typu lub podtyp go.</span><span class="sxs-lookup"><span data-stu-id="acde4-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="acde4-115">`OFTYPE` Wyrażenie jest skrótem następującego wyrażenia kwerendy:</span><span class="sxs-lookup"><span data-stu-id="acde4-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="acde4-116">Biorąc pod uwagę, że Menedżer jest podtypem pracowników, poniższe wyrażenie daje kolekcję tylko menedżerowie z kolekcji pracowników:</span><span class="sxs-lookup"><span data-stu-id="acde4-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="acde4-117">Istnieje również możliwość nawet rzutowania kolekcji za pomocą filtru typu:</span><span class="sxs-lookup"><span data-stu-id="acde4-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="acde4-118">Ponieważ wszyscy przedstawiciele kadry kierowniczej menedżerów, wynikowy kolekcji nadal zawiera wszystkie oryginalne przedstawiciele kadry kierowniczej, chociaż kolekcji jest teraz wpisane jako kolekcja menedżerów.</span><span class="sxs-lookup"><span data-stu-id="acde4-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="acde4-119">W poniższej tabeli przedstawiono zachowania `OFTYPE` operatora przez niektóre wzorce.</span><span class="sxs-lookup"><span data-stu-id="acde4-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="acde4-120">Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem dostawcy:</span><span class="sxs-lookup"><span data-stu-id="acde4-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="acde4-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="acde4-121">Pattern</span></span>|<span data-ttu-id="acde4-122">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="acde4-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="acde4-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="acde4-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="acde4-124">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="acde4-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="acde4-125">OFTYPE(Collection(complexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="acde4-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="acde4-126">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="acde4-126">Throws</span></span>|  
|<span data-ttu-id="acde4-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="acde4-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="acde4-128">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="acde4-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="acde4-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="acde4-129">Example</span></span>  
 <span data-ttu-id="acde4-130">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora OFTYPE zwracać kolekcję OnsiteCourse obiektów z kolekcji oczywiście obiekty.</span><span class="sxs-lookup"><span data-stu-id="acde4-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="acde4-131">Zapytanie jest oparty na [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="acde4-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="acde4-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acde4-132">See also</span></span>

- [<span data-ttu-id="acde4-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="acde4-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
