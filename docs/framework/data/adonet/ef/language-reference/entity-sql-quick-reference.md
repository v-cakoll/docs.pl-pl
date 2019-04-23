---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207074"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="e8274-102">Szybkie odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8274-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="e8274-103">Ten temat zawiera krótki przewodnik po [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8274-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="e8274-104">Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e8274-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="e8274-105">Literały</span><span class="sxs-lookup"><span data-stu-id="e8274-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="e8274-106">String</span><span class="sxs-lookup"><span data-stu-id="e8274-106">String</span></span>  
 <span data-ttu-id="e8274-107">Dostępne są literały ciągów znaków Unicode i innego niż Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8274-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="e8274-108">Ciągi Unicode są poprzedzonej ciągiem N. Na przykład `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="e8274-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="e8274-109">Oto przykład literału ciągu Unicode inne niż:</span><span class="sxs-lookup"><span data-stu-id="e8274-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="e8274-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-110">Output:</span></span>  
  
|<span data-ttu-id="e8274-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-112">Cześć</span><span class="sxs-lookup"><span data-stu-id="e8274-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="e8274-113">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="e8274-113">DateTime</span></span>  
 <span data-ttu-id="e8274-114">W literałach daty/godziny daty i godziny części są obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="e8274-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="e8274-115">Brak wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="e8274-115">There are no default values.</span></span>  
  
 <span data-ttu-id="e8274-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="e8274-117">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-117">Output:</span></span>  
  
|<span data-ttu-id="e8274-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="e8274-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="e8274-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="e8274-120">Integer</span></span>  
 <span data-ttu-id="e8274-121">Literały całkowite mogą być typu Int32 (123) UInt32 (123U), Int64 (123L), a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="e8274-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="e8274-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="e8274-123">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-123">Output:</span></span>  
  
|<span data-ttu-id="e8274-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-125">1</span><span class="sxs-lookup"><span data-stu-id="e8274-125">1</span></span>|  
|<span data-ttu-id="e8274-126">2</span><span class="sxs-lookup"><span data-stu-id="e8274-126">2</span></span>|  
|<span data-ttu-id="e8274-127">3</span><span class="sxs-lookup"><span data-stu-id="e8274-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="e8274-128">Inne</span><span class="sxs-lookup"><span data-stu-id="e8274-128">Other</span></span>  
 <span data-ttu-id="e8274-129">Inne literały, obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to identyfikator Guid, pliku binarnego, Float/Double, Decimal, i `null`.</span><span class="sxs-lookup"><span data-stu-id="e8274-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="e8274-130">Wartość null, literałów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodne z każdego innego typu w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="e8274-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="e8274-131">Konstruktorzy typów</span><span class="sxs-lookup"><span data-stu-id="e8274-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="e8274-132">ROW</span><span class="sxs-lookup"><span data-stu-id="e8274-132">ROW</span></span>  
 <span data-ttu-id="e8274-133">[WIERSZ](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) tworzy anonimowe, strukturalnie wpisane (rekordów) wartością jako: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="e8274-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="e8274-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="e8274-135">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-135">Output:</span></span>  
  
|<span data-ttu-id="e8274-136">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e8274-136">ProductID</span></span>|<span data-ttu-id="e8274-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e8274-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="e8274-138">1</span><span class="sxs-lookup"><span data-stu-id="e8274-138">1</span></span>|<span data-ttu-id="e8274-139">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e8274-139">Adjustable Race</span></span>|  
|<span data-ttu-id="e8274-140">879</span><span class="sxs-lookup"><span data-stu-id="e8274-140">879</span></span>|<span data-ttu-id="e8274-141">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e8274-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e8274-142">712</span><span class="sxs-lookup"><span data-stu-id="e8274-142">712</span></span>|<span data-ttu-id="e8274-143">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e8274-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e8274-144">...</span><span class="sxs-lookup"><span data-stu-id="e8274-144">...</span></span>|<span data-ttu-id="e8274-145">...</span><span class="sxs-lookup"><span data-stu-id="e8274-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="e8274-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="e8274-146">MULTISET</span></span>  
 <span data-ttu-id="e8274-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) tworzy kolekcji, takie jak:</span><span class="sxs-lookup"><span data-stu-id="e8274-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="e8274-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="e8274-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="e8274-149">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="e8274-150">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-150">Output:</span></span>  
  
|<span data-ttu-id="e8274-151">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e8274-151">ProductID</span></span>|<span data-ttu-id="e8274-152">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="e8274-152">Name</span></span>|<span data-ttu-id="e8274-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="e8274-153">ProductNumber</span></span>|<span data-ttu-id="e8274-154">…</span><span class="sxs-lookup"><span data-stu-id="e8274-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="e8274-155">842</span><span class="sxs-lookup"><span data-stu-id="e8274-155">842</span></span>|<span data-ttu-id="e8274-156">Sakwy turystyczne, duże</span><span class="sxs-lookup"><span data-stu-id="e8274-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="e8274-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="e8274-157">PA-T100</span></span>|<span data-ttu-id="e8274-158">…</span><span class="sxs-lookup"><span data-stu-id="e8274-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="e8274-159">Obiekt</span><span class="sxs-lookup"><span data-stu-id="e8274-159">Object</span></span>  
 <span data-ttu-id="e8274-160">[O nazwie konstruktora typu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) tworzy obiekty zdefiniowane przez użytkownika (o nazwie), takie jak `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="e8274-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="e8274-161">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="e8274-162">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-162">Output:</span></span>  
  
