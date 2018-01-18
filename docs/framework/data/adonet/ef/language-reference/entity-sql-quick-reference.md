---
title: "Szybkie odwołanie do jednostki SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 81fd76d09f9cc02e89ac34d5f8fa74bd7f9d92f9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="07b70-102">Szybkie odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="07b70-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="07b70-103">Ten temat zawiera krótkie odwołanie do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="07b70-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="07b70-104">Zapytania w tym temacie są oparte na modelu AdventureWorks sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="07b70-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="07b70-105">Literały</span><span class="sxs-lookup"><span data-stu-id="07b70-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="07b70-106">String</span><span class="sxs-lookup"><span data-stu-id="07b70-106">String</span></span>  
 <span data-ttu-id="07b70-107">Brak literałów ciągów znaków Unicode i z systemem innym niż Unicode.</span><span class="sxs-lookup"><span data-stu-id="07b70-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="07b70-108">Ciągi Unicode są poprzedzony przez N. Na przykład `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="07b70-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="07b70-109">Poniżej przedstawiono przykład literału ciągu Non-Unicode:</span><span class="sxs-lookup"><span data-stu-id="07b70-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="07b70-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-110">Output:</span></span>  
  
|<span data-ttu-id="07b70-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-112">Cześć</span><span class="sxs-lookup"><span data-stu-id="07b70-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="07b70-113">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="07b70-113">DateTime</span></span>  
 <span data-ttu-id="07b70-114">W literałach DateTime części zarówno data i godzina są obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="07b70-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="07b70-115">Brak wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="07b70-115">There are no default values.</span></span>  
  
 <span data-ttu-id="07b70-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="07b70-117">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-117">Output:</span></span>  
  
|<span data-ttu-id="07b70-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-119">12/25/2006 1:01:00: 00</span><span class="sxs-lookup"><span data-stu-id="07b70-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="07b70-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="07b70-120">Integer</span></span>  
 <span data-ttu-id="07b70-121">Literały całkowite może być typu Int32 (123) UInt32 (123U), Int64 (123L) i UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="07b70-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="07b70-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="07b70-123">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-123">Output:</span></span>  
  
|<span data-ttu-id="07b70-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-125">1</span><span class="sxs-lookup"><span data-stu-id="07b70-125">1</span></span>|  
|<span data-ttu-id="07b70-126">2</span><span class="sxs-lookup"><span data-stu-id="07b70-126">2</span></span>|  
|<span data-ttu-id="07b70-127">3</span><span class="sxs-lookup"><span data-stu-id="07b70-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="07b70-128">Inne</span><span class="sxs-lookup"><span data-stu-id="07b70-128">Other</span></span>  
 <span data-ttu-id="07b70-129">Inne literały obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są identyfikatora Guid, Binary, Float/Double, Decimal, i `null`.</span><span class="sxs-lookup"><span data-stu-id="07b70-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="07b70-130">Pusty literał w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodny z każdym innym typem w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="07b70-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="07b70-131">Konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="07b70-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="07b70-132">WIERSZ</span><span class="sxs-lookup"><span data-stu-id="07b70-132">ROW</span></span>  
 <span data-ttu-id="07b70-133">[WIERSZ](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) tworzy anonimowe, strukturę wpisane wartości (rekordów) jak w:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="07b70-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="07b70-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="07b70-135">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-135">Output:</span></span>  
  
|<span data-ttu-id="07b70-136">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="07b70-136">ProductID</span></span>|<span data-ttu-id="07b70-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07b70-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="07b70-138">1</span><span class="sxs-lookup"><span data-stu-id="07b70-138">1</span></span>|<span data-ttu-id="07b70-139">Regulowany wyścigu</span><span class="sxs-lookup"><span data-stu-id="07b70-139">Adjustable Race</span></span>|  
|<span data-ttu-id="07b70-140">879</span><span class="sxs-lookup"><span data-stu-id="07b70-140">879</span></span>|<span data-ttu-id="07b70-141">Uniwersalny roweru wstrzymania</span><span class="sxs-lookup"><span data-stu-id="07b70-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="07b70-142">712</span><span class="sxs-lookup"><span data-stu-id="07b70-142">712</span></span>|<span data-ttu-id="07b70-143">Logo AWC centralnych zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="07b70-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="07b70-144">...</span><span class="sxs-lookup"><span data-stu-id="07b70-144">...</span></span>|<span data-ttu-id="07b70-145">...</span><span class="sxs-lookup"><span data-stu-id="07b70-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="07b70-146">ZESTAW WIELOKROTNY</span><span class="sxs-lookup"><span data-stu-id="07b70-146">MULTISET</span></span>  
 <span data-ttu-id="07b70-147">[Zestaw WIELOKROTNY](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) tworzy kolekcje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="07b70-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="07b70-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="07b70-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="07b70-149">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="07b70-150">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-150">Output:</span></span>  
  
