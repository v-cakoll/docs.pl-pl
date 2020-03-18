---
title: Jak znaleźć powiązane elementy (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: f74c338019c0451ab5e3ac0d8da10392ae5601ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169236"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="ecef3-102">Jak znaleźć powiązane elementy (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ecef3-102">How to find related elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="ecef3-103">W tym temacie pokazano, jak uzyskać element wybierający atrybut, do której odnosi się wartość innego elementu.</span><span class="sxs-lookup"><span data-stu-id="ecef3-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="ecef3-104">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="ecef3-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="ecef3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecef3-105">Example</span></span>  
 <span data-ttu-id="ecef3-106">W tym przykładzie znajduje `Order` 12 element, a następnie znajduje nabywcy dla tego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="ecef3-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="ecef3-107">Należy zauważyć, że indeksowanie do listy w .NET jest oparte na "zero".</span><span class="sxs-lookup"><span data-stu-id="ecef3-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="ecef3-108">Indeksowanie do kolekcji węzłów w predykatxPath jest "jeden" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="ecef3-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="ecef3-109">Ten przykład odzwierciedla tę różnicę.</span><span class="sxs-lookup"><span data-stu-id="ecef3-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="ecef3-110">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="ecef3-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XDocument co = XDocument.Load("CustomersOrders.xml");  
  
// LINQ to XML query  
XElement customer1 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .ToList()[11]  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// An alternate way to write the query that avoids creation  
// of a System.Collections.Generic.List:  
XElement customer2 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .Skip(11).First()  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// XPath expression  
XElement customer3 = co.XPathSelectElement(  
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");  
  
if (customer1 == customer2 && customer1 == customer3)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(customer1);  
```  
  
 <span data-ttu-id="ecef3-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ecef3-111">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
