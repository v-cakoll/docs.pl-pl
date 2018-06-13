---
title: Praca z globalnej przestrzeni nazw (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: c1f34b374f956ec0a8b9658742e529d7ccb1b2ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648908"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Praca z globalnej przestrzeni nazw (LINQ do XML) (Visual Basic)
Jednym z kluczowych funkcji usługi literałów XML w Visual Basic jest możliwość deklarowanie przestrzeni nazw XML za pomocą `Imports` instrukcji. Tej funkcji można zadeklarować przestrzeni nazw XML, który zawiera prefiks lub mogą zadeklarować domyślnej przestrzeni nazw XML.  
  
 Ta funkcja jest przydatna w dwóch sytuacjach. Najpierw przestrzenie nazw zadeklarowany w literałach XML nie jest przenoszone do wyrażenia osadzonego. Deklarowanie globalnej przestrzeni nazw zmniejsza ilość pracy, które należy wykonać, aby użyć wyrażenia osadzone z przestrzeni nazw. Po drugie należy zadeklarować globalnej przestrzeni nazw do przestrzeni nazw za pomocą właściwości XML.  
  
 Można zadeklarować globalnej przestrzeni nazw na poziomie projektu. Można również zadeklarować globalnej przestrzeni nazw na poziomie modułu, co zastępuje globalnej przestrzeni nazw poziom projektu. Na koniec można zastąpić globalnej przestrzeni nazw w postaci literału ciągu XML.  
  
 Podczas korzystania z literały XML i właściwości XML, znajdujących się w zadeklarowany globalnie przestrzeni nazw, można zobaczyć rozwiniętą nazwą literały XML i właściwości, ustawiając kursor nad nimi w programie Visual Studio. Zobaczysz rozwiniętą nazwą w etykietce narzędzia.  
  
 Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada za pomocą globalnej przestrzeni nazw `GetXmlNamespace` metody.  
  
## <a name="examples-of-global-namespaces"></a>Przykłady globalnej przestrzeni nazw  
 Poniższy przykład deklaruje globalne domyślnej przestrzeni nazw przy użyciu `Imports` instrukcji, a następnie używa literał XML zainicjować <xref:System.Xml.Linq.XElement> obiektu w tej przestrzeni nazw:  
  
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
  
 Poniższy przykład deklaruje globalnej przestrzeni nazw z prefiksem, a następnie używa literał XML można zainicjować elementu:  
  
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
  
## <a name="global-namespaces-and-embedded-expressions"></a>Globalne obszary nazw i wyrażenia osadzone  
 Przestrzenie nazw, które są zadeklarowane w literałach XML nie przenoszone do wyrażenia osadzonego. Poniższy przykład deklaruje domyślnej przestrzeni nazw. Następnie używa wyrażenia osadzonego dla `Child` elementu.  
  
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
  
 Jak widać, wynikowy kod XML zawiera deklarację domyślnej przestrzeni nazw, aby `Child` elementu jest bez przestrzeni nazw.  
  
 Można ponownie zadeklarować przestrzeni nazw w wyrażenia osadzonego w następujący sposób:  
  
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
  
 Jest to jednak bardziej skomplikowane niż korzystanie z domyślnej globalnej przestrzeni nazw, która jest lepszym rozwiązaniem. W domyślnej globalnej przestrzeni nazw możesz użyć literałów XML bez deklarowanie przestrzeni nazw. Wynikowy kod XML będzie mieć zadeklarowany globalnie domyślnej przestrzeni nazw.  
  
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
  
## <a name="using-namespaces-with-xml-properties"></a>Używanie przestrzeni nazw z właściwości XML  
 Jeśli pracujesz z drzewa XML, który znajduje się w przestrzeni nazw, a następnie użyj właściwości XML, konieczne jest użycie globalnej przestrzeni nazw, aby właściwości XML będzie również poprawną przestrzeń nazw. Poniższy przykład deklaruje drzewo XML w przestrzeni nazw. Następnie drukuje liczbę `Child` elementów.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 W tym przykładzie wskazuje, że nie istnieją żadne `Child` elementów. Tworzy następujące dane wyjściowe:  
  
```  
0  
```  
  
 Jeśli jednak deklarowaniu globalne domyślnej przestrzeni nazw, następnie zarówno literał XML i właściwości XML znajdują się w domyślnej globalnej przestrzeni nazw:  
  
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
  
 W tym przykładzie oznacza, że istnieje jeden `Child` elementu. Tworzy następujące dane wyjściowe:  
  
```  
1  
```  
  
 Przy deklarowaniu globalnej przestrzeni nazw z prefiksem można używać prefiksu literały XML i właściwości XML:  
  
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
 Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiektu przy użyciu `GetXmlNamespace` metody:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
