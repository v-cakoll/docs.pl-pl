---
title: 'Porady: Użyj adnotacje do przekształcania LINQ do XML drzew stylów XSLT (C#)'
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 551be4fe39bcfc9fd5492366014322d78416ba58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328841"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="ff688-102">Porady: Użyj adnotacje do przekształcania LINQ do XML drzew stylów XSLT (C#)</span><span class="sxs-lookup"><span data-stu-id="ff688-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>
<span data-ttu-id="ff688-103">Adnotacje może służyć do ułatwienia transformacji XML drzewa.</span><span class="sxs-lookup"><span data-stu-id="ff688-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="ff688-104">Niektóre dokumenty XML to "dokument stanowi z zawartością mieszaną."</span><span class="sxs-lookup"><span data-stu-id="ff688-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="ff688-105">Z tych dokumentów nie zawsze wiadomo kształt podrzędny węzły elementu.</span><span class="sxs-lookup"><span data-stu-id="ff688-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="ff688-106">Na przykład węzeł, który zawiera tekst może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ff688-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="ff688-107">Dla dowolnego węzła podany tekst może być dowolną liczbę podrzędnych `<b>` i `<i>` elementy.</span><span class="sxs-lookup"><span data-stu-id="ff688-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="ff688-108">Takie podejście rozszerza wielu innych sytuacjach, takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak regularne akapitów, akapitów punktowanych i bitmapy.</span><span class="sxs-lookup"><span data-stu-id="ff688-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="ff688-109">Komórek w tabeli mogą zawierać tekstu, listy rozwijanej list i map bitowych.</span><span class="sxs-lookup"><span data-stu-id="ff688-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="ff688-110">Jedną z właściwości głównej dokumentu XML na to, nie wiadomo element podrzędny, które będzie mieć jeden z elementów.</span><span class="sxs-lookup"><span data-stu-id="ff688-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="ff688-111">Jeśli chcesz Przekształcanie elementów w drzewie, w którym niekoniecznie znasz te informacje o podrzędnych elementów, które chcesz przekształcić tej metody, która używa adnotacji jest efektywne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="ff688-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="ff688-112">Podsumowanie podejście jest:</span><span class="sxs-lookup"><span data-stu-id="ff688-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="ff688-113">Po pierwsze dodawać adnotacje elementów w drzewie z elementem zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="ff688-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="ff688-114">Po drugie iterację całe drzewo, tworzenie nowego drzewa, gdzie można zastąpić każdy element jego adnotacji.</span><span class="sxs-lookup"><span data-stu-id="ff688-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="ff688-115">W tym przykładzie implementuje iteracji i utworzenie nowego drzewa w funkcji o nazwie `XForm`.</span><span class="sxs-lookup"><span data-stu-id="ff688-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="ff688-116">Szczegółowo to rozwiązanie obejmuje:</span><span class="sxs-lookup"><span data-stu-id="ff688-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="ff688-117">Wykonanie co najmniej jednego składnika LINQ to XML zapytań, które zwracają zestaw elementów, które mają być Przekształć z jednego kształtu.</span><span class="sxs-lookup"><span data-stu-id="ff688-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="ff688-118">Dla każdego elementu w zapytaniu, Dodaj nową <xref:System.Xml.Linq.XElement> obiektu adnotacji do elementu.</span><span class="sxs-lookup"><span data-stu-id="ff688-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="ff688-119">Ten nowy element spowoduje zastąpienie adnotacjami elementu w drzewie nowy, po przekształceniu.</span><span class="sxs-lookup"><span data-stu-id="ff688-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="ff688-120">Jest to za pomocą prostego kodu do zapisu, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff688-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="ff688-121">Nowy element, który zostanie dodany jako adnotacja może zawierać nowe węzły podrzędne; utworzenia poddrzewa z dowolnego żądanego kształtu.</span><span class="sxs-lookup"><span data-stu-id="ff688-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="ff688-122">Jest specjalną regułę: Jeśli elementem podrzędnym nowego elementu jest w innej przestrzeni nazw przestrzeni nazw, która składa się w tym celu (w tym przykładzie przestrzeń nazw jest `http://www.microsoft.com/LinqToXmlTransform/2007`), następnie ten element podrzędny nie jest kopiowany do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="ff688-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="ff688-123">Zamiast tego, czy przestrzeń nazw jest wyżej specjalne przestrzeni nazw i nazwę lokalną elementu jest `ApplyTransforms`, a następnie węzły podrzędne elementu w drzewie źródła są iterowane i skopiowane do nowego drzew (z wyjątkiem, że adnotacji podrzędne elementy są samodzielnie przekształcone zgodnie z następującymi regułami).</span><span class="sxs-lookup"><span data-stu-id="ff688-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="ff688-124">Jest to przypomina specyfikację transformacje w XSL.</span><span class="sxs-lookup"><span data-stu-id="ff688-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="ff688-125">Zapytanie wybierające zestawu węzłów jest odpowiednikiem wyrażenie XPath dla szablonu.</span><span class="sxs-lookup"><span data-stu-id="ff688-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="ff688-126">Kod, aby utworzyć nowy <xref:System.Xml.Linq.XElement> zapisane jako adnotacja jest analogiczna do konstruktora sekwencji w XSL i `ApplyTransforms` element jest analogiczna w funkcji `xsl:apply-templates` element XSL.</span><span class="sxs-lookup"><span data-stu-id="ff688-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="ff688-127">Jedną z zalet tej metody - podczas wykonywania sformułować zapytań, są zawsze Pisanie zapytań w drzewie źródłowym zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="ff688-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="ff688-128">Nie muszą zwracaj wpływ zmiany w drzewie zapytań, które pisania.</span><span class="sxs-lookup"><span data-stu-id="ff688-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="ff688-129">Przekształcanie drzewa</span><span class="sxs-lookup"><span data-stu-id="ff688-129">Transforming a Tree</span></span>  
 <span data-ttu-id="ff688-130">W tym przykładzie pierwsze zmienia nazwę wszystkich `Paragraph` węzłów do `para`.</span><span class="sxs-lookup"><span data-stu-id="ff688-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement root = XElement.Parse(@"  
