---
title: Wprowadzenie do literałów XML w Visual BASIC2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397587"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Wprowadzenie do literałów XML w Visual Basic
Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w Visual Basic.  
  
 Aby uzyskać informacje o używaniu wyników zapytań LINQ jako zawartości dla drzewa XML, zobacz [funkcjonalne konstruowanie (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).  
  
 Aby uzyskać więcej informacji na temat literałów XML w Visual Basic, zobacz [omówienie LINQ to XML w Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Tworzenie drzew XML  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Xml.Linq.XElement> , w tym przypadku `contacts` :  
  
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
 Można utworzyć obiekt zawierający <xref:System.Xml.Linq.XElement> prostą zawartość w następujący sposób:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Tworzenie pustego elementu  
 Można utworzyć pustą <xref:System.Xml.Linq.XElement> w następujący sposób:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Używanie wyrażeń osadzonych  
 Ważną funkcją literałów XML jest to, że dopuszczają one osadzone wyrażenia. Wyrażenia osadzone umożliwiają ocenę wyrażenia i wstawianie wyników wyrażenia do drzewa XML. Jeśli wyrażenie szacuje typ <xref:System.Xml.Linq.XElement> , element zostanie wstawiony do drzewa. Jeśli wyrażenie szacuje typ <xref:System.Xml.Linq.XAttribute> , atrybut zostanie wstawiony do drzewa. Elementy i atrybuty można wstawiać do drzewa tylko wtedy, gdy są prawidłowe.  
  
 Należy pamiętać, że tylko pojedyncze wyrażenie może przejść do wyrażenia osadzonego. Nie można osadzić wielu instrukcji. Jeśli wyrażenie wykracza poza pojedynczy wiersz, należy użyć znaku kontynuacji wiersza.  
  
 Jeśli używasz wyrażenia osadzonego do dodawania istniejących węzłów (w tym elementów) i atrybutów do nowego drzewa XML i jeśli istniejące węzły są już nadrzędne, węzły są klonowane. Nowo sklonowane węzły są dołączone do nowego drzewa XML. Jeśli istniejące węzły nie są nadrzędne, węzły są po prostu dołączone do nowego drzewa XML. W ostatnim przykładzie w tym temacie pokazano, jak to zrobić.  
  
 W poniższym przykładzie do wstawienia elementu do drzewa jest stosowane wyrażenie osadzone:  
  
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
 Możesz użyć wyrażenia osadzonego, aby dostarczyć zawartość elementu:  
  
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
 Możesz użyć wyników zapytania LINQ dla zawartości elementu:  
  
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
  
### <a name="using-embedded-expressions-for-node-names"></a>Używanie wyrażeń osadzonych dla nazw węzłów  
 Możesz również użyć wyrażeń osadzonych do obliczania nazw atrybutów, wartości atrybutów, nazw elementów i wartości elementów:  
  
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
 Jak wspomniano wcześniej, jeśli używasz wyrażenia osadzonego do dodawania istniejących węzłów (w tym elementów) i atrybutów do nowego drzewa XML, jeśli istniejące węzły są już nadrzędne, węzły są klonowane i nowo sklonowane węzły są dołączone do nowego drzewa XML. Jeśli istniejące węzły nie są nadrzędne, są one po prostu dołączone do nowego drzewa XML.  
  
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

- [Tworzenie drzew XML (Visual Basic)](creating-xml-trees.md)
