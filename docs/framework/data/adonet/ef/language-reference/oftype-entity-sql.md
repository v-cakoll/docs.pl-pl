---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 36701a5e75e804ea541d242aaff243de0b24cec3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249795"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="01fa5-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="01fa5-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="01fa5-103">Zwraca kolekcję obiektów z wyrażenia zapytania, które jest określonego typu.</span><span class="sxs-lookup"><span data-stu-id="01fa5-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fa5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01fa5-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="01fa5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="01fa5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="01fa5-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="01fa5-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="01fa5-107">Typ do testowania każdego obiektu zwróconego przez `expression` .</span><span class="sxs-lookup"><span data-stu-id="01fa5-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="01fa5-108">Typ musi być kwalifikowany za pomocą przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="01fa5-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01fa5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="01fa5-109">Return Value</span></span>  
 <span data-ttu-id="01fa5-110">Kolekcja obiektów typu `test_type`, lub typ podstawowy lub `test_type`typ pochodny.</span><span class="sxs-lookup"><span data-stu-id="01fa5-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="01fa5-111">Jeśli jest określony tylko, zostaną zwrócone tylko wystąpienia `test_type` lub pustą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="01fa5-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01fa5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01fa5-112">Remarks</span></span>  
 <span data-ttu-id="01fa5-113">`OFTYPE` Wyrażenie określa wyrażenie typu, które zostało wystawione w celu przeprowadzenia testu typu dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="01fa5-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="01fa5-114">`OFTYPE` Wyrażenie tworzy nową kolekcję określonego typu zawierającego tylko te elementy, które były równoważne temu typowi lub podtyp.</span><span class="sxs-lookup"><span data-stu-id="01fa5-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="01fa5-115">`OFTYPE` Wyrażenie jest skrótem następującego wyrażenia zapytania:</span><span class="sxs-lookup"><span data-stu-id="01fa5-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="01fa5-116">Mając na względzie, że Menedżer jest podtypem pracownika, następujące wyrażenie tworzy kolekcję tylko menedżerów z kolekcji Employees:</span><span class="sxs-lookup"><span data-stu-id="01fa5-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="01fa5-117">Istnieje również możliwość rzutowania kolekcji przy użyciu filtru typu:</span><span class="sxs-lookup"><span data-stu-id="01fa5-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="01fa5-118">Ze względu na to, że wszyscy kierownicy są menedżerami, powstająca kolekcja nadal zawiera wszystkie pierwotnych kierownictwa, chociaż kolekcja została teraz wpisana jako kolekcja menedżerów.</span><span class="sxs-lookup"><span data-stu-id="01fa5-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="01fa5-119">W poniższej tabeli przedstawiono zachowanie `OFTYPE` operatora względem niektórych wzorców.</span><span class="sxs-lookup"><span data-stu-id="01fa5-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="01fa5-120">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:</span><span class="sxs-lookup"><span data-stu-id="01fa5-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="01fa5-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="01fa5-121">Pattern</span></span>|<span data-ttu-id="01fa5-122">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="01fa5-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="01fa5-123">OFTYPE (kolekcja (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="01fa5-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="01fa5-124">Kolekcja (EntityType)</span><span class="sxs-lookup"><span data-stu-id="01fa5-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="01fa5-125">OFTYPE (kolekcja (ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="01fa5-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="01fa5-126">Generuje</span><span class="sxs-lookup"><span data-stu-id="01fa5-126">Throws</span></span>|  
|<span data-ttu-id="01fa5-127">OFTYPE (Collection (RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="01fa5-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="01fa5-128">Generuje</span><span class="sxs-lookup"><span data-stu-id="01fa5-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="01fa5-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="01fa5-129">Example</span></span>  
 <span data-ttu-id="01fa5-130">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora OFTYPE do zwrócenia kolekcji obiektów OnsiteCourse z kolekcji obiektów kursów.</span><span class="sxs-lookup"><span data-stu-id="01fa5-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="01fa5-131">Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="01fa5-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="01fa5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01fa5-132">See also</span></span>

- [<span data-ttu-id="01fa5-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="01fa5-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
