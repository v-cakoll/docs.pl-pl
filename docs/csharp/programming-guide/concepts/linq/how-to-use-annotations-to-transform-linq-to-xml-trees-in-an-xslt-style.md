---
title: Jak używać adnotacji do przekształcania linq do drzew XML w stylu XSLT (C#)
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 7d6d646bb9b7b344750c22cb24bc81999da5210d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168560"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="3be7f-102">Jak używać adnotacji do przekształcania linq do drzew XML w stylu XSLT (C#)</span><span class="sxs-lookup"><span data-stu-id="3be7f-102">How to use annotations to transform LINQ to XML trees in an XSLT style (C#)</span></span>
<span data-ttu-id="3be7f-103">Adnotacje mogą służyć do ułatwienia przekształcenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3be7f-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="3be7f-104">Niektóre dokumenty XML są "skoncentrowane na dokumencie z zawartością mieszaną".</span><span class="sxs-lookup"><span data-stu-id="3be7f-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="3be7f-105">W przypadku takich dokumentów niekoniecznie znasz kształt węzłów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="3be7f-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="3be7f-106">Na przykład węzeł zawierający tekst może wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="3be7f-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="3be7f-107">Dla dowolnego węzła tekstowego może istnieć `<b>` `<i>` dowolna liczba elementów podrzędnych i elementów.</span><span class="sxs-lookup"><span data-stu-id="3be7f-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="3be7f-108">Takie podejście obejmuje wiele innych sytuacji, takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak zwykłe akapity, akapity punktowane i mapy bitowe.</span><span class="sxs-lookup"><span data-stu-id="3be7f-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="3be7f-109">Komórki w tabeli mogą zawierać tekst, listy rozwijane lub mapy bitowe.</span><span class="sxs-lookup"><span data-stu-id="3be7f-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="3be7f-110">Jedną z podstawowych cech dokumentu centric XML jest to, że nie wiadomo, który element podrzędny będzie miał dowolny element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="3be7f-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="3be7f-111">Jeśli chcesz przekształcić elementy w drzewie, gdzie niekoniecznie wiesz zbyt wiele o elementach podrzędnych elementów, które chcesz przekształcić, to takie podejście, które używa adnotacji jest skuteczne podejście.</span><span class="sxs-lookup"><span data-stu-id="3be7f-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="3be7f-112">Podsumowanie podejścia jest następujące:</span><span class="sxs-lookup"><span data-stu-id="3be7f-112">The summary of the approach is:</span></span>  
  
- <span data-ttu-id="3be7f-113">Najpierw należy adnotować elementy w drzewie za pomocą elementu zastępczego.</span><span class="sxs-lookup"><span data-stu-id="3be7f-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
- <span data-ttu-id="3be7f-114">Po drugie, iterate przez całe drzewo, tworząc nowe drzewo, w którym można zastąpić każdy element z jego adnotacji.</span><span class="sxs-lookup"><span data-stu-id="3be7f-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="3be7f-115">W tym przykładzie implementuje iteracji i tworzenia nowego `XForm`drzewa w funkcji o nazwie .</span><span class="sxs-lookup"><span data-stu-id="3be7f-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="3be7f-116">W szczegółach podejście składa się z:</span><span class="sxs-lookup"><span data-stu-id="3be7f-116">In detail, the approach consists of:</span></span>  
  
- <span data-ttu-id="3be7f-117">Wykonaj co najmniej jeden LINQ do xml kwerend, które zwracają zestaw elementów, które chcesz przekształcić z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="3be7f-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="3be7f-118">Dla każdego elementu w kwerendzie <xref:System.Xml.Linq.XElement> dodaj nowy obiekt jako adnotację do elementu.</span><span class="sxs-lookup"><span data-stu-id="3be7f-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="3be7f-119">Ten nowy element zastąpi element z adnotami w nowym, przekształconym drzewie.</span><span class="sxs-lookup"><span data-stu-id="3be7f-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="3be7f-120">Jest to prosty kod do napisania, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3be7f-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
- <span data-ttu-id="3be7f-121">Nowy element, który jest dodawany jako adnotacja może zawierać nowe węzły podrzędne; może tworzyć poddrzewo o dowolnym pożądanym kształcie.</span><span class="sxs-lookup"><span data-stu-id="3be7f-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
- <span data-ttu-id="3be7f-122">Istnieje specjalna reguła: Jeśli węzeł podrzędny nowego elementu znajduje się w innym obszarze nazw, obszar nazw, który składa `http://www.microsoft.com/LinqToXmlTransform/2007`się w tym celu (w tym przykładzie obszar nazw jest), to ten element podrzędny nie jest kopiowany do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="3be7f-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="3be7f-123">Zamiast tego jeśli obszar nazw jest wyżej wymienionym specjalnym obszarem nazw, a lokalna nazwa elementu to `ApplyTransforms`, wówczas węzły podrzędne elementu w drzewie źródłowym są iterowane i kopiowane do nowego drzewa (z wyjątkiem tego, że elementy podrzędne z adnotacjami są przekształcane zgodnie z tymi regułami).</span><span class="sxs-lookup"><span data-stu-id="3be7f-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
- <span data-ttu-id="3be7f-124">Jest to nieco analogiczne do specyfikacji przekształceń w XSL.</span><span class="sxs-lookup"><span data-stu-id="3be7f-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="3be7f-125">Kwerenda, która wybiera zestaw węzłów jest analogiczna do wyrażenia XPath dla szablonu.</span><span class="sxs-lookup"><span data-stu-id="3be7f-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="3be7f-126">Kod do tworzenia <xref:System.Xml.Linq.XElement> nowego, który jest zapisywany jako adnotacja jest analogiczny do konstruktora sekwencyjnego w XSL, a `ApplyTransforms` element jest analogiczny w funkcji do `xsl:apply-templates` elementu w XSL.</span><span class="sxs-lookup"><span data-stu-id="3be7f-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
- <span data-ttu-id="3be7f-127">Jedną z zalet do podjęcia tego podejścia — podczas formułowanie zapytań, zawsze piszesz zapytania na niezmodyfikowanedrzewo źródłowe.</span><span class="sxs-lookup"><span data-stu-id="3be7f-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="3be7f-128">Nie musisz się martwić o to, jak modyfikacje drzewa wpływają na kwerendy, które piszesz.</span><span class="sxs-lookup"><span data-stu-id="3be7f-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="3be7f-129">Przekształcanie drzewa</span><span class="sxs-lookup"><span data-stu-id="3be7f-129">Transforming a Tree</span></span>  
 <span data-ttu-id="3be7f-130">W tym pierwszym `Paragraph` przykładzie zmienia `para`nazwę wszystkich węzłów na .</span><span class="sxs-lookup"><span data-stu-id="3be7f-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
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
  
 <span data-ttu-id="3be7f-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3be7f-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="3be7f-132">Bardziej skomplikowana transformacja</span><span class="sxs-lookup"><span data-stu-id="3be7f-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="3be7f-133">Poniższy przykład zapytuje drzewo i oblicza `Data` średnią i sumę elementów i dodaje je jako nowe elementy do drzewa.</span><span class="sxs-lookup"><span data-stu-id="3be7f-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
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
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average", $"{avg:F4}"),
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
  
 <span data-ttu-id="3be7f-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3be7f-134">This example produces the following output:</span></span>  
  
```output  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="3be7f-135">Wprowadzanie transformacji</span><span class="sxs-lookup"><span data-stu-id="3be7f-135">Effecting the Transform</span></span>  
 <span data-ttu-id="3be7f-136">Mała funkcja, `XForm`tworzy nowe przekształcone drzewo z oryginalnego drzewa z adnotatorem.</span><span class="sxs-lookup"><span data-stu-id="3be7f-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
- <span data-ttu-id="3be7f-137">Pseudo kod funkcji jest dość prosty:</span><span class="sxs-lookup"><span data-stu-id="3be7f-137">The pseudo code for the function is quite simple:</span></span>  
  
```text  
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
  
 <span data-ttu-id="3be7f-138">Poniżej znajduje się implementacja tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="3be7f-138">Following is the implementation of this function:</span></span>  
  
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
  
## <a name="complete-example"></a><span data-ttu-id="3be7f-139">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="3be7f-139">Complete Example</span></span>  
 <span data-ttu-id="3be7f-140">Poniższy kod jest kompletnym przykładem, który zawiera `XForm` funkcję.</span><span class="sxs-lookup"><span data-stu-id="3be7f-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="3be7f-141">Zawiera kilka typowych zastosowań tego typu transformacji:</span><span class="sxs-lookup"><span data-stu-id="3be7f-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
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
  
 <span data-ttu-id="3be7f-142">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3be7f-142">This example produces the following output:</span></span>  
  
```output  
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
  