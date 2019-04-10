---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207074"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="e503a-102">Szybkie odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e503a-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="e503a-103">Ten temat zawiera krótki przewodnik po [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="e503a-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="e503a-104">Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e503a-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="e503a-105">Literały</span><span class="sxs-lookup"><span data-stu-id="e503a-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="e503a-106">String</span><span class="sxs-lookup"><span data-stu-id="e503a-106">String</span></span>  
 <span data-ttu-id="e503a-107">Dostępne są literały ciągów znaków Unicode i innego niż Unicode.</span><span class="sxs-lookup"><span data-stu-id="e503a-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="e503a-108">Ciągi Unicode są poprzedzonej ciągiem N. Na przykład `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="e503a-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="e503a-109">Oto przykład literału ciągu Unicode inne niż:</span><span class="sxs-lookup"><span data-stu-id="e503a-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="e503a-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-110">Output:</span></span>  
  
|<span data-ttu-id="e503a-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-112">Cześć</span><span class="sxs-lookup"><span data-stu-id="e503a-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="e503a-113">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="e503a-113">DateTime</span></span>  
 <span data-ttu-id="e503a-114">W literałach daty/godziny daty i godziny części są obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="e503a-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="e503a-115">Brak wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="e503a-115">There are no default values.</span></span>  
  
 <span data-ttu-id="e503a-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="e503a-117">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-117">Output:</span></span>  
  
|<span data-ttu-id="e503a-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="e503a-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="e503a-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="e503a-120">Integer</span></span>  
 <span data-ttu-id="e503a-121">Literały całkowite mogą być typu Int32 (123) UInt32 (123U), Int64 (123L), a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="e503a-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="e503a-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="e503a-123">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-123">Output:</span></span>  
  
|<span data-ttu-id="e503a-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-125">1</span><span class="sxs-lookup"><span data-stu-id="e503a-125">1</span></span>|  
|<span data-ttu-id="e503a-126">2</span><span class="sxs-lookup"><span data-stu-id="e503a-126">2</span></span>|  
|<span data-ttu-id="e503a-127">3</span><span class="sxs-lookup"><span data-stu-id="e503a-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="e503a-128">Inne</span><span class="sxs-lookup"><span data-stu-id="e503a-128">Other</span></span>  
 <span data-ttu-id="e503a-129">Inne literały, obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to identyfikator Guid, pliku binarnego, Float/Double, Decimal, i `null`.</span><span class="sxs-lookup"><span data-stu-id="e503a-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="e503a-130">Wartość null, literałów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodne z każdego innego typu w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="e503a-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="e503a-131">Konstruktorzy typów</span><span class="sxs-lookup"><span data-stu-id="e503a-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="e503a-132">ROW</span><span class="sxs-lookup"><span data-stu-id="e503a-132">ROW</span></span>  
 <span data-ttu-id="e503a-133">[WIERSZ](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) tworzy anonimowe, strukturalnie wpisane (rekordów) wartością jako:</span><span class="sxs-lookup"><span data-stu-id="e503a-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in:</span></span> `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 <span data-ttu-id="e503a-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="e503a-135">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-135">Output:</span></span>  
  
|<span data-ttu-id="e503a-136">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e503a-136">ProductID</span></span>|<span data-ttu-id="e503a-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e503a-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="e503a-138">1</span><span class="sxs-lookup"><span data-stu-id="e503a-138">1</span></span>|<span data-ttu-id="e503a-139">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e503a-139">Adjustable Race</span></span>|  
|<span data-ttu-id="e503a-140">879</span><span class="sxs-lookup"><span data-stu-id="e503a-140">879</span></span>|<span data-ttu-id="e503a-141">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e503a-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e503a-142">712</span><span class="sxs-lookup"><span data-stu-id="e503a-142">712</span></span>|<span data-ttu-id="e503a-143">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e503a-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e503a-144">...</span><span class="sxs-lookup"><span data-stu-id="e503a-144">...</span></span>|<span data-ttu-id="e503a-145">...</span><span class="sxs-lookup"><span data-stu-id="e503a-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="e503a-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="e503a-146">MULTISET</span></span>  
 <span data-ttu-id="e503a-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) tworzy kolekcji, takie jak:</span><span class="sxs-lookup"><span data-stu-id="e503a-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 <span data-ttu-id="e503a-148">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-148">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="e503a-149">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-149">Output:</span></span>  
  
