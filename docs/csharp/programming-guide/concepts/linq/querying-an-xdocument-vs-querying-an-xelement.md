---
title: Kwerenda vs klasy XDocument. Wykonywanie zapytania XElement (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b315a9b298a786cbb78eb18efd4ecf3ea8e0b90c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="d27d6-102">Kwerenda vs klasy XDocument. Wykonywanie zapytania XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="d27d6-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="d27d6-103">Podczas ładowania dokumentu za pomocą <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, zauważysz, trzeba pisać zapytania nieco inaczej niż podczas ładowania za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d27d6-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="d27d6-104">Porównanie XDocument.Load i XElement.Load</span><span class="sxs-lookup"><span data-stu-id="d27d6-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="d27d6-105">Podczas ładowania dokumentu XML do <xref:System.Xml.Linq.XElement> za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> w katalogu głównym pliku XML drzewo zawiera element główny załadowanego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d27d6-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="d27d6-106">Jednak podczas ładowania tego samego dokumentu XML do <xref:System.Xml.Linq.XDocument> za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, katalog główny drzewa jest <xref:System.Xml.Linq.XDocument> węzła i element główny załadowanego dokumentu jest jeden element podrzędny dozwolonych <xref:System.Xml.Linq.XElement> węzła <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d27d6-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="d27d6-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osie działać względem węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="d27d6-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="d27d6-108">W tym przykładzie pierwsze ładuje drzewa XML przy użyciu <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="d27d6-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="d27d6-109">Następnie zapytania dotyczące elementów podrzędnych katalogu głównego drzewa.</span><span class="sxs-lookup"><span data-stu-id="d27d6-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="d27d6-110">Zgodnie z oczekiwaniami, w tym przykładzie tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d27d6-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="d27d6-111">Poniższy przykład jest taki sam, jak powyżej, z wyjątkiem ładowanej drzewa XML do <xref:System.Xml.Linq.XDocument> zamiast <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d27d6-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="d27d6-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d27d6-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="d27d6-113">Zwróć uwagę, samo zapytanie zwrócony jeden `Root` węzła zamiast trzech węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d27d6-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="d27d6-114">Jeden ze sposobów postępowania z tym jest użycie <xref:System.Xml.Linq.XDocument.Root%2A> właściwości przed uzyskaniem dostępu do metody osi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d27d6-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d27d6-115">To zapytanie wykonuje obecnie w taki sam sposób jak zapytania na drzewo umieszczone w <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d27d6-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="d27d6-116">Przykład tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d27d6-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d27d6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d27d6-117">See Also</span></span>  
 [<span data-ttu-id="d27d6-118">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d27d6-118">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