|<span data-ttu-id="07b70-151">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="07b70-151">ProductID</span></span>|<span data-ttu-id="07b70-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07b70-152">Name</span></span>|<span data-ttu-id="07b70-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="07b70-153">ProductNumber</span></span>|<span data-ttu-id="07b70-154">…</span><span class="sxs-lookup"><span data-stu-id="07b70-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="07b70-155">842</span><span class="sxs-lookup"><span data-stu-id="07b70-155">842</span></span>|<span data-ttu-id="07b70-156">Sakwy turystyczne, duże</span><span class="sxs-lookup"><span data-stu-id="07b70-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="07b70-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="07b70-157">PA-T100</span></span>|<span data-ttu-id="07b70-158">…</span><span class="sxs-lookup"><span data-stu-id="07b70-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="07b70-159">Obiekt</span><span class="sxs-lookup"><span data-stu-id="07b70-159">Object</span></span>  
 <span data-ttu-id="07b70-160">[O nazwie konstruktora typu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) tworzy (nazwane) obiekty zdefiniowane przez użytkownika, takie jak `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="07b70-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="07b70-161">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="07b70-162">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-162">Output:</span></span>  
  
|<span data-ttu-id="07b70-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="07b70-163">SalesOrderDetailID</span></span>|<span data-ttu-id="07b70-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="07b70-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="07b70-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="07b70-165">OrderQty</span></span>|<span data-ttu-id="07b70-166">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="07b70-166">ProductID</span></span>|<span data-ttu-id="07b70-167">...</span><span class="sxs-lookup"><span data-stu-id="07b70-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="07b70-168">1</span><span class="sxs-lookup"><span data-stu-id="07b70-168">1</span></span>|<span data-ttu-id="07b70-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="07b70-169">4911-403C-98</span></span>|<span data-ttu-id="07b70-170">1</span><span class="sxs-lookup"><span data-stu-id="07b70-170">1</span></span>|<span data-ttu-id="07b70-171">776</span><span class="sxs-lookup"><span data-stu-id="07b70-171">776</span></span>|<span data-ttu-id="07b70-172">...</span><span class="sxs-lookup"><span data-stu-id="07b70-172">...</span></span>|  
|<span data-ttu-id="07b70-173">2</span><span class="sxs-lookup"><span data-stu-id="07b70-173">2</span></span>|<span data-ttu-id="07b70-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="07b70-174">4911-403C-98</span></span>|<span data-ttu-id="07b70-175">3</span><span class="sxs-lookup"><span data-stu-id="07b70-175">3</span></span>|<span data-ttu-id="07b70-176">777</span><span class="sxs-lookup"><span data-stu-id="07b70-176">777</span></span>|<span data-ttu-id="07b70-177">...</span><span class="sxs-lookup"><span data-stu-id="07b70-177">...</span></span>|  
|<span data-ttu-id="07b70-178">...</span><span class="sxs-lookup"><span data-stu-id="07b70-178">...</span></span>|<span data-ttu-id="07b70-179">...</span><span class="sxs-lookup"><span data-stu-id="07b70-179">...</span></span>|<span data-ttu-id="07b70-180">...</span><span class="sxs-lookup"><span data-stu-id="07b70-180">...</span></span>|<span data-ttu-id="07b70-181">...</span><span class="sxs-lookup"><span data-stu-id="07b70-181">...</span></span>|<span data-ttu-id="07b70-182">...</span><span class="sxs-lookup"><span data-stu-id="07b70-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="07b70-183">Odwołania</span><span class="sxs-lookup"><span data-stu-id="07b70-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="07b70-184">REF</span><span class="sxs-lookup"><span data-stu-id="07b70-184">REF</span></span>  
 <span data-ttu-id="07b70-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="07b70-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="07b70-186">Na przykład następujące zapytanie zwraca odwołania do każdej jednostki kolejności w zestawie jednostek zleceń:</span><span class="sxs-lookup"><span data-stu-id="07b70-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="07b70-187">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-187">Output:</span></span>  
  
|<span data-ttu-id="07b70-188">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-189">1</span><span class="sxs-lookup"><span data-stu-id="07b70-189">1</span></span>|  
|<span data-ttu-id="07b70-190">2</span><span class="sxs-lookup"><span data-stu-id="07b70-190">2</span></span>|  
|<span data-ttu-id="07b70-191">3</span><span class="sxs-lookup"><span data-stu-id="07b70-191">3</span></span>|  
|<span data-ttu-id="07b70-192">...</span><span class="sxs-lookup"><span data-stu-id="07b70-192">...</span></span>|  
  
 <span data-ttu-id="07b70-193">W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) do dostępu do właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="07b70-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="07b70-194">Gdy jest używany operator wyodrębniania właściwości, odwołanie jest automatycznie wyłuskiwany.</span><span class="sxs-lookup"><span data-stu-id="07b70-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="07b70-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="07b70-196">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-196">Output:</span></span>  
  
|<span data-ttu-id="07b70-197">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-198">Regulowany wyścigu</span><span class="sxs-lookup"><span data-stu-id="07b70-198">Adjustable Race</span></span>|  
|<span data-ttu-id="07b70-199">Uniwersalny roweru wstrzymania</span><span class="sxs-lookup"><span data-stu-id="07b70-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="07b70-200">Logo AWC centralnych zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="07b70-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="07b70-201">...</span><span class="sxs-lookup"><span data-stu-id="07b70-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="07b70-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="07b70-202">DEREF</span></span>  
 <span data-ttu-id="07b70-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do.</span><span class="sxs-lookup"><span data-stu-id="07b70-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="07b70-204">Na przykład następujące zapytanie generuje jednostek kolejności dla każdej kolejności w zestawie jednostek zamówień: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="07b70-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="07b70-205">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="07b70-206">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-206">Output:</span></span>  
  
|<span data-ttu-id="07b70-207">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-208">Regulowany wyścigu</span><span class="sxs-lookup"><span data-stu-id="07b70-208">Adjustable Race</span></span>|  
|<span data-ttu-id="07b70-209">Uniwersalny roweru wstrzymania</span><span class="sxs-lookup"><span data-stu-id="07b70-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="07b70-210">Logo AWC centralnych zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="07b70-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="07b70-211">...</span><span class="sxs-lookup"><span data-stu-id="07b70-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="07b70-212">CREATEREF I KLUCZ</span><span class="sxs-lookup"><span data-stu-id="07b70-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="07b70-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) tworzy odwołanie przekazanie klucza.</span><span class="sxs-lookup"><span data-stu-id="07b70-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="07b70-214">[KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) wyodrębnia część klucza wyrażenie z typem odwołania.</span><span class="sxs-lookup"><span data-stu-id="07b70-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="07b70-215">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="07b70-216">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-216">Output:</span></span>  
  
|<span data-ttu-id="07b70-217">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="07b70-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="07b70-218">980</span><span class="sxs-lookup"><span data-stu-id="07b70-218">980</span></span>|  
|<span data-ttu-id="07b70-219">365</span><span class="sxs-lookup"><span data-stu-id="07b70-219">365</span></span>|  
|<span data-ttu-id="07b70-220">771</span><span class="sxs-lookup"><span data-stu-id="07b70-220">771</span></span>|  
|<span data-ttu-id="07b70-221">...</span><span class="sxs-lookup"><span data-stu-id="07b70-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="07b70-222">Funkcje</span><span class="sxs-lookup"><span data-stu-id="07b70-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="07b70-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="07b70-223">Canonical</span></span>  
 <span data-ttu-id="07b70-224">W obszarze nazw [kanonicznej funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) jest Edm, podobnie jak w `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="07b70-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="07b70-225">Nie trzeba określać przestrzeń nazw, chyba że innej przestrzeni nazw jest importowany zawierającego funkcję z taką samą nazwę jak kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="07b70-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="07b70-226">Jeśli dwie przestrzenie nazw ma taką samą funkcję, użytkownik musi określonych pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="07b70-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="07b70-227">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="07b70-228">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-228">Output:</span></span>  
  