|<span data-ttu-id="e8274-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="e8274-163">SalesOrderDetailID</span></span>|<span data-ttu-id="e8274-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="e8274-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="e8274-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="e8274-165">OrderQty</span></span>|<span data-ttu-id="e8274-166">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e8274-166">ProductID</span></span>|<span data-ttu-id="e8274-167">...</span><span class="sxs-lookup"><span data-stu-id="e8274-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="e8274-168">1</span><span class="sxs-lookup"><span data-stu-id="e8274-168">1</span></span>|<span data-ttu-id="e8274-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="e8274-169">4911-403C-98</span></span>|<span data-ttu-id="e8274-170">1</span><span class="sxs-lookup"><span data-stu-id="e8274-170">1</span></span>|<span data-ttu-id="e8274-171">776</span><span class="sxs-lookup"><span data-stu-id="e8274-171">776</span></span>|<span data-ttu-id="e8274-172">...</span><span class="sxs-lookup"><span data-stu-id="e8274-172">...</span></span>|  
|<span data-ttu-id="e8274-173">2</span><span class="sxs-lookup"><span data-stu-id="e8274-173">2</span></span>|<span data-ttu-id="e8274-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="e8274-174">4911-403C-98</span></span>|<span data-ttu-id="e8274-175">3</span><span class="sxs-lookup"><span data-stu-id="e8274-175">3</span></span>|<span data-ttu-id="e8274-176">777</span><span class="sxs-lookup"><span data-stu-id="e8274-176">777</span></span>|<span data-ttu-id="e8274-177">...</span><span class="sxs-lookup"><span data-stu-id="e8274-177">...</span></span>|  
|<span data-ttu-id="e8274-178">...</span><span class="sxs-lookup"><span data-stu-id="e8274-178">...</span></span>|<span data-ttu-id="e8274-179">...</span><span class="sxs-lookup"><span data-stu-id="e8274-179">...</span></span>|<span data-ttu-id="e8274-180">...</span><span class="sxs-lookup"><span data-stu-id="e8274-180">...</span></span>|<span data-ttu-id="e8274-181">...</span><span class="sxs-lookup"><span data-stu-id="e8274-181">...</span></span>|<span data-ttu-id="e8274-182">...</span><span class="sxs-lookup"><span data-stu-id="e8274-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="e8274-183">Odwołania</span><span class="sxs-lookup"><span data-stu-id="e8274-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e8274-184">REF</span><span class="sxs-lookup"><span data-stu-id="e8274-184">REF</span></span>  
 <span data-ttu-id="e8274-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="e8274-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="e8274-186">Na przykład następujące zapytanie zwraca odwołania do każdej jednostki kolejność w zestawie jednostek zamówień:</span><span class="sxs-lookup"><span data-stu-id="e8274-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="e8274-187">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-187">Output:</span></span>  
  
