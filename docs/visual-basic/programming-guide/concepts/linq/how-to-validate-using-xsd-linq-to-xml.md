---
title: 'Instrukcje: weryfikowanie przy użyciu XSD (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a0fe88d4-4e77-49e7-90de-8953feeccc21
ms.openlocfilehash: 07a5df7af5512bb3db2dfd48a71e1ef07bbc7446
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332387"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-visual-basic"></a>Instrukcje: sprawdzanie poprawności przy użyciu XSD (LINQ to XML) (Visual Basic)
Przestrzeń nazw <xref:System.Xml.Schema> zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku języka definicji schematu XML (XSD). Aby uzyskać więcej informacji, zobacz dokumentację metody <xref:System.Xml.Schema.Extensions.Validate%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Xml.Schema.XmlSchemaSet>, a następnie sprawdza poprawność dwóch obiektów <xref:System.Xml.Linq.XDocument> względem zestawu schematów. Jeden z dokumentów jest prawidłowy, drugi nie jest.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```console  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sprawdza, czy dokument XML z [przykładowego pliku XML: klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) są prawidłowe dla schematu z [przykładowego pliku XSD: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Następnie modyfikuje źródłowy dokument XML. Zmienia atrybut `CustomerID` pierwszego klienta. Po zmianie zamówienia odwołują się do klienta, który nie istnieje, więc dokument XML nie zostanie już zweryfikowany.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```console  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
