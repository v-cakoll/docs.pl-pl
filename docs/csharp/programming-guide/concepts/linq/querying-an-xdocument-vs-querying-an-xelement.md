---
title: Wykonywanie zapytań dotyczących dokumentu XDocument a wykonywanie zapytań dotyczących elementu XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253141"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="22f79-102">Wykonywanie zapytań dotyczących dokumentu XDocument a wykonywanie zapytań dotyczących elementu XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="22f79-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="22f79-103">Podczas ładowania dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>za pośrednictwem , można zauważyć, że trzeba napisać <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>zapytania nieco inaczej niż podczas ładowania za pośrednictwem .</span><span class="sxs-lookup"><span data-stu-id="22f79-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="22f79-104">Porównanie XDocument.Load i XElement.Load</span><span class="sxs-lookup"><span data-stu-id="22f79-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="22f79-105">Po załadowaniu dokumentu XML <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>do <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement> via, w katalogu głównym drzewa XML zawiera element główny załadowanego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22f79-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="22f79-106">Jednak po załadowaniu tego samego <xref:System.Xml.Linq.XDocument> dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>XML do via <xref:System.Xml.Linq.XDocument> , katalog główny drzewa jest węzłem, a <xref:System.Xml.Linq.XElement> elementem głównym <xref:System.Xml.Linq.XDocument>załadowanego dokumentu jest jeden dozwolony węzeł podrzędny .</span><span class="sxs-lookup"><span data-stu-id="22f79-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="22f79-107">Osie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] działają względem węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="22f79-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="22f79-108">W tym pierwszym przykładzie wczytuje drzewo XML przy użyciu . <xref:System.Xml.Linq.XElement.Load%2A></span><span class="sxs-lookup"><span data-stu-id="22f79-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="22f79-109">Następnie kwerendy dla elementów podrzędnych katalogu głównego drzewa.</span><span class="sxs-lookup"><span data-stu-id="22f79-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="22f79-110">Zgodnie z oczekiwaniami w tym przykładzie daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="22f79-110">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="22f79-111">Poniższy przykład jest taki sam jak powyżej, z wyjątkiem drzewa XML <xref:System.Xml.Linq.XDocument> jest <xref:System.Xml.Linq.XElement>ładowany do zamiast .</span><span class="sxs-lookup"><span data-stu-id="22f79-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="22f79-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="22f79-112">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="22f79-113">Należy zauważyć, że ta `Root` sama kwerenda zwróciła jeden węzeł zamiast trzech węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="22f79-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="22f79-114">Jednym z podejść do radzenia <xref:System.Xml.Linq.XDocument.Root%2A> sobie z tym jest użycie właściwości przed dostępem do metod osi, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22f79-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="22f79-115">Ta kwerenda jest teraz wykonywana w taki sam <xref:System.Xml.Linq.XElement>sposób, jak kwerenda na drzewie zakorzenionym w programie .</span><span class="sxs-lookup"><span data-stu-id="22f79-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="22f79-116">W przykładzie przedstawiono następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="22f79-116">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  