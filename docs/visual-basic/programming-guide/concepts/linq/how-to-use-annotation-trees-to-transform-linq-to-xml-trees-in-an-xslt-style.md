---
title: 'Instrukcje: używanie adnotacji do przekształcania drzew LINQ to XML w stylu XSLT (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: b8f15c4dc6016e48619d26e7cc8717a2a3c5acd5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581977"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="2679b-102">Instrukcje: używanie adnotacji do przekształcania drzew LINQ to XML w stylu XSLT (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2679b-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>

<span data-ttu-id="2679b-103">Adnotacje mogą służyć do ułatwienia transformacji drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2679b-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>

<span data-ttu-id="2679b-104">Niektóre dokumenty XML to "dokument zorientowany na zawartość mieszaną".</span><span class="sxs-lookup"><span data-stu-id="2679b-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="2679b-105">W takich dokumentach nie trzeba znać kształtu węzłów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="2679b-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="2679b-106">Na przykład węzeł zawierający tekst może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2679b-106">For instance, a node that contains text may look like this:</span></span>

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

<span data-ttu-id="2679b-107">Dla dowolnego węzła tekstowego może istnieć wiele elementów podrzędnych `<b>` i `<i>`.</span><span class="sxs-lookup"><span data-stu-id="2679b-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="2679b-108">Takie podejście rozciąga się do wielu innych sytuacji: takich jak strony, które mogą zawierać różne elementy podrzędne, takie jak regularne akapity, punktowane akapity i mapy bitowe.</span><span class="sxs-lookup"><span data-stu-id="2679b-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="2679b-109">Komórki w tabeli mogą zawierać tekst, listy rozwijane lub mapy bitowe.</span><span class="sxs-lookup"><span data-stu-id="2679b-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="2679b-110">Jedną z podstawowych cech języka XML zorientowanego na dokument jest to, że nie wiesz, który element podrzędny ma określony element.</span><span class="sxs-lookup"><span data-stu-id="2679b-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>

<span data-ttu-id="2679b-111">Jeśli chcesz przekształcić elementy w drzewie, w której nie ma potrzeby bardzo często wiedzieć o elementach podrzędnych elementów, które chcesz przekształcić, to podejście wykorzystujące adnotacje jest skutecznym podejściem.</span><span class="sxs-lookup"><span data-stu-id="2679b-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>

<span data-ttu-id="2679b-112">Podsumowanie podejścia to:</span><span class="sxs-lookup"><span data-stu-id="2679b-112">The summary of the approach is:</span></span>

- <span data-ttu-id="2679b-113">Najpierw Dodaj adnotację do elementów w drzewie z elementem zastępującym.</span><span class="sxs-lookup"><span data-stu-id="2679b-113">First, annotate elements in the tree with a replacement element.</span></span>

- <span data-ttu-id="2679b-114">Następnie wykonaj iterację w całym drzewie, tworząc nowe drzewo, w którym każdy element jest zastępowany adnotacją.</span><span class="sxs-lookup"><span data-stu-id="2679b-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="2679b-115">Ten przykład implementuje iterację i tworzenie nowego drzewa w funkcji o nazwie `XForm`.</span><span class="sxs-lookup"><span data-stu-id="2679b-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>

<span data-ttu-id="2679b-116">Szczegółowo podejście obejmuje:</span><span class="sxs-lookup"><span data-stu-id="2679b-116">In detail, the approach consists of:</span></span>

- <span data-ttu-id="2679b-117">Wykonaj co najmniej jedno LINQ to XML zapytania, które zwracają zestaw elementów, które chcesz przekształcić z jednego kształtu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="2679b-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="2679b-118">Dla każdego elementu w zapytaniu Dodaj nowy obiekt <xref:System.Xml.Linq.XElement> jako adnotację do elementu.</span><span class="sxs-lookup"><span data-stu-id="2679b-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="2679b-119">Ten nowy element spowoduje zamianę elementu z adnotacją w nowym, przekształconym drzewie.</span><span class="sxs-lookup"><span data-stu-id="2679b-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="2679b-120">Jest to prosty kod do zapisu, jak pokazano na przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2679b-120">This is simple code to write, as demonstrated by the example.</span></span>

