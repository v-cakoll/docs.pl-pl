---
title: 'Instrukcje: Adnotacje umożliwiają przekształcanie drzew LINQ to XML w stylu XSLT (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: a8db5f9dc29b4053321c81c9da58e12610ef63c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824874"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Instrukcje: Adnotacje umożliwiają przekształcanie drzew LINQ to XML w stylu XSLT (Visual Basic)
Adnotacje może służyć do ułatwienia przekształcenia drzewa XML.  
  
 Niektóre dokumenty XML są "dokument przetwarzających z zawartością mieszaną". Za pomocą tych dokumentów nie zawsze wiadomo kształt podrzędny węzłów elementu. Na przykład węzeł, który zawiera tekst może wyglądać następująco:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Dla dowolnego węzła dany tekst może być dowolną liczbę podrzędnych `<b>` i `<i>` elementów. To podejście obejmuje szereg innych sytuacjach: takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak regularne akapitów, akapitów punktowanych i map bitowych. Komórek w tabeli może zawierać tekst, lista rozwijana list i map bitowych. Jedna z właściwości podstawowy dokument, który skoncentrowane na kod XML jest, że nie znasz elementu podrzędnego, które będzie mieć jeden z elementów.  
  
 Jeśli chcesz przekształcić elementy w drzewie, na którym nie zawsze znasz te informacje, elementy podrzędne elementy, które chcesz przekształcić takie podejście, który używa adnotacji jest efektywne podejście.  
  
 Podsumowanie podejście jest:  
  
-   Po pierwsze Dodawanie adnotacji do elementów w drzewie z elementem zastępczy.  
  
-   Po drugie iterację całego drzewa, tworzenie nowego drzewa, gdzie należy zamienić każdy element jej adnotacji. W tym przykładzie implementuje iteracji i utworzenie nowego drzewa w funkcji o nazwie `XForm`.  
  
 Szczegółowo podejścia składa się z:  
  
-   Wykonaj co najmniej jeden zapytaniach składnika LINQ to XML, które zwracają zestaw elementów, które chcesz przekształcić z jednego kształtu do innego. Dla każdego elementu w zapytaniu, Dodaj nowy <xref:System.Xml.Linq.XElement> obiektu jako adnotacji do elementu. Ten nowy element spowoduje zastąpienie adnotacjami elementu w drzewie nowe, przekształcone. Jest to prosty kod, aby zapisywać, jak pokazano na przykładzie.  
  
-   Nowy element, który jest dodawany jako adnotacja może zawierać nowe węzły podrzędne; utworzenia poddrzewie przy użyciu dowolnego żądanego kształtu.  
  
-   Brak specjalną regułę: Jeśli węzeł podrzędny nowego elementu jest w innej przestrzeni nazw przestrzeni nazw, która składa się w tym celu (w tym przykładzie obszar nazw jest `http://www.microsoft.com/LinqToXmlTransform/2007`), a następnie ten element podrzędny nie jest kopiowany do nowego drzewa. Zamiast tego, czy przestrzeń nazw jest wyżej specjalne przestrzeni nazw i lokalna nazwa elementu jest `ApplyTransforms`, a następnie węzły podrzędne elementu w drzewie źródła są postanowiliśmy i skopiowane do nowego drzewa (z wyjątkiem, które są elementy podrzędne z adnotacjami same przekształcane zgodnie z tych reguł).  
  
-   Jest to nieco analogiczne do specyfikacji przekształcenia w XSL. Zapytania, który wybiera zestaw węzłów jest odpowiednikiem wyrażenie XPath dla szablonu. Kod, aby utworzyć nowy <xref:System.Xml.Linq.XElement> zapisane jako adnotacja jest analogiczne do konstruktora sekwencji w XSL i `ApplyTransforms` element jest analogiczne w funkcji `xsl:apply-templates` elementu XSL.  
  
-   Jedną z zalet zastosowaniu takiego podejścia — jak sformułowania zapytań, są zawsze Pisanie zapytań w drzewie źródła zostały zmodyfikowane. Nie muszą się martwić o wpływ zmian w drzewie zapytań, które piszesz.  
  
