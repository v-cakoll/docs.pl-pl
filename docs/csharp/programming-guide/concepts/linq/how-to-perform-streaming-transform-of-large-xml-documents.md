---
title: 'Instrukcje: Wykonywanie przekształceń strumieniowych dużych dokumentów XML (C#)'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 8ddd7e25cf160526b741db5769a78682970c3724
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524679"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="68436-102">Instrukcje: Wykonywanie przekształceń strumieniowych dużych dokumentów XML (C#)</span><span class="sxs-lookup"><span data-stu-id="68436-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="68436-103">Czasami trzeba Przekształcanie dużych plików XML i pisania aplikacji, więc, że zużycie pamięci aplikacji jest przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="68436-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="68436-104">Jeśli zostanie podjęta próba wypełnianie drzewa XML z bardzo dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku (oznacza to, że nadmierne).</span><span class="sxs-lookup"><span data-stu-id="68436-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="68436-105">W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="68436-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="68436-106">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="68436-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="68436-107">Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="68436-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="68436-108">Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="68436-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="68436-109">Nawet w przypadku używania techniki opisanej w [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), Jeśli spróbujesz utworzyć drzewa XML zawierający przekształcone dokumentu jest zbyt duże użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="68436-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="68436-110">Dostępne są dwie główne opcje.</span><span class="sxs-lookup"><span data-stu-id="68436-110">There are two main approaches.</span></span> <span data-ttu-id="68436-111">Jedno z podejść jest użycie właściwości przetwarzanie odroczone <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="68436-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="68436-112">Innym rozwiązaniem jest utworzenie <xref:System.Xml.XmlWriter>oraz korzystać z możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisania elementów <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="68436-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="68436-113">W tym temacie przedstawiono oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="68436-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68436-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="68436-114">Example</span></span>  
 <span data-ttu-id="68436-115">Poniższy przykład opiera się na przykład w [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="68436-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="68436-116">W tym przykładzie użyto funkcji odroczonego wykonania <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="68436-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="68436-117">W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="68436-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="68436-118">Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`) napisano specjalnie tak, aby oczekuje, że dokument zawierający `Customer`, `Name`, i `Item` elementów i że tak jak w następującym dokumencie Source.xml rozmieszczenia tych elementów.</span><span class="sxs-lookup"><span data-stu-id="68436-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="68436-119">Bardziej niezawodna implementacji będzie jednak przygotowane przeanalizować nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="68436-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="68436-120">Dokument źródłowy Source.xml jest następująca:</span><span class="sxs-lookup"><span data-stu-id="68436-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="68436-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="68436-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="68436-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="68436-122">Example</span></span>  
 <span data-ttu-id="68436-123">Poniższy przykład opiera się również na przykład w [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="68436-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="68436-124">W tym przykładzie użyto możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisania elementów <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="68436-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="68436-125">W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="68436-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="68436-126">Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`) napisano specjalnie tak, aby oczekuje, że dokument zawierający `Customer`, `Name`, i `Item` elementów i że tak jak w następującym dokumencie Source.xml rozmieszczenia tych elementów.</span><span class="sxs-lookup"><span data-stu-id="68436-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="68436-127">Jednak implementacja bardziej niezawodne, albo czy sprawdzanie poprawności dokumentu źródłowego przy użyciu XSD lub jest gotowy do analizowania nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="68436-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="68436-128">W tym przykładzie użyto tego samego dokumentu źródłowego Source.xml, jak w poprzednim przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="68436-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="68436-129">Generuje ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="68436-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="68436-130">Za pomocą <xref:System.Xml.Linq.XStreamingElement> dla przesyłania strumieniowego wyjściowy plik XML jest preferowana względem zapisywania <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="68436-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="68436-131">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="68436-131">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68436-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68436-132">See also</span></span>

- [<span data-ttu-id="68436-133">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="68436-133">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
