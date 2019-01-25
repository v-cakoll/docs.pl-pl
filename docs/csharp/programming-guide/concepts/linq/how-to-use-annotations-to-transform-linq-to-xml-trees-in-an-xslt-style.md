---
title: 'Instrukcje: Adnotacje umożliwiają przekształcanie drzew LINQ to XML w stylu XSLT (C#)'
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 64287abbf8a411d8c231ceaf3311c51738d7ea96
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733964"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="7c8bd-102">Instrukcje: Adnotacje umożliwiają przekształcanie drzew LINQ to XML w stylu XSLT (C#)</span><span class="sxs-lookup"><span data-stu-id="7c8bd-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>
<span data-ttu-id="7c8bd-103">Adnotacje może służyć do ułatwienia przekształcenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="7c8bd-104">Niektóre dokumenty XML są "dokument przetwarzających z zawartością mieszaną".</span><span class="sxs-lookup"><span data-stu-id="7c8bd-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="7c8bd-105">Za pomocą tych dokumentów nie zawsze wiadomo kształt podrzędny węzłów elementu.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="7c8bd-106">Na przykład węzeł, który zawiera tekst może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="7c8bd-107">Dla dowolnego węzła dany tekst może być dowolną liczbę podrzędnych `<b>` i `<i>` elementów.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="7c8bd-108">To podejście obejmuje szereg innych sytuacjach, takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak regularne akapitów, akapitów punktowanych i map bitowych.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="7c8bd-109">Komórek w tabeli może zawierać tekst, lista rozwijana list i map bitowych.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="7c8bd-110">Jedna z właściwości podstawowy dokument, który skoncentrowane na kod XML jest, że nie znasz elementu podrzędnego, które będzie mieć jeden z elementów.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="7c8bd-111">Jeśli chcesz przekształcić elementy w drzewie, na którym nie zawsze znasz te informacje, elementy podrzędne elementy, które chcesz przekształcić takie podejście, który używa adnotacji jest efektywne podejście.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="7c8bd-112">Podsumowanie podejście jest:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="7c8bd-113">Po pierwsze Dodawanie adnotacji do elementów w drzewie z elementem zastępczy.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="7c8bd-114">Po drugie iterację całego drzewa, tworzenie nowego drzewa, gdzie należy zamienić każdy element jej adnotacji.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="7c8bd-115">W tym przykładzie implementuje iteracji i utworzenie nowego drzewa w funkcji o nazwie `XForm`.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="7c8bd-116">Szczegółowo podejścia składa się z:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="7c8bd-117">Wykonaj co najmniej jeden zapytaniach składnika LINQ to XML, które zwracają zestaw elementów, które chcesz przekształcić z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="7c8bd-118">Dla każdego elementu w zapytaniu, Dodaj nowy <xref:System.Xml.Linq.XElement> obiektu jako adnotacji do elementu.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="7c8bd-119">Ten nowy element spowoduje zastąpienie adnotacjami elementu w drzewie nowe, przekształcone.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="7c8bd-120">Jest to prosty kod, aby zapisywać, jak pokazano na przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="7c8bd-121">Nowy element, który jest dodawany jako adnotacja może zawierać nowe węzły podrzędne; utworzenia poddrzewie przy użyciu dowolnego żądanego kształtu.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="7c8bd-122">Brak specjalną regułę: Jeśli węzeł podrzędny nowego elementu jest w innej przestrzeni nazw przestrzeni nazw, która składa się w tym celu (w tym przykładzie obszar nazw jest `http://www.microsoft.com/LinqToXmlTransform/2007`), a następnie ten element podrzędny nie jest kopiowany do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="7c8bd-123">Zamiast tego, czy przestrzeń nazw jest wyżej specjalne przestrzeni nazw i lokalna nazwa elementu jest `ApplyTransforms`, a następnie węzły podrzędne elementu w drzewie źródła są postanowiliśmy i skopiowane do nowego drzewa (z wyjątkiem, które są elementy podrzędne z adnotacjami same przekształcane zgodnie z tych reguł).</span><span class="sxs-lookup"><span data-stu-id="7c8bd-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="7c8bd-124">Jest to nieco analogiczne do specyfikacji przekształcenia w XSL.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="7c8bd-125">Zapytania, który wybiera zestaw węzłów jest odpowiednikiem wyrażenie XPath dla szablonu.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="7c8bd-126">Kod, aby utworzyć nowy <xref:System.Xml.Linq.XElement> zapisane jako adnotacja jest analogiczne do konstruktora sekwencji w XSL i `ApplyTransforms` element jest analogiczne w funkcji `xsl:apply-templates` elementu XSL.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="7c8bd-127">Jedną z zalet zastosowaniu takiego podejścia — jak sformułowania zapytań, są zawsze Pisanie zapytań w drzewie źródła zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="7c8bd-128">Nie muszą się martwić o wpływ zmian w drzewie zapytań, które piszesz.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="7c8bd-129">Przekształcanie drzewa</span><span class="sxs-lookup"><span data-stu-id="7c8bd-129">Transforming a Tree</span></span>  
 <span data-ttu-id="7c8bd-130">W pierwszym przykładzie zmienia nazwę wszystkich `Paragraph` węzłów `para`.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
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
  
 <span data-ttu-id="7c8bd-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="7c8bd-132">Bardziej złożone przekształcenia</span><span class="sxs-lookup"><span data-stu-id="7c8bd-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="7c8bd-133">W poniższym przykładzie zapytania drzewa i oblicza, średnia i suma `Data` elementów i dodaje je jako nowe elementy do drzewa.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
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
  
 <span data-ttu-id="7c8bd-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-134">This example produces the following output:</span></span>  
  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="7c8bd-135">Dokonywanie przekształcenia</span><span class="sxs-lookup"><span data-stu-id="7c8bd-135">Effecting the Transform</span></span>  
 <span data-ttu-id="7c8bd-136">Małej funkcji `XForm`, tworzy nowe drzewo przekształcone z drzewa oryginalny, adnotacjami.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="7c8bd-137">Pseudo kod funkcji jest bardzo proste:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-137">The pseudo code for the function is quite simple:</span></span>  
  
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
  
 <span data-ttu-id="7c8bd-138">Oto implementacja tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-138">Following is the implementation of this function:</span></span>  
  
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
  
## <a name="complete-example"></a><span data-ttu-id="7c8bd-139">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="7c8bd-139">Complete Example</span></span>  
 <span data-ttu-id="7c8bd-140">Poniższy kod jest kompletny przykład, który zawiera `XForm` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7c8bd-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="7c8bd-141">Obejmuje niektóre typowe zastosowania tego typu przekształcenia:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
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
  
 <span data-ttu-id="7c8bd-142">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7c8bd-142">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c8bd-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c8bd-143">See also</span></span>

- [<span data-ttu-id="7c8bd-144">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="7c8bd-144">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
