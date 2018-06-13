---
title: Wprowadzenie do literałów XML w Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: bac0a4a297dcecce5465e5a1a1c02e4cbc9848a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646812"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Wprowadzenie do literałów XML w Visual Basic
Ta sekcja zawiera informacje o tworzeniu drzew XML w Visual Basic.  
  
 Aby dowiedzieć się, jak przy użyciu wyników zapytania LINQ jako zawartość dla drzewa XML, zobacz [funkcjonalności konstrukcji (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Aby uzyskać więcej informacji w literałach XML w Visual Basic, zobacz [Przegląd LINQ do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Tworzenie XML drzewa  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Xml.Linq.XElement>, w tym przypadku `contacts`:  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Tworzenie XElement o zawartości prostej  
 Można utworzyć <xref:System.Xml.Linq.XElement> prostej zawartości, który zawiera w następujący sposób:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Tworzenie pustego elementu  
 Możesz utworzyć pustą <xref:System.Xml.Linq.XElement>w następujący sposób:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Za pomocą wyrażenia osadzone  
 Ważna cecha literałów XML to, czy umożliwiają one wyrażenia osadzone. Wyrażenia osadzone umożliwiają oszacować wyrażenia i Wstaw wyniki wyrażenia do drzewa XML. Jeśli wyrażenie ma typ <xref:System.Xml.Linq.XElement>, element znajduje się w drzewie. Jeśli wyrażenie ma typ <xref:System.Xml.Linq.XAttribute>, atrybut zostaną wstawione do drzewa. Elementy i atrybuty można wstawiać do drzewa, tylko gdy są one prawidłowe.  
  
 Należy pamiętać, że tylko jedno wyrażenie można przejść do wyrażenia osadzonego. Nie można osadzić użycie wielu instrukcji. Jeśli wyrażenie wykracza poza jednym wierszu, należy użyć znak kontynuacji wiersza.  
  
 Użycie wyrażenia osadzonego, aby dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzew XML i jeśli przez istniejące węzły są już element nadrzędny, węzły są klonowane. Nowo sklonowanego węzły są dołączone do nowego drzew XML. Jeśli istniejących węzłów nie jest elementem nadrzędnym, węzły są po prostu dołączone do nowego drzew XML. W ostatnim przykładzie w tym temacie pokazano to.  
  
 W poniższym przykładzie użyto wyrażenia osadzonego można wstawić elementu do drzewa:  
  
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
  
### <a name="using-embedded-expressions-for-content"></a>Za pomocą wyrażenia osadzone zawartości  
 Można użyć wyrażenia osadzonego do dostarczania zawartości elementu:  
  
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
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>W wyrażeniu osadzonych za pomocą zapytań LINQ  
 Można użyć wyników zapytania LINQ dla zawartości elementu:  
  
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
  
### <a name="using-embedded-expressions-for-node-names"></a>Dla nazwy węzła przy użyciu wyrażenia osadzone  
 Wyrażenia osadzone umożliwia również obliczyć nazwy atrybutów, wartości atrybutu nazwy elementów i wartości elementów:  
  
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
  
### <a name="cloning-vs-attaching"></a>Vs w klonowania. Dołączanie  
 Jak wspomniano wcześniej, jeśli używasz wyrażenia osadzonego dodać istniejących węzłów (w tym elementy) i atrybuty do nowego drzew XML, jeśli istniejące węzły są już element nadrzędny, węzły są klonowane i nowo sklonowanego węzły są dołączone do nowego drzew XML. Jeśli istniejących węzłów nie jest elementem nadrzędnym, po prostu są one dołączone do nowego drzew XML.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