|<span data-ttu-id="e8274-188">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-189">1</span><span class="sxs-lookup"><span data-stu-id="e8274-189">1</span></span>|  
|<span data-ttu-id="e8274-190">2</span><span class="sxs-lookup"><span data-stu-id="e8274-190">2</span></span>|  
|<span data-ttu-id="e8274-191">3</span><span class="sxs-lookup"><span data-stu-id="e8274-191">3</span></span>|  
|<span data-ttu-id="e8274-192">...</span><span class="sxs-lookup"><span data-stu-id="e8274-192">...</span></span>|  
  
 <span data-ttu-id="e8274-193">W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) do dostępu do właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="e8274-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="e8274-194">Gdy używany jest operator wyodrębniania właściwości, odwołanie jest automatycznie wyłuskiwany.</span><span class="sxs-lookup"><span data-stu-id="e8274-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="e8274-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e8274-196">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-196">Output:</span></span>  
  
|<span data-ttu-id="e8274-197">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-198">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e8274-198">Adjustable Race</span></span>|  
|<span data-ttu-id="e8274-199">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e8274-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e8274-200">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e8274-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e8274-201">...</span><span class="sxs-lookup"><span data-stu-id="e8274-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="e8274-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="e8274-202">DEREF</span></span>  
 <span data-ttu-id="e8274-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) wyłuskań wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e8274-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="e8274-204">Na przykład, następujące zapytanie generuje jednostki zamówienia dla każdego zamówienia w zestawie jednostek zamówienia: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="e8274-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="e8274-205">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e8274-206">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-206">Output:</span></span>  
  
|<span data-ttu-id="e8274-207">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-208">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e8274-208">Adjustable Race</span></span>|  
|<span data-ttu-id="e8274-209">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e8274-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e8274-210">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e8274-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e8274-211">...</span><span class="sxs-lookup"><span data-stu-id="e8274-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="e8274-212">CREATEREF I KLUCZ</span><span class="sxs-lookup"><span data-stu-id="e8274-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="e8274-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) tworzy odwołanie przekazywania klucza.</span><span class="sxs-lookup"><span data-stu-id="e8274-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="e8274-214">[KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) wyodrębnia część klucza wyrażeniu zawierającym odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="e8274-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="e8274-215">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e8274-216">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-216">Output:</span></span>  
  
