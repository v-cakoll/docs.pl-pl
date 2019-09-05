---
title: 'Instrukcje: Znajdź elementy pokrewne (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 2aa3f6c6c2c2ac327ff2dffc206cdd294e12d7a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253641"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="736a0-102">Instrukcje: Znajdź elementy pokrewne (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="736a0-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="736a0-103">W tym temacie pokazano, jak uzyskać element, wybierając atrybut, który jest określany przez wartość innego elementu.</span><span class="sxs-lookup"><span data-stu-id="736a0-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="736a0-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="736a0-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="736a0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="736a0-105">Example</span></span>  
 <span data-ttu-id="736a0-106">Ten przykład znajduje dwunasty `Order` element, a następnie wyszukuje klienta dla tego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="736a0-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="736a0-107">Należy zauważyć, że indeksowanie do listy w .NET jest oparte na "zero".</span><span class="sxs-lookup"><span data-stu-id="736a0-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="736a0-108">Indeksowanie do kolekcji węzłów w predykacie XPath jest oparte na "jednej".</span><span class="sxs-lookup"><span data-stu-id="736a0-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="736a0-109">Ten przykład odzwierciedla tę różnicę.</span><span class="sxs-lookup"><span data-stu-id="736a0-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="736a0-110">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="736a0-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="736a0-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="736a0-111">This example produces the following output:</span></span>  
  
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
 