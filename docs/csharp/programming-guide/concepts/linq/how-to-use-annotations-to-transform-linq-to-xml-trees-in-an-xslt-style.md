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
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a>Jak używać adnotacji do przekształcania linq do drzew XML w stylu XSLT (C#)
Adnotacje mogą służyć do ułatwienia przekształcenia drzewa XML.  
  
 Niektóre dokumenty XML są "skoncentrowane na dokumencie z zawartością mieszaną". W przypadku takich dokumentów niekoniecznie znasz kształt węzłów podrzędnych elementu. Na przykład węzeł zawierający tekst może wyglądać tak:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Dla dowolnego węzła tekstowego może istnieć `<b>` `<i>` dowolna liczba elementów podrzędnych i elementów. Takie podejście obejmuje wiele innych sytuacji, takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak zwykłe akapity, akapity punktowane i mapy bitowe. Komórki w tabeli mogą zawierać tekst, listy rozwijane lub mapy bitowe. Jedną z podstawowych cech dokumentu centric XML jest to, że nie wiadomo, który element podrzędny będzie miał dowolny element podrzędny.  
  
 Jeśli chcesz przekształcić elementy w drzewie, gdzie niekoniecznie wiesz zbyt wiele o elementach podrzędnych elementów, które chcesz przekształcić, to takie podejście, które używa adnotacji jest skuteczne podejście.  
  
 Podsumowanie podejścia jest następujące:  
  
- Najpierw należy adnotować elementy w drzewie za pomocą elementu zastępczego.  
  
- Po drugie, iterate przez całe drzewo, tworząc nowe drzewo, w którym można zastąpić każdy element z jego adnotacji. W tym przykładzie implementuje iteracji i tworzenia nowego `XForm`drzewa w funkcji o nazwie .  
  
 W szczegółach podejście składa się z:  
  
- Wykonaj co najmniej jeden LINQ do xml kwerend, które zwracają zestaw elementów, które chcesz przekształcić z jednego kształtu do innego. Dla każdego elementu w kwerendzie <xref:System.Xml.Linq.XElement> dodaj nowy obiekt jako adnotację do elementu. Ten nowy element zastąpi element z adnotami w nowym, przekształconym drzewie. Jest to prosty kod do napisania, jak pokazano w przykładzie.  
  
- Nowy element, który jest dodawany jako adnotacja może zawierać nowe węzły podrzędne; może tworzyć poddrzewo o dowolnym pożądanym kształcie.  
  
- Istnieje specjalna reguła: Jeśli węzeł podrzędny nowego elementu znajduje się w innym obszarze nazw, obszar nazw, który składa `http://www.microsoft.com/LinqToXmlTransform/2007`się w tym celu (w tym przykładzie obszar nazw jest), to ten element podrzędny nie jest kopiowany do nowego drzewa. Zamiast tego jeśli obszar nazw jest wyżej wymienionym specjalnym obszarem nazw, a lokalna nazwa elementu to `ApplyTransforms`, wówczas węzły podrzędne elementu w drzewie źródłowym są iterowane i kopiowane do nowego drzewa (z wyjątkiem tego, że elementy podrzędne z adnotacjami są przekształcane zgodnie z tymi regułami).  
  
- Jest to nieco analogiczne do specyfikacji przekształceń w XSL. Kwerenda, która wybiera zestaw węzłów jest analogiczna do wyrażenia XPath dla szablonu. Kod do tworzenia <xref:System.Xml.Linq.XElement> nowego, który jest zapisywany jako adnotacja jest analogiczny do konstruktora sekwencyjnego w XSL, a `ApplyTransforms` element jest analogiczny w funkcji do `xsl:apply-templates` elementu w XSL.  
  
- Jedną z zalet do podjęcia tego podejścia — podczas formułowanie zapytań, zawsze piszesz zapytania na niezmodyfikowanedrzewo źródłowe. Nie musisz się martwić o to, jak modyfikacje drzewa wpływają na kwerendy, które piszesz.  
  
## <a name="transforming-a-tree"></a>Przekształcanie drzewa  
 W tym pierwszym `Paragraph` przykładzie zmienia `para`nazwę wszystkich węzłów na .  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Bardziej skomplikowana transformacja  
 Poniższy przykład zapytuje drzewo i oblicza `Data` średnią i sumę elementów i dodaje je jako nowe elementy do drzewa.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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
  
## <a name="effecting-the-transform"></a>Wprowadzanie transformacji  
 Mała funkcja, `XForm`tworzy nowe przekształcone drzewo z oryginalnego drzewa z adnotatorem.  
  
- Pseudo kod funkcji jest dość prosty:  
  
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
  
 Poniżej znajduje się implementacja tej funkcji:  
  
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
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest kompletnym przykładem, który zawiera `XForm` funkcję. Zawiera kilka typowych zastosowań tego typu transformacji:  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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
  