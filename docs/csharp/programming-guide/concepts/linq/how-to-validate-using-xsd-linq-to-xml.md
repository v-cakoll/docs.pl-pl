---
title: Jak sprawdzić poprawność przy użyciu XSD (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 29830457b63f36dd401a412364060339344f35cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347254"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="f6680-102">Jak sprawdzić poprawność przy użyciu XSD (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f6680-102">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f6680-103">Obszar <xref:System.Xml.Schema> nazw zawiera metody rozszerzenia, które ułatwiają sprawdzanie poprawności drzewa XML względem pliku XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="f6680-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="f6680-104">Aby uzyskać więcej <xref:System.Xml.Schema.Extensions.Validate%2A> informacji, zobacz dokumentację metody.</span><span class="sxs-lookup"><span data-stu-id="f6680-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6680-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6680-105">Example</span></span>  
 <span data-ttu-id="f6680-106">Poniższy przykład tworzy <xref:System.Xml.Schema.XmlSchemaSet>, a <xref:System.Xml.Linq.XDocument> następnie sprawdza poprawność dwóch obiektów względem zestawu schematów.</span><span class="sxs-lookup"><span data-stu-id="f6680-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="f6680-107">Jeden z dokumentów jest ważny, drugi nie.</span><span class="sxs-lookup"><span data-stu-id="f6680-107">One of the documents is valid, the other is not.</span></span>  
  
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
  
 <span data-ttu-id="f6680-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f6680-108">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="f6680-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6680-109">Example</span></span>  
 <span data-ttu-id="f6680-110">W poniższym przykładzie sprawdza się, czy dokument XML z [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) jest prawidłowy dla schematu z [przykładowego pliku XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="f6680-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="f6680-111">Następnie modyfikuje źródłowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="f6680-111">It then modifies the source XML document.</span></span> <span data-ttu-id="f6680-112">Zmienia `CustomerID` atrybut na pierwszym kliencie.</span><span class="sxs-lookup"><span data-stu-id="f6680-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="f6680-113">Po zmianie zamówienia będą następnie odwoływać się do odbiorcy, który nie istnieje, więc dokument XML nie będzie już sprawdzał poprawności.</span><span class="sxs-lookup"><span data-stu-id="f6680-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="f6680-114">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="f6680-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="f6680-115">W tym przykładzie użyto następującego schematu XSD: [Przykładowy plik XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="f6680-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
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
  
 <span data-ttu-id="f6680-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f6680-116">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6680-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6680-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="f6680-118">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f6680-118">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
