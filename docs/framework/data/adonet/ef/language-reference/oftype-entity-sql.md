---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: f1dd5ba92c7b1eaf7117c9732a78e04e5d5a317a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319453"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="80c17-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="80c17-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="80c17-103">Zwraca kolekcję obiektów z wyrażenia zapytania, które jest określonego typu.</span><span class="sxs-lookup"><span data-stu-id="80c17-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80c17-104">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="80c17-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="80c17-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="80c17-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="80c17-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="80c17-107">Typ do testowania każdego obiektu zwróconego przez `expression` względem.</span><span class="sxs-lookup"><span data-stu-id="80c17-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="80c17-108">Typ musi być kwalifikowany za pomocą przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80c17-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80c17-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80c17-109">Return Value</span></span>  
 <span data-ttu-id="80c17-110">Kolekcja obiektów typu `test_type` lub typ podstawowy lub typ pochodny `test_type`.</span><span class="sxs-lookup"><span data-stu-id="80c17-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="80c17-111">Jeśli jest określony tylko, zostaną zwrócone tylko wystąpienia `test_type` lub pustej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="80c17-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80c17-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80c17-112">Remarks</span></span>  
 <span data-ttu-id="80c17-113">Wyrażenie `OFTYPE` określa wyrażenie typu, które jest wydawane, aby wykonać test typu dla każdego elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="80c17-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="80c17-114">Wyrażenie `OFTYPE` generuje nową kolekcję określonego typu zawierającego tylko te elementy, które były równoważne temu typowi lub podtyp.</span><span class="sxs-lookup"><span data-stu-id="80c17-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="80c17-115">Wyrażenie `OFTYPE` jest skrótem następującego wyrażenia zapytania:</span><span class="sxs-lookup"><span data-stu-id="80c17-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="80c17-116">Mając na względzie, że Menedżer jest podtypem pracownika, następujące wyrażenie tworzy kolekcję tylko menedżerów z kolekcji Employees:</span><span class="sxs-lookup"><span data-stu-id="80c17-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="80c17-117">Istnieje również możliwość rzutowania kolekcji przy użyciu filtru typu:</span><span class="sxs-lookup"><span data-stu-id="80c17-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="80c17-118">Ze względu na to, że wszyscy kierownicy są menedżerami, powstająca kolekcja nadal zawiera wszystkie pierwotnych kierownictwa, chociaż kolekcja została teraz wpisana jako kolekcja menedżerów.</span><span class="sxs-lookup"><span data-stu-id="80c17-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="80c17-119">W poniższej tabeli przedstawiono zachowanie operatora `OFTYPE` na niektórych wzorcach.</span><span class="sxs-lookup"><span data-stu-id="80c17-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="80c17-120">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:</span><span class="sxs-lookup"><span data-stu-id="80c17-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="80c17-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="80c17-121">Pattern</span></span>|<span data-ttu-id="80c17-122">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="80c17-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="80c17-123">OFTYPE (kolekcja (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="80c17-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="80c17-124">Kolekcja (EntityType)</span><span class="sxs-lookup"><span data-stu-id="80c17-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="80c17-125">OFTYPE (kolekcja (ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="80c17-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="80c17-126">Generuje</span><span class="sxs-lookup"><span data-stu-id="80c17-126">Throws</span></span>|  
|<span data-ttu-id="80c17-127">OFTYPE (Collection (RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="80c17-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="80c17-128">Generuje</span><span class="sxs-lookup"><span data-stu-id="80c17-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="80c17-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c17-129">Example</span></span>  
 <span data-ttu-id="80c17-130">Następujące zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa operatora OFTYPE do zwracania kolekcji obiektów OnsiteCourse z kolekcji obiektów kursów.</span><span class="sxs-lookup"><span data-stu-id="80c17-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="80c17-131">Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="80c17-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="80c17-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80c17-132">See also</span></span>

- [<span data-ttu-id="80c17-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="80c17-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
