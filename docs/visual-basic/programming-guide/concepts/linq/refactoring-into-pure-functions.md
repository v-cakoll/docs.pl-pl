---
title: Refaktoryzacja do czystych funkcji (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0a1b8d314cf1403ef5065e5432f7acd15ebb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refaktoryzacja do czystych funkcji (Visual Basic)
Ważnym aspektem czysty przekształcenia funkcjonalności jest poznanie Refaktoryzuj kodu za pomocą czystych funkcji.  
  
 Jak już wspomniano w tej sekcji, czystej funkcji ma dwie przydatne cechy:  
  
-   Go nie ma skutków ubocznych. Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu poza funkcję.  
  
-   Jest ona zgodna. Biorąc pod uwagę ten sam zestaw danych wejściowych, zawsze zwróci taką samą wartość w danych wyjściowych.  
  
 Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Refaktoryzuj istniejący kod, aby wyeliminować niepotrzebne efektów ubocznych i zależnościami zewnętrznymi. W ten sposób można utworzyć wersji czystej funkcji istniejącego kodu.  
  
 W tym temacie omówiono jest funkcja czysty i co nie jest. [Samouczek: manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu schemat WordprocessingML i zawiera dwa przykłady do refaktoryzacji przy użyciu czystej funkcji.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Wyeliminowanie efektów ubocznych i zależnościami zewnętrznymi  
 Poniższe przykłady kontrastu dwóch funkcji nie jest czysty i czystej funkcji.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Czystej funkcji, która zmienia elementu członkowskiego klasy  
 W poniższym kodzie `HypenatedConcat` funkcja nie jest czystej funkcji, ponieważ modyfikuje `aMember` element członkowski danych klasy:  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
StringOne-StringTwo  
```  
  
 Zwróć uwagę, że jego nie znaczenia czy dane są modyfikowane ma `public` lub `private` dostępu lub jest `shared` elementu członkowskiego lub elementu członkowskiego wystąpienia. Czystej funkcji nie zmienia żadnych danych poza funkcję.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Czystej funkcji, która zmienia argumentu  
 Ponadto następujące wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jej parametr `sb`.  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 Ta wersja programu daje takie same dane wyjściowe jako pierwszej wersji, ponieważ `HypenatedConcat` funkcja została zmieniona wartość (stan) jej pierwszy parametr wywołując <xref:System.Text.StringBuilder.Append%2A> funkcję elementu członkowskiego. Należy pamiętać, że ta zmiana występuje mimo fakt który `HypenatedConcat` używa przekazywanie parametru wywołania przez wartość.  
  
> [!IMPORTANT]
>  Dla typów referencyjnych Jeśli parametr zostanie przekazany przez wartość, jej wynikiem kopię odwołanie do obiektu przekazywany. Ta kopia nadal jest skojarzona z tych samych danych wystąpienia co oryginalny odwołania (do czasu zmienna odwołania jest przypisana do nowego obiektu). Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.  
  
### <a name="pure-function"></a>Czystej funkcji  
 Ta następnej wersji programu hows implementowania `HypenatedConcat` działać jako czystej funkcji.  
  
```vb  
Module Module1  
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String  
        Return (s & "-" & appendStr)  
    End Function  
  
    Sub Main()  
        Dim s1 As String = "StringOne"  
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")  
        Console.WriteLine(s2)  
    End Sub  
End Module  
```  
  
 Ponownie, ta wersja tworzy w tym samym wierszu danych wyjściowych: `StringOne-StringTwo`. Należy pamiętać, że aby zachować wartości połączonych, jest ona przechowywana w zmiennej pośredniego `s2`.  
  
 Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (to, że ich zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty. Takie funkcje ma wiele cech możliwości pożądane, ale uniknąć kilku więcej zwichrowanych funkcjonalności idioms programowania, np. konieczności rekursję podczas proste pętli będzie wykonywać samo.  
  
## <a name="standard-query-operators"></a>Standardowe operatory zapytań  
 Istotne cechy standardowych operatorów zapytań jest, że są one zaimplementowane jako czystych funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności czysty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkcjonalności vs programowania. Programowanie imperatywnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
