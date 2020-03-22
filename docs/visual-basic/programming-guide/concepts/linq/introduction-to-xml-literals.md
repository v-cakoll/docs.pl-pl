---
title: Wprowadzenie do literałów XML w języku Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 9f5c54574e51c537d9ea58d307afda10736d0d88
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266953"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Wprowadzenie do literałów XML w języku Visual Basic
Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w języku Visual Basic.  
  
 Aby uzyskać informacje na temat używania wyników zapytań LINQ jako zawartości drzewa XML, zobacz [Konstrukcja funkcjonalna (LINQ do XML) (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)  
  
 Aby uzyskać więcej informacji na temat literałów XML w języku Visual Basic, zobacz [Omówienie LINQ do XML w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Tworzenie drzew XML  
 W poniższym <xref:System.Xml.Linq.XElement>przykładzie pokazano, jak `contacts`utworzyć , w tym przypadku:  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Tworzenie XElement z prostą zawartością  
 Można utworzyć <xref:System.Xml.Linq.XElement> zawartość prostą w następujący sposób:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Tworzenie pustego elementu  
 Można utworzyć pustą <xref:System.Xml.Linq.XElement>, w następujący sposób:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Korzystanie z wyrażeń osadzonych  
 Ważną cechą literałów XML jest to, że zezwalają na osadzone wyrażenia. Osadzone wyrażenia umożliwiają ocenę wyrażenia i wstawianie wyników wyrażenia do drzewa XML. Jeśli wyrażenie jest obliczane <xref:System.Xml.Linq.XElement>na typ , element jest wstawiany do drzewa. Jeśli wyrażenie jest obliczane <xref:System.Xml.Linq.XAttribute>na typ , atrybut jest wstawiany do drzewa. Elementy i atrybuty można wstawiać do drzewa tylko wtedy, gdy są prawidłowe.  
  
 Należy pamiętać, że tylko pojedyncze wyrażenie może przejść do wyrażenia osadzonego. Nie można osadzić wielu instrukcji. Jeśli wyrażenie wykracza poza pojedynczy wiersz, należy użyć znaku kontynuacji wiersza.  
  
 Jeśli użyto wyrażenia osadzonego do dodania istniejących węzłów (w tym elementów) i atrybutów do nowego drzewa XML, a istniejące węzły są już nadrzędne, węzły zostaną sklonowane. Nowo sklonowane węzły są dołączone do nowego drzewa XML. Jeśli istniejące węzły nie są nadrzędne, węzły są po prostu dołączone do nowego drzewa XML. Ostatni przykład w tym temacie pokazuje to.  
  
 W poniższym przykładzie użyto wyrażenia osadzonego w celu wstawienia elementu do drzewa:  
  
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
  
### <a name="using-embedded-expressions-for-content"></a>Używanie osadzonych wyrażeń dla zawartości  
 Za pomocą wyrażenia osadzonego można podać zawartość elementu:  
  
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
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Używanie zapytania LINQ w wyrażeniu osadzonym  
 Można użyć wyników kwerendy LINQ dla zawartości elementu:  
  
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
  
### <a name="using-embedded-expressions-for-node-names"></a>Używanie osadzonych wyrażeń dla nazw węzłów  
 Można również użyć wyrażeń osadzonych do obliczania nazw atrybutów, wartości atrybutów, nazw elementów i wartości elementów:  
  
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
 Jak wspomniano wcześniej, jeśli używasz wyrażenia osadzonego, aby dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzewa XML, jeśli istniejące węzły są już nadrzędne, węzły są klonowane, a nowo sklonowane węzły są dołączone do nowego drzewa XML. Jeśli istniejące węzły nie są nadrzędne, są po prostu dołączone do nowego drzewa XML.  
  
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
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