<Root>  
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
    <Paragraph>More text.</Paragraph>  
</Root>");  
  
// replace Paragraph with para  
foreach (var el in root.Descendants("Paragraph"))  
    el.AddAnnotation(  
        new XElement("para",  
            // same idea as xsl:apply-templates  
            new XElement(xf + "ApplyTransforms")  
        )  
    );  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newRoot = XForm(root);  
  
Console.WriteLine(newRoot);  
```  
  
 <span data-ttu-id="ff688-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ff688-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="ff688-132">Bardziej złożone przekształcenia</span><span class="sxs-lookup"><span data-stu-id="ff688-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="ff688-133">W poniższym przykładzie zapytanie drzewa i oblicza średnią i sumę `Data` elementów i dodaje je jako nowe elementy do drzewa.</span><span class="sxs-lookup"><span data-stu-id="ff688-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement data = new XElement("Root",  
    new XElement("Data", 20),  
    new XElement("Data", 10),  
    new XElement("Data", 3)  
);  
  
// while adding annotations, you can query the source tree all you want,  
// as the tree is not mutated while annotating.  
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average",  
            String.Format("{0:F4}",  
                data  
                .Elements("Data")  
                .Select(z => (Decimal)z)  
                .Average()  
            )  
        ),  
        new XElement("Sum",  
            data  
            .Elements("Data")  
            .Select(z => (int)z)  
            .Sum()  
        )  
    )  
);  
  
Console.WriteLine("Before Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(data);  
Console.WriteLine();  
Console.WriteLine();  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newData = XForm(data);  
  
Console.WriteLine("After Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="ff688-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ff688-134">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a><span data-ttu-id="ff688-135">Kilkukrotnie transformacji</span><span class="sxs-lookup"><span data-stu-id="ff688-135">Effecting the Transform</span></span>  
 <span data-ttu-id="ff688-136">Funkcja małe, `XForm`, tworzy nowe drzewo przekształcone z oryginalnego, adnotacjami drzewa.</span><span class="sxs-lookup"><span data-stu-id="ff688-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="ff688-137">Pseudo kod dla tej funkcji jest prosta:</span><span class="sxs-lookup"><span data-stu-id="ff688-137">The pseudo code for the function is quite simple:</span></span>  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 <span data-ttu-id="ff688-138">Poniżej znajduje się stosowania tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="ff688-138">Following is the implementation of this function:</span></span>  
  
```csharp  
// Build a transformed XML tree per the annotations  
static XElement XForm(XElement source)  
{  
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    XName at = xf + "ApplyTransforms";  
  
    if (source.Annotation<XElement>() != null)  
    {  
        XElement anno = source.Annotation<XElement>();  
        return new XElement(anno.Name,  
            anno.Attributes(),  
            anno  
            .Nodes()  
            .Select(  
                (XNode n) =>  
                {  
                    XElement annoEl = n as XElement;  
                    if (annoEl != null)  
                    {  
                        if (annoEl.Name == at)  
                            return (object)(  
                                source.Nodes()  
                                .Select(  
                                    (XNode n2) =>  
                                    {  
                                        XElement e2 = n2 as XElement;  
                                        if (e2 == null)  
                                            return n2;  
                                        else  
                                            return XForm(e2);  
                                    }  
                                )  
                            );  
                        else  
                            return n;  
                    }  
                    else  
                        return n;  
                }  
            )  
        );  
    }  
    else  
    {  
        return new XElement(source.Name,  
            source.Attributes(),  
            source  
                .Nodes()  
                .Select(n =>  
                {  
                    XElement el = n as XElement;  
                    if (el == null)  
                        return n;  
                    else  
                        return XForm(el);  
                }  
                )  
        );  
    }  
}   
```  
  
## <a name="complete-example"></a><span data-ttu-id="ff688-139">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="ff688-139">Complete Example</span></span>  
 <span data-ttu-id="ff688-140">Następujący kod jest pełny przykład, który zawiera `XForm` funkcji.</span><span class="sxs-lookup"><span data-stu-id="ff688-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="ff688-141">Zawiera kilka typowym zastosowaniem tego typu transformacji:</span><span class="sxs-lookup"><span data-stu-id="ff688-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Xml;  
using System.Xml.Linq;  
  
class Program  
{  
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    static XName at = xf + "ApplyTransforms";  
  
    // Build a transformed XML tree per the annotations  
    static XElement XForm(XElement source)  
    {  
        if (source.Annotation<XElement>() != null)  
        {  
            XElement anno = source.Annotation<XElement>();  
            return new XElement(anno.Name,  
                anno.Attributes(),  
                anno  
                .Nodes()  
                .Select(  
                    (XNode n) =>  
                    {  
                        XElement annoEl = n as XElement;  
                        if (annoEl != null)  
                        {  
                            if (annoEl.Name == at)  
                                return (object)(  
                                    source.Nodes()  
                                    .Select(  
                                        (XNode n2) =>  
                                        {  
                                            XElement e2 = n2 as XElement;  
                                            if (e2 == null)  
                                                return n2;  
                                            else  
                                                return XForm(e2);  
                                        }  
                                    )  
                                );  
                            else  
                                return n;  
                        }  
                        else  
                            return n;  
                    }  
                )  
            );  
        }  
        else  
        {  
            return new XElement(source.Name,  
                source.Attributes(),  
                source  
                    .Nodes()  
                    .Select(n =>  
                    {  
                        XElement el = n as XElement;  
                        if (el == null)  
                            return n;  
                        else  
                            return XForm(el);  
                    }  
                    )  
            );  
        }  
    }  
  
    static void Main(string[] args)  
    {  
        XElement root = new XElement("Root",  
            new XComment("A comment"),  
            new XAttribute("Att1", 123),  
            new XElement("Child", 1),  
            new XElement("Child", 2),  
            new XElement("Other",  
                new XElement("GC", 3),  
                new XElement("GC", 4)  
            ),  
            XElement.Parse(  
              "<SomeMixedContent>This is <i>an</i> element that " +  
              "<b>has</b> some mixed content</SomeMixedContent>"),  
            new XElement("AnUnchangedElement", 42)  
        );  
  
        // each of the following serves the same semantic purpose as  
        // XSLT templates and sequence constructors  
  
        // replace Child with NewChild  
        foreach (var el in root.Elements("Child"))  
            el.AddAnnotation(new XElement("NewChild", (string)el));  
  
        // replace first GC with GrandChild, add an attribute  
        foreach (var el in root.Descendants("GC").Take(1))  
            el.AddAnnotation(  
                new XElement("GrandChild",  
                    new XAttribute("ANewAttribute", 999),  
                    (string)el  
                )  
            );  
  
        // replace Other with NewOther, add new child elements around original content  
        foreach (var el in root.Elements("Other"))  
            el.AddAnnotation(  
                new XElement("NewOther",  
                    new XElement("MyNewChild", 1),  
                    // same idea as xsl:apply-templates  
                    new XElement(xf + "ApplyTransforms"),  
                    new XElement("ChildThatComesAfter")  
                )  
            );  
  
        // change name of element that has mixed content  
        root.Descendants("SomeMixedContent").First().AddAnnotation(  
            new XElement("MixedContent",  
                new XElement(xf + "ApplyTransforms")  
            )  
        );  
  
        // replace <b> with <Bold>  
        foreach (var el in root.Descendants("b"))  
            el.AddAnnotation(  
                new XElement("Bold",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        // replace <i> with <Italic>  
        foreach (var el in root.Descendants("i"))  
            el.AddAnnotation(  
                new XElement("Italic",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        Console.WriteLine("Before Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(root);  
        Console.WriteLine();  
        Console.WriteLine();  
        XElement newRoot = XForm(root);  
  
        Console.WriteLine("After Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(newRoot);  
    }  
}  
```  
  
 <span data-ttu-id="ff688-142">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ff688-142">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff688-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff688-143">See Also</span></span>  
 [<span data-ttu-id="ff688-144">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="ff688-144">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
