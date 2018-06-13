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
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a>Porady: Użyj adnotacje do przekształcania LINQ do XML drzew stylów XSLT (C#)
Adnotacje może służyć do ułatwienia transformacji XML drzewa.  
  
 Niektóre dokumenty XML to "dokument stanowi z zawartością mieszaną." Z tych dokumentów nie zawsze wiadomo kształt podrzędny węzły elementu. Na przykład węzeł, który zawiera tekst może wyglądać następująco:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Dla dowolnego węzła podany tekst może być dowolną liczbę podrzędnych `<b>` i `<i>` elementy. Takie podejście rozszerza wielu innych sytuacjach, takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak regularne akapitów, akapitów punktowanych i bitmapy. Komórek w tabeli mogą zawierać tekstu, listy rozwijanej list i map bitowych. Jedną z właściwości głównej dokumentu XML na to, nie wiadomo element podrzędny, które będzie mieć jeden z elementów.  
  
 Jeśli chcesz Przekształcanie elementów w drzewie, w którym niekoniecznie znasz te informacje o podrzędnych elementów, które chcesz przekształcić tej metody, która używa adnotacji jest efektywne rozwiązanie.  
  
 Podsumowanie podejście jest:  
  
-   Po pierwsze dodawać adnotacje elementów w drzewie z elementem zastąpienia.  
  
-   Po drugie iterację całe drzewo, tworzenie nowego drzewa, gdzie można zastąpić każdy element jego adnotacji. W tym przykładzie implementuje iteracji i utworzenie nowego drzewa w funkcji o nazwie `XForm`.  
  
 Szczegółowo to rozwiązanie obejmuje:  
  
-   Wykonanie co najmniej jednego składnika LINQ to XML zapytań, które zwracają zestaw elementów, które mają być Przekształć z jednego kształtu. Dla każdego elementu w zapytaniu, Dodaj nową <xref:System.Xml.Linq.XElement> obiektu adnotacji do elementu. Ten nowy element spowoduje zastąpienie adnotacjami elementu w drzewie nowy, po przekształceniu. Jest to za pomocą prostego kodu do zapisu, jak pokazano w przykładzie.  
  
-   Nowy element, który zostanie dodany jako adnotacja może zawierać nowe węzły podrzędne; utworzenia poddrzewa z dowolnego żądanego kształtu.  
  
-   Jest specjalną regułę: Jeśli elementem podrzędnym nowego elementu jest w innej przestrzeni nazw przestrzeni nazw, która składa się w tym celu (w tym przykładzie przestrzeń nazw jest `http://www.microsoft.com/LinqToXmlTransform/2007`), następnie ten element podrzędny nie jest kopiowany do nowego drzewa. Zamiast tego, czy przestrzeń nazw jest wyżej specjalne przestrzeni nazw i nazwę lokalną elementu jest `ApplyTransforms`, a następnie węzły podrzędne elementu w drzewie źródła są iterowane i skopiowane do nowego drzew (z wyjątkiem, że adnotacji podrzędne elementy są samodzielnie przekształcone zgodnie z następującymi regułami).  
  
-   Jest to przypomina specyfikację transformacje w XSL. Zapytanie wybierające zestawu węzłów jest odpowiednikiem wyrażenie XPath dla szablonu. Kod, aby utworzyć nowy <xref:System.Xml.Linq.XElement> zapisane jako adnotacja jest analogiczna do konstruktora sekwencji w XSL i `ApplyTransforms` element jest analogiczna w funkcji `xsl:apply-templates` element XSL.  
  
-   Jedną z zalet tej metody - podczas wykonywania sformułować zapytań, są zawsze Pisanie zapytań w drzewie źródłowym zostały zmodyfikowane. Nie muszą zwracaj wpływ zmiany w drzewie zapytań, które pisania.  
  
## <a name="transforming-a-tree"></a>Przekształcanie drzewa  
 W tym przykładzie pierwsze zmienia nazwę wszystkich `Paragraph` węzłów do `para`.  
  
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
  
## <a name="a-more-complicated-transform"></a>Bardziej złożone przekształcenia  
 W poniższym przykładzie zapytanie drzewa i oblicza średnią i sumę `Data` elementów i dodaje je jako nowe elementy do drzewa.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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
  
## <a name="effecting-the-transform"></a>Kilkukrotnie transformacji  
 Funkcja małe, `XForm`, tworzy nowe drzewo przekształcone z oryginalnego, adnotacjami drzewa.  
  
-   Pseudo kod dla tej funkcji jest prosta:  
  
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
  
 Poniżej znajduje się stosowania tej funkcji:  
  
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
 Następujący kod jest pełny przykład, który zawiera `XForm` funkcji. Zawiera kilka typowym zastosowaniem tego typu transformacji:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane LINQ do XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
