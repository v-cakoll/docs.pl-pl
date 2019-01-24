---
title: Szybkie odwołanie do jednostki SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 20d8d1cb1e4b5cbf37dffcce6a7e79c2a4c265d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539406"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="f327b-102">Szybkie odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f327b-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="f327b-103">Ten temat zawiera krótki przewodnik po [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="f327b-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="f327b-104">Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f327b-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="f327b-105">Literały</span><span class="sxs-lookup"><span data-stu-id="f327b-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="f327b-106">String</span><span class="sxs-lookup"><span data-stu-id="f327b-106">String</span></span>  
 <span data-ttu-id="f327b-107">Dostępne są literały ciągów znaków Unicode i innego niż Unicode.</span><span class="sxs-lookup"><span data-stu-id="f327b-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="f327b-108">Ciągi Unicode są poprzedzonej ciągiem N. Na przykład `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="f327b-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="f327b-109">Oto przykład literału ciągu Unicode inne niż:</span><span class="sxs-lookup"><span data-stu-id="f327b-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="f327b-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-110">Output:</span></span>  
  
|<span data-ttu-id="f327b-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-112">Cześć</span><span class="sxs-lookup"><span data-stu-id="f327b-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="f327b-113">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="f327b-113">DateTime</span></span>  
 <span data-ttu-id="f327b-114">W literałach daty/godziny daty i godziny części są obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="f327b-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="f327b-115">Brak wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f327b-115">There are no default values.</span></span>  
  
 <span data-ttu-id="f327b-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="f327b-117">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-117">Output:</span></span>  
  
|<span data-ttu-id="f327b-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="f327b-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="f327b-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="f327b-120">Integer</span></span>  
 <span data-ttu-id="f327b-121">Literały całkowite mogą być typu Int32 (123) UInt32 (123U), Int64 (123L), a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="f327b-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="f327b-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="f327b-123">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-123">Output:</span></span>  
  
|<span data-ttu-id="f327b-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-125">1</span><span class="sxs-lookup"><span data-stu-id="f327b-125">1</span></span>|  
|<span data-ttu-id="f327b-126">2</span><span class="sxs-lookup"><span data-stu-id="f327b-126">2</span></span>|  
|<span data-ttu-id="f327b-127">3</span><span class="sxs-lookup"><span data-stu-id="f327b-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="f327b-128">Inne</span><span class="sxs-lookup"><span data-stu-id="f327b-128">Other</span></span>  
 <span data-ttu-id="f327b-129">Inne literały, obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to identyfikator Guid, pliku binarnego, Float/Double, Decimal, i `null`.</span><span class="sxs-lookup"><span data-stu-id="f327b-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="f327b-130">Wartość null, literałów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodne z każdego innego typu w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f327b-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="f327b-131">Konstruktorzy typów</span><span class="sxs-lookup"><span data-stu-id="f327b-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="f327b-132">WIERSZ</span><span class="sxs-lookup"><span data-stu-id="f327b-132">ROW</span></span>  
 <span data-ttu-id="f327b-133">[WIERSZ](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) tworzy anonimowe, strukturalnie wpisane (rekordów) wartością jako: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="f327b-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="f327b-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="f327b-135">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-135">Output:</span></span>  
  
|<span data-ttu-id="f327b-136">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="f327b-136">ProductID</span></span>|<span data-ttu-id="f327b-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f327b-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="f327b-138">1</span><span class="sxs-lookup"><span data-stu-id="f327b-138">1</span></span>|<span data-ttu-id="f327b-139">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="f327b-139">Adjustable Race</span></span>|  
|<span data-ttu-id="f327b-140">879</span><span class="sxs-lookup"><span data-stu-id="f327b-140">879</span></span>|<span data-ttu-id="f327b-141">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="f327b-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="f327b-142">712</span><span class="sxs-lookup"><span data-stu-id="f327b-142">712</span></span>|<span data-ttu-id="f327b-143">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="f327b-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="f327b-144">...</span><span class="sxs-lookup"><span data-stu-id="f327b-144">...</span></span>|<span data-ttu-id="f327b-145">...</span><span class="sxs-lookup"><span data-stu-id="f327b-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="f327b-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="f327b-146">MULTISET</span></span>  
 <span data-ttu-id="f327b-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) tworzy kolekcji, takie jak:</span><span class="sxs-lookup"><span data-stu-id="f327b-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="f327b-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="f327b-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="f327b-149">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="f327b-150">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-150">Output:</span></span>  
  
