---
title: "Porady: Sprawdzanie poprawności za pomocą schematu XSD (LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0fe88d4-4e77-49e7-90de-8953feeccc21
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53b4f96e4fe31588c948d8e860be2c3bd3fa372a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-using-xsd-linq-to-xml-visual-basic"></a><span data-ttu-id="0f5a5-102">Porady: Sprawdzanie poprawności za pomocą schematu XSD (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5a5-102">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0f5a5-103"><xref:System.Xml.Schema> Przestrzeń nazw zawiera metody rozszerzenia, które ułatwiają sprawdzanie poprawności drzewo XML przed plik języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="0f5a5-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="0f5a5-104">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Schema.Extensions.Validate%2A> dokumentacji metody.</span><span class="sxs-lookup"><span data-stu-id="0f5a5-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5a5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f5a5-105">Example</span></span>  
 <span data-ttu-id="0f5a5-106">Poniższy przykład tworzy <xref:System.Xml.Schema.XmlSchemaSet>, następnie weryfikuje dwa <xref:System.Xml.Linq.XDocument> obiektów względem zestawu schematu.</span><span class="sxs-lookup"><span data-stu-id="0f5a5-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="0f5a5-107">Jeden z dokumentów jest nieprawidłowy, innych nie.</span><span class="sxs-lookup"><span data-stu-id="0f5a5-107">One of the documents is valid, the other is not.</span></span>  
  
```vb  
Dim errors As Boolean = False  
  
Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)  
    Console.WriteLine("{0}", e.Message)  
    errors = True  
End Sub  
  
Sub Main()  
    Dim xsdMarkup As XElement = _  
        <xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
            <xsd:element name='Root'>  
                <xsd:complexType>  
                    <xsd:sequence>  
                        <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
                        <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
                    </xsd:sequence>  
                </xsd:complexType>  
            </xsd:element>  
        </xsd:schema>  
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()  
    schemas.Add("", xsdMarkup.CreateReader)  
  
    Dim doc1 As XDocument = _  
        <?xml version='1.0'?>  
        <Root>  
            <Child1>content1</Child1>  
            <Child2>content1</Child2>  
        </Root>  
  
    Dim doc2 As XDocument = _  
        <?xml version='1.0'?>  
        <Root>  
            <Child1>content1</Child1>  
            <Child3>content1</Child3>  
        </Root>  
  
    Console.WriteLine("Validating doc1")  
    errors = False  
    doc1.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("doc1 {0}", IIf(errors = True, "did not validate", "validated"))  
  
    Console.WriteLine()  
    Console.WriteLine("Validating doc2")  
    errors = False  
    doc2.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("doc2 {0}", IIf(errors = True, "did not validate", "validated"))  
End Sub  
```  
  
 <span data-ttu-id="0f5a5-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0f5a5-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="0f5a5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f5a5-109">Example</span></span>  
 <span data-ttu-id="0f5a5-110">Poniższy przykład sprawdza, czy z dokumentu XML [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) jest prawidłowy według schematu z [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="0f5a5-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) is valid per the schema from [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="0f5a5-111">Modyfikuje źródło dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0f5a5-111">It then modifies the source XML document.</span></span> <span data-ttu-id="0f5a5-112">Zmienia `CustomerID` atrybutu pierwszego klienta.</span><span class="sxs-lookup"><span data-stu-id="0f5a5-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="0f5a5-113">Po zmianie zamówienia będzie następnie odnosić się do klienta, który nie istnieje, więc dokument XML nie zostanie poprawnie zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="0f5a5-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="0f5a5-114">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0f5a5-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0f5a5-115">W tym przykładzie użyto następujących schematu XSD: [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="0f5a5-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
```vb  
Dim errors As Boolean = False  
  
Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)  
    Console.WriteLine("{0}", e.Message)  
    errors = True  
End Sub  
  
Sub Main()  
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()  
    schemas.Add("", "CustomersOrders.xsd")  
  
    Console.WriteLine("Attempting to validate")  
    Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
    errors = False  
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))  
  
    Console.WriteLine()  
    ' Modify the source document so that it will not validate.  
    custOrdDoc.<Root>.<Orders>.<Order>.<CustomerID>(0).Value = "AAAAA"  
    Console.WriteLine("Attempting to validate after modification")  
    errors = False  
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))  
End Sub  
```  
  
 <span data-ttu-id="0f5a5-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0f5a5-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f5a5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f5a5-117">See Also</span></span>  
 <xref:System.Xml.Schema.Extensions.Validate%2A>  
 [<span data-ttu-id="0f5a5-118">Tworzenie drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5a5-118">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
