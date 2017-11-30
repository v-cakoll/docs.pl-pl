---
title: "Porady: znajdowanie powiązanych elementów (XPath-LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6153db1e77b957d35160d1de75f18e163817ba6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b0806-102">Porady: znajdowanie powiązanych elementów (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0806-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b0806-103">W tym temacie przedstawiono sposób uzyskać elementu zaznaczenie na atrybut, który jest określana przez wartość innego elementu.</span><span class="sxs-lookup"><span data-stu-id="b0806-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="b0806-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="b0806-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="b0806-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0806-105">Example</span></span>  
 <span data-ttu-id="b0806-106">W tym przykładzie znajduje 12 `Order` elementu, a następnie znalezienie klienta dla tego zlecenia.</span><span class="sxs-lookup"><span data-stu-id="b0806-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="b0806-107">Należy pamiętać, że przeprowadzane jest indeksowanie do listy w programie .net "zero" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="b0806-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="b0806-108">Przeprowadzane jest indeksowanie do kolekcji węzłów predykatu języka XPath jest "one" na podstawie.</span><span class="sxs-lookup"><span data-stu-id="b0806-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="b0806-109">W tym przykładzie odzwierciedla tej różnicy.</span><span class="sxs-lookup"><span data-stu-id="b0806-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="b0806-110">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b0806-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b0806-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b0806-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0806-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0806-112">See Also</span></span>  
 [<span data-ttu-id="b0806-113">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0806-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
