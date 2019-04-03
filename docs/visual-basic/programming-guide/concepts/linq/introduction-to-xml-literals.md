---
title: Wprowadzenie do literałów XML w Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 68ba1e018d4ad9501532745a88090f0f756b5c17
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841303"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Wprowadzenie do literałów XML w Visual Basic
Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w Visual Basic.  
  
 Aby dowiedzieć się, jak za pomocą wyników zapytania LINQ jako zawartość dla drzewa XML, zobacz [konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Aby uzyskać więcej informacji na temat literałów XML w Visual Basic, zobacz [Przegląd LINQ to XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Tworzenie drzew XML  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Xml.Linq.XElement>, w tym przypadku `contacts`:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a>Tworzenie XElement za pomocą prostej zawartości  
 Możesz utworzyć <xref:System.Xml.Linq.XElement> prostej zawartości, która zawiera w następujący sposób:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Tworzenie pustego elementu  
 Możesz utworzyć pustą <xref:System.Xml.Linq.XElement>, wykonując następujące czynności:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Za pomocą wyrażenia osadzone  
 Ważną funkcją literałów XML jest, że zezwalają na wyrażenia osadzone. Wyrażenia osadzone umożliwiają ocena wyrażenia i Wstaw wyniki wyrażenia do drzewa XML. Jeśli wyrażenie typu <xref:System.Xml.Linq.XElement>, element jest wstawiany do drzewa. Jeśli wyrażenie typu <xref:System.Xml.Linq.XAttribute>, atrybut jest wstawiany do drzewa. W drzewie, tylko gdy są one prawidłowe, można wstawić elementów i atrybutów.  
  
 Należy zauważyć pojedyncze wyrażenie mogą być wprowadzanie do wyrażenia osadzone. Nie można osadzić użycie wielu instrukcji. Jeśli wyrażenie wykracza poza jednym wierszu, należy użyć wstawić znak kontynuacji wiersza.  
  
 Jeśli używasz osadzone wyrażenie Aby dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzewa XML, a jeśli istniejące węzły są już elementem nadrzędnym w węzłach są klonowane. Nowo sklonowanego węzły są dołączone do nowego drzewa XML. Jeśli istniejące węzły są elementu nadrzędnego, węzły są po prostu dołączone do nowego drzewa XML. Przykład ostatniego, w tym temacie przedstawia to.  
  
 W poniższym przykładzie użyto wyrażenia osadzone, aby wstawić element do drzewa:  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>Za pomocą wyrażenia osadzone w zawartości  
 Wyrażenia osadzone służy do dostarczania zawartości elementu:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>W wyrażeniu Embedded za pomocą zapytań LINQ  
 Można użyć z wynikami zapytania LINQ dla zawartości elementu:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Za pomocą wyrażenia osadzone dla nazwy węzła  
 Wyrażenia osadzone umożliwia również obliczyć nazwy atrybutu, wartości atrybutów, nazwy elementów i wartości elementów:  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Klonowanie a dołączanie  
 Jak wspomniano wcześniej, korzystając z wyrażenia osadzone dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzewa XML, jeśli istniejące węzły są już nadrzędny, węzły są klonowane, a nowo sklonowanego węzły są dołączone do nowego drzewa XML. Jeśli istniejące węzły są elementu nadrzędnego, są one po prostu dołączone do nowego drzewa XML.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