|<span data-ttu-id="07b70-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="07b70-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="07b70-230">6</span><span class="sxs-lookup"><span data-stu-id="07b70-230">6</span></span>|  
|<span data-ttu-id="07b70-231">6</span><span class="sxs-lookup"><span data-stu-id="07b70-231">6</span></span>|  
|<span data-ttu-id="07b70-232">5</span><span class="sxs-lookup"><span data-stu-id="07b70-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="07b70-233">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="07b70-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="07b70-234">[Funkcje właściwe dla dostawcy Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) w `SqlServer` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="07b70-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="07b70-235">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="07b70-236">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-236">Output:</span></span>  
  
|<span data-ttu-id="07b70-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="07b70-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="07b70-238">27</span><span class="sxs-lookup"><span data-stu-id="07b70-238">27</span></span>|  
|<span data-ttu-id="07b70-239">27</span><span class="sxs-lookup"><span data-stu-id="07b70-239">27</span></span>|  
|<span data-ttu-id="07b70-240">26</span><span class="sxs-lookup"><span data-stu-id="07b70-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="07b70-241">Namespaces</span><span class="sxs-lookup"><span data-stu-id="07b70-241">Namespaces</span></span>  
 <span data-ttu-id="07b70-242">[Przy użyciu](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) określa obszarów nazw używanych w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="07b70-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="07b70-243">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="07b70-244">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-244">Output:</span></span>  
  
