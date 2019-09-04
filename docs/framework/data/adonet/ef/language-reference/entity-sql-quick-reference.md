---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251028"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="97502-102">Szybkie odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="97502-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="97502-103">Ten temat zawiera krótkie informacje o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="97502-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="97502-104">Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="97502-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="97502-105">Literały</span><span class="sxs-lookup"><span data-stu-id="97502-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="97502-106">String</span><span class="sxs-lookup"><span data-stu-id="97502-106">String</span></span>  
 <span data-ttu-id="97502-107">Istnieją literały ciągu Unicode i inne niż Unicode.</span><span class="sxs-lookup"><span data-stu-id="97502-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="97502-108">Ciągi Unicode są poprzedzone znakiem N. Na przykład `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="97502-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="97502-109">Poniżej znajduje się przykład literału ciągu innego niż Unicode:</span><span class="sxs-lookup"><span data-stu-id="97502-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="97502-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-110">Output:</span></span>  
  
|<span data-ttu-id="97502-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-112">Cześć</span><span class="sxs-lookup"><span data-stu-id="97502-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="97502-113">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="97502-113">DateTime</span></span>  
 <span data-ttu-id="97502-114">W literałach DateTime oba części daty i godziny są obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="97502-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="97502-115">Brak wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="97502-115">There are no default values.</span></span>  
  
 <span data-ttu-id="97502-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="97502-117">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-117">Output:</span></span>  
  
|<span data-ttu-id="97502-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="97502-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="97502-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="97502-120">Integer</span></span>  
 <span data-ttu-id="97502-121">Literały całkowite mogą być typu Int32 (123), UInt32 (123U), Int64 (123L) i UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="97502-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="97502-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="97502-123">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-123">Output:</span></span>  
  
|<span data-ttu-id="97502-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-125">1</span><span class="sxs-lookup"><span data-stu-id="97502-125">1</span></span>|  
|<span data-ttu-id="97502-126">2</span><span class="sxs-lookup"><span data-stu-id="97502-126">2</span></span>|  
|<span data-ttu-id="97502-127">3</span><span class="sxs-lookup"><span data-stu-id="97502-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="97502-128">Inne</span><span class="sxs-lookup"><span data-stu-id="97502-128">Other</span></span>  
 <span data-ttu-id="97502-129">Inne literały obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] program to GUID, Binary, float/Double, Decimal i `null`.</span><span class="sxs-lookup"><span data-stu-id="97502-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="97502-130">Literały o wartości [!INCLUDE[esql](../../../../../../includes/esql-md.md)] null w są uważane za zgodne z każdym innym typem w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="97502-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="97502-131">Konstruktory typów</span><span class="sxs-lookup"><span data-stu-id="97502-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="97502-132">ROW</span><span class="sxs-lookup"><span data-stu-id="97502-132">ROW</span></span>  
 <span data-ttu-id="97502-133">[Wiersz](row-entity-sql.md) konstruuje anonimową, strukturalnie wpisaną wartość w postaci:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="97502-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="97502-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="97502-135">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-135">Output:</span></span>  
  
|<span data-ttu-id="97502-136">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="97502-136">ProductID</span></span>|<span data-ttu-id="97502-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="97502-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="97502-138">1</span><span class="sxs-lookup"><span data-stu-id="97502-138">1</span></span>|<span data-ttu-id="97502-139">Wyścigi regulowane</span><span class="sxs-lookup"><span data-stu-id="97502-139">Adjustable Race</span></span>|  
|<span data-ttu-id="97502-140">879</span><span class="sxs-lookup"><span data-stu-id="97502-140">879</span></span>|<span data-ttu-id="97502-141">Podstawa roweru ogólnego przeznaczenia</span><span class="sxs-lookup"><span data-stu-id="97502-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="97502-142">712</span><span class="sxs-lookup"><span data-stu-id="97502-142">712</span></span>|<span data-ttu-id="97502-143">AWC logo</span><span class="sxs-lookup"><span data-stu-id="97502-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="97502-144">...</span><span class="sxs-lookup"><span data-stu-id="97502-144">...</span></span>|<span data-ttu-id="97502-145">...</span><span class="sxs-lookup"><span data-stu-id="97502-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="97502-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="97502-146">MULTISET</span></span>  
 <span data-ttu-id="97502-147">Kolekcje [zestawów wielokrotnych](multiset-entity-sql.md) , takie jak:</span><span class="sxs-lookup"><span data-stu-id="97502-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="97502-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="97502-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="97502-149">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="97502-150">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-150">Output:</span></span>  
  
