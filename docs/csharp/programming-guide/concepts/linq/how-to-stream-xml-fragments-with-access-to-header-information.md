---
title: 'Instrukcje: Strumieniowe fragmenty XML z dostępem do informacji nagłówkaC#()'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d40fa5b7ae60836c0fd947d36f88765eafc60334
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592339"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="931d0-102">Instrukcje: Strumieniowe fragmenty XML z dostępem do informacji nagłówkaC#()</span><span class="sxs-lookup"><span data-stu-id="931d0-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="931d0-103">Czasami konieczne jest odczytanie arbitralnie dużych plików XML i zapisanie aplikacji w celu przewidzenia rozmiaru pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="931d0-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="931d0-104">W przypadku próby wypełnienia drzewa XML przy użyciu dużego pliku XML użycie pamięci będzie proporcjonalne do rozmiaru pliku, czyli nadmierne.</span><span class="sxs-lookup"><span data-stu-id="931d0-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="931d0-105">W związku z tym należy zamiast tego użyć techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="931d0-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="931d0-106">Jedną z opcji jest zapisanie aplikacji przy <xref:System.Xml.XmlReader>użyciu programu.</span><span class="sxs-lookup"><span data-stu-id="931d0-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="931d0-107">Można jednak użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , aby zbadać drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="931d0-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="931d0-108">W takim przypadku można napisać własną metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="931d0-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="931d0-109">Aby uzyskać więcej informacji, zobacz [jak: Napisz metodę osi LINQ to XML (C#).](./how-to-write-a-linq-to-xml-axis-method.md)</span><span class="sxs-lookup"><span data-stu-id="931d0-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="931d0-110">Aby napisać własną metodę osi, napisz małą metodę, która używa <xref:System.Xml.XmlReader> do odczytu węzłów do momentu osiągnięcia jednego z węzłów, w których Cię interesują.</span><span class="sxs-lookup"><span data-stu-id="931d0-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="931d0-111">Metoda następnie wywołuje <xref:System.Xml.Linq.XNode.ReadFrom%2A>, który odczytuje <xref:System.Xml.XmlReader> z i tworzy wystąpienie fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="931d0-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="931d0-112">Następnie przekazuje każdy fragment `yield return` do metody, która wylicza metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="931d0-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="931d0-113">Następnie można napisać zapytania LINQ na niestandardowej metodzie osi.</span><span class="sxs-lookup"><span data-stu-id="931d0-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="931d0-114">Techniki przesyłania strumieniowego najlepiej zastosować w sytuacjach, gdy trzeba przetwarzać dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="931d0-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="931d0-115">Niektóre standardowe operatory zapytań, takie jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteruje źródło, zbierają wszystkie dane, sortują je, a następnie zwracają pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="931d0-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="931d0-116">Należy pamiętać, że jeśli używasz operatora zapytania, który materializuje jego źródło przed uzyskaniem pierwszego elementu, nie będzie zachowana mała ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="931d0-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="931d0-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="931d0-117">Example</span></span>  
 <span data-ttu-id="931d0-118">Czasami problem jest znacznie bardziej interesujący.</span><span class="sxs-lookup"><span data-stu-id="931d0-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="931d0-119">W poniższym dokumencie XML konsument niestandardowej metody osi musi znać nazwę klienta, do którego należy każdy element.</span><span class="sxs-lookup"><span data-stu-id="931d0-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="931d0-120">Podejście, które ten przykład przyjmuje, ma również na celu śledzenie informacji o tym nagłówku, zapisanie informacji nagłówka, a następnie utworzenie małego drzewa XML zawierającego zarówno informacje nagłówka, jak i szczegóły wyliczane.</span><span class="sxs-lookup"><span data-stu-id="931d0-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="931d0-121">Następnie metoda osi daje nowe, małe drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="931d0-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="931d0-122">Następnie zapytanie ma dostęp do informacji nagłówka oraz informacji szczegółowych.</span><span class="sxs-lookup"><span data-stu-id="931d0-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="931d0-123">Takie podejście ma niewielkie rozmiary pamięci.</span><span class="sxs-lookup"><span data-stu-id="931d0-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="931d0-124">Ze względu na to, że każdy szczegółowy fragment kodu XML jest przewidziany, żadne odwołania nie są przechowywane w poprzednim fragmencie i jest dostępny do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="931d0-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="931d0-125">Należy zauważyć, że ta technika tworzy wiele obiektów krótkotrwałych na stercie.</span><span class="sxs-lookup"><span data-stu-id="931d0-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="931d0-126">Poniższy przykład przedstawia sposób implementacji i używania niestandardowej metody osi, która strumieniuje fragmenty XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="931d0-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="931d0-127">Ta oś niestandardowa jest zapisywana w taki sposób, że oczekuje dokumentu `Customer` `Name`,, i `Item` elementów, i że te elementy będą ułożone jak w powyższym `Source.xml` dokumencie.</span><span class="sxs-lookup"><span data-stu-id="931d0-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="931d0-128">Jest to implementacja uproszczony.</span><span class="sxs-lookup"><span data-stu-id="931d0-128">It is a simplistic implementation.</span></span> <span data-ttu-id="931d0-129">Bardziej niezawodna implementacja zostanie przygotowana do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="931d0-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="931d0-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="931d0-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  