|<span data-ttu-id="e503a-150">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e503a-150">ProductID</span></span>|<span data-ttu-id="e503a-151">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="e503a-151">Name</span></span>|<span data-ttu-id="e503a-152">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="e503a-152">ProductNumber</span></span>|<span data-ttu-id="e503a-153">…</span><span class="sxs-lookup"><span data-stu-id="e503a-153">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="e503a-154">842</span><span class="sxs-lookup"><span data-stu-id="e503a-154">842</span></span>|<span data-ttu-id="e503a-155">Sakwy turystyczne, duże</span><span class="sxs-lookup"><span data-stu-id="e503a-155">Touring-Panniers, Large</span></span>|<span data-ttu-id="e503a-156">PA-T100</span><span class="sxs-lookup"><span data-stu-id="e503a-156">PA-T100</span></span>|<span data-ttu-id="e503a-157">…</span><span class="sxs-lookup"><span data-stu-id="e503a-157">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="e503a-158">Obiekt</span><span class="sxs-lookup"><span data-stu-id="e503a-158">Object</span></span>  
 <span data-ttu-id="e503a-159">[O nazwie konstruktora typu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) tworzy obiekty zdefiniowane przez użytkownika (o nazwie), takie jak `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="e503a-159">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="e503a-160">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-160">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="e503a-161">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-161">Output:</span></span>  
  
|<span data-ttu-id="e503a-162">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="e503a-162">SalesOrderDetailID</span></span>|<span data-ttu-id="e503a-163">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="e503a-163">CarrierTrackingNumber</span></span>|<span data-ttu-id="e503a-164">OrderQty</span><span class="sxs-lookup"><span data-stu-id="e503a-164">OrderQty</span></span>|<span data-ttu-id="e503a-165">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e503a-165">ProductID</span></span>|<span data-ttu-id="e503a-166">...</span><span class="sxs-lookup"><span data-stu-id="e503a-166">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="e503a-167">1</span><span class="sxs-lookup"><span data-stu-id="e503a-167">1</span></span>|<span data-ttu-id="e503a-168">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="e503a-168">4911-403C-98</span></span>|<span data-ttu-id="e503a-169">1</span><span class="sxs-lookup"><span data-stu-id="e503a-169">1</span></span>|<span data-ttu-id="e503a-170">776</span><span class="sxs-lookup"><span data-stu-id="e503a-170">776</span></span>|<span data-ttu-id="e503a-171">...</span><span class="sxs-lookup"><span data-stu-id="e503a-171">...</span></span>|  
|<span data-ttu-id="e503a-172">2</span><span class="sxs-lookup"><span data-stu-id="e503a-172">2</span></span>|<span data-ttu-id="e503a-173">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="e503a-173">4911-403C-98</span></span>|<span data-ttu-id="e503a-174">3</span><span class="sxs-lookup"><span data-stu-id="e503a-174">3</span></span>|<span data-ttu-id="e503a-175">777</span><span class="sxs-lookup"><span data-stu-id="e503a-175">777</span></span>|<span data-ttu-id="e503a-176">...</span><span class="sxs-lookup"><span data-stu-id="e503a-176">...</span></span>|  
|<span data-ttu-id="e503a-177">...</span><span class="sxs-lookup"><span data-stu-id="e503a-177">...</span></span>|<span data-ttu-id="e503a-178">...</span><span class="sxs-lookup"><span data-stu-id="e503a-178">...</span></span>|<span data-ttu-id="e503a-179">...</span><span class="sxs-lookup"><span data-stu-id="e503a-179">...</span></span>|<span data-ttu-id="e503a-180">...</span><span class="sxs-lookup"><span data-stu-id="e503a-180">...</span></span>|<span data-ttu-id="e503a-181">...</span><span class="sxs-lookup"><span data-stu-id="e503a-181">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="e503a-182">Odwołania</span><span class="sxs-lookup"><span data-stu-id="e503a-182">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e503a-183">REF</span><span class="sxs-lookup"><span data-stu-id="e503a-183">REF</span></span>  
 <span data-ttu-id="e503a-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="e503a-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="e503a-185">Na przykład następujące zapytanie zwraca odwołania do każdej jednostki kolejność w zestawie jednostek zamówień:</span><span class="sxs-lookup"><span data-stu-id="e503a-185">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="e503a-186">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-186">Output:</span></span>  
  
|<span data-ttu-id="e503a-187">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-187">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-188">1</span><span class="sxs-lookup"><span data-stu-id="e503a-188">1</span></span>|  
|<span data-ttu-id="e503a-189">2</span><span class="sxs-lookup"><span data-stu-id="e503a-189">2</span></span>|  
|<span data-ttu-id="e503a-190">3</span><span class="sxs-lookup"><span data-stu-id="e503a-190">3</span></span>|  
|<span data-ttu-id="e503a-191">...</span><span class="sxs-lookup"><span data-stu-id="e503a-191">...</span></span>|  
  
 <span data-ttu-id="e503a-192">W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) do dostępu do właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="e503a-192">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="e503a-193">Gdy używany jest operator wyodrębniania właściwości, odwołanie jest automatycznie wyłuskiwany.</span><span class="sxs-lookup"><span data-stu-id="e503a-193">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="e503a-194">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-194">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e503a-195">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-195">Output:</span></span>  
  
|<span data-ttu-id="e503a-196">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-196">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-197">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e503a-197">Adjustable Race</span></span>|  
|<span data-ttu-id="e503a-198">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e503a-198">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e503a-199">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e503a-199">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e503a-200">...</span><span class="sxs-lookup"><span data-stu-id="e503a-200">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="e503a-201">DEREF</span><span class="sxs-lookup"><span data-stu-id="e503a-201">DEREF</span></span>  
 <span data-ttu-id="e503a-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) wyłuskań wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e503a-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="e503a-203">Na przykład, następujące zapytanie generuje jednostki zamówienia dla każdego zamówienia w zestawie jednostek zamówienia: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="e503a-203">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="e503a-204">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-204">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e503a-205">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-205">Output:</span></span>  
  
|<span data-ttu-id="e503a-206">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-206">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-207">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e503a-207">Adjustable Race</span></span>|  
|<span data-ttu-id="e503a-208">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e503a-208">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e503a-209">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e503a-209">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e503a-210">...</span><span class="sxs-lookup"><span data-stu-id="e503a-210">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="e503a-211">CREATEREF I KLUCZ</span><span class="sxs-lookup"><span data-stu-id="e503a-211">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="e503a-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) tworzy odwołanie przekazywania klucza.</span><span class="sxs-lookup"><span data-stu-id="e503a-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="e503a-213">[KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) wyodrębnia część klucza wyrażeniu zawierającym odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="e503a-213">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="e503a-214">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-214">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e503a-215">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-215">Output:</span></span>  
  
|<span data-ttu-id="e503a-216">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e503a-216">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="e503a-217">980</span><span class="sxs-lookup"><span data-stu-id="e503a-217">980</span></span>|  
|<span data-ttu-id="e503a-218">365</span><span class="sxs-lookup"><span data-stu-id="e503a-218">365</span></span>|  
|<span data-ttu-id="e503a-219">771</span><span class="sxs-lookup"><span data-stu-id="e503a-219">771</span></span>|  
|<span data-ttu-id="e503a-220">...</span><span class="sxs-lookup"><span data-stu-id="e503a-220">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="e503a-221">Funkcje</span><span class="sxs-lookup"><span data-stu-id="e503a-221">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="e503a-222">Canonical</span><span class="sxs-lookup"><span data-stu-id="e503a-222">Canonical</span></span>  
 <span data-ttu-id="e503a-223">Przestrzeń nazw dla [funkcje canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) jest Edm, podobnie jak w `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="e503a-223">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="e503a-224">Nie masz Określ obszar nazw, chyba że innej przestrzeni nazw jest importowany zawierającego funkcję z taką samą nazwę jak kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e503a-224">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="e503a-225">Jeśli dwie przestrzenie nazw mają taką samą funkcję, użytkownik musi określonych imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="e503a-225">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="e503a-226">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-226">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="e503a-227">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-227">Output:</span></span>  
  