|<span data-ttu-id="97502-151">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="97502-151">ProductID</span></span>|<span data-ttu-id="97502-152">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="97502-152">Name</span></span>|<span data-ttu-id="97502-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="97502-153">ProductNumber</span></span>|<span data-ttu-id="97502-154">…</span><span class="sxs-lookup"><span data-stu-id="97502-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="97502-155">842</span><span class="sxs-lookup"><span data-stu-id="97502-155">842</span></span>|<span data-ttu-id="97502-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="97502-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="97502-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="97502-157">PA-T100</span></span>|<span data-ttu-id="97502-158">…</span><span class="sxs-lookup"><span data-stu-id="97502-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="97502-159">Obiekt</span><span class="sxs-lookup"><span data-stu-id="97502-159">Object</span></span>  
 <span data-ttu-id="97502-160">Konstrukcje [konstruktorów nazwanych](named-type-constructor-entity-sql.md) (o nazwach) obiekty zdefiniowane przez użytkownika `person("abc", 12)`, takie jak.</span><span class="sxs-lookup"><span data-stu-id="97502-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="97502-161">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="97502-162">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-162">Output:</span></span>  
  
|<span data-ttu-id="97502-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="97502-163">SalesOrderDetailID</span></span>|<span data-ttu-id="97502-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="97502-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="97502-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="97502-165">OrderQty</span></span>|<span data-ttu-id="97502-166">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="97502-166">ProductID</span></span>|<span data-ttu-id="97502-167">...</span><span class="sxs-lookup"><span data-stu-id="97502-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="97502-168">1</span><span class="sxs-lookup"><span data-stu-id="97502-168">1</span></span>|<span data-ttu-id="97502-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="97502-169">4911-403C-98</span></span>|<span data-ttu-id="97502-170">1</span><span class="sxs-lookup"><span data-stu-id="97502-170">1</span></span>|<span data-ttu-id="97502-171">776</span><span class="sxs-lookup"><span data-stu-id="97502-171">776</span></span>|<span data-ttu-id="97502-172">...</span><span class="sxs-lookup"><span data-stu-id="97502-172">...</span></span>|  
|<span data-ttu-id="97502-173">2</span><span class="sxs-lookup"><span data-stu-id="97502-173">2</span></span>|<span data-ttu-id="97502-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="97502-174">4911-403C-98</span></span>|<span data-ttu-id="97502-175">3</span><span class="sxs-lookup"><span data-stu-id="97502-175">3</span></span>|<span data-ttu-id="97502-176">777</span><span class="sxs-lookup"><span data-stu-id="97502-176">777</span></span>|<span data-ttu-id="97502-177">...</span><span class="sxs-lookup"><span data-stu-id="97502-177">...</span></span>|  
|<span data-ttu-id="97502-178">...</span><span class="sxs-lookup"><span data-stu-id="97502-178">...</span></span>|<span data-ttu-id="97502-179">...</span><span class="sxs-lookup"><span data-stu-id="97502-179">...</span></span>|<span data-ttu-id="97502-180">...</span><span class="sxs-lookup"><span data-stu-id="97502-180">...</span></span>|<span data-ttu-id="97502-181">...</span><span class="sxs-lookup"><span data-stu-id="97502-181">...</span></span>|<span data-ttu-id="97502-182">...</span><span class="sxs-lookup"><span data-stu-id="97502-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="97502-183">Odwołania</span><span class="sxs-lookup"><span data-stu-id="97502-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="97502-184">REF</span><span class="sxs-lookup"><span data-stu-id="97502-184">REF</span></span>  
 <span data-ttu-id="97502-185">[Ref](ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="97502-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="97502-186">Na przykład następujące zapytanie zwraca odwołania do każdej jednostki zamówienia w zestawie jednostek Orders:</span><span class="sxs-lookup"><span data-stu-id="97502-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="97502-187">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-187">Output:</span></span>  
  
|<span data-ttu-id="97502-188">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-189">1</span><span class="sxs-lookup"><span data-stu-id="97502-189">1</span></span>|  
|<span data-ttu-id="97502-190">2</span><span class="sxs-lookup"><span data-stu-id="97502-190">2</span></span>|  
|<span data-ttu-id="97502-191">3</span><span class="sxs-lookup"><span data-stu-id="97502-191">3</span></span>|  
|<span data-ttu-id="97502-192">...</span><span class="sxs-lookup"><span data-stu-id="97502-192">...</span></span>|  
  
 <span data-ttu-id="97502-193">Poniższy przykład używa operatora wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="97502-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="97502-194">Gdy jest używany operator wyodrębniania właściwości, odwołanie jest automatycznie wywoływać.</span><span class="sxs-lookup"><span data-stu-id="97502-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="97502-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="97502-196">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-196">Output:</span></span>  
  
|<span data-ttu-id="97502-197">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-198">Wyścigi regulowane</span><span class="sxs-lookup"><span data-stu-id="97502-198">Adjustable Race</span></span>|  
|<span data-ttu-id="97502-199">Podstawa roweru ogólnego przeznaczenia</span><span class="sxs-lookup"><span data-stu-id="97502-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="97502-200">AWC logo</span><span class="sxs-lookup"><span data-stu-id="97502-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="97502-201">...</span><span class="sxs-lookup"><span data-stu-id="97502-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="97502-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="97502-202">DEREF</span></span>  
 <span data-ttu-id="97502-203">[DEREF](deref-entity-sql.md) odwołuje się do wartości odniesienia i tworzy wynik tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="97502-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="97502-204">Na przykład następujące zapytanie tworzy jednostki Order dla każdego zamówienia w zestawie jednostek Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span><span class="sxs-lookup"><span data-stu-id="97502-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="97502-205">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="97502-206">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-206">Output:</span></span>  
  
|<span data-ttu-id="97502-207">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-208">Wyścigi regulowane</span><span class="sxs-lookup"><span data-stu-id="97502-208">Adjustable Race</span></span>|  
|<span data-ttu-id="97502-209">Podstawa roweru ogólnego przeznaczenia</span><span class="sxs-lookup"><span data-stu-id="97502-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="97502-210">AWC logo</span><span class="sxs-lookup"><span data-stu-id="97502-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="97502-211">...</span><span class="sxs-lookup"><span data-stu-id="97502-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="97502-212">CREATEREF I KLUCZ</span><span class="sxs-lookup"><span data-stu-id="97502-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="97502-213">[CreateRef](createref-entity-sql.md) tworzy odwołanie z przekazywaniem klucza.</span><span class="sxs-lookup"><span data-stu-id="97502-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="97502-214">[Klucz](key-entity-sql.md) wyodrębnia część klucza wyrażenia z odwołaniem do typu.</span><span class="sxs-lookup"><span data-stu-id="97502-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="97502-215">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="97502-216">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-216">Output:</span></span>  
  
|<span data-ttu-id="97502-217">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="97502-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="97502-218">980</span><span class="sxs-lookup"><span data-stu-id="97502-218">980</span></span>|  
|<span data-ttu-id="97502-219">365</span><span class="sxs-lookup"><span data-stu-id="97502-219">365</span></span>|  
|<span data-ttu-id="97502-220">771</span><span class="sxs-lookup"><span data-stu-id="97502-220">771</span></span>|  
|<span data-ttu-id="97502-221">...</span><span class="sxs-lookup"><span data-stu-id="97502-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="97502-222">Funkcje</span><span class="sxs-lookup"><span data-stu-id="97502-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="97502-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="97502-223">Canonical</span></span>  
 <span data-ttu-id="97502-224">Przestrzeń nazw dla [funkcji kanonicznych](canonical-functions.md) to EDM, jak `Edm.Length("string")`w.</span><span class="sxs-lookup"><span data-stu-id="97502-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="97502-225">Nie trzeba określać przestrzeni nazw, chyba że zostanie zaimportowana inna przestrzeń nazw, która zawiera funkcję o takiej samej nazwie jak funkcja kanoniczna.</span><span class="sxs-lookup"><span data-stu-id="97502-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="97502-226">Jeśli dwie przestrzenie nazw mają tę samą funkcję, użytkownik powinien mieć określoną pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="97502-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="97502-227">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="97502-228">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-228">Output:</span></span>  
  
|<span data-ttu-id="97502-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="97502-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="97502-230">6</span><span class="sxs-lookup"><span data-stu-id="97502-230">6</span></span>|  
|<span data-ttu-id="97502-231">6</span><span class="sxs-lookup"><span data-stu-id="97502-231">6</span></span>|  
|<span data-ttu-id="97502-232">5</span><span class="sxs-lookup"><span data-stu-id="97502-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="97502-233">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="97502-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="97502-234">[Funkcje specyficzne dla dostawcy firmy Microsoft](../sqlclient-for-ef-functions.md) znajdują `SqlServer` się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="97502-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="97502-235">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="97502-236">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-236">Output:</span></span>  
  
|<span data-ttu-id="97502-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="97502-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="97502-238">27</span><span class="sxs-lookup"><span data-stu-id="97502-238">27</span></span>|  
|<span data-ttu-id="97502-239">27</span><span class="sxs-lookup"><span data-stu-id="97502-239">27</span></span>|  
|<span data-ttu-id="97502-240">26</span><span class="sxs-lookup"><span data-stu-id="97502-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="97502-241">Namespaces</span><span class="sxs-lookup"><span data-stu-id="97502-241">Namespaces</span></span>  
 <span data-ttu-id="97502-242">[Użycie](using-entity-sql.md) określa przestrzenie nazw używane w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="97502-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="97502-243">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="97502-244">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-244">Output:</span></span>  
  
|<span data-ttu-id="97502-245">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-246">aa</span><span class="sxs-lookup"><span data-stu-id="97502-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="97502-247">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="97502-247">Paging</span></span>  
 <span data-ttu-id="97502-248">Stronicowanie może być wyrażone za pomocą deklaracji podrzędnych klauzul [Skip](skip-entity-sql.md) i [Limit](limit-entity-sql.md) do klauzuli [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="97502-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="97502-249">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="97502-250">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-250">Output:</span></span>  
  
|<span data-ttu-id="97502-251">id</span><span class="sxs-lookup"><span data-stu-id="97502-251">ID</span></span>|<span data-ttu-id="97502-252">Nazwa</span><span class="sxs-lookup"><span data-stu-id="97502-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="97502-253">10</span><span class="sxs-lookup"><span data-stu-id="97502-253">10</span></span>|<span data-ttu-id="97502-254">Adina</span><span class="sxs-lookup"><span data-stu-id="97502-254">Adina</span></span>|  
|<span data-ttu-id="97502-255">11</span><span class="sxs-lookup"><span data-stu-id="97502-255">11</span></span>|<span data-ttu-id="97502-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="97502-256">Agcaoili</span></span>|  
|<span data-ttu-id="97502-257">12</span><span class="sxs-lookup"><span data-stu-id="97502-257">12</span></span>|<span data-ttu-id="97502-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="97502-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="97502-259">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="97502-259">Grouping</span></span>  
 <span data-ttu-id="97502-260">[Grupowanie według](group-by-entity-sql.md) określa grupy, do których obiekty zwracane przez zapytanie ([SELECT](select-entity-sql.md)) mają zostać umieszczone.</span><span class="sxs-lookup"><span data-stu-id="97502-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="97502-261">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="97502-262">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-262">Output:</span></span>  
  
|<span data-ttu-id="97502-263">nazwa</span><span class="sxs-lookup"><span data-stu-id="97502-263">name</span></span>|  
|----------|  
|<span data-ttu-id="97502-264">WSZYSTKO — zestaw stanowisk górskich</span><span class="sxs-lookup"><span data-stu-id="97502-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="97502-265">Zestaw siedzeń górskich ML</span><span class="sxs-lookup"><span data-stu-id="97502-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="97502-266">Zestaw miejsc górskich HL</span><span class="sxs-lookup"><span data-stu-id="97502-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="97502-267">...</span><span class="sxs-lookup"><span data-stu-id="97502-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="97502-268">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="97502-268">Navigation</span></span>  
 <span data-ttu-id="97502-269">Operator nawigacji relacji umożliwia nawigowanie po relacji od jednej jednostki (od końca) do innej (do końca).</span><span class="sxs-lookup"><span data-stu-id="97502-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="97502-270">[Nawigacja](navigate-entity-sql.md) przyjmuje typ relacji kwalifikowana jako \<przestrzeń nazw >.\< Nazwa typu relacji >.</span><span class="sxs-lookup"><span data-stu-id="97502-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="97502-271">Funkcja nawigacji zwraca\<wartość Ref T >, jeśli Kardynalność do końca jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="97502-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="97502-272">Jeśli Kardynalność do końca to n, zostanie zwrócona kolekcja < ref\<T > >.</span><span class="sxs-lookup"><span data-stu-id="97502-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="97502-273">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="97502-274">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-274">Output:</span></span>  
  
|<span data-ttu-id="97502-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="97502-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="97502-276">1</span><span class="sxs-lookup"><span data-stu-id="97502-276">1</span></span>|  
|<span data-ttu-id="97502-277">2</span><span class="sxs-lookup"><span data-stu-id="97502-277">2</span></span>|  
|<span data-ttu-id="97502-278">3</span><span class="sxs-lookup"><span data-stu-id="97502-278">3</span></span>|  
|<span data-ttu-id="97502-279">...</span><span class="sxs-lookup"><span data-stu-id="97502-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="97502-280">WYBIERZ POZYCJĘ WARTOŚĆ I WYBIERZ POZYCJĘ</span><span class="sxs-lookup"><span data-stu-id="97502-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="97502-281">WYBIERZ WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="97502-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="97502-282">udostępnia klauzulę SELECT VALUE, aby pominąć konstruowanie niejawnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="97502-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="97502-283">W klauzuli SELECT VALUE można określić tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="97502-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="97502-284">Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w klauzuli SELECT i można utworzyć kolekcję żądanego kształtu, na przykład: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="97502-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="97502-285">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="97502-286">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-286">Output:</span></span>  
  
|<span data-ttu-id="97502-287">Nazwa</span><span class="sxs-lookup"><span data-stu-id="97502-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="97502-288">Wyścigi regulowane</span><span class="sxs-lookup"><span data-stu-id="97502-288">Adjustable Race</span></span>|  
|<span data-ttu-id="97502-289">Podstawa roweru ogólnego przeznaczenia</span><span class="sxs-lookup"><span data-stu-id="97502-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="97502-290">AWC logo</span><span class="sxs-lookup"><span data-stu-id="97502-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="97502-291">...</span><span class="sxs-lookup"><span data-stu-id="97502-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="97502-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="97502-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="97502-293">udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="97502-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="97502-294">Zaznacz powoduje, że co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami, na `SELECT a, b, c`przykład:.</span><span class="sxs-lookup"><span data-stu-id="97502-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="97502-295">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-295">Example:</span></span>  
  
 <span data-ttu-id="97502-296">Wybierz pozycję p.Name, p. ProductID z AdventureWorksEntities. Product jako p Output:</span><span class="sxs-lookup"><span data-stu-id="97502-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="97502-297">Nazwa</span><span class="sxs-lookup"><span data-stu-id="97502-297">Name</span></span>|<span data-ttu-id="97502-298">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="97502-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="97502-299">Wyścigi regulowane</span><span class="sxs-lookup"><span data-stu-id="97502-299">Adjustable Race</span></span>|<span data-ttu-id="97502-300">1</span><span class="sxs-lookup"><span data-stu-id="97502-300">1</span></span>|  
|<span data-ttu-id="97502-301">Podstawa roweru ogólnego przeznaczenia</span><span class="sxs-lookup"><span data-stu-id="97502-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="97502-302">879</span><span class="sxs-lookup"><span data-stu-id="97502-302">879</span></span>|  
|<span data-ttu-id="97502-303">AWC logo</span><span class="sxs-lookup"><span data-stu-id="97502-303">AWC Logo Cap</span></span>|<span data-ttu-id="97502-304">712</span><span class="sxs-lookup"><span data-stu-id="97502-304">712</span></span>|  
|<span data-ttu-id="97502-305">...</span><span class="sxs-lookup"><span data-stu-id="97502-305">...</span></span>|<span data-ttu-id="97502-306">...</span><span class="sxs-lookup"><span data-stu-id="97502-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="97502-307">WYRAŻENIE CASE</span><span class="sxs-lookup"><span data-stu-id="97502-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="97502-308">[Wyrażenie CASE](case-entity-sql.md) oblicza zestaw wyrażeń logicznych, aby określić wynik.</span><span class="sxs-lookup"><span data-stu-id="97502-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="97502-309">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97502-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="97502-310">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97502-310">Output:</span></span>  
  
|<span data-ttu-id="97502-311">Wartość</span><span class="sxs-lookup"><span data-stu-id="97502-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="97502-312">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="97502-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97502-313">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97502-313">See also</span></span>

- [<span data-ttu-id="97502-314">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="97502-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="97502-315">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="97502-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