- <span data-ttu-id="2679b-121">Nowy element, który jest dodawany jako Adnotacja może zawierać nowe węzły podrzędne; można utworzyć poddrzewo z dowolnym żądanym kształtem.</span><span class="sxs-lookup"><span data-stu-id="2679b-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>

- <span data-ttu-id="2679b-122">Istnieje specjalna reguła: Jeśli węzeł podrzędny nowego elementu znajduje się w innej przestrzeni nazw, przestrzeń nazw, która została przeprowadzona do tego celu (w tym przykładzie przestrzeń nazw ma `http://www.microsoft.com/LinqToXmlTransform/2007`), a następnie ten element podrzędny nie jest kopiowany do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="2679b-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="2679b-123">Zamiast tego, jeśli obszar nazw jest wyżej wspomnianą specjalną przestrzenią nazw, a lokalna nazwa elementu jest `ApplyTransforms`, wówczas węzły podrzędne elementu w drzewie źródłowym są powtarzane i kopiowane do nowego drzewa (z wyjątkiem tego, że elementy podrzędne z adnotacjami są są one przekształcane zgodnie z tymi regułami.</span><span class="sxs-lookup"><span data-stu-id="2679b-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>

- <span data-ttu-id="2679b-124">Jest to nieco analogiczne do specyfikacji transformacji w kodzie XSL.</span><span class="sxs-lookup"><span data-stu-id="2679b-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="2679b-125">Zapytanie wybierające zestaw węzłów jest analogiczne do wyrażenia XPath dla szablonu.</span><span class="sxs-lookup"><span data-stu-id="2679b-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="2679b-126">Kod służący do tworzenia nowego <xref:System.Xml.Linq.XElement>, który jest zapisywany jako Adnotacja, jest analogiczny do konstruktora sekwencji w XSL, a element `ApplyTransforms` jest analogiczny w funkcji do elementu `xsl:apply-templates` w kodzie XSL.</span><span class="sxs-lookup"><span data-stu-id="2679b-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>

- <span data-ttu-id="2679b-127">Jedną z zalet tego podejścia — podczas redagowania zapytań są zawsze zapisywane zapytania w niezmodyfikowanym drzewie źródła.</span><span class="sxs-lookup"><span data-stu-id="2679b-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="2679b-128">Nie musisz martwić się o to, jak zmiany w drzewie mają wpływ na zapisywanych zapytań.</span><span class="sxs-lookup"><span data-stu-id="2679b-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>

## <a name="transforming-a-tree"></a><span data-ttu-id="2679b-129">Przekształcanie drzewa</span><span class="sxs-lookup"><span data-stu-id="2679b-129">Transforming a Tree</span></span>

<span data-ttu-id="2679b-130">Ten pierwszy przykład zmienia nazwę wszystkich węzłów `Paragraph` na `para`:</span><span class="sxs-lookup"><span data-stu-id="2679b-130">This first example renames all `Paragraph` nodes to `para`:</span></span>

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

 <span data-ttu-id="2679b-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2679b-131">This example produces the following output:</span></span>

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="a-more-complicated-transform"></a><span data-ttu-id="2679b-132">Bardziej skomplikowana transformacja</span><span class="sxs-lookup"><span data-stu-id="2679b-132">A more complicated transform</span></span>

<span data-ttu-id="2679b-133">Poniższy przykład wykonuje zapytanie do drzewa i oblicza średnią i sumę elementów `Data` i dodaje je jako nowe elementy do drzewa.</span><span class="sxs-lookup"><span data-stu-id="2679b-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>

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

<span data-ttu-id="2679b-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2679b-134">This example produces the following output:</span></span>

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

## <a name="effecting-the-transform"></a><span data-ttu-id="2679b-135">Efekt przekształcenia</span><span class="sxs-lookup"><span data-stu-id="2679b-135">Effecting the transform</span></span>

<span data-ttu-id="2679b-136">Niewielka funkcja `XForm` tworzy nowe przekształcone drzewo z oryginalnego drzewa z adnotacjami.</span><span class="sxs-lookup"><span data-stu-id="2679b-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>

