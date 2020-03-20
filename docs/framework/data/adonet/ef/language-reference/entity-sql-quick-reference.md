---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150353"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="75e3b-102">Szybkie odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="75e3b-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="75e3b-103">Ten temat zawiera szybkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] odwołanie do zapytań.</span><span class="sxs-lookup"><span data-stu-id="75e3b-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="75e3b-104">Zapytania w tym temacie są oparte na modelu AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="75e3b-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="75e3b-105">Literały</span><span class="sxs-lookup"><span data-stu-id="75e3b-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="75e3b-106">Ciąg</span><span class="sxs-lookup"><span data-stu-id="75e3b-106">String</span></span>  
 <span data-ttu-id="75e3b-107">Istnieją literały znaków Unicode i innych niż Unicode.</span><span class="sxs-lookup"><span data-stu-id="75e3b-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="75e3b-108">Ciągi Unicode są poprzedzane z N. Na przykład `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="75e3b-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="75e3b-109">Poniżej przedstawiono przykład literału ciągu non-Unicode:</span><span class="sxs-lookup"><span data-stu-id="75e3b-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="75e3b-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-110">Output:</span></span>  
  
|<span data-ttu-id="75e3b-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-112">hello</span><span class="sxs-lookup"><span data-stu-id="75e3b-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="75e3b-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="75e3b-113">DateTime</span></span>  
 <span data-ttu-id="75e3b-114">W datetime literały, zarówno daty i godziny części są obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="75e3b-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="75e3b-115">Nie ma żadnych wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="75e3b-115">There are no default values.</span></span>  
  
 <span data-ttu-id="75e3b-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="75e3b-117">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-117">Output:</span></span>  
  
|<span data-ttu-id="75e3b-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-119">25.01.2006 1:01:00</span><span class="sxs-lookup"><span data-stu-id="75e3b-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="75e3b-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="75e3b-120">Integer</span></span>  
 <span data-ttu-id="75e3b-121">Literały liczby całkowite mogą być typu Int32 (123), UInt32 (123U), Int64 (123L) i UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="75e3b-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="75e3b-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="75e3b-123">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-123">Output:</span></span>  
  
