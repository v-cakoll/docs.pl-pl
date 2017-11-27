---
title: "Porady: wykonaj przesyłania strumieniowego transformacji dokumentów XML duże (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1f3bc1876097474eae6f329711139a2f3797db97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="01c38-102">Porady: wykonaj przesyłania strumieniowego transformacji dokumentów XML duże (C#)</span><span class="sxs-lookup"><span data-stu-id="01c38-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="01c38-103">Czasami trzeba transformacji dużych plików XML i zapisać aplikacji, dzięki czemu zużycie pamięci aplikacji jest atrybutem wartości prognozowanych.</span><span class="sxs-lookup"><span data-stu-id="01c38-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="01c38-104">Jeśli spróbujesz wypełnić drzewo XML z bardzo dużych plików XML, użycie pamięci będzie proporcjonalny do rozmiaru pliku (to znaczy nadmiernego).</span><span class="sxs-lookup"><span data-stu-id="01c38-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="01c38-105">W związku z tym należy w zamian użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="01c38-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="01c38-106">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy musisz przetworzyć dokumentu źródłowego tylko raz i może przetwarzać elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="01c38-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="01c38-107">Niektóre standardowy kwerendy operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródłem Zbieraj wszystkie dane, sortowanie ich i ostatecznie yield pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="01c38-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="01c38-108">Należy pamiętać, że użycie operatora zapytania, który zostaje źródła przed reaguje pierwszy element można nie zostaną zachowane zużycie pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01c38-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="01c38-109">Nawet jeśli używasz techniki opisane w [porady: fragmenty XML strumienia z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), jeśli użytkownik próbuje utworzyć drzewa XML, który zawiera dokument przekształcone, pamięci, użycie jest zbyt duża.</span><span class="sxs-lookup"><span data-stu-id="01c38-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="01c38-110">Istnieją dwie metody głównej.</span><span class="sxs-lookup"><span data-stu-id="01c38-110">There are two main approaches.</span></span> <span data-ttu-id="01c38-111">Jednym z podejść jest użycie właściwości przetwarzania odroczonego <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="01c38-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="01c38-112">Innym rozwiązaniem jest utworzenie <xref:System.Xml.XmlWriter>i korzystanie z możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w trybie zapisywania elementów do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="01c38-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="01c38-113">W tym temacie przedstawiono obu podejść.</span><span class="sxs-lookup"><span data-stu-id="01c38-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01c38-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="01c38-114">Example</span></span>  
 <span data-ttu-id="01c38-115">Poniższy przykład tworzy na przykład w [porady: strumień fragmenty XML z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="01c38-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="01c38-116">W tym przykładzie użyto możliwości wykonanie odroczone <xref:System.Xml.Linq.XStreamingElement> do strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="01c38-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="01c38-117">W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="01c38-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="01c38-118">Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`), aby oczekuje, że dokument jest opracowane specjalnie mający `Customer`, `Name`, i `Item` elementy i rozmieszczenia tych elementów, jak w następującym dokumencie Source.xml.</span><span class="sxs-lookup"><span data-stu-id="01c38-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="01c38-119">Implementacja bardziej niezawodne, może jednak przygotowane do analizy nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="01c38-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="01c38-120">Poniżej przedstawiono dokument źródłowy Source.xml:</span><span class="sxs-lookup"><span data-stu-id="01c38-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="01c38-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="01c38-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="01c38-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="01c38-122">Example</span></span>  
 <span data-ttu-id="01c38-123">Poniższy przykład tworzy się również na przykład w [porady: strumień fragmenty XML z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="01c38-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="01c38-124">W tym przykładzie użyto możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w trybie zapisywania elementów do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="01c38-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="01c38-125">W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="01c38-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="01c38-126">Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`), aby oczekuje, że dokument jest opracowane specjalnie mający `Customer`, `Name`, i `Item` elementy i rozmieszczenia tych elementów, jak w następującym dokumencie Source.xml.</span><span class="sxs-lookup"><span data-stu-id="01c38-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="01c38-127">Jednak implementacja bardziej niezawodne, czy albo sprawdza, czy dokument źródłowy schematu XSD lub jest gotowy do analizy nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="01c38-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="01c38-128">W tym przykładzie używa tego samego dokumentu źródłowego Source.xml, co w poprzednim przykładzie, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="01c38-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="01c38-129">Tworzy dokładnie tych samych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="01c38-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="01c38-130">Przy użyciu <xref:System.Xml.Linq.XStreamingElement> do strumienia wyjściowego XML jest preferowane zapisywania <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="01c38-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="01c38-131">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="01c38-131">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01c38-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01c38-132">See Also</span></span>  
 [<span data-ttu-id="01c38-133">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="01c38-133">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
