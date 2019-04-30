---
title: Tworzenie zapytań dotyczących elementu XDocument a Podczas badania XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 125b0811296695a0909f804931e0caca81f63df6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680782"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="c2205-102">Tworzenie zapytań dotyczących elementu XDocument a Podczas badania XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="c2205-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="c2205-103">Podczas ładowania dokumentu za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, zauważysz, trzeba nieco inaczej niż podczas ładowania za pośrednictwem pisać zapytania <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2205-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="c2205-104">Porównanie XDocument.Load i XElement.Load</span><span class="sxs-lookup"><span data-stu-id="c2205-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="c2205-105">Podczas ładowania dokumentu XML do <xref:System.Xml.Linq.XElement> za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> w katalogu głównym pliku XML drzewo zawiera element główny dokumentu załadowane.</span><span class="sxs-lookup"><span data-stu-id="c2205-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="c2205-106">Jednak podczas ładowania tego samego dokumentu XML do <xref:System.Xml.Linq.XDocument> za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, katalog główny drzewa jest <xref:System.Xml.Linq.XDocument> węzłem, a element główny dokumentu załadować jest jeden element podrzędny z dozwolonych <xref:System.Xml.Linq.XElement> węzła <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="c2205-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="c2205-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osi działać względem węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="c2205-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="c2205-108">W pierwszym przykładzie ładuje drzewa XML przy użyciu <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2205-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="c2205-109">Następnie zapytania dotyczące elementów podrzędnych katalogu głównego drzewa.</span><span class="sxs-lookup"><span data-stu-id="c2205-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="c2205-110">Zgodnie z oczekiwaniami, ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c2205-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="c2205-111">Poniższy przykład jest taki sam jak ten powyżej, z wyjątkiem, że drzewa XML jest ładowany do <xref:System.Xml.Linq.XDocument> zamiast <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c2205-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="c2205-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c2205-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="c2205-113">Zwróć uwagę, tego samego zapytania zwrócony jeden `Root` węzła zamiast trzech węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c2205-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="c2205-114">Jedno z podejść do radzenia sobie z tym jest użycie <xref:System.Xml.Linq.XDocument.Root%2A> właściwości przed uzyskaniem dostępu do metody osi:</span><span class="sxs-lookup"><span data-stu-id="c2205-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="c2205-115">To zapytanie wykonuje teraz w taki sam sposób jak zapytania drzewa osadzonego w <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c2205-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c2205-116">Przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c2205-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2205-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2205-117">See also</span></span>

- [<span data-ttu-id="c2205-118">Podstawowe zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c2205-118">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
