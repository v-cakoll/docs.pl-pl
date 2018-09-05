---
title: 'Porady: wyszukiwanie elementów powiązanych (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 57cbba6e52feec05ed6381899017f1ce5d1e8ec1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518629"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="c655d-102">Porady: wyszukiwanie elementów powiązanych (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c655d-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c655d-103">W tym temacie pokazano, jak można pobrać elementu, wybierając na atrybut, który odwołuje się do wartości innego elementu.</span><span class="sxs-lookup"><span data-stu-id="c655d-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="c655d-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="c655d-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="c655d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c655d-105">Example</span></span>  
 <span data-ttu-id="c655d-106">W tym przykładzie wyszukuje 12 `Order` elementu, a następnie znalezienie klienta dla tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c655d-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="c655d-107">Należy pamiętać, że indeksowanie w liście .net "zero" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="c655d-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="c655d-108">Indeksowanie w kolekcji węzłów w predykatu języka XPath jest "jeden" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="c655d-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="c655d-109">W tym przykładzie odzwierciedla tę różnicę.</span><span class="sxs-lookup"><span data-stu-id="c655d-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="c655d-110">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="c655d-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="c655d-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c655d-111">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="c655d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c655d-112">See Also</span></span>

- [<span data-ttu-id="c655d-113">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="c655d-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
