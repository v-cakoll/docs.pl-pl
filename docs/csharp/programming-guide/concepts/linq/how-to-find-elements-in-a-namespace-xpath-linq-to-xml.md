---
title: 'Instrukcje: Znajdowanie elementów w Namespace (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: 8ba5fc03bbd831cfee0c4fd15e71708c4eafd212
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667986"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="96b94-102">Instrukcje: Znajdowanie elementów w Namespace (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="96b94-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="96b94-103">Wyrażenia XPath można znaleźć węzły w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96b94-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="96b94-104">Wyrażenia XPath używać prefiksów przestrzeni nazw do określania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96b94-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="96b94-105">Aby analizować wyrażenie XPath, który zawiera prefiksy przestrzeni nazw, należy przekazać obiekt do metody XPath, które implementuje <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="96b94-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="96b94-106">W tym przykładzie użyto <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="96b94-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="96b94-107">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="96b94-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="96b94-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="96b94-108">Example</span></span>  
 <span data-ttu-id="96b94-109">Poniższy przykład odczytuje drzewa XML, który zawiera dwie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96b94-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="96b94-110">Używa ona <xref:System.Xml.XmlReader> do odczytu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="96b94-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="96b94-111">Następnie pobiera <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader>i <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="96b94-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="96b94-112">Używa ona <xref:System.Xml.XmlNamespaceManager> podczas wybierania elementów.</span><span class="sxs-lookup"><span data-stu-id="96b94-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");  
XElement root = XElement.Load(reader);  
XmlNameTable nameTable = reader.NameTable;  
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");  
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);  
IEnumerable<XElement> list2 =  
    from el in root.Elements()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="96b94-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96b94-113">This example produces the following output:</span></span>  
  
```  
Results are identical  
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96b94-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96b94-114">See also</span></span>

- [<span data-ttu-id="96b94-115">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="96b94-115">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
