---
title: 'Instrukcje: Znajdowanie powiązanych elementów (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
ms.openlocfilehash: e250572e7bd73e769e4ab06b7b7ff9e3b3d38c47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344644"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b5059-102">Instrukcje: Znajdowanie powiązanych elementów (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5059-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b5059-103">W tym temacie pokazano, jak uzyskać element, wybierając atrybut, który jest określany przez wartość innego elementu.</span><span class="sxs-lookup"><span data-stu-id="b5059-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="b5059-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="b5059-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="b5059-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5059-105">Example</span></span>  
 <span data-ttu-id="b5059-106">Ten przykład znajduje 12 `Order` elementu, a następnie wyszukuje klienta dla tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b5059-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="b5059-107">Należy zauważyć, że indeksowanie do listy w .NET jest oparte na "zero".</span><span class="sxs-lookup"><span data-stu-id="b5059-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="b5059-108">Indeksowanie do kolekcji węzłów w predykacie XPath jest oparte na "jednej".</span><span class="sxs-lookup"><span data-stu-id="b5059-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="b5059-109">Ten przykład odzwierciedla tę różnicę.</span><span class="sxs-lookup"><span data-stu-id="b5059-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="b5059-110">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b5059-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b5059-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b5059-111">This example produces the following output:</span></span>  
  
```console
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
  
## <a name="see-also"></a><span data-ttu-id="b5059-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5059-112">See also</span></span>

- [<span data-ttu-id="b5059-113">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5059-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
