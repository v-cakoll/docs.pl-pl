---
title: Jak strumieniowo fragmenty XML z elementu XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714651"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="91741-102">Jak strumieniowo fragmenty XML z elementu XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="91741-102">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="91741-103">W przypadku konieczności przetworzenia dużych plików XML może nie być możliwe załadowanie całego drzewa XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="91741-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="91741-104">W tym temacie pokazano, jak przesyłać fragmenty strumieni przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="91741-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="91741-105">Jednym z najbardziej skutecznych sposobów używania <xref:System.Xml.XmlReader> do odczytu obiektów <xref:System.Xml.Linq.XElement> jest pisanie własnej niestandardowej metody osi.</span><span class="sxs-lookup"><span data-stu-id="91741-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="91741-106">Metoda osi zwykle zwraca kolekcję, taką jak <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="91741-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="91741-107">W metodzie osi niestandardowej po utworzeniu fragmentu kodu XML przez wywołanie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> Zwróć kolekcję przy użyciu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="91741-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="91741-108">Zapewnia to odroczoną semantykę wykonania do niestandardowej metody osi.</span><span class="sxs-lookup"><span data-stu-id="91741-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="91741-109">Podczas tworzenia drzewa XML na podstawie obiektu <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReader> musi być umieszczony w elemencie.</span><span class="sxs-lookup"><span data-stu-id="91741-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="91741-110">Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nie zwraca do momentu odczytania tagu zamknięcia elementu.</span><span class="sxs-lookup"><span data-stu-id="91741-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="91741-111">Jeśli chcesz utworzyć częściowe drzewo, Utwórz wystąpienie <xref:System.Xml.XmlReader>, umieść czytnik w węźle, który ma zostać przekonwertowany na drzewo <xref:System.Xml.Linq.XElement>, a następnie Utwórz obiekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="91741-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="91741-112">Temat [jak przesyłać fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i przykład na potrzeby przesyłania strumieniowego bardziej złożonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="91741-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="91741-113">Temat [jak wykonywać transformację strumieniową dużych dokumentów XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład użycia LINQ to XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="91741-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91741-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="91741-114">Example</span></span>  
 <span data-ttu-id="91741-115">W tym przykładzie jest tworzona Metoda osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="91741-115">This example creates a custom axis method.</span></span> <span data-ttu-id="91741-116">Zapytanie można wykonać za pomocą zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="91741-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="91741-117">Metoda osi niestandardowej, `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytywania dokumentu, który ma powtarzający się element `Child`.</span><span class="sxs-lookup"><span data-stu-id="91741-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="91741-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="91741-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="91741-119">W tym przykładzie dokument źródłowy jest bardzo mały.</span><span class="sxs-lookup"><span data-stu-id="91741-119">In this example, the source document is very small.</span></span> <span data-ttu-id="91741-120">Jednak nawet jeśli wystąpiły miliony elementów `Child`, ten przykład nadal ma niewielki wpływ na pamięć.</span><span class="sxs-lookup"><span data-stu-id="91741-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
