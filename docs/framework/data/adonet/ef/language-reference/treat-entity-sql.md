---
title: TRAKTUJ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 1a65c73b8c6013c2b78343224c5bbb925101f9f3
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903776"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="248f5-102">TRAKTUJ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="248f5-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="248f5-103">Traktuje obiektu określonego typu podstawowego, jako obiekt określonego typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="248f5-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="248f5-104">Syntax</span></span>  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="248f5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="248f5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="248f5-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca jednostkę.</span><span class="sxs-lookup"><span data-stu-id="248f5-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="248f5-107">Typ określonego wyrażenie musi być podtypem elementów określonego typu danych lub typ danych musi być podtypem typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="248f5-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="248f5-108">Typ jednostki.</span><span class="sxs-lookup"><span data-stu-id="248f5-108">An entity type.</span></span> <span data-ttu-id="248f5-109">Typ musi być kwalifikowana przez obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="248f5-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="248f5-110">Określone wyrażenie musi być podtypem elementów określonego typu danych lub typ danych musi być podtypem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="248f5-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="248f5-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="248f5-111">Return Value</span></span>  
 <span data-ttu-id="248f5-112">Wartość na określony typ danych.</span><span class="sxs-lookup"><span data-stu-id="248f5-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="248f5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="248f5-113">Remarks</span></span>  
 <span data-ttu-id="248f5-114">TRAKTUJ jest używany do wykonywania Rzutowanie rozszerzające między powiązanymi klasami.</span><span class="sxs-lookup"><span data-stu-id="248f5-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="248f5-115">Na przykład jeśli `Employee` pochodzi od klasy `Person` i p jest typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a ogólny `Person` wystąpienia do `Employee`; oznacza to, że umożliwia traktowanie p jako `Employee`.</span><span class="sxs-lookup"><span data-stu-id="248f5-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="248f5-116">TRAKTUJ jest używany w scenariuszach dziedziczenia, w których można wykonują zapytania podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="248f5-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="248f5-117">To zapytanie upcasts `Person` jednostki `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="248f5-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="248f5-118">Jeśli wartość p nie jest faktycznie typu `Employee`, wyrażenie daje wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="248f5-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="248f5-119">Określone wyrażenie `Employee` musi być podtypem typu danych określonego `Person`, lub typ danych musi być podtypem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="248f5-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="248f5-120">W przeciwnym wypadku wyrażenie spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="248f5-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="248f5-121">W poniższej tabeli przedstawiono zachowania Traktuj przez niektóre typowe wzorce i pewne mniej typowe wzorce.</span><span class="sxs-lookup"><span data-stu-id="248f5-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="248f5-122">Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem pobiera dostawcy:</span><span class="sxs-lookup"><span data-stu-id="248f5-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="248f5-123">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="248f5-123">Pattern</span></span>|<span data-ttu-id="248f5-124">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="248f5-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="248f5-125">Zwraca `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="248f5-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="248f5-126">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="248f5-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="248f5-127">Zgłasza wyjątek /</span><span class="sxs-lookup"><span data-stu-id="248f5-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="248f5-128">Zwraca `EntityType` lub `null`.</span><span class="sxs-lookup"><span data-stu-id="248f5-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="248f5-129">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="248f5-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="248f5-130">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="248f5-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="248f5-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="248f5-131">Example</span></span>  
 <span data-ttu-id="248f5-132">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="248f5-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="248f5-133">Zapytanie jest oparty na [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="248f5-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="248f5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="248f5-134">See also</span></span>
- [<span data-ttu-id="248f5-135">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="248f5-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="248f5-136">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="248f5-136">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
