---
title: 'Instrukcje: używanie adnotacji do przekształcania drzew LINQ to XML w stylu XSLT (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: b950f823b65299689f4ed829138a6689f6789c18
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395960"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Instrukcje: używanie adnotacji do przekształcania drzew LINQ to XML w stylu XSLT (Visual Basic)

Adnotacje mogą służyć do ułatwienia transformacji drzewa XML.

Niektóre dokumenty XML to "dokument zorientowany na zawartość mieszaną". W takich dokumentach nie trzeba znać kształtu węzłów podrzędnych elementu. Na przykład węzeł zawierający tekst może wyglądać następująco:

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

Dla dowolnego węzła tekstowego może istnieć wiele elementów podrzędnych `<b>` i `<i>`. Takie podejście rozciąga się do wielu innych sytuacji: takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak regularne akapity, punktowane akapity i mapy bitowe. Komórki w tabeli mogą zawierać tekst, listy rozwijane lub mapy bitowe. Jedną z podstawowych cech języka XML zorientowanego na dokument jest to, że nie wiesz, który element podrzędny ma określony element.

Jeśli chcesz przekształcić elementy w drzewie, w której nie ma potrzeby bardzo często wiedzieć o elementach podrzędnych elementów, które chcesz przekształcić, to podejście wykorzystujące adnotacje jest skutecznym podejściem.

Podsumowanie podejścia to:

- Najpierw Dodaj adnotację do elementów w drzewie z elementem zastępującym.

- Następnie wykonaj iterację w całym drzewie, tworząc nowe drzewo, w którym każdy element jest zastępowany adnotacją. Ten przykład implementuje iterację i tworzenie nowego drzewa w funkcji o nazwie `XForm`.

Szczegółowo podejście obejmuje:

- Wykonaj co najmniej jedno LINQ to XML zapytania, które zwracają zestaw elementów, które chcesz przekształcić z jednego kształtu do drugiego. Dla każdego elementu w zapytaniu Dodaj nowy obiekt <xref:System.Xml.Linq.XElement> jako adnotację do elementu. Ten nowy element spowoduje zamianę elementu z adnotacją w nowym, przekształconym drzewie. Jest to prosty kod do zapisu, jak pokazano na przykładzie.

- Nowy element, który jest dodawany jako Adnotacja może zawierać nowe węzły podrzędne; można utworzyć poddrzewo z dowolnym żądanym kształtem.

- Istnieje specjalna reguła: Jeśli węzeł podrzędny nowego elementu znajduje się w innej przestrzeni nazw, przestrzeń nazw, która została przeprowadzona do tego celu (w tym przykładzie przestrzeń nazw ma `http://www.microsoft.com/LinqToXmlTransform/2007`), a następnie ten element podrzędny nie jest kopiowany do nowego drzewa. Zamiast tego, jeśli obszar nazw jest wyżej wspomnianą specjalną przestrzenią nazw, a lokalna nazwa elementu jest `ApplyTransforms`, wówczas węzły podrzędne elementu w drzewie źródłowym są powtarzane i kopiowane do nowego drzewa (z wyjątkiem tego, że elementy podrzędne z adnotacjami są są one przekształcane zgodnie z tymi regułami.

- Jest to nieco analogiczne do specyfikacji transformacji w kodzie XSL. Zapytanie wybierające zestaw węzłów jest analogiczne do wyrażenia XPath dla szablonu. Kod służący do tworzenia nowego <xref:System.Xml.Linq.XElement>, który jest zapisywany jako Adnotacja, jest analogiczny do konstruktora sekwencji w XSL, a element `ApplyTransforms` jest analogiczny w funkcji do elementu `xsl:apply-templates` w kodzie XSL.

- Jedną z zalet tego podejścia — podczas redagowania zapytań są zawsze zapisywane zapytania w niezmodyfikowanym drzewie źródła. Nie musisz martwić się o to, jak zmiany w drzewie mają wpływ na zapisywanych zapytań.

## <a name="transforming-a-tree"></a>Przekształcanie drzewa

Ten pierwszy przykład zmienia nazwę wszystkich węzłów `Paragraph` na `para`:

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

## <a name="a-more-complicated-transform"></a>Bardziej skomplikowana transformacja

 Poniższy przykład wykonuje zapytanie do drzewa i oblicza średnią i sumę elementów `Data` i dodaje je jako nowe elementy do drzewa.

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

```console
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

## <a name="effecting-the-transform"></a>Efekt przekształcenia

Niewielka funkcja `XForm` tworzy nowe przekształcone drzewo z oryginalnego drzewa z adnotacjami.

Pseudo kod dla funkcji jest bardzo prosty:

> Funkcja przyjmuje XElement jako argument i zwraca XElement.
> 
> Jeśli element ma adnotację XElement, zwróć nową XElement:
>
> - Nazwa nowego XElement jest nazwą elementu adnotacji.
> - Wszystkie atrybuty są kopiowane z adnotacji do nowego węzła.
> - Wszystkie węzły podrzędne są kopiowane z adnotacji, z wyjątkiem tego, że jest rozpoznawany węzeł specjalny XF: ApplyTransforms, a węzły podrzędne elementu źródłowego są powtarzane. Jeśli źródłowy węzeł podrzędny nie jest XElement, jest kopiowany do nowego drzewa. Jeśli źródło jest XElement, jest przekształcane przez wywołanie tej funkcji cyklicznie.
>
> Jeśli element nie ma adnotacji:
>
> - Zwróć nowy XElement
>   - Nazwą nowego XElement jest nazwa elementu źródłowego.
>   - Wszystkie atrybuty są kopiowane z elementu źródłowego do elementu docelowego.
>   - Wszystkie węzły podrzędne są kopiowane z elementu źródłowego.
>   - Jeśli źródłowy węzeł podrzędny nie jest XElement, jest kopiowany do nowego drzewa. Jeśli źródło jest XElement, jest przekształcane przez wywołanie tej funkcji cyklicznie.

Następujący kod jest implementacją tej funkcji:

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

## <a name="complete-example"></a>Pełny przykład

Poniższy kod jest kompletnym przykładem zawierającym funkcję `XForm`. Zawiera kilka typowych zastosowania tego typu transformacji:

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

```console
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

- [Zaawansowane programowanie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