## <a name="transforming-a-tree"></a>Przekształcanie drzewa  
 W pierwszym przykładzie zmienia nazwę wszystkich `Paragraph` węzłów `para`.  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
                <Paragraph>More text.</Paragraph>  
            </Root>  
  
        ' Replace Paragraph with p.  
        For Each el In root...<Paragraph>  
            ' same idea as xsl:apply-templates  
            el.AddAnnotation( _  
                <para>  
                    <<%= at %>></>  
                </para>)  
        Next  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newRoot As XElement = XForm(root)  
        Console.WriteLine(newRoot)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Bardziej złożone przekształcenia  
 W poniższym przykładzie zapytania drzewa i oblicza, średnia i suma `Data` elementów i dodaje je jako nowe elementy do drzewa.  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim data As XElement = _  
            <Root>  
                <Data>20</Data>  
                <Data>10</Data>  
                <Data>3</Data>  
            </Root>  
  
        ' While adding annotations, you can query the source tree all you want,  
        ' as the tree is not mutated while annotating.  
        data.AddAnnotation( _  
            <Root>  
                <<%= at %>/>  
                <Average>  
                    <%= _  
                        String.Format("{0:F4}", _  
                        data.Elements("Data") _  
                        .Select(Function(z) CDec(z)).Average()) _  
                    %>  
                </Average>  
                <Sum>  
                    <%= _  
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _  
                    %>  
                </Sum>  
            </Root> _  
        )  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(data)  
        Console.WriteLine(vbNewLine)  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newData As XElement = XForm(data)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newData)  
    End Sub  
End Module   
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
  
## <a name="effecting-the-transform"></a>Dokonywanie przekształcenia  
 Małej funkcji `XForm`, tworzy nowe drzewo przekształcone z drzewa oryginalny, adnotacjami.  
  
-   Pseudo kod funkcji jest bardzo proste:  
  
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
  
 Oto implementacja tej funkcji:  
  
```vb  
' Build a transformed XML tree per the annotations.  
Function XForm(ByVal source As XElement) As XElement  
    If source.Annotation(Of XElement)() IsNot Nothing Then  
        Dim anno As XElement = source.Annotation(Of XElement)()  
        Return _  
            <<%= anno.Name.ToString() %>>  
                <%= anno.Attributes() %>  
                <%= anno.Nodes().Select(Function(n As XNode) _  
                    GetSubNodes(n, source)) %>  
            </>  
    Else  
        Return _  
            <<%= source.Name %>>  
                <%= source.Attributes() %>  
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
            </>  
    End If  
End Function  
  
Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
    Dim annoEl As XElement = TryCast(n, XElement)  
    If annoEl IsNot Nothing Then  
        If annoEl.Name = at Then  
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
        End If  
    End If  
    Return n  
End Function  
  
Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
    Dim e2 As XElement = TryCast(n2, XElement)  
    If e2 Is Nothing Then  
        Return n2  
    Else  
        Return XForm(e2)  
    End If  
End Function  
```  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest kompletny przykład, który zawiera `XForm` funkcji. Obejmuje niektóre typowe zastosowania tego typu przekształcenia:  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports System.Xml  
Imports System.Xml.Linq  
  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    ' Build a transformed XML tree per the annotations.  
    Function XForm(ByVal source As XElement) As XElement  
        If source.Annotation(Of XElement)() IsNot Nothing Then  
            Dim anno As XElement = source.Annotation(Of XElement)()  
            Return _  
                <<%= anno.Name.ToString() %>>  
                    <%= anno.Attributes() %>  
                    <%= anno.Nodes().Select(Function(n As XNode) _  
                        GetSubNodes(n, source)) %>  
                </>  
        Else  
            Return _  
                <<%= source.Name %>>  
                    <%= source.Attributes() %>  
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
                </>  
        End If  
    End Function  
  
    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
        Dim annoEl As XElement = TryCast(n, XElement)  
        If annoEl IsNot Nothing Then  
            If annoEl.Name = at Then  
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
            End If  
        End If  
        Return n  
    End Function  
  
    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
        Dim e2 As XElement = TryCast(n2, XElement)  
        If e2 Is Nothing Then  
            Return n2  
        Else  
            Return XForm(e2)  
        End If  
    End Function  
  
    Sub Main()  
        Dim root As XElement = _  
<Root Att1='123'>  
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
  
        ' Each of the following serves the same semantic purpose as  
        ' XSLT templates and sequence constructors.  
  
        ' Replace Child with NewChild.  
        For Each el In root.<Child>  
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)  
        Next  
  
        ' Replace first GC with GrandChild, add an attribute.  
        For Each el In root...<GC>.Take(1)  
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)  
        Next  
  
        ' Replace Other with NewOther, add new child elements around original content.  
        For Each el In root.<Other>  
            el.AddAnnotation( _  
                <NewOther>  
                    <MyNewChild>1</MyNewChild>  
                    <<%= at %>></>  
                    <ChildThatComesAfter/>  
                </NewOther>)  
        Next  
  
        ' Change name of element that has mixed content.  
        root...<SomeMixedContent>(0).AddAnnotation( _  
                <MixedContent><<%= at %>></></MixedContent>)  
  
        ' Replace <b> with <Bold>.  
        For Each el In root...<b>  
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)  
        Next  
  
        ' Replace <i> with <Italic>.  
        For Each el In root...<i>  
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)  
        Next  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(root)  
        Console.WriteLine(vbNewLine)  
        Dim newRoot As XElement = XForm(root)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newRoot)  
    End Sub  
End Module   
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
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane LINQ to XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
