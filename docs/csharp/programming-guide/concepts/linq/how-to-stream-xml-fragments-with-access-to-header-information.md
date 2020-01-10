---
title: Jak przesyłać fragmenty XML z dostępem do informacji nagłówka (C#)
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712393"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="2aa95-102">Jak przesyłać fragmenty XML z dostępem do informacji nagłówka (C#)</span><span class="sxs-lookup"><span data-stu-id="2aa95-102">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="2aa95-103">Czasami konieczne jest odczytanie arbitralnie dużych plików XML i zapisanie aplikacji w celu przewidzenia rozmiaru pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2aa95-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="2aa95-104">W przypadku próby wypełnienia drzewa XML przy użyciu dużego pliku XML użycie pamięci będzie proporcjonalne do rozmiaru pliku, czyli nadmierne.</span><span class="sxs-lookup"><span data-stu-id="2aa95-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="2aa95-105">W związku z tym należy zamiast tego użyć techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2aa95-105">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="2aa95-106">Jedną z opcji jest zapisanie aplikacji przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="2aa95-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2aa95-107">Można jednak użyć LINQ do wykonywania zapytań w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="2aa95-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="2aa95-108">W takim przypadku można napisać własną metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="2aa95-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="2aa95-109">Aby uzyskać więcej informacji, zobacz [jak napisać metodę osi LINQ to XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="2aa95-109">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="2aa95-110">Aby napisać własną metodę osi, napisz małą metodę, która używa <xref:System.Xml.XmlReader> do odczytywania węzłów do momentu osiągnięcia jednego z węzłów, w których interesują Cię zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="2aa95-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="2aa95-111">Metoda następnie wywołuje <xref:System.Xml.Linq.XNode.ReadFrom%2A>, który odczytuje z <xref:System.Xml.XmlReader> i tworzy wystąpienie fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="2aa95-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="2aa95-112">Następnie przekazuje każdą z nich `yield return` do metody, która wylicza metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="2aa95-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="2aa95-113">Następnie można napisać zapytania LINQ na niestandardowej metodzie osi.</span><span class="sxs-lookup"><span data-stu-id="2aa95-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="2aa95-114">Techniki przesyłania strumieniowego najlepiej zastosować w sytuacjach, gdy trzeba przetwarzać dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2aa95-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="2aa95-115">Niektóre standardowe operatory zapytań, takie jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródła, zbierają wszystkie dane, sortują je, a następnie zwracają pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="2aa95-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="2aa95-116">Jeśli używasz operatora zapytania, który materializuje jego źródło przed uzyskaniem pierwszego elementu, nie zostanie zachowana mała ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="2aa95-116">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aa95-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aa95-117">Example</span></span>  

<span data-ttu-id="2aa95-118">Czasami problem jest znacznie bardziej interesujący.</span><span class="sxs-lookup"><span data-stu-id="2aa95-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="2aa95-119">W poniższym dokumencie XML konsument niestandardowej metody osi musi znać nazwę klienta, do którego należy każdy element.</span><span class="sxs-lookup"><span data-stu-id="2aa95-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="2aa95-120">Podejście, które ten przykład przyjmuje, ma również na celu śledzenie informacji o tym nagłówku, zapisanie informacji nagłówka, a następnie utworzenie małego drzewa XML zawierającego zarówno informacje nagłówka, jak i szczegóły wyliczane.</span><span class="sxs-lookup"><span data-stu-id="2aa95-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="2aa95-121">Następnie metoda osi daje nowe, małe drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="2aa95-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="2aa95-122">Następnie zapytanie ma dostęp do informacji nagłówka oraz informacji szczegółowych.</span><span class="sxs-lookup"><span data-stu-id="2aa95-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="2aa95-123">Takie podejście ma niewielkie rozmiary pamięci.</span><span class="sxs-lookup"><span data-stu-id="2aa95-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="2aa95-124">Ze względu na to, że każdy szczegółowy fragment kodu XML jest przewidziany, żadne odwołania nie są przechowywane w poprzednim fragmencie i jest dostępny do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2aa95-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="2aa95-125">Ta technika tworzy wiele krótkoterminowych obiektów na stercie.</span><span class="sxs-lookup"><span data-stu-id="2aa95-125">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="2aa95-126">Poniższy przykład przedstawia sposób implementacji i używania niestandardowej metody osi, która strumieniuje fragmenty XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="2aa95-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="2aa95-127">Ta niestandardowa oś jest zapisywana w taki sposób, że oczekuje dokumentu, który ma `Customer`, `Name`i `Item` elementów oraz że te elementy zostaną ułożone tak jak w powyższym `Source.xml` dokumencie.</span><span class="sxs-lookup"><span data-stu-id="2aa95-127">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="2aa95-128">Jest to implementacja uproszczony.</span><span class="sxs-lookup"><span data-stu-id="2aa95-128">It is a simplistic implementation.</span></span> <span data-ttu-id="2aa95-129">Bardziej niezawodna implementacja zostanie przygotowana do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2aa95-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="2aa95-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2aa95-130">This code produces the following output:</span></span>  
  
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
