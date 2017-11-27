---
title: "Zakres domyślne obszary nazw w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aaf5395f1216b0cb56f2d1f003e42ed30790012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Zakres domyślne obszary nazw w Visual Basic
Domyślne obszary nazw reprezentowany w drzewie XML nie są w zakresie zapytania. Jeśli masz kod XML, który znajduje się w domyślnej przestrzeni nazw, nadal należy zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i połączyć ją z nazwą lokalną aby kwalifikowana nazwa do użycia w zapytaniu.  
  
 Jest jedną z najczęściej występujących problemów podczas wykonywania zapytania drzewa XML, że jeśli drzewo składni XML ma domyślnej przestrzeni nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie zostały w przestrzeni nazw.  
  
 Pierwszy zestaw przykłady w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest załadowany, ale jest poddawany kwerendzie nieprawidłowo.  
  
 Drugi zestaw przykładach niezbędnych poprawek, aby wykonać zapytanie XML w przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia tworzenie XML w przestrzeni nazw, a następnie ustaw kwerendę, która zwraca żadnego wyniku.  
  
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
 Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie zakodowanej poprawnie.  
  
 W przeciwieństwie do niepoprawnie zakodowany powyższym przykładzie właściwe podejście, korzystając z języka Visual Basic jest zadeklarować i zainicjować domyślnej globalnej przestrzeni nazw. Wszystkie właściwości XML to umieszcza w domyślnej przestrzeni nazw. Nie inne zmiany są wymagane, na przykład aby działać poprawnie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
