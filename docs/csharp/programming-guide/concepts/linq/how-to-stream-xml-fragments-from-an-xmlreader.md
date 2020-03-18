---
title: Jak przesyłać strumieniowo fragmenty XML z czytnika XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714651"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="0ce46-102">Jak przesyłać strumieniowo fragmenty XML z czytnika XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="0ce46-102">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="0ce46-103">Gdy trzeba przetworzyć duże pliki XML, może nie być możliwe załadowanie całego drzewa XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="0ce46-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="0ce46-104">W tym temacie pokazano, <xref:System.Xml.XmlReader>jak przesyłać strumieniowo fragmenty przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="0ce46-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="0ce46-105">Jednym z najbardziej skutecznych <xref:System.Xml.XmlReader> sposobów <xref:System.Xml.Linq.XElement> używania do odczytu obiektów jest napisać własną metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="0ce46-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="0ce46-106">Metoda osi zazwyczaj zwraca kolekcję, takich jak <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="0ce46-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="0ce46-107">W metodzie osi niestandardowej po utworzeniu fragmentu XML przez wywołanie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody, zwróć kolekcję przy użyciu . `yield return`</span><span class="sxs-lookup"><span data-stu-id="0ce46-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="0ce46-108">Zapewnia to semantyki odroczonego wykonania do metody osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="0ce46-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="0ce46-109">Podczas tworzenia drzewa XML <xref:System.Xml.XmlReader> z obiektu, <xref:System.Xml.XmlReader> musi być umieszczony na elemencie.</span><span class="sxs-lookup"><span data-stu-id="0ce46-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="0ce46-110">Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nie zwraca, dopóki nie odczytał tag zamknięcia elementu.</span><span class="sxs-lookup"><span data-stu-id="0ce46-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="0ce46-111">Jeśli chcesz utworzyć częściowe drzewo, możesz utworzyć wystąpienie <xref:System.Xml.XmlReader>czytnika w węźle, który chcesz <xref:System.Xml.Linq.XElement> przekonwertować na <xref:System.Xml.Linq.XElement> drzewo, a następnie utworzyć obiekt.</span><span class="sxs-lookup"><span data-stu-id="0ce46-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="0ce46-112">Temat [Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i przykład sposobu przesyłania strumieniowego bardziej złożonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0ce46-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="0ce46-113">Temat [Jak wykonać transformację przesyłania strumieniowego dużych dokumentów XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład użycia LINQ do XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="0ce46-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce46-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ce46-114">Example</span></span>  
 <span data-ttu-id="0ce46-115">W tym przykładzie tworzy metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="0ce46-115">This example creates a custom axis method.</span></span> <span data-ttu-id="0ce46-116">Można go zbadać za pomocą kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="0ce46-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="0ce46-117">Metoda osi niestandardowej , jest metodą, `StreamRootChildDoc`która jest przeznaczona specjalnie do `Child` odczytu dokumentu, który ma element powtarzający.</span><span class="sxs-lookup"><span data-stu-id="0ce46-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="0ce46-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0ce46-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="0ce46-119">W tym przykładzie dokument źródłowy jest bardzo mały.</span><span class="sxs-lookup"><span data-stu-id="0ce46-119">In this example, the source document is very small.</span></span> <span data-ttu-id="0ce46-120">Jednak nawet jeśli istnieją `Child` miliony elementów, w tym przykładzie nadal będzie miał niewielki rozmiar pamięci.</span><span class="sxs-lookup"><span data-stu-id="0ce46-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
