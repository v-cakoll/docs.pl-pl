---
title: 'Instrukcje: Weryfikuj przy użyciu XSD (LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 47704a5aa06bb837c9d76516762330e4aa24e074
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592243"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="95282-102">Instrukcje: Weryfikuj przy użyciu XSD (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="95282-102">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="95282-103"><xref:System.Xml.Schema> Przestrzeń nazw zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="95282-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="95282-104">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Schema.Extensions.Validate%2A> dokumentację metody.</span><span class="sxs-lookup"><span data-stu-id="95282-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95282-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="95282-105">Example</span></span>  
 <span data-ttu-id="95282-106">Poniższy przykład tworzy <xref:System.Xml.Schema.XmlSchemaSet>, a następnie weryfikuje dwa <xref:System.Xml.Linq.XDocument> obiekty względem zestawu schematów.</span><span class="sxs-lookup"><span data-stu-id="95282-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="95282-107">Jeden z dokumentów jest prawidłowy, drugi nie jest.</span><span class="sxs-lookup"><span data-stu-id="95282-107">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="95282-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="95282-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="95282-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="95282-109">Example</span></span>  
 <span data-ttu-id="95282-110">Poniższy przykład sprawdza, czy dokument XML z [przykładowego pliku XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) są prawidłowe dla schematu z [przykładowego pliku XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="95282-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="95282-111">Następnie modyfikuje źródłowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="95282-111">It then modifies the source XML document.</span></span> <span data-ttu-id="95282-112">Zmienia `CustomerID` atrybut pierwszego klienta.</span><span class="sxs-lookup"><span data-stu-id="95282-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="95282-113">Po zmianie zamówienia odwołują się do klienta, który nie istnieje, więc dokument XML nie zostanie już zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="95282-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="95282-114">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="95282-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="95282-115">W tym przykładzie zastosowano następujący schemat XSD: [Przykładowy plik XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="95282-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="95282-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="95282-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="95282-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95282-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="95282-118">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="95282-118">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