|<span data-ttu-id="f327b-151">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="f327b-151">ProductID</span></span>|<span data-ttu-id="f327b-152">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="f327b-152">Name</span></span>|<span data-ttu-id="f327b-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="f327b-153">ProductNumber</span></span>|<span data-ttu-id="f327b-154">…</span><span class="sxs-lookup"><span data-stu-id="f327b-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="f327b-155">842</span><span class="sxs-lookup"><span data-stu-id="f327b-155">842</span></span>|<span data-ttu-id="f327b-156">Sakwy turystyczne, duże</span><span class="sxs-lookup"><span data-stu-id="f327b-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="f327b-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="f327b-157">PA-T100</span></span>|<span data-ttu-id="f327b-158">…</span><span class="sxs-lookup"><span data-stu-id="f327b-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="f327b-159">Obiekt</span><span class="sxs-lookup"><span data-stu-id="f327b-159">Object</span></span>  
 <span data-ttu-id="f327b-160">[O nazwie konstruktora typu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) tworzy obiekty zdefiniowane przez użytkownika (o nazwie), takie jak `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="f327b-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="f327b-161">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="f327b-162">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-162">Output:</span></span>  
  
|<span data-ttu-id="f327b-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="f327b-163">SalesOrderDetailID</span></span>|<span data-ttu-id="f327b-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="f327b-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="f327b-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="f327b-165">OrderQty</span></span>|<span data-ttu-id="f327b-166">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="f327b-166">ProductID</span></span>|<span data-ttu-id="f327b-167">...</span><span class="sxs-lookup"><span data-stu-id="f327b-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="f327b-168">1</span><span class="sxs-lookup"><span data-stu-id="f327b-168">1</span></span>|<span data-ttu-id="f327b-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="f327b-169">4911-403C-98</span></span>|<span data-ttu-id="f327b-170">1</span><span class="sxs-lookup"><span data-stu-id="f327b-170">1</span></span>|<span data-ttu-id="f327b-171">776</span><span class="sxs-lookup"><span data-stu-id="f327b-171">776</span></span>|<span data-ttu-id="f327b-172">...</span><span class="sxs-lookup"><span data-stu-id="f327b-172">...</span></span>|  
|<span data-ttu-id="f327b-173">2</span><span class="sxs-lookup"><span data-stu-id="f327b-173">2</span></span>|<span data-ttu-id="f327b-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="f327b-174">4911-403C-98</span></span>|<span data-ttu-id="f327b-175">3</span><span class="sxs-lookup"><span data-stu-id="f327b-175">3</span></span>|<span data-ttu-id="f327b-176">777</span><span class="sxs-lookup"><span data-stu-id="f327b-176">777</span></span>|<span data-ttu-id="f327b-177">...</span><span class="sxs-lookup"><span data-stu-id="f327b-177">...</span></span>|  
|<span data-ttu-id="f327b-178">...</span><span class="sxs-lookup"><span data-stu-id="f327b-178">...</span></span>|<span data-ttu-id="f327b-179">...</span><span class="sxs-lookup"><span data-stu-id="f327b-179">...</span></span>|<span data-ttu-id="f327b-180">...</span><span class="sxs-lookup"><span data-stu-id="f327b-180">...</span></span>|<span data-ttu-id="f327b-181">...</span><span class="sxs-lookup"><span data-stu-id="f327b-181">...</span></span>|<span data-ttu-id="f327b-182">...</span><span class="sxs-lookup"><span data-stu-id="f327b-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="f327b-183">Odwołania</span><span class="sxs-lookup"><span data-stu-id="f327b-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f327b-184">REF</span><span class="sxs-lookup"><span data-stu-id="f327b-184">REF</span></span>  
 <span data-ttu-id="f327b-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="f327b-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="f327b-186">Na przykład następujące zapytanie zwraca odwołania do każdej jednostki kolejność w zestawie jednostek zamówień:</span><span class="sxs-lookup"><span data-stu-id="f327b-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="f327b-187">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-187">Output:</span></span>  
  
|<span data-ttu-id="f327b-188">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-189">1</span><span class="sxs-lookup"><span data-stu-id="f327b-189">1</span></span>|  
|<span data-ttu-id="f327b-190">2</span><span class="sxs-lookup"><span data-stu-id="f327b-190">2</span></span>|  
|<span data-ttu-id="f327b-191">3</span><span class="sxs-lookup"><span data-stu-id="f327b-191">3</span></span>|  
|<span data-ttu-id="f327b-192">...</span><span class="sxs-lookup"><span data-stu-id="f327b-192">...</span></span>|  
  
 <span data-ttu-id="f327b-193">W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) do dostępu do właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="f327b-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="f327b-194">Gdy używany jest operator wyodrębniania właściwości, odwołanie jest automatycznie wyłuskiwany.</span><span class="sxs-lookup"><span data-stu-id="f327b-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="f327b-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="f327b-196">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-196">Output:</span></span>  
  
|<span data-ttu-id="f327b-197">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-198">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="f327b-198">Adjustable Race</span></span>|  
|<span data-ttu-id="f327b-199">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="f327b-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="f327b-200">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="f327b-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="f327b-201">...</span><span class="sxs-lookup"><span data-stu-id="f327b-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="f327b-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="f327b-202">DEREF</span></span>  
 <span data-ttu-id="f327b-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) wyłuskań wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f327b-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="f327b-204">Na przykład, następujące zapytanie generuje jednostki zamówienia dla każdego zamówienia w zestawie jednostek zamówienia: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="f327b-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="f327b-205">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="f327b-206">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-206">Output:</span></span>  
  
|<span data-ttu-id="f327b-207">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-208">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="f327b-208">Adjustable Race</span></span>|  
|<span data-ttu-id="f327b-209">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="f327b-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="f327b-210">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="f327b-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="f327b-211">...</span><span class="sxs-lookup"><span data-stu-id="f327b-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="f327b-212">CREATEREF I KLUCZ</span><span class="sxs-lookup"><span data-stu-id="f327b-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="f327b-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) tworzy odwołanie przekazywania klucza.</span><span class="sxs-lookup"><span data-stu-id="f327b-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="f327b-214">[KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) wyodrębnia część klucza wyrażeniu zawierającym odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="f327b-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="f327b-215">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="f327b-216">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-216">Output:</span></span>  
  
|<span data-ttu-id="f327b-217">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="f327b-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="f327b-218">980</span><span class="sxs-lookup"><span data-stu-id="f327b-218">980</span></span>|  
|<span data-ttu-id="f327b-219">365</span><span class="sxs-lookup"><span data-stu-id="f327b-219">365</span></span>|  
|<span data-ttu-id="f327b-220">771</span><span class="sxs-lookup"><span data-stu-id="f327b-220">771</span></span>|  
|<span data-ttu-id="f327b-221">...</span><span class="sxs-lookup"><span data-stu-id="f327b-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="f327b-222">Funkcje</span><span class="sxs-lookup"><span data-stu-id="f327b-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="f327b-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="f327b-223">Canonical</span></span>  
 <span data-ttu-id="f327b-224">Przestrzeń nazw dla [funkcje canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) jest Edm, podobnie jak w `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="f327b-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="f327b-225">Nie masz Określ obszar nazw, chyba że innej przestrzeni nazw jest importowany zawierającego funkcję z taką samą nazwę jak kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f327b-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="f327b-226">Jeśli dwie przestrzenie nazw mają taką samą funkcję, użytkownik musi określonych imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="f327b-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="f327b-227">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="f327b-228">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-228">Output:</span></span>  
  