|<span data-ttu-id="e503a-228">NameLen</span><span class="sxs-lookup"><span data-stu-id="e503a-228">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="e503a-229">6</span><span class="sxs-lookup"><span data-stu-id="e503a-229">6</span></span>|  
|<span data-ttu-id="e503a-230">6</span><span class="sxs-lookup"><span data-stu-id="e503a-230">6</span></span>|  
|<span data-ttu-id="e503a-231">5</span><span class="sxs-lookup"><span data-stu-id="e503a-231">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="e503a-232">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="e503a-232">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="e503a-233">[Funkcje właściwe dla dostawcy Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) znajdują się w `SqlServer` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e503a-233">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="e503a-234">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-234">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="e503a-235">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-235">Output:</span></span>  
  
|<span data-ttu-id="e503a-236">EmailLen</span><span class="sxs-lookup"><span data-stu-id="e503a-236">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="e503a-237">27</span><span class="sxs-lookup"><span data-stu-id="e503a-237">27</span></span>|  
|<span data-ttu-id="e503a-238">27</span><span class="sxs-lookup"><span data-stu-id="e503a-238">27</span></span>|  
|<span data-ttu-id="e503a-239">26</span><span class="sxs-lookup"><span data-stu-id="e503a-239">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="e503a-240">Namespaces</span><span class="sxs-lookup"><span data-stu-id="e503a-240">Namespaces</span></span>  
 <span data-ttu-id="e503a-241">[Za pomocą](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Określa przestrzeń nazw używaną w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="e503a-241">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="e503a-242">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-242">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="e503a-243">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-243">Output:</span></span>  
  
|<span data-ttu-id="e503a-244">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-244">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-245">aa</span><span class="sxs-lookup"><span data-stu-id="e503a-245">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="e503a-246">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="e503a-246">Paging</span></span>  
 <span data-ttu-id="e503a-247">Stronicowania może być wyrażona przez zadeklarowanie [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul do [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e503a-247">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="e503a-248">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-248">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="e503a-249">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-249">Output:</span></span>  
  
|<span data-ttu-id="e503a-250">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e503a-250">ID</span></span>|<span data-ttu-id="e503a-251">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e503a-251">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="e503a-252">10</span><span class="sxs-lookup"><span data-stu-id="e503a-252">10</span></span>|<span data-ttu-id="e503a-253">Adina</span><span class="sxs-lookup"><span data-stu-id="e503a-253">Adina</span></span>|  
|<span data-ttu-id="e503a-254">11</span><span class="sxs-lookup"><span data-stu-id="e503a-254">11</span></span>|<span data-ttu-id="e503a-255">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="e503a-255">Agcaoili</span></span>|  
|<span data-ttu-id="e503a-256">12</span><span class="sxs-lookup"><span data-stu-id="e503a-256">12</span></span>|<span data-ttu-id="e503a-257">Aguilar</span><span class="sxs-lookup"><span data-stu-id="e503a-257">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="e503a-258">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="e503a-258">Grouping</span></span>  
 <span data-ttu-id="e503a-259">[Grupowanie według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) określa grupy, do których obiektów zwróconych przez zapytanie ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) wyrażenie, które mają być umieszczone.</span><span class="sxs-lookup"><span data-stu-id="e503a-259">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="e503a-260">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-260">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="e503a-261">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-261">Output:</span></span>  
  
|<span data-ttu-id="e503a-262">nazwa</span><span class="sxs-lookup"><span data-stu-id="e503a-262">name</span></span>|  
|----------|  
|<span data-ttu-id="e503a-263">LL górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="e503a-263">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e503a-264">Uczenie Maszynowe górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="e503a-264">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e503a-265">Rama górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="e503a-265">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e503a-266">...</span><span class="sxs-lookup"><span data-stu-id="e503a-266">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="e503a-267">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="e503a-267">Navigation</span></span>  
 <span data-ttu-id="e503a-268">Operator nawigacji relacji można przejść przez relacji z jednej jednostki (od końca) do innego (w celu zakończenia).</span><span class="sxs-lookup"><span data-stu-id="e503a-268">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="e503a-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) przyjmuje odpowiednio wykwalifikowany typ relacji \<przestrzeni nazw >.\< Nazwa typu relacji >.</span><span class="sxs-lookup"><span data-stu-id="e503a-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="e503a-270">Przejdź zwraca Ref\<T > Jeśli kardynalność do końca jest 1.</span><span class="sxs-lookup"><span data-stu-id="e503a-270">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="e503a-271">Jeśli kardynalność do końca jest n, kolekcji < Ref\<T >> zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e503a-271">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="e503a-272">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-272">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="e503a-273">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-273">Output:</span></span>  
  
|<span data-ttu-id="e503a-274">AddressID</span><span class="sxs-lookup"><span data-stu-id="e503a-274">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="e503a-275">1</span><span class="sxs-lookup"><span data-stu-id="e503a-275">1</span></span>|  
|<span data-ttu-id="e503a-276">2</span><span class="sxs-lookup"><span data-stu-id="e503a-276">2</span></span>|  
|<span data-ttu-id="e503a-277">3</span><span class="sxs-lookup"><span data-stu-id="e503a-277">3</span></span>|  
|<span data-ttu-id="e503a-278">...</span><span class="sxs-lookup"><span data-stu-id="e503a-278">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="e503a-279">WYBIERZ WARTOŚĆ I WYBIERZ POZYCJĘ</span><span class="sxs-lookup"><span data-stu-id="e503a-279">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="e503a-280">WYBIERZ WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e503a-280">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e503a-281">udostępnia klauzula SELECT VALUE, aby pominąć konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="e503a-281">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="e503a-282">Można określić tylko jeden element w klauzuli SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="e503a-282">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="e503a-283">Takie klauzula jest używana, nie otoki wiersza jest konstruowany wokół elementów w klauzuli SELECT, gdy kolekcja żądany kształt może wygenerować, na przykład: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="e503a-283">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="e503a-284">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-284">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="e503a-285">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-285">Output:</span></span>  
  
|<span data-ttu-id="e503a-286">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e503a-286">Name</span></span>|  
|----------|  
|<span data-ttu-id="e503a-287">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e503a-287">Adjustable Race</span></span>|  
|<span data-ttu-id="e503a-288">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e503a-288">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e503a-289">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e503a-289">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e503a-290">...</span><span class="sxs-lookup"><span data-stu-id="e503a-290">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="e503a-291">SELECT</span><span class="sxs-lookup"><span data-stu-id="e503a-291">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e503a-292">zapewnia także Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="e503a-292">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="e503a-293">Wybierz przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych z polami, na przykład: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="e503a-293">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="e503a-294">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-294">Example:</span></span>  
  
 <span data-ttu-id="e503a-295">Wybierz p.Name, p.ProductID z AdventureWorksEntities.Product jako dane wyjściowe p:</span><span class="sxs-lookup"><span data-stu-id="e503a-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="e503a-296">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e503a-296">Name</span></span>|<span data-ttu-id="e503a-297">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="e503a-297">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="e503a-298">Wyścig zmienianych</span><span class="sxs-lookup"><span data-stu-id="e503a-298">Adjustable Race</span></span>|<span data-ttu-id="e503a-299">1</span><span class="sxs-lookup"><span data-stu-id="e503a-299">1</span></span>|  
|<span data-ttu-id="e503a-300">Uniwersalny roweru autonomicznej</span><span class="sxs-lookup"><span data-stu-id="e503a-300">All-Purpose Bike Stand</span></span>|<span data-ttu-id="e503a-301">879</span><span class="sxs-lookup"><span data-stu-id="e503a-301">879</span></span>|  
|<span data-ttu-id="e503a-302">Czapka z Logo AWC</span><span class="sxs-lookup"><span data-stu-id="e503a-302">AWC Logo Cap</span></span>|<span data-ttu-id="e503a-303">712</span><span class="sxs-lookup"><span data-stu-id="e503a-303">712</span></span>|  
|<span data-ttu-id="e503a-304">...</span><span class="sxs-lookup"><span data-stu-id="e503a-304">...</span></span>|<span data-ttu-id="e503a-305">...</span><span class="sxs-lookup"><span data-stu-id="e503a-305">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="e503a-306">WYRAŻENIE CASE</span><span class="sxs-lookup"><span data-stu-id="e503a-306">CASE EXPRESSION</span></span>  
 <span data-ttu-id="e503a-307">[Zamierzone, Zapisz wyrażenie](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) obliczenie zestawu wyrażeń logicznych w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="e503a-307">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="e503a-308">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e503a-308">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="e503a-309">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e503a-309">Output:</span></span>  
  
|<span data-ttu-id="e503a-310">Wartość</span><span class="sxs-lookup"><span data-stu-id="e503a-310">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e503a-311">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="e503a-311">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e503a-312">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e503a-312">See also</span></span>

- [<span data-ttu-id="e503a-313">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e503a-313">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e503a-314">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e503a-314">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
