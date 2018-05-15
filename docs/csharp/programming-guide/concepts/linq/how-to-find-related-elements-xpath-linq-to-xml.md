---
title: 'Porady: znajdowanie powiązanych elementów (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: e5367c1b47f24dd269f5055f692c657ecd748b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="58945-102">Porady: znajdowanie powiązanych elementów (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="58945-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="58945-103">W tym temacie przedstawiono sposób uzyskać elementu zaznaczenie na atrybut, który jest określana przez wartość innego elementu.</span><span class="sxs-lookup"><span data-stu-id="58945-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="58945-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="58945-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="58945-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="58945-105">Example</span></span>  
 <span data-ttu-id="58945-106">W tym przykładzie znajduje 12 `Order` elementu, a następnie znalezienie klienta dla tego zlecenia.</span><span class="sxs-lookup"><span data-stu-id="58945-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="58945-107">Należy pamiętać, że przeprowadzane jest indeksowanie do listy w programie .net "zero" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="58945-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="58945-108">Przeprowadzane jest indeksowanie do kolekcji węzłów predykatu języka XPath jest "one" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="58945-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="58945-109">W tym przykładzie odzwierciedla tej różnicy.</span><span class="sxs-lookup"><span data-stu-id="58945-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="58945-110">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="58945-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="58945-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="58945-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58945-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58945-112">See Also</span></span>  
 [<span data-ttu-id="58945-113">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="58945-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
