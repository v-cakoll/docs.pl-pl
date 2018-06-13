---
title: 'Porady: znajdowanie elementów w Namespace (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: 5c5c8e20195bf7c676b9df7e9db54e79bbb0ca06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325438"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="6c4cb-102">Porady: znajdowanie elementów w Namespace (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c4cb-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="6c4cb-103">Wyrażenia XPath można znaleźć węzłów w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="6c4cb-104">Wyrażenia XPath Użyj prefiksy przestrzeni nazw dla określenie obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="6c4cb-105">Aby analizować wyrażenie XPath, który zawiera prefiksy przestrzeni nazw, trzeba przekazać do metody XPath, które implementuje obiektu <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="6c4cb-106">W tym przykładzie użyto <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="6c4cb-107">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="6c4cb-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="6c4cb-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c4cb-108">Example</span></span>  
 <span data-ttu-id="6c4cb-109">Poniższy przykład odczytuje drzewo XML, który zawiera dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="6c4cb-110">Używa <xref:System.Xml.XmlReader> dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="6c4cb-111">Następnie pobiera <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader>i <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="6c4cb-112">Używa <xref:System.Xml.XmlNamespaceManager> podczas wybierania elementów.</span><span class="sxs-lookup"><span data-stu-id="6c4cb-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
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
  
 <span data-ttu-id="6c4cb-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6c4cb-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c4cb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c4cb-114">See Also</span></span>  
 [<span data-ttu-id="6c4cb-115">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="6c4cb-115">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