|<span data-ttu-id="07b70-245">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-246">aa</span><span class="sxs-lookup"><span data-stu-id="07b70-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="07b70-247">Stronicowania</span><span class="sxs-lookup"><span data-stu-id="07b70-247">Paging</span></span>  
 <span data-ttu-id="07b70-248">Stronicowania można wyrazić za deklarowanie [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul do [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="07b70-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="07b70-249">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="07b70-250">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-250">Output:</span></span>  
  
|<span data-ttu-id="07b70-251">ID</span><span class="sxs-lookup"><span data-stu-id="07b70-251">ID</span></span>|<span data-ttu-id="07b70-252">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07b70-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="07b70-253">10</span><span class="sxs-lookup"><span data-stu-id="07b70-253">10</span></span>|<span data-ttu-id="07b70-254">Adina</span><span class="sxs-lookup"><span data-stu-id="07b70-254">Adina</span></span>|  
|<span data-ttu-id="07b70-255">11</span><span class="sxs-lookup"><span data-stu-id="07b70-255">11</span></span>|<span data-ttu-id="07b70-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="07b70-256">Agcaoili</span></span>|  
|<span data-ttu-id="07b70-257">12</span><span class="sxs-lookup"><span data-stu-id="07b70-257">12</span></span>|<span data-ttu-id="07b70-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="07b70-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="07b70-259">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="07b70-259">Grouping</span></span>  
 <span data-ttu-id="07b70-260">[Grupowanie według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Określa grupę, do których obiektów zwróconych przez kwerendę ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) zostaną umieszczone wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="07b70-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="07b70-261">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="07b70-262">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-262">Output:</span></span>  
  
|<span data-ttu-id="07b70-263">nazwa</span><span class="sxs-lookup"><span data-stu-id="07b70-263">name</span></span>|  
|----------|  
|<span data-ttu-id="07b70-264">Wszystki górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="07b70-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="07b70-265">ML górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="07b70-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="07b70-266">HL górski stanowisko zestawu</span><span class="sxs-lookup"><span data-stu-id="07b70-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="07b70-267">...</span><span class="sxs-lookup"><span data-stu-id="07b70-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="07b70-268">Nawigacji</span><span class="sxs-lookup"><span data-stu-id="07b70-268">Navigation</span></span>  
 <span data-ttu-id="07b70-269">Operator nawigacji relacji umożliwia przejście przez relacji z jednego obiektu (od końca) do innej (Aby zakończyć).</span><span class="sxs-lookup"><span data-stu-id="07b70-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="07b70-270">[Nawigacja](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ma typ relacji kwalifikowany jako \<przestrzeń nazw >.\< Nazwa typu relacji >.</span><span class="sxs-lookup"><span data-stu-id="07b70-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="07b70-271">Przejdź zwraca Ref\<T > Jeśli kardynalność na koniec jest 1.</span><span class="sxs-lookup"><span data-stu-id="07b70-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="07b70-272">Jeśli kardynalność na koniec jest n, kolekcji < Ref\<T >> zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="07b70-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="07b70-273">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="07b70-274">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-274">Output:</span></span>  
  
|<span data-ttu-id="07b70-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="07b70-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="07b70-276">1</span><span class="sxs-lookup"><span data-stu-id="07b70-276">1</span></span>|  
|<span data-ttu-id="07b70-277">2</span><span class="sxs-lookup"><span data-stu-id="07b70-277">2</span></span>|  
|<span data-ttu-id="07b70-278">3</span><span class="sxs-lookup"><span data-stu-id="07b70-278">3</span></span>|  
|<span data-ttu-id="07b70-279">...</span><span class="sxs-lookup"><span data-stu-id="07b70-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="07b70-280">WYBIERZ WARTOŚĆ I WYBIERZ POZYCJĘ</span><span class="sxs-lookup"><span data-stu-id="07b70-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="07b70-281">WYBIERZ WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="07b70-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="07b70-282">udostępnia w klauzuli SELECT VALUE pomijania konstrukcji niejawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="07b70-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="07b70-283">W klauzuli SELECT VALUE można określić tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="07b70-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="07b70-284">Podczas takiej klauzuli jest używana, nie otoki wiersza jest tworzony wokół elementów w klauzuli SELECT i kolekcji żądanego kształtu można wyprodukować, na przykład: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="07b70-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="07b70-285">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="07b70-286">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-286">Output:</span></span>  
  
|<span data-ttu-id="07b70-287">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07b70-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="07b70-288">Regulowany wyścigu</span><span class="sxs-lookup"><span data-stu-id="07b70-288">Adjustable Race</span></span>|  
|<span data-ttu-id="07b70-289">Uniwersalny roweru wstrzymania</span><span class="sxs-lookup"><span data-stu-id="07b70-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="07b70-290">Logo AWC centralnych zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="07b70-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="07b70-291">...</span><span class="sxs-lookup"><span data-stu-id="07b70-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="07b70-292">WYBIERZ</span><span class="sxs-lookup"><span data-stu-id="07b70-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="07b70-293">udostępnia również Konstruktor row do utworzenia dowolnego wierszy.</span><span class="sxs-lookup"><span data-stu-id="07b70-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="07b70-294">Wybierz przyjmuje jeden lub więcej elementów w projekcji i wyników w rekordzie danych z polami, na przykład: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="07b70-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="07b70-295">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-295">Example:</span></span>  
  
 <span data-ttu-id="07b70-296">Wybierz p.Name, p.ProductID z AdventureWorksEntities.Product jako dane wyjściowe p:</span><span class="sxs-lookup"><span data-stu-id="07b70-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="07b70-297">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07b70-297">Name</span></span>|<span data-ttu-id="07b70-298">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="07b70-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="07b70-299">Regulowany wyścigu</span><span class="sxs-lookup"><span data-stu-id="07b70-299">Adjustable Race</span></span>|<span data-ttu-id="07b70-300">1</span><span class="sxs-lookup"><span data-stu-id="07b70-300">1</span></span>|  
|<span data-ttu-id="07b70-301">Uniwersalny roweru wstrzymania</span><span class="sxs-lookup"><span data-stu-id="07b70-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="07b70-302">879</span><span class="sxs-lookup"><span data-stu-id="07b70-302">879</span></span>|  
|<span data-ttu-id="07b70-303">Logo AWC centralnych zasad dostępu</span><span class="sxs-lookup"><span data-stu-id="07b70-303">AWC Logo Cap</span></span>|<span data-ttu-id="07b70-304">712</span><span class="sxs-lookup"><span data-stu-id="07b70-304">712</span></span>|  
|<span data-ttu-id="07b70-305">...</span><span class="sxs-lookup"><span data-stu-id="07b70-305">...</span></span>|<span data-ttu-id="07b70-306">...</span><span class="sxs-lookup"><span data-stu-id="07b70-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="07b70-307">WYRAŻENIE CASE</span><span class="sxs-lookup"><span data-stu-id="07b70-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="07b70-308">[Przypadek wyrażenie](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) ocenia zestaw wyrażeń logicznych w celu ustalenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="07b70-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="07b70-309">Przykład:</span><span class="sxs-lookup"><span data-stu-id="07b70-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="07b70-310">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="07b70-310">Output:</span></span>  
  
|<span data-ttu-id="07b70-311">Wartość</span><span class="sxs-lookup"><span data-stu-id="07b70-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="07b70-312">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="07b70-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07b70-313">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07b70-313">See Also</span></span>  
 [<span data-ttu-id="07b70-314">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="07b70-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="07b70-315">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="07b70-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
