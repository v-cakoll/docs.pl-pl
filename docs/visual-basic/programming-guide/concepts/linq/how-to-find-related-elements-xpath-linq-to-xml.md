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
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Wyszukiwanie elementów powiązanych (XPath-LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak można pobrać elementu, wybierając na atrybut, który odwołuje się do wartości innego elementu.  
  
 Wyrażenie XPath jest:  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje 12 `Order` elementu, a następnie znalezienie klienta dla tej kolejności.  
  
 Należy pamiętać, że indeksowanie w liście .NET "zero" na podstawie. Indeksowanie w kolekcji węzłów w predykatu języka XPath jest "jeden" na podstawie. W tym przykładzie odzwierciedla tę różnicę.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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
  
## <a name="see-also"></a>Zobacz także
- [LINQ to XML dla użytkowników metody XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