|<span data-ttu-id="75e3b-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-125">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-125">1</span></span>|  
|<span data-ttu-id="75e3b-126">2</span><span class="sxs-lookup"><span data-stu-id="75e3b-126">2</span></span>|  
|<span data-ttu-id="75e3b-127">3</span><span class="sxs-lookup"><span data-stu-id="75e3b-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="75e3b-128">Inne</span><span class="sxs-lookup"><span data-stu-id="75e3b-128">Other</span></span>  
 <span data-ttu-id="75e3b-129">Inne literały obsługiwane [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przez to Guid, Binary, Float/Double, `null`Decimal i .</span><span class="sxs-lookup"><span data-stu-id="75e3b-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="75e3b-130">Literały null [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w są uważane za zgodne z każdym innym typem w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="75e3b-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="75e3b-131">Konstruktory typów</span><span class="sxs-lookup"><span data-stu-id="75e3b-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="75e3b-132">ROW</span><span class="sxs-lookup"><span data-stu-id="75e3b-132">ROW</span></span>  
 <span data-ttu-id="75e3b-133">[ROW](row-entity-sql.md) konstruuje wartość anonimową, typięcą strukturalną (rekord) jak w:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="75e3b-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="75e3b-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="75e3b-135">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-135">Output:</span></span>  
  
|<span data-ttu-id="75e3b-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="75e3b-136">ProductID</span></span>|<span data-ttu-id="75e3b-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75e3b-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="75e3b-138">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-138">1</span></span>|<span data-ttu-id="75e3b-139">Regulowany wyścig</span><span class="sxs-lookup"><span data-stu-id="75e3b-139">Adjustable Race</span></span>|  
|<span data-ttu-id="75e3b-140">879</span><span class="sxs-lookup"><span data-stu-id="75e3b-140">879</span></span>|<span data-ttu-id="75e3b-141">Uniwersalny stojak rowerowy</span><span class="sxs-lookup"><span data-stu-id="75e3b-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="75e3b-142">712</span><span class="sxs-lookup"><span data-stu-id="75e3b-142">712</span></span>|<span data-ttu-id="75e3b-143">Czapka z logo AWC</span><span class="sxs-lookup"><span data-stu-id="75e3b-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="75e3b-144">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-144">...</span></span>|<span data-ttu-id="75e3b-145">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="75e3b-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="75e3b-146">MULTISET</span></span>  
 <span data-ttu-id="75e3b-147">[MULTISET](multiset-entity-sql.md) tworzy kolekcje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="75e3b-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="75e3b-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="75e3b-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="75e3b-149">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="75e3b-150">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-150">Output:</span></span>  
  
|<span data-ttu-id="75e3b-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="75e3b-151">ProductID</span></span>|<span data-ttu-id="75e3b-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75e3b-152">Name</span></span>|<span data-ttu-id="75e3b-153">Productnumber</span><span class="sxs-lookup"><span data-stu-id="75e3b-153">ProductNumber</span></span>|<span data-ttu-id="75e3b-154">…</span><span class="sxs-lookup"><span data-stu-id="75e3b-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="75e3b-155">842</span><span class="sxs-lookup"><span data-stu-id="75e3b-155">842</span></span>|<span data-ttu-id="75e3b-156">Touring-Panniers, Duży</span><span class="sxs-lookup"><span data-stu-id="75e3b-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="75e3b-157">Pa-T100</span><span class="sxs-lookup"><span data-stu-id="75e3b-157">PA-T100</span></span>|<span data-ttu-id="75e3b-158">…</span><span class="sxs-lookup"><span data-stu-id="75e3b-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="75e3b-159">Obiekt</span><span class="sxs-lookup"><span data-stu-id="75e3b-159">Object</span></span>  
 <span data-ttu-id="75e3b-160">[Nazwane konstrukcje konstruktora](named-type-constructor-entity-sql.md) typu (nazwane) obiekty zdefiniowane przez użytkownika, takie jak `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="75e3b-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="75e3b-161">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="75e3b-162">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-162">Output:</span></span>  
  
|<span data-ttu-id="75e3b-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="75e3b-163">SalesOrderDetailID</span></span>|<span data-ttu-id="75e3b-164">Numer śledzenia przewoźnika</span><span class="sxs-lookup"><span data-stu-id="75e3b-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="75e3b-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="75e3b-165">OrderQty</span></span>|<span data-ttu-id="75e3b-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="75e3b-166">ProductID</span></span>|<span data-ttu-id="75e3b-167">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="75e3b-168">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-168">1</span></span>|<span data-ttu-id="75e3b-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="75e3b-169">4911-403C-98</span></span>|<span data-ttu-id="75e3b-170">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-170">1</span></span>|<span data-ttu-id="75e3b-171">776</span><span class="sxs-lookup"><span data-stu-id="75e3b-171">776</span></span>|<span data-ttu-id="75e3b-172">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-172">...</span></span>|  
|<span data-ttu-id="75e3b-173">2</span><span class="sxs-lookup"><span data-stu-id="75e3b-173">2</span></span>|<span data-ttu-id="75e3b-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="75e3b-174">4911-403C-98</span></span>|<span data-ttu-id="75e3b-175">3</span><span class="sxs-lookup"><span data-stu-id="75e3b-175">3</span></span>|<span data-ttu-id="75e3b-176">777</span><span class="sxs-lookup"><span data-stu-id="75e3b-176">777</span></span>|<span data-ttu-id="75e3b-177">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-177">...</span></span>|  
|<span data-ttu-id="75e3b-178">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-178">...</span></span>|<span data-ttu-id="75e3b-179">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-179">...</span></span>|<span data-ttu-id="75e3b-180">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-180">...</span></span>|<span data-ttu-id="75e3b-181">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-181">...</span></span>|<span data-ttu-id="75e3b-182">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="75e3b-183">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="75e3b-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="75e3b-184">REF</span><span class="sxs-lookup"><span data-stu-id="75e3b-184">REF</span></span>  
 <span data-ttu-id="75e3b-185">[REF](ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="75e3b-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="75e3b-186">Na przykład następująca kwerenda zwraca odwołania do każdej encji Zamówienia w zestawie jednostek Zamówienia:</span><span class="sxs-lookup"><span data-stu-id="75e3b-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="75e3b-187">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-187">Output:</span></span>  
  
|<span data-ttu-id="75e3b-188">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-189">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-189">1</span></span>|  
|<span data-ttu-id="75e3b-190">2</span><span class="sxs-lookup"><span data-stu-id="75e3b-190">2</span></span>|  
|<span data-ttu-id="75e3b-191">3</span><span class="sxs-lookup"><span data-stu-id="75e3b-191">3</span></span>|  
|<span data-ttu-id="75e3b-192">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-192">...</span></span>|  
  
 <span data-ttu-id="75e3b-193">W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="75e3b-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="75e3b-194">Gdy operator wyodrębniania właściwości jest używany, odwołanie jest automatycznie wyłuskiwane.</span><span class="sxs-lookup"><span data-stu-id="75e3b-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="75e3b-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="75e3b-196">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-196">Output:</span></span>  
  
|<span data-ttu-id="75e3b-197">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-198">Regulowany wyścig</span><span class="sxs-lookup"><span data-stu-id="75e3b-198">Adjustable Race</span></span>|  
|<span data-ttu-id="75e3b-199">Uniwersalny stojak rowerowy</span><span class="sxs-lookup"><span data-stu-id="75e3b-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="75e3b-200">Czapka z logo AWC</span><span class="sxs-lookup"><span data-stu-id="75e3b-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="75e3b-201">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="75e3b-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="75e3b-202">DEREF</span></span>  
 <span data-ttu-id="75e3b-203">[DEREF](deref-entity-sql.md) wyłudzenie wartości referencyjnej i tworzy wynik tego wyłuskania.</span><span class="sxs-lookup"><span data-stu-id="75e3b-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="75e3b-204">Na przykład następująca kwerenda tworzy Order jednostek dla każdego `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`Zamówienia w zestaw jednostek Zamówienia: ..</span><span class="sxs-lookup"><span data-stu-id="75e3b-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="75e3b-205">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="75e3b-206">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-206">Output:</span></span>  
  
|<span data-ttu-id="75e3b-207">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-208">Regulowany wyścig</span><span class="sxs-lookup"><span data-stu-id="75e3b-208">Adjustable Race</span></span>|  
|<span data-ttu-id="75e3b-209">Uniwersalny stojak rowerowy</span><span class="sxs-lookup"><span data-stu-id="75e3b-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="75e3b-210">Czapka z logo AWC</span><span class="sxs-lookup"><span data-stu-id="75e3b-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="75e3b-211">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="75e3b-212">CREATEREF I KLUCZ</span><span class="sxs-lookup"><span data-stu-id="75e3b-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="75e3b-213">[CREATEREF](createref-entity-sql.md) tworzy odwołanie przekazując klucz.</span><span class="sxs-lookup"><span data-stu-id="75e3b-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="75e3b-214">[KEY](key-entity-sql.md) wyodrębnia kluczową część wyrażenia z odwołaniem do typu.</span><span class="sxs-lookup"><span data-stu-id="75e3b-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="75e3b-215">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="75e3b-216">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-216">Output:</span></span>  
  
|<span data-ttu-id="75e3b-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="75e3b-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="75e3b-218">980</span><span class="sxs-lookup"><span data-stu-id="75e3b-218">980</span></span>|  
|<span data-ttu-id="75e3b-219">365</span><span class="sxs-lookup"><span data-stu-id="75e3b-219">365</span></span>|  
|<span data-ttu-id="75e3b-220">771</span><span class="sxs-lookup"><span data-stu-id="75e3b-220">771</span></span>|  
|<span data-ttu-id="75e3b-221">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="75e3b-222">Funkcje</span><span class="sxs-lookup"><span data-stu-id="75e3b-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="75e3b-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="75e3b-223">Canonical</span></span>  
 <span data-ttu-id="75e3b-224">Obszar nazw dla [funkcji kanonicznych](canonical-functions.md) jest Edm, jak w `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="75e3b-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="75e3b-225">Nie trzeba określać obszaru nazw, chyba że zostanie zaimportowana inna przestrzeń nazw zawierająca funkcję o takiej samej nazwie jak funkcja kanoniczna.</span><span class="sxs-lookup"><span data-stu-id="75e3b-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="75e3b-226">Jeśli dwie przestrzenie nazw mają tę samą funkcję, użytkownik powinien podać pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="75e3b-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="75e3b-227">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="75e3b-228">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-228">Output:</span></span>  
  
|<span data-ttu-id="75e3b-229">NazwaLen</span><span class="sxs-lookup"><span data-stu-id="75e3b-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="75e3b-230">6</span><span class="sxs-lookup"><span data-stu-id="75e3b-230">6</span></span>|  
|<span data-ttu-id="75e3b-231">6</span><span class="sxs-lookup"><span data-stu-id="75e3b-231">6</span></span>|  
|<span data-ttu-id="75e3b-232">5</span><span class="sxs-lookup"><span data-stu-id="75e3b-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="75e3b-233">Specyficzne dla dostawcy firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="75e3b-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="75e3b-234">[Funkcje specyficzne dla](../sqlclient-for-ef-functions.md) dostawcy `SqlServer` firmy Microsoft znajdują się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="75e3b-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="75e3b-235">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="75e3b-236">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-236">Output:</span></span>  
  
|<span data-ttu-id="75e3b-237">Wyślij wiadomość e-mailLen</span><span class="sxs-lookup"><span data-stu-id="75e3b-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="75e3b-238">27</span><span class="sxs-lookup"><span data-stu-id="75e3b-238">27</span></span>|  
|<span data-ttu-id="75e3b-239">27</span><span class="sxs-lookup"><span data-stu-id="75e3b-239">27</span></span>|  
|<span data-ttu-id="75e3b-240">26</span><span class="sxs-lookup"><span data-stu-id="75e3b-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="75e3b-241">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="75e3b-241">Namespaces</span></span>  
 <span data-ttu-id="75e3b-242">[USING](using-entity-sql.md) określa obszary nazw używane w wyrażeniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="75e3b-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="75e3b-243">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="75e3b-244">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-244">Output:</span></span>  
  
|<span data-ttu-id="75e3b-245">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-246">aa</span><span class="sxs-lookup"><span data-stu-id="75e3b-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="75e3b-247">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="75e3b-247">Paging</span></span>  
 <span data-ttu-id="75e3b-248">Stronicowanie może być wyrażone przez zadeklarowanie [skip](skip-entity-sql.md) i [limit](limit-entity-sql.md) podpunktów do [ORDER BY](order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="75e3b-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="75e3b-249">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="75e3b-250">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-250">Output:</span></span>  
  
|<span data-ttu-id="75e3b-251">ID</span><span class="sxs-lookup"><span data-stu-id="75e3b-251">ID</span></span>|<span data-ttu-id="75e3b-252">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75e3b-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="75e3b-253">10</span><span class="sxs-lookup"><span data-stu-id="75e3b-253">10</span></span>|<span data-ttu-id="75e3b-254">Adina</span><span class="sxs-lookup"><span data-stu-id="75e3b-254">Adina</span></span>|  
|<span data-ttu-id="75e3b-255">11</span><span class="sxs-lookup"><span data-stu-id="75e3b-255">11</span></span>|<span data-ttu-id="75e3b-256">Okręg wyborczy Agcaoili</span><span class="sxs-lookup"><span data-stu-id="75e3b-256">Agcaoili</span></span>|  
|<span data-ttu-id="75e3b-257">12</span><span class="sxs-lookup"><span data-stu-id="75e3b-257">12</span></span>|<span data-ttu-id="75e3b-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="75e3b-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="75e3b-259">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="75e3b-259">Grouping</span></span>  
 <span data-ttu-id="75e3b-260">[POLECENIE GRUPOWANIE WEDŁUG](group-by-entity-sql.md) określa grupy, do których mają być umieszczone obiekty zwracane przez wyrażenie kwerendy ([SELECT).](select-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="75e3b-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="75e3b-261">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="75e3b-262">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-262">Output:</span></span>  
  
|<span data-ttu-id="75e3b-263">name</span><span class="sxs-lookup"><span data-stu-id="75e3b-263">name</span></span>|  
|----------|  
|<span data-ttu-id="75e3b-264">LL Zgromadzenie siedzeń górskich</span><span class="sxs-lookup"><span data-stu-id="75e3b-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="75e3b-265">ML Zgromadzenie siedzeń górskich</span><span class="sxs-lookup"><span data-stu-id="75e3b-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="75e3b-266">HL Montaż siedzenia górskiego</span><span class="sxs-lookup"><span data-stu-id="75e3b-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="75e3b-267">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="75e3b-268">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="75e3b-268">Navigation</span></span>  
 <span data-ttu-id="75e3b-269">Operator nawigacji relacji umożliwia przechodzenie przez relację z jednej encji (od końca) do drugiej (do końca).</span><span class="sxs-lookup"><span data-stu-id="75e3b-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="75e3b-270">[NAVIGATE](navigate-entity-sql.md) przyjmuje typ relacji \<zakwalifikowany jako obszar nazw>. \<nazwa typu relacji>.</span><span class="sxs-lookup"><span data-stu-id="75e3b-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="75e3b-271">Navigate zwraca\<ref T>, jeśli kardynalność do końca jest 1.</span><span class="sxs-lookup"><span data-stu-id="75e3b-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="75e3b-272">Jeśli kardynalność do końca jest n, Kolekcja\<<Ref T>> zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="75e3b-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="75e3b-273">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="75e3b-274">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-274">Output:</span></span>  
  
|<span data-ttu-id="75e3b-275">Addressid</span><span class="sxs-lookup"><span data-stu-id="75e3b-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="75e3b-276">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-276">1</span></span>|  
|<span data-ttu-id="75e3b-277">2</span><span class="sxs-lookup"><span data-stu-id="75e3b-277">2</span></span>|  
|<span data-ttu-id="75e3b-278">3</span><span class="sxs-lookup"><span data-stu-id="75e3b-278">3</span></span>|  
|<span data-ttu-id="75e3b-279">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="75e3b-280">WYBIERZ WARTOŚĆ I WYBIERZ</span><span class="sxs-lookup"><span data-stu-id="75e3b-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="75e3b-281">WYBIERZ WARTOŚĆ</span><span class="sxs-lookup"><span data-stu-id="75e3b-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="75e3b-282">zawiera select value klauzuli pominąć niejawną konstrukcję wiersza.</span><span class="sxs-lookup"><span data-stu-id="75e3b-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="75e3b-283">W klauzuli WYBIERZ WARTOŚĆ można określić tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="75e3b-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="75e3b-284">Gdy taka klauzula jest używana, wokół elementów w klauzuli SELECT nie jest skonstruowane żadne otoki `SELECT VALUE a`wierszy, a można utworzyć kolekcję żądanego kształtu, na przykład: .</span><span class="sxs-lookup"><span data-stu-id="75e3b-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="75e3b-285">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="75e3b-286">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-286">Output:</span></span>  
  
|<span data-ttu-id="75e3b-287">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75e3b-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="75e3b-288">Regulowany wyścig</span><span class="sxs-lookup"><span data-stu-id="75e3b-288">Adjustable Race</span></span>|  
|<span data-ttu-id="75e3b-289">Uniwersalny stojak rowerowy</span><span class="sxs-lookup"><span data-stu-id="75e3b-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="75e3b-290">Czapka z logo AWC</span><span class="sxs-lookup"><span data-stu-id="75e3b-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="75e3b-291">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="75e3b-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="75e3b-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="75e3b-293">udostępnia również konstruktora wierszy do konstruowania dowolnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="75e3b-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="75e3b-294">Select przyjmuje jeden lub więcej elementów w projekcji i powoduje `SELECT a, b, c`rekord danych z polami, na przykład: .</span><span class="sxs-lookup"><span data-stu-id="75e3b-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="75e3b-295">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-295">Example:</span></span>  
  
 <span data-ttu-id="75e3b-296">WYBIERZ p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="75e3b-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="75e3b-297">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75e3b-297">Name</span></span>|<span data-ttu-id="75e3b-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="75e3b-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="75e3b-299">Regulowany wyścig</span><span class="sxs-lookup"><span data-stu-id="75e3b-299">Adjustable Race</span></span>|<span data-ttu-id="75e3b-300">1</span><span class="sxs-lookup"><span data-stu-id="75e3b-300">1</span></span>|  
|<span data-ttu-id="75e3b-301">Uniwersalny stojak rowerowy</span><span class="sxs-lookup"><span data-stu-id="75e3b-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="75e3b-302">879</span><span class="sxs-lookup"><span data-stu-id="75e3b-302">879</span></span>|  
|<span data-ttu-id="75e3b-303">Czapka z logo AWC</span><span class="sxs-lookup"><span data-stu-id="75e3b-303">AWC Logo Cap</span></span>|<span data-ttu-id="75e3b-304">712</span><span class="sxs-lookup"><span data-stu-id="75e3b-304">712</span></span>|  
|<span data-ttu-id="75e3b-305">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-305">...</span></span>|<span data-ttu-id="75e3b-306">...</span><span class="sxs-lookup"><span data-stu-id="75e3b-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="75e3b-307">WYRAŻENIE SPRAWY</span><span class="sxs-lookup"><span data-stu-id="75e3b-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="75e3b-308">Wyrażenie [case](case-entity-sql.md) ocenia zestaw wyrażeń logicznych w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="75e3b-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="75e3b-309">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75e3b-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="75e3b-310">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75e3b-310">Output:</span></span>  
  
|<span data-ttu-id="75e3b-311">Wartość</span><span class="sxs-lookup"><span data-stu-id="75e3b-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="75e3b-312">Prawda</span><span class="sxs-lookup"><span data-stu-id="75e3b-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75e3b-313">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75e3b-313">See also</span></span>

- [<span data-ttu-id="75e3b-314">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="75e3b-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="75e3b-315">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="75e3b-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
