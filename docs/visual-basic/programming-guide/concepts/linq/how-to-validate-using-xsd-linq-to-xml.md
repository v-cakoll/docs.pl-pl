---
title: 'Instrukcje: weryfikowanie przy użyciu XSD (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a0fe88d4-4e77-49e7-90de-8953feeccc21
ms.openlocfilehash: fd9931530bde2c47dcc8c7b7363a0d5ffae85b8a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383095"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-visual-basic"></a><span data-ttu-id="89d1f-102">Instrukcje: sprawdzanie poprawności przy użyciu XSD (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89d1f-102">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="89d1f-103"><xref:System.Xml.Schema>Przestrzeń nazw zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="89d1f-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="89d1f-104">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Schema.Extensions.Validate%2A> dokumentację metody.</span><span class="sxs-lookup"><span data-stu-id="89d1f-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89d1f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="89d1f-105">Example</span></span>  
 <span data-ttu-id="89d1f-106">Poniższy przykład tworzy <xref:System.Xml.Schema.XmlSchemaSet> , a następnie weryfikuje dwa <xref:System.Xml.Linq.XDocument> obiekty względem zestawu schematów.</span><span class="sxs-lookup"><span data-stu-id="89d1f-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="89d1f-107">Jeden z dokumentów jest prawidłowy, drugi nie jest.</span><span class="sxs-lookup"><span data-stu-id="89d1f-107">One of the documents is valid, the other is not.</span></span>  
  
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
  
 <span data-ttu-id="89d1f-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="89d1f-108">This example produces the following output:</span></span>  
  
```console  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="89d1f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="89d1f-109">Example</span></span>  
 <span data-ttu-id="89d1f-110">Poniższy przykład sprawdza, czy dokument XML z [przykładowego pliku XML: klienci i zamówienia (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) są prawidłowe dla schematu z [przykładowego pliku XSD: klienci i zamówienia](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="89d1f-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) is valid per the schema from [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="89d1f-111">Następnie modyfikuje źródłowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="89d1f-111">It then modifies the source XML document.</span></span> <span data-ttu-id="89d1f-112">Zmienia `CustomerID` atrybut pierwszego klienta.</span><span class="sxs-lookup"><span data-stu-id="89d1f-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="89d1f-113">Po zmianie zamówienia odwołują się do klienta, który nie istnieje, więc dokument XML nie zostanie już zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="89d1f-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="89d1f-114">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="89d1f-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="89d1f-115">W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="89d1f-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="89d1f-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="89d1f-116">This example produces the following output:</span></span>  
  
```console  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="89d1f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89d1f-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="89d1f-118">Tworzenie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89d1f-118">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
