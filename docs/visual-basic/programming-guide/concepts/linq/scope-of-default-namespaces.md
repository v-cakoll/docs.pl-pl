---
title: Zakres domyślnych przestrzeni nazw w języku Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: e33505dd8e8ad94e3c758f15f245d0cbaf6987bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836717"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Zakres domyślnych przestrzeni nazw w języku Visual Basic
Domyślne obszary nazw, reprezentowany w drzewie XML nie są uwzględnione w zakresie zapytania. Jeśli masz plik XML, który znajduje się w domyślnej przestrzeni nazw, nadal należy zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i łączą je z nazwą lokalną, można utworzyć kwalifikowane nazwy ma być używany w zapytaniu.  
  
 Jedną z najbardziej typowych problemów podczas wykonywania zapytań dotyczących drzew XML jest, że jeśli drzewa XML ma domyślny obszar nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie znajdowały się w przestrzeni nazw.  
  
 Pierwszy zestaw przykładów w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest ładowany, że jest nieprawidłowo wysyłane zapytanie.  
  
 Drugi zestaw przykładach pokazano niezbędnych poprawek, dzięki czemu można tworzyć zapytania XML w przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano tworzenie obiektu XML w przestrzeni nazw i ustaw zapytania, które zwraca żadnego wyniku.  
  
### <a name="code"></a>Kod  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano tworzenie obiektu XML w przestrzeni nazw i zapytanie, które są poprawnie kodowane.  
  
 W przeciwieństwie do kodowane niepoprawnie powyższym przykładzie właściwe podejście, korzystając z języka Visual Basic jest zadeklarowania i zainicjowania domyślnej globalnej przestrzeni nazw. Umieszcza wszystkie właściwości XML domyślny obszar nazw. Nie inne modyfikacje są wymagane do przykładu tak, aby upewnić się, że działa prawidłowo.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Zobacz także

- [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
