---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149898"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="22d2d-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="22d2d-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="22d2d-103">Traktuje obiekt określonego typu podstawowego jako obiekt określonego typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="22d2d-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22d2d-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="22d2d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="22d2d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="22d2d-106">Dowolne prawidłowe wyrażenie kwerendy zwracane encję.</span><span class="sxs-lookup"><span data-stu-id="22d2d-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22d2d-107">Typ określonego wyrażenia musi być podtypem określonego typu danych lub typ danych musi być podtypem typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22d2d-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="22d2d-108">Typ jednostki.</span><span class="sxs-lookup"><span data-stu-id="22d2d-108">An entity type.</span></span> <span data-ttu-id="22d2d-109">Typ musi być kwalifikowany przez obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="22d2d-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22d2d-110">Określone wyrażenie musi być podtypem określonego typu danych lub typ danych musi być podtypem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22d2d-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22d2d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="22d2d-111">Return Value</span></span>  
 <span data-ttu-id="22d2d-112">Wartość określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="22d2d-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22d2d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22d2d-113">Remarks</span></span>  
 <span data-ttu-id="22d2d-114">TREAT jest używany do wykonywania upcasting między powiązanych klas.</span><span class="sxs-lookup"><span data-stu-id="22d2d-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="22d2d-115">Na przykład, `Employee` jeśli `Person` pochodzi z i `Person` `TREAT(p AS NamespaceName.Employee)` p jest typu `Person` , `Employee`upcasts ogólne wystąpienie do ; oznacza to, że pozwala na `Employee`traktowanie p jako .</span><span class="sxs-lookup"><span data-stu-id="22d2d-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="22d2d-116">TREAT jest używany w scenariuszach dziedziczenia, w których można wykonać kwerendę, podobną do następującej:</span><span class="sxs-lookup"><span data-stu-id="22d2d-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="22d2d-117">Ta kwerenda `Person` upcasts `Employee` jednostek do typu.</span><span class="sxs-lookup"><span data-stu-id="22d2d-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="22d2d-118">Jeśli wartość p nie jest `Employee`faktycznie typu, wyrażenie `null`daje wartość .</span><span class="sxs-lookup"><span data-stu-id="22d2d-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22d2d-119">Określone wyrażenie `Employee` musi być podtypem określonego `Person`typu danych lub typ danych musi być podtypem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22d2d-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="22d2d-120">W przeciwnym razie wyrażenie spowoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="22d2d-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="22d2d-121">W poniższej tabeli przedstawiono zachowanie leczenia przez niektóre typowe wzorce i niektóre mniej typowe wzorce.</span><span class="sxs-lookup"><span data-stu-id="22d2d-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="22d2d-122">Wszystkie wyjątki są generowane od strony klienta, zanim dostawca zostanie wywołany:</span><span class="sxs-lookup"><span data-stu-id="22d2d-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="22d2d-123">Wzorce</span><span class="sxs-lookup"><span data-stu-id="22d2d-123">Pattern</span></span>|<span data-ttu-id="22d2d-124">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="22d2d-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="22d2d-125">Zwraca wartość `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="22d2d-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="22d2d-126">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="22d2d-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="22d2d-127">Zgłasza wyjątek/</span><span class="sxs-lookup"><span data-stu-id="22d2d-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="22d2d-128">Zwraca `EntityType` `null`lub .</span><span class="sxs-lookup"><span data-stu-id="22d2d-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="22d2d-129">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="22d2d-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="22d2d-130">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="22d2d-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="22d2d-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="22d2d-131">Example</span></span>  
 <span data-ttu-id="22d2d-132">Poniższa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kwerenda używa TREAT operator do konwersji obiektu typu Course do kolekcji obiektów typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="22d2d-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="22d2d-133">Kwerenda jest oparta na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="22d2d-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="22d2d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22d2d-134">See also</span></span>

- [<span data-ttu-id="22d2d-135">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="22d2d-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="22d2d-136">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="22d2d-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