|<span data-ttu-id="e8274-217">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e8274-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="e8274-218">980</span><span class="sxs-lookup"><span data-stu-id="e8274-218">980</span></span>|  
|<span data-ttu-id="e8274-219">365</span><span class="sxs-lookup"><span data-stu-id="e8274-219">365</span></span>|  
|<span data-ttu-id="e8274-220">771</span><span class="sxs-lookup"><span data-stu-id="e8274-220">771</span></span>|  
|<span data-ttu-id="e8274-221">...</span><span class="sxs-lookup"><span data-stu-id="e8274-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="e8274-222">Funkcje</span><span class="sxs-lookup"><span data-stu-id="e8274-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="e8274-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="e8274-223">Canonical</span></span>  
 <span data-ttu-id="e8274-224">Przestrzeń nazw dla [funkcje canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) jest Edm, podobnie jak w `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="e8274-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="e8274-225">Nie masz Określ obszar nazw, chyba że innej przestrzeni nazw jest importowany zawierającego funkcję z taką samą nazwę jak kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e8274-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="e8274-226">Jeśli dwie przestrzenie nazw mają taką samą funkcję, użytkownik musi określonych imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="e8274-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="e8274-227">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="e8274-228">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-228">Output:</span></span>  
  
|<span data-ttu-id="e8274-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="e8274-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="e8274-230">6</span><span class="sxs-lookup"><span data-stu-id="e8274-230">6</span></span>|  
|<span data-ttu-id="e8274-231">6</span><span class="sxs-lookup"><span data-stu-id="e8274-231">6</span></span>|  
|<span data-ttu-id="e8274-232">5</span><span class="sxs-lookup"><span data-stu-id="e8274-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="e8274-233">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="e8274-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="e8274-234">[Funkcje właściwe dla dostawcy Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) znajdują się w `SqlServer` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e8274-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="e8274-235">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="e8274-236">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-236">Output:</span></span>  
  
|<span data-ttu-id="e8274-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="e8274-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="e8274-238">27</span><span class="sxs-lookup"><span data-stu-id="e8274-238">27</span></span>|  
|<span data-ttu-id="e8274-239">27</span><span class="sxs-lookup"><span data-stu-id="e8274-239">27</span></span>|  
|<span data-ttu-id="e8274-240">26</span><span class="sxs-lookup"><span data-stu-id="e8274-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="e8274-241">Namespaces</span><span class="sxs-lookup"><span data-stu-id="e8274-241">Namespaces</span></span>  
 <span data-ttu-id="e8274-242">[Za pomocą](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Określa przestrzeń nazw używaną w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8274-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="e8274-243">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="e8274-244">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-244">Output:</span></span>  
  
|<span data-ttu-id="e8274-245">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-246">aa</span><span class="sxs-lookup"><span data-stu-id="e8274-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="e8274-247">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="e8274-247">Paging</span></span>  
 <span data-ttu-id="e8274-248">Stronicowania może być wyrażona przez zadeklarowanie [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul do [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e8274-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="e8274-249">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="e8274-250">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-250">Output:</span></span>  
  
|<span data-ttu-id="e8274-251">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e8274-251">ID</span></span>|<span data-ttu-id="e8274-252">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e8274-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="e8274-253">10</span><span class="sxs-lookup"><span data-stu-id="e8274-253">10</span></span>|<span data-ttu-id="e8274-254">Adina</span><span class="sxs-lookup"><span data-stu-id="e8274-254">Adina</span></span>|  
|<span data-ttu-id="e8274-255">11</span><span class="sxs-lookup"><span data-stu-id="e8274-255">11</span></span>|<span data-ttu-id="e8274-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="e8274-256">Agcaoili</span></span>|  
|<span data-ttu-id="e8274-257">12</span><span class="sxs-lookup"><span data-stu-id="e8274-257">12</span></span>|<span data-ttu-id="e8274-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="e8274-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="e8274-259">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="e8274-259">Grouping</span></span>  
 <span data-ttu-id="e8274-260">[Grupowanie według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) określa grupy, do których obiektów zwróconych przez zapytanie ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) wyrażenie, które mają być umieszczone.</span><span class="sxs-lookup"><span data-stu-id="e8274-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="e8274-261">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="e8274-262">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-262">Output:</span></span>  
  
|<span data-ttu-id="e8274-263">nazwa</span><span class="sxs-lookup"><span data-stu-id="e8274-263">name</span></span>|  
|----------|  
|<span data-ttu-id="e8274-264">LL górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="e8274-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e8274-265">Uczenie Maszynowe górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="e8274-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e8274-266">Rama górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="e8274-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e8274-267">...</span><span class="sxs-lookup"><span data-stu-id="e8274-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="e8274-268">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="e8274-268">Navigation</span></span>  
 <span data-ttu-id="e8274-269">Operator nawigacji relacji można przejść przez relacji z jednej jednostki (od końca) do innego (w celu zakończenia).</span><span class="sxs-lookup"><span data-stu-id="e8274-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="e8274-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) przyjmuje odpowiednio wykwalifikowany typ relacji \<przestrzeni nazw >.\< Nazwa typu relacji >.</span><span class="sxs-lookup"><span data-stu-id="e8274-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="e8274-271">Przejdź zwraca Ref\<T > Jeśli kardynalność do końca jest 1.</span><span class="sxs-lookup"><span data-stu-id="e8274-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="e8274-272">Jeśli kardynalność do końca jest n, kolekcji < Ref\<T >> zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e8274-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="e8274-273">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="e8274-274">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-274">Output:</span></span>  
  
|<span data-ttu-id="e8274-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="e8274-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="e8274-276">1</span><span class="sxs-lookup"><span data-stu-id="e8274-276">1</span></span>|  
|<span data-ttu-id="e8274-277">2</span><span class="sxs-lookup"><span data-stu-id="e8274-277">2</span></span>|  
|<span data-ttu-id="e8274-278">3</span><span class="sxs-lookup"><span data-stu-id="e8274-278">3</span></span>|  
|<span data-ttu-id="e8274-279">...</span><span class="sxs-lookup"><span data-stu-id="e8274-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="e8274-280">WYBIERZ WARTOŚĆ I WYBIERZ POZYCJĘ</span><span class="sxs-lookup"><span data-stu-id="e8274-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="e8274-281">WYBIERZ WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e8274-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e8274-282">udostępnia klauzula SELECT VALUE, aby pominąć konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="e8274-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="e8274-283">Można określić tylko jeden element w klauzuli SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="e8274-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="e8274-284">Takie klauzula jest używana, nie otoki wiersza jest konstruowany wokół elementów w klauzuli SELECT, gdy kolekcja żądany kształt może wygenerować, na przykład: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="e8274-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="e8274-285">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e8274-286">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-286">Output:</span></span>  
  
|<span data-ttu-id="e8274-287">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e8274-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="e8274-288">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e8274-288">Adjustable Race</span></span>|  
|<span data-ttu-id="e8274-289">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e8274-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e8274-290">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e8274-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e8274-291">...</span><span class="sxs-lookup"><span data-stu-id="e8274-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="e8274-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="e8274-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e8274-293">zapewnia także Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="e8274-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="e8274-294">Wybierz przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych z polami, na przykład: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="e8274-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="e8274-295">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-295">Example:</span></span>  
  
 <span data-ttu-id="e8274-296">Wybierz p.Name, p.ProductID z AdventureWorksEntities.Product jako dane wyjściowe p:</span><span class="sxs-lookup"><span data-stu-id="e8274-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="e8274-297">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e8274-297">Name</span></span>|<span data-ttu-id="e8274-298">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e8274-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="e8274-299">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e8274-299">Adjustable Race</span></span>|<span data-ttu-id="e8274-300">1</span><span class="sxs-lookup"><span data-stu-id="e8274-300">1</span></span>|  
|<span data-ttu-id="e8274-301">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e8274-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="e8274-302">879</span><span class="sxs-lookup"><span data-stu-id="e8274-302">879</span></span>|  
|<span data-ttu-id="e8274-303">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e8274-303">AWC Logo Cap</span></span>|<span data-ttu-id="e8274-304">712</span><span class="sxs-lookup"><span data-stu-id="e8274-304">712</span></span>|  
|<span data-ttu-id="e8274-305">...</span><span class="sxs-lookup"><span data-stu-id="e8274-305">...</span></span>|<span data-ttu-id="e8274-306">...</span><span class="sxs-lookup"><span data-stu-id="e8274-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="e8274-307">WYRAŻENIE CASE</span><span class="sxs-lookup"><span data-stu-id="e8274-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="e8274-308">[Zamierzone, Zapisz wyrażenie](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) obliczenie zestawu wyrażeń logicznych w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="e8274-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="e8274-309">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e8274-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="e8274-310">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e8274-310">Output:</span></span>  
  
|<span data-ttu-id="e8274-311">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8274-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e8274-312">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="e8274-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8274-313">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8274-313">See also</span></span>

- [<span data-ttu-id="e8274-314">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e8274-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e8274-315">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e8274-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
