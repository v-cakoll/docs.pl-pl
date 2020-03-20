---
title: ISNULL (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150203"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="26459-102">ISNULL (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="26459-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="26459-103">Określa, czy wyrażenie kwerendy ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="26459-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26459-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26459-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="26459-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26459-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="26459-106">Dowolne prawidłowe wyrażenie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="26459-106">Any valid query expression.</span></span> <span data-ttu-id="26459-107">Nie może być kolekcją, mają członków kolekcji lub typu rekordu z właściwościami typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="26459-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="26459-108">NOT</span><span class="sxs-lookup"><span data-stu-id="26459-108">NOT</span></span>  
 <span data-ttu-id="26459-109">Neguje EDM. Wynik logiczny wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="26459-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26459-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="26459-110">Return Value</span></span>  
 <span data-ttu-id="26459-111">`true`jeśli `expression` zwraca wartość null; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="26459-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26459-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26459-112">Remarks</span></span>  
 <span data-ttu-id="26459-113">Służy `IS NULL` do określenia, czy element sprzężenia zewnętrznego ma wartość null:</span><span class="sxs-lookup"><span data-stu-id="26459-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="26459-114">Służy `IS NULL` do określenia, czy element członkowski ma rzeczywistą wartość:</span><span class="sxs-lookup"><span data-stu-id="26459-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="26459-115">W poniższej tabeli `IS NULL` przedstawiono zachowanie ponad niektóre wzorce.</span><span class="sxs-lookup"><span data-stu-id="26459-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="26459-116">Wszystkie wyjątki są generowane od strony klienta, zanim dostawca zostanie wywołany:</span><span class="sxs-lookup"><span data-stu-id="26459-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="26459-117">Wzorce</span><span class="sxs-lookup"><span data-stu-id="26459-117">Pattern</span></span>|<span data-ttu-id="26459-118">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="26459-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="26459-119">wartość null jest zerowa</span><span class="sxs-lookup"><span data-stu-id="26459-119">null IS NULL</span></span>|<span data-ttu-id="26459-120">Zwraca wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="26459-120">Returns `true`.</span></span>|  
|<span data-ttu-id="26459-121">TREAT (null AS EntityType) MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="26459-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="26459-122">Zwraca wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="26459-122">Returns `true`.</span></span>|  
|<span data-ttu-id="26459-123">TREAT (null AS ComplexType) MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="26459-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="26459-124">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="26459-124">Throws an error.</span></span>|  
|<span data-ttu-id="26459-125">TREAT (null AS RowType) MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="26459-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="26459-126">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="26459-126">Throws an error.</span></span>|  
|<span data-ttu-id="26459-127">Typ encji ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="26459-127">EntityType IS NULL</span></span>|<span data-ttu-id="26459-128">Zwraca `true` `false`lub .</span><span class="sxs-lookup"><span data-stu-id="26459-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="26459-129">Typ kompleksu JEST NULL</span><span class="sxs-lookup"><span data-stu-id="26459-129">ComplexType IS NULL</span></span>|<span data-ttu-id="26459-130">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="26459-130">Throws an error.</span></span>|  
|<span data-ttu-id="26459-131">Typ wiersza ma wartość null</span><span class="sxs-lookup"><span data-stu-id="26459-131">RowType IS NULL</span></span>|<span data-ttu-id="26459-132">Zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="26459-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="26459-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="26459-133">Example</span></span>  
 <span data-ttu-id="26459-134">Następująca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kwerenda używa operatora IS NOT NULL do określenia, czy wyrażenie kwerendy nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="26459-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="26459-135">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="26459-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="26459-136">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="26459-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="26459-137">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="26459-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="26459-138">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="26459-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="26459-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26459-139">See also</span></span>

- [<span data-ttu-id="26459-140">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="26459-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
