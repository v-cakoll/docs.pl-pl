---
title: Praca z globalnymi przestrzeniami nazw (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 93c7c654e43b579456633dea90ba6a362ff095f7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582356"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Praca z globalnymi przestrzeniami nazw (Visual Basic) (LINQ to XML)
Jedną z najważniejszych funkcji literałów XML w Visual Basic jest możliwość deklarowania przestrzeni nazw XML przy użyciu instrukcji `Imports`. Korzystając z tej funkcji, można zadeklarować przestrzeń nazw XML, która używa prefiksu lub można zadeklarować domyślną przestrzeń nazw XML.  
  
 Ta funkcja jest przydatna w dwóch sytuacjach. Po pierwsze obszary nazw zadeklarowane w literałach XML nie są przenoszone do wyrażeń osadzonych. Deklarowanie globalnych przestrzeni nazw zmniejsza ilość pracy, którą trzeba wykonać, aby korzystać z osadzonych wyrażeń z przestrzeniami nazw. Po drugie należy zadeklarować globalne przestrzenie nazw w celu używania przestrzeni nazw z właściwościami XML.  
  
 Można zadeklarować globalne przestrzenie nazw na poziomie projektu. Można również zadeklarować globalne przestrzenie nazw na poziomie modułu, który zastępuje globalne przestrzenie nazw na poziomie projektu. Na koniec można przesłonić globalne przestrzenie nazw w literale XML.  
  
 W przypadku używania literałów XML lub właściwości XML, które znajdują się w globalnie zadeklarowanych przestrzeniach nazw, można zobaczyć rozwinięte nazwy literałów XML lub właściwości przez umieszczenie ich w programie Visual Studio. Rozwinięta nazwa zostanie wyświetlona w etykietce narzędzia.  
  
 Można uzyskać <xref:System.Xml.Linq.XNamespace> obiektu, który odpowiada globalnej przestrzeni nazw, przy użyciu metody `GetXmlNamespace`.  
  
## <a name="examples-of-global-namespaces"></a>Przykłady globalnych przestrzeni nazw  
 Poniższy przykład deklaruje domyślną globalną przestrzeń nazw przy użyciu instrukcji `Imports`, a następnie używa literału XML do zainicjowania obiektu <xref:System.Xml.Linq.XElement> w tej przestrzeni nazw:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 Poniższy przykład deklaruje globalną przestrzeń nazw z prefiksem, a następnie używa literału XML do zainicjowania elementu:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>Globalne przestrzenie nazw i wyrażenia osadzone  
 Przestrzenie nazw, które są zadeklarowane w literałach XML, nie są przenoszone do wyrażeń osadzonych. Poniższy przykład deklaruje domyślną przestrzeń nazw. Następnie używa osadzonego wyrażenia dla elementu `Child`.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 Jak widać, otrzymany kod XML zawiera deklarację domyślnej przestrzeni nazw, dzięki czemu element `Child` nie jest w żadnej przestrzeni nazw.  
  
 Można ponownie zadeklarować przestrzeń nazw w wyrażeniu osadzonym w następujący sposób:  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 Jednak jest to bardziej skomplikowany sposób użycia niż Globalna domyślna przestrzeń nazw, która jest lepszym rozwiązaniem. Przy użyciu globalnej domyślnej przestrzeni nazw można używać literałów XML bez deklarowania przestrzeni nazw. Otrzymany kod XML będzie w globalnie zadeklarowanej przestrzeni nazw default.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>Używanie przestrzeni nazw z właściwościami XML  
 Jeśli pracujesz z drzewem XML, który znajduje się w przestrzeni nazw, i używasz właściwości XML, należy użyć globalnej przestrzeni nazw, aby właściwości XML również znajdować się w poprawnej przestrzeni nazw. Poniższy przykład deklaruje drzewo XML w przestrzeni nazw. Następnie drukuje liczbę elementów `Child`.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Ten przykład wskazuje, że nie ma żadnych `Child` elementów. Generuje następujące dane wyjściowe:  
  
```console  
0  
```  
  
 Jeśli jednak zostanie zadeklarowana Domyślna globalna przestrzeń nazw, wówczas zarówno literał XML, jak i Właściwość XML znajdują się w domyślnej globalnej przestrzeni nazw:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 Ten przykład wskazuje, że istnieje jeden `Child` elementu. Generuje następujące dane wyjściowe:  
  
```console  
1  
```  
  
 Jeśli zadeklarujesz globalną przestrzeń nazw, która ma prefiks, można użyć prefiksu dla obu literałów XML i właściwości XML:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace i globalne przestrzenie nazw  
 Obiekt <xref:System.Xml.Linq.XNamespace> można uzyskać za pomocą metody `GetXmlNamespace`:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
