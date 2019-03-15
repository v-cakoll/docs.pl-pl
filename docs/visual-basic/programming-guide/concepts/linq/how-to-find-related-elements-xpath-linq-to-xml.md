---
title: 'Instrukcje: Wyszukiwanie elementów powiązanych (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
ms.openlocfilehash: be7dc6d28c6f176108e33a5c783863fdfc5aed81
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845950"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="dacea-102">Instrukcje: Wyszukiwanie elementów powiązanych (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacea-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="dacea-103">W tym temacie pokazano, jak można pobrać elementu, wybierając na atrybut, który odwołuje się do wartości innego elementu.</span><span class="sxs-lookup"><span data-stu-id="dacea-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="dacea-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="dacea-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="dacea-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="dacea-105">Example</span></span>  
 <span data-ttu-id="dacea-106">W tym przykładzie wyszukuje 12 `Order` elementu, a następnie znalezienie klienta dla tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="dacea-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="dacea-107">Należy pamiętać, że indeksowanie w liście .NET "zero" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="dacea-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="dacea-108">Indeksowanie w kolekcji węzłów w predykatu języka XPath jest "jeden" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="dacea-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="dacea-109">W tym przykładzie odzwierciedla tę różnicę.</span><span class="sxs-lookup"><span data-stu-id="dacea-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="dacea-110">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dacea-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 <span data-ttu-id="dacea-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="dacea-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dacea-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dacea-112">See also</span></span>
- [<span data-ttu-id="dacea-113">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacea-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
