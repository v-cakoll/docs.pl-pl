---
title: Jak przeprowadzić transformację strumieniową dużych dokumentów XML (C#)
description: Dowiedz się, jak wykonać transmisję strumienia tekstu do pliku XML w języku C#, aby uniknąć nadmiernego wykorzystania pamięci dla niektórych plików.
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: e1ab2866079b2244dc764271d7ba63173349e2f3
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104869"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="a7ac2-103">Jak przeprowadzić transformację strumieniową dużych dokumentów XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a7ac2-103">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="a7ac2-104">Czasami konieczne jest przekształcenie dużych plików XML i zapisanie aplikacji w celu przewidzenia rozmiaru pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-104">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="a7ac2-105">Jeśli spróbujesz wypełnić drzewo XML bardzo dużym plikiem XML, użycie pamięci będzie proporcjonalne do rozmiaru pliku (to jest zbyt duże).</span><span class="sxs-lookup"><span data-stu-id="a7ac2-105">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="a7ac2-106">W związku z tym należy zamiast tego użyć techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-106">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="a7ac2-107">Techniki przesyłania strumieniowego najlepiej zastosować w sytuacjach, gdy trzeba przetwarzać dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-107">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="a7ac2-108">Niektóre standardowe operatory zapytań, takie jak <xref:System.Linq.Enumerable.OrderBy%2A> , iteruje źródło, zbierają wszystkie dane, sortują je, a następnie zwracają pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-108">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="a7ac2-109">Należy pamiętać, że jeśli używasz operatora zapytania, który materializuje jego źródło przed uzyskaniem pierwszego elementu, nie będzie zachowana mała ilość pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-109">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="a7ac2-110">Nawet jeśli używasz techniki opisanej w artykule [Jak przesłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), jeśli próbujesz utworzyć drzewo XML zawierające przekształcony dokument, użycie pamięci będzie zbyt duże.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-110">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="a7ac2-111">Istnieją dwa główne podejścia.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-111">There are two main approaches.</span></span> <span data-ttu-id="a7ac2-112">Jednym z metod jest użycie odroczonych charakterystyk przetwarzania <xref:System.Xml.Linq.XStreamingElement> .</span><span class="sxs-lookup"><span data-stu-id="a7ac2-112">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="a7ac2-113">Innym rozwiązaniem jest utworzenie <xref:System.Xml.XmlWriter> i użycie funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisu elementów do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="a7ac2-113">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="a7ac2-114">W tym temacie przedstawiono oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-114">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7ac2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7ac2-115">Example</span></span>  
 <span data-ttu-id="a7ac2-116">Poniższy przykład kompiluje w przykładzie [przesyłania strumieniowego XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="a7ac2-116">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="a7ac2-117">W tym przykładzie zastosowano opóźnione funkcje wykonywania <xref:System.Xml.Linq.XStreamingElement> w celu przesyłania strumieniowego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-117">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="a7ac2-118">W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-118">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="a7ac2-119">Należy zauważyć, że niestandardowa oś () została zaprojektowana w `StreamCustomerItem` taki sposób, aby oczekuje dokumentu, `Customer` `Name` , i `Item` elementów, i że te elementy będą ułożone jak w poniższym Source.xml dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-119">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="a7ac2-120">Jednak bardziej niezawodna implementacja zostanie przygotowana do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-120">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="a7ac2-121">Poniżej znajduje się dokument źródłowy, Source.xml:</span><span class="sxs-lookup"><span data-stu-id="a7ac2-121">The following is the source document, Source.xml:</span></span>  
  
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
                        if (item != null)  
                        {  
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
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 <span data-ttu-id="a7ac2-122">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="a7ac2-122">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="a7ac2-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7ac2-123">Example</span></span>  
<span data-ttu-id="a7ac2-124">W poniższym przykładzie pokazano również, [Jak przesłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="a7ac2-124">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="a7ac2-125">Ten przykład używa funkcji, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Aby pisać elementy do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="a7ac2-125">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="a7ac2-126">W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-126">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="a7ac2-127">Należy zauważyć, że niestandardowa oś () została zaprojektowana w `StreamCustomerItem` taki sposób, aby oczekuje dokumentu, `Customer` `Name` , i `Item` elementów, i że te elementy będą ułożone jak w poniższym Source.xml dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-127">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="a7ac2-128">Bardziej niezawodna implementacja może jednak spowodować sprawdzenie poprawności dokumentu źródłowego przy użyciu XSD lub przygotowania do przeanalizowania nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-128">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="a7ac2-129">Ten przykład używa tego samego dokumentu źródłowego, Source.xml, jak w poprzednim przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-129">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="a7ac2-130">Generuje również dokładnie te same dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a7ac2-130">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="a7ac2-131">Użycie <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego wyjściowego pliku XML jest preferowany przez zapis do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="a7ac2-131">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 <span data-ttu-id="a7ac2-132">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="a7ac2-132">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  