<span data-ttu-id="2679b-137">Pseudo kod dla funkcji jest bardzo prosty:</span><span class="sxs-lookup"><span data-stu-id="2679b-137">The pseudo code for the function is quite simple:</span></span>

> <span data-ttu-id="2679b-138">Funkcja przyjmuje XElement jako argument i zwraca XElement.</span><span class="sxs-lookup"><span data-stu-id="2679b-138">The function takes an XElement as an argument and returns an XElement.</span></span>
>
> <span data-ttu-id="2679b-139">Jeśli element ma adnotację XElement, zwróć nową XElement:</span><span class="sxs-lookup"><span data-stu-id="2679b-139">If an element has an XElement annotation, then return a new XElement:</span></span>
>
> - <span data-ttu-id="2679b-140">Nazwa nowego XElement jest nazwą elementu adnotacji.</span><span class="sxs-lookup"><span data-stu-id="2679b-140">The name of the new XElement is the annotation element's name.</span></span>
> - <span data-ttu-id="2679b-141">Wszystkie atrybuty są kopiowane z adnotacji do nowego węzła.</span><span class="sxs-lookup"><span data-stu-id="2679b-141">All attributes are copied from the annotation to the new node.</span></span>
> - <span data-ttu-id="2679b-142">Wszystkie węzły podrzędne są kopiowane z adnotacji, z wyjątkiem tego, że jest rozpoznawany węzeł specjalny XF: ApplyTransforms, a węzły podrzędne elementu źródłowego są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="2679b-142">All child nodes are copied from the annotation, with the exception that the special node xf:ApplyTransforms is recognized, and the source element's child nodes are iterated.</span></span> <span data-ttu-id="2679b-143">Jeśli źródłowy węzeł podrzędny nie jest XElement, jest kopiowany do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="2679b-143">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="2679b-144">Jeśli źródło jest XElement, jest przekształcane przez wywołanie tej funkcji cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="2679b-144">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>
>
> <span data-ttu-id="2679b-145">Jeśli element nie ma adnotacji:</span><span class="sxs-lookup"><span data-stu-id="2679b-145">If an element is not annotated:</span></span>
>
> - <span data-ttu-id="2679b-146">Zwróć nowy XElement</span><span class="sxs-lookup"><span data-stu-id="2679b-146">Return a new XElement</span></span>
>   - <span data-ttu-id="2679b-147">Nazwą nowego XElement jest nazwa elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2679b-147">The name of the new XElement is the source element's name.</span></span>
>   - <span data-ttu-id="2679b-148">Wszystkie atrybuty są kopiowane z elementu źródłowego do elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2679b-148">All attributes are copied from the source element to the destination's element.</span></span>
>   - <span data-ttu-id="2679b-149">Wszystkie węzły podrzędne są kopiowane z elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2679b-149">All child nodes are copied from the source element.</span></span>
>   - <span data-ttu-id="2679b-150">Jeśli źródłowy węzeł podrzędny nie jest XElement, jest kopiowany do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="2679b-150">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="2679b-151">Jeśli źródło jest XElement, jest przekształcane przez wywołanie tej funkcji cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="2679b-151">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>

<span data-ttu-id="2679b-152">Następujący kod jest implementacją tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="2679b-152">The following code is the implementation of this function:</span></span>

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

## <a name="complete-example"></a><span data-ttu-id="2679b-153">Pełny przykład</span><span class="sxs-lookup"><span data-stu-id="2679b-153">Complete example</span></span>

<span data-ttu-id="2679b-154">Poniższy kod jest kompletnym przykładem zawierającym funkcję `XForm`.</span><span class="sxs-lookup"><span data-stu-id="2679b-154">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="2679b-155">Zawiera kilka typowych zastosowania tego typu transformacji:</span><span class="sxs-lookup"><span data-stu-id="2679b-155">It includes a few of the typical uses of this type of transform:</span></span>

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

<span data-ttu-id="2679b-156">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2679b-156">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2679b-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2679b-157">See also</span></span>

- [<span data-ttu-id="2679b-158">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2679b-158">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