|<span data-ttu-id="f327b-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="f327b-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="f327b-230">6</span><span class="sxs-lookup"><span data-stu-id="f327b-230">6</span></span>|  
|<span data-ttu-id="f327b-231">6</span><span class="sxs-lookup"><span data-stu-id="f327b-231">6</span></span>|  
|<span data-ttu-id="f327b-232">5</span><span class="sxs-lookup"><span data-stu-id="f327b-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="f327b-233">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="f327b-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="f327b-234">[Funkcje właściwe dla dostawcy Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) znajdują się w `SqlServer` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f327b-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="f327b-235">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="f327b-236">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-236">Output:</span></span>  
  
|<span data-ttu-id="f327b-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="f327b-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="f327b-238">27</span><span class="sxs-lookup"><span data-stu-id="f327b-238">27</span></span>|  
|<span data-ttu-id="f327b-239">27</span><span class="sxs-lookup"><span data-stu-id="f327b-239">27</span></span>|  
|<span data-ttu-id="f327b-240">26</span><span class="sxs-lookup"><span data-stu-id="f327b-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="f327b-241">Namespaces</span><span class="sxs-lookup"><span data-stu-id="f327b-241">Namespaces</span></span>  
 <span data-ttu-id="f327b-242">[Za pomocą](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Określa przestrzeń nazw używaną w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="f327b-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="f327b-243">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="f327b-244">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-244">Output:</span></span>  
  
|<span data-ttu-id="f327b-245">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-246">aa</span><span class="sxs-lookup"><span data-stu-id="f327b-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="f327b-247">Stronicowania</span><span class="sxs-lookup"><span data-stu-id="f327b-247">Paging</span></span>  
 <span data-ttu-id="f327b-248">Stronicowania może być wyrażona przez zadeklarowanie [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul do [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f327b-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="f327b-249">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="f327b-250">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-250">Output:</span></span>  
  
|<span data-ttu-id="f327b-251">ID</span><span class="sxs-lookup"><span data-stu-id="f327b-251">ID</span></span>|<span data-ttu-id="f327b-252">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f327b-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="f327b-253">10</span><span class="sxs-lookup"><span data-stu-id="f327b-253">10</span></span>|<span data-ttu-id="f327b-254">Adina</span><span class="sxs-lookup"><span data-stu-id="f327b-254">Adina</span></span>|  
|<span data-ttu-id="f327b-255">11</span><span class="sxs-lookup"><span data-stu-id="f327b-255">11</span></span>|<span data-ttu-id="f327b-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="f327b-256">Agcaoili</span></span>|  
|<span data-ttu-id="f327b-257">12</span><span class="sxs-lookup"><span data-stu-id="f327b-257">12</span></span>|<span data-ttu-id="f327b-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="f327b-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="f327b-259">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="f327b-259">Grouping</span></span>  
 <span data-ttu-id="f327b-260">[Grupowanie według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) określa grupy, do których obiektów zwróconych przez zapytanie ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) wyrażenie, które mają być umieszczone.</span><span class="sxs-lookup"><span data-stu-id="f327b-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="f327b-261">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="f327b-262">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-262">Output:</span></span>  
  
|<span data-ttu-id="f327b-263">nazwa</span><span class="sxs-lookup"><span data-stu-id="f327b-263">name</span></span>|  
|----------|  
|<span data-ttu-id="f327b-264">LL górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="f327b-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="f327b-265">Uczenie Maszynowe górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="f327b-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="f327b-266">Rama górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="f327b-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="f327b-267">...</span><span class="sxs-lookup"><span data-stu-id="f327b-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="f327b-268">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="f327b-268">Navigation</span></span>  
 <span data-ttu-id="f327b-269">Operator nawigacji relacji można przejść przez relacji z jednej jednostki (od końca) do innego (w celu zakończenia).</span><span class="sxs-lookup"><span data-stu-id="f327b-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="f327b-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) przyjmuje odpowiednio wykwalifikowany typ relacji \<przestrzeni nazw >.\< Nazwa typu relacji >.</span><span class="sxs-lookup"><span data-stu-id="f327b-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="f327b-271">Przejdź zwraca Ref\<T > Jeśli kardynalność do końca jest 1.</span><span class="sxs-lookup"><span data-stu-id="f327b-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="f327b-272">Jeśli kardynalność do końca jest n, kolekcji < Ref\<T >> zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f327b-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="f327b-273">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="f327b-274">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-274">Output:</span></span>  
  
|<span data-ttu-id="f327b-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="f327b-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="f327b-276">1</span><span class="sxs-lookup"><span data-stu-id="f327b-276">1</span></span>|  
|<span data-ttu-id="f327b-277">2</span><span class="sxs-lookup"><span data-stu-id="f327b-277">2</span></span>|  
|<span data-ttu-id="f327b-278">3</span><span class="sxs-lookup"><span data-stu-id="f327b-278">3</span></span>|  
|<span data-ttu-id="f327b-279">...</span><span class="sxs-lookup"><span data-stu-id="f327b-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="f327b-280">WYBIERZ WARTOŚĆ I WYBIERZ POZYCJĘ</span><span class="sxs-lookup"><span data-stu-id="f327b-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="f327b-281">WYBIERZ WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="f327b-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f327b-282">udostępnia klauzula SELECT VALUE, aby pominąć konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="f327b-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="f327b-283">Można określić tylko jeden element w klauzuli SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="f327b-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="f327b-284">Takie klauzula jest używana, nie otoki wiersza jest konstruowany wokół elementów w klauzuli SELECT, gdy kolekcja żądany kształt może wygenerować, na przykład: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="f327b-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="f327b-285">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="f327b-286">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-286">Output:</span></span>  
  
|<span data-ttu-id="f327b-287">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f327b-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="f327b-288">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="f327b-288">Adjustable Race</span></span>|  
|<span data-ttu-id="f327b-289">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="f327b-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="f327b-290">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="f327b-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="f327b-291">...</span><span class="sxs-lookup"><span data-stu-id="f327b-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="f327b-292">WYBIERZ POZYCJĘ</span><span class="sxs-lookup"><span data-stu-id="f327b-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f327b-293">zapewnia także Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="f327b-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="f327b-294">Wybierz przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych z polami, na przykład: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="f327b-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="f327b-295">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-295">Example:</span></span>  
  
 <span data-ttu-id="f327b-296">Wybierz p.Name, p.ProductID z AdventureWorksEntities.Product jako dane wyjściowe p:</span><span class="sxs-lookup"><span data-stu-id="f327b-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="f327b-297">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f327b-297">Name</span></span>|<span data-ttu-id="f327b-298">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="f327b-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="f327b-299">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="f327b-299">Adjustable Race</span></span>|<span data-ttu-id="f327b-300">1</span><span class="sxs-lookup"><span data-stu-id="f327b-300">1</span></span>|  
|<span data-ttu-id="f327b-301">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="f327b-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="f327b-302">879</span><span class="sxs-lookup"><span data-stu-id="f327b-302">879</span></span>|  
|<span data-ttu-id="f327b-303">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="f327b-303">AWC Logo Cap</span></span>|<span data-ttu-id="f327b-304">712</span><span class="sxs-lookup"><span data-stu-id="f327b-304">712</span></span>|  
|<span data-ttu-id="f327b-305">...</span><span class="sxs-lookup"><span data-stu-id="f327b-305">...</span></span>|<span data-ttu-id="f327b-306">...</span><span class="sxs-lookup"><span data-stu-id="f327b-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="f327b-307">WYRAŻENIE CASE</span><span class="sxs-lookup"><span data-stu-id="f327b-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="f327b-308">[Zamierzone, Zapisz wyrażenie](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) obliczenie zestawu wyrażeń logicznych w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="f327b-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="f327b-309">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f327b-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="f327b-310">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f327b-310">Output:</span></span>  
  
|<span data-ttu-id="f327b-311">Wartość</span><span class="sxs-lookup"><span data-stu-id="f327b-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="f327b-312">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="f327b-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f327b-313">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f327b-313">See also</span></span>
- [<span data-ttu-id="f327b-314">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f327b-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f327b-315">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f327b-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
