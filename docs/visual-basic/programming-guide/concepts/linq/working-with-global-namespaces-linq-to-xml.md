---
title: Praca z globalnymi przestrzeniami nazw (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: d8e74e949815d36f06f522460cc31ca6c3ccabb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827383"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Praca z globalnymi przestrzeniami nazw (LINQ to XML) (Visual Basic)
Jedną z kluczowych funkcji literałów XML w Visual Basic jest możliwość zadeklarować przestrzeni nazw XML przy użyciu `Imports` instrukcji. Dzięki tej funkcji można zadeklarować przestrzeni nazw XML, który używa prefiksu lub można zadeklarować domyślnej przestrzeni nazw XML.  
  
 Ta możliwość jest przydatna w dwóch sytuacjach. Po pierwsze przestrzenie nazw zadeklarowanych w literałach XML nie jest przenoszone do wyrażenia osadzone. Deklarowanie globalnymi przestrzeniami nazw zmniejsza ilość pracy, które należy wykonać wyrażenia osadzone za pomocą przestrzeni nazw. Po drugie należy zadeklarować globalnymi przestrzeniami nazw, aby można było używać przestrzeni nazw za pomocą właściwości XML.  
  
 Można zadeklarować globalnymi przestrzeniami nazw na poziomie projektu. Można również zadeklarować globalnej przestrzeni nazw na poziom modułu, który zastępuje globalnymi przestrzeniami nazw na poziomie projektu. Na koniec można zastąpić globalnej przestrzeni nazw w literał XML.  
  
 Korzystając z literały XML i właściwości XML, które znajdują się w przestrzeni nazw z globalnie zadeklarowane, widać rozwiniętej nazwy w literałach XML i właściwości, umieszczając kursor myszy nad nimi w programie Visual Studio. Zobaczysz rozwiniętą nazwę w etykietce narzędzia.  
  
 Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do globalnej przestrzeni nazw za pomocą `GetXmlNamespace` metody.  
  
## <a name="examples-of-global-namespaces"></a>Przykłady globalnymi przestrzeniami nazw  
 Poniższy przykład deklaruje globalnej domyślnej przestrzeni nazw za pomocą `Imports` instrukcji, a następnie używa literał XML można zainicjować <xref:System.Xml.Linq.XElement> obiektów w tej przestrzeni nazw:  
  
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
  
 Poniższy przykład deklaruje globalnej przestrzeni nazw z prefiksem, a następnie używa literał XML, aby zainicjować element:  
  
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
 Przestrzenie nazw, które są zadeklarowane w literałach XML nie przeniosą się do wyrażenia osadzone. Poniższy przykład deklaruje domyślny obszar nazw. Następnie używa wyrażenia osadzone dla `Child` elementu.  
  
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
  
 Jak widać, wynikowy kod XML zawiera deklarację domyślnej przestrzeni nazw, aby `Child` element znajduje się w żadnej przestrzeni nazw.  
  
 Można ponownie zadeklarować przestrzeni nazw w wyrażeniu osadzonego w następujący sposób:  
  
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
  
 To bardziej skomplikowane niż korzystanie z domyślnej globalnej przestrzeni nazw, który jest lepszym rozwiązaniem. Przy użyciu domyślnej globalnej przestrzeni nazw możesz użyć literałów XML bez deklarowanie przestrzeni nazw. Wynikowy kod XML będzie mieć globalnie zadeklarowane domyślny obszar nazw.  
  
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
  
## <a name="using-namespaces-with-xml-properties"></a>Używanie przestrzeni nazw za pomocą właściwości XML  
 Jeśli pracujesz z drzewa XML, który znajduje się w przestrzeni nazw i korzystać z właściwości XML, następnie należy użyć globalnej przestrzeni nazw, aby właściwości XML będzie również poprawną przestrzeń nazw. Poniższy przykład deklaruje drzewa XML w przestrzeni nazw. Następnie wyświetla liczbę `Child` elementów.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 W tym przykładzie wskazuje, że nie istnieją żadne `Child` elementów. Generuje następujące wyniki:  
  
```  
0  
```  
  
 Jeśli jednak zadeklarować globalnych domyślny obszar nazw, następnie literał XML i właściwości XML znajdują się w globalnej przestrzeni nazw z domyślnej:  
  
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
  
 W tym przykładzie wskazuje, że istnieje jeden `Child` elementu. Generuje następujące wyniki:  
  
```  
1  
```  
  
 Jeśli zadeklarujesz globalnej przestrzeni nazw, który zawiera prefiks służy prefiks dla literały XML i właściwości XML:  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace i globalnej przestrzeni nazw  
 Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiektu za pomocą `GetXmlNamespace` metody:  
  
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
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Zobacz także

- [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
