---
title: Nawigacja (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319542"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="93a06-102">Nawigacja (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="93a06-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="93a06-103">Nawiguje nad relacją ustanowioną między jednostkami.</span><span class="sxs-lookup"><span data-stu-id="93a06-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="93a06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93a06-104">Syntax</span></span>

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="93a06-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="93a06-105">Arguments</span></span>

<span data-ttu-id="93a06-106">`instance-expression` wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="93a06-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="93a06-107">`relationship-type` nazwę typu relacji z pliku koncepcyjnego języka definicji schematu (CSDL).</span><span class="sxs-lookup"><span data-stu-id="93a06-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="93a06-108">`relationship-type` jest kwalifikowana jako \<przestrzeni nazw >. > nazwy typu relacji\<.</span><span class="sxs-lookup"><span data-stu-id="93a06-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="93a06-109">`to` koniec relacji.</span><span class="sxs-lookup"><span data-stu-id="93a06-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="93a06-110">`from` początku relacji.</span><span class="sxs-lookup"><span data-stu-id="93a06-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="93a06-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="93a06-111">Return Value</span></span>

<span data-ttu-id="93a06-112">Jeśli Kardynalność do końca wynosi 1, wartość zwracana zostanie `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="93a06-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="93a06-113">Jeśli Kardynalność do końca to n, wartość zwracana zostanie `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="93a06-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="93a06-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93a06-114">Remarks</span></span>

<span data-ttu-id="93a06-115">Relacje to konstrukcje pierwszej klasy w Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="93a06-115">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="93a06-116">Relacje można ustanawiać między dwoma lub większą liczbą typów jednostek, a użytkownicy mogą przechodzić przez relację od jednego końca (jednostki) do innej.</span><span class="sxs-lookup"><span data-stu-id="93a06-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="93a06-117">`from` i `to` są warunkowo opcjonalne, gdy w ramach rozpoznawania nazw nie ma niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="93a06-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="93a06-118">NAWIGOWANIe jest prawidłowe w miejscu i O i C.</span><span class="sxs-lookup"><span data-stu-id="93a06-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="93a06-119">Ogólny formularz konstrukcji nawigacyjnej jest następujący:</span><span class="sxs-lookup"><span data-stu-id="93a06-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="93a06-120">Nawigacja (`instance-expression`, `relationship-type`, [`to-end` [, `from-end`]])</span><span class="sxs-lookup"><span data-stu-id="93a06-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="93a06-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="93a06-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="93a06-122">Gdzie OrderCustomer jest `relationship`, a klient i zamówienie to `to-end` (klient) i `from-end` (zamówienie) relacji.</span><span class="sxs-lookup"><span data-stu-id="93a06-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="93a06-123">Jeśli OrderCustomer była relacją n:1, typ wyniku wyrażenia nawigacji to ref\<Customer >.</span><span class="sxs-lookup"><span data-stu-id="93a06-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="93a06-124">Prostszy formularz tego wyrażenia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="93a06-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="93a06-125">Podobnie w przypadku zapytania w następującej postaci wyrażenie nawigacji spowoduje utworzenie kolekcji < ref\<kolejności > >.</span><span class="sxs-lookup"><span data-stu-id="93a06-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="93a06-126">Wyrażenie wystąpienia musi być typu jednostki/odwołania.</span><span class="sxs-lookup"><span data-stu-id="93a06-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="93a06-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="93a06-127">Example</span></span>

<span data-ttu-id="93a06-128">Poniższe zapytanie Entity SQL używa operatora nawigacji, aby nawigować przez relację między typami jednostek Address i SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="93a06-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="93a06-129">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="93a06-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="93a06-130">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="93a06-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="93a06-131">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="93a06-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="93a06-132">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="93a06-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a><span data-ttu-id="93a06-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a06-133">See also</span></span>

- [<span data-ttu-id="93a06-134">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="93a06-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="93a06-135">Instrukcje: nawigowanie po relacjach za pomocą operatora nawigacji</span><span class="sxs-lookup"><span data-stu-id="93a06-135">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
