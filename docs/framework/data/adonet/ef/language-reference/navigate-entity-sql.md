---
title: Przejdź (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 993c07b824d30c89773c5cfea90c7c194c6b3869
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760418"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="3e8ea-102">Przejdź (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="3e8ea-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="3e8ea-103">Przechodzi przez relację między jednostkami.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e8ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e8ea-104">Syntax</span></span>

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="3e8ea-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3e8ea-105">Arguments</span></span>

<span data-ttu-id="3e8ea-106">`instance-expression` Wystąpienie jednostki.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="3e8ea-107">`relationship-type` Nazwa typu relacji z pliku (CSDL) języka definicji schematu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="3e8ea-108">`relationship-type` Jest kwalifikowana jako \<przestrzeni nazw >.\< Nazwa typu relacji >.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="3e8ea-109">`to` Zakończenie relacji.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="3e8ea-110">`from` Początek relacji.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e8ea-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3e8ea-111">Return Value</span></span>

<span data-ttu-id="3e8ea-112">Jeśli kardynalność do końca wynosi 1, zwracaną wartością będzie `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="3e8ea-113">Jeśli kardynalność do końca n, zwracaną wartością będzie `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e8ea-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e8ea-114">Remarks</span></span>

<span data-ttu-id="3e8ea-115">Relacje są konstrukcje najwyższej jakości w [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM struktury).</span><span class="sxs-lookup"><span data-stu-id="3e8ea-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="3e8ea-116">Można ustanowić relacji między co najmniej dwóch typów jednostek, a użytkownicy mogą uzyskać dostęp za pośrednictwem relacji z jednej strony (jednostka) do innego.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="3e8ea-117">`from` i `to` są warunkowo opcjonalne, jeśli nie ma żadnych niejednoznaczności w rozpoznawanie w relacji.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="3e8ea-118">Nawigacja jest prawidłowa w przestrzeni O i C.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="3e8ea-119">Ogólna postać konstrukcję nawigacji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3e8ea-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="3e8ea-120">Przejdź (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])</span><span class="sxs-lookup"><span data-stu-id="3e8ea-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="3e8ea-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3e8ea-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="3e8ea-122">Gdzie jest OrderCustomer `relationship`, i klienta i zamówienia są `to-end` (klienta) i `from-end` (zamówienie) relacji.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="3e8ea-123">Jeśli OrderCustomer została relacji n: 1, a typ wyniku wyrażenie navigate jest Ref\<klienta >.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="3e8ea-124">Prostsze formularza to wyrażenie jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3e8ea-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="3e8ea-125">Podobnie w zapytaniu o następującej postaci wyrażenie navigate dałby w efekcie kolekcji < Ref\<kolejności >>.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="3e8ea-126">Wyrażenia wystąpienia musi być typem jednostki/ref.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="3e8ea-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e8ea-127">Example</span></span>

<span data-ttu-id="3e8ea-128">Następujące zapytanie SQL jednostki używa operatora przejdź do nawigacji w relacji między adres i SalesOrderHeader typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="3e8ea-129">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3e8ea-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3e8ea-130">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3e8ea-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="3e8ea-131">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3e8ea-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="3e8ea-132">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="3e8ea-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a><span data-ttu-id="3e8ea-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e8ea-133">See also</span></span>

- [<span data-ttu-id="3e8ea-134">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3e8ea-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3e8ea-135">Instrukcje: Przejdź relacjach za pomocą operatora nawigowania</span><span class="sxs-lookup"><span data-stu-id="3e8ea-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
