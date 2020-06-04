---
title: Mieszane błędy kodu deklaratywnego i imperatywnego (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e5526a64805b19ea293d3ef28636738923d03662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84361076"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Mieszany kod deklaratywny/niezbędny kod (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera różne metody, które umożliwiają bezpośrednie modyfikowanie drzewa XML. Możesz dodać elementy, usunąć elementy, zmienić zawartość elementu, dodać atrybuty i tak dalej. Ten interfejs programowania został opisany w temacie [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md). Jeśli dokonujesz iteracji przez jedną z osi, na przykład <xref:System.Xml.Linq.XContainer.Elements%2A> , i modyfikujesz drzewo XML podczas iteracji przez oś, możesz zakończyć z niektórymi niektórymi usterkami.  
  
 Ten problem jest czasami znany jako "problem z Halloween".  
  
## <a name="definition-of-the-problem"></a>Definicja problemu  
 Podczas pisania kodu przy użyciu LINQ, który wykonuje iterację kolekcji, piszesz kod w stylu deklaratywnym. Więcej informacji o tym, *co* chcesz zrobić, jest bardziej zbliżone, a tym samym, *jak* chcesz go wykonać. Jeśli napiszesz kod, który 1) pobierze pierwszy element, 2) testuje go w pewnym stanie, 3) modyfikuje go, a 4) umieszcza go z powrotem na liście, wówczas będzie to kod zapasowy. Poinformujesz o tym, *jak* to zrobić.  
  
 Mieszanie tych stylów kodu w tej samej operacji polega na tym, co prowadzi do problemów. Rozważ następujące źródła:  
  
 Załóżmy, że masz połączoną listę z trzema elementami (a, b i c):  
  
 `a -> b -> c`  
  
 Teraz Załóżmy, że chcesz przejść przez połączoną listę, dodając trzy nowe elementy (a ", b" i c "). Chcesz, aby połączona lista wyglądała następująco:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Dlatego Napisz kod, który wykonuje iterację na liście, i dla każdego elementu, dodaje nowy element po nim. Co się dzieje, gdy Twój kod będzie najpierw widział `a` element i Wstaw `a'` po nim. Teraz kod zostanie przeniesiony do następnego węzła na liście, który jest teraz `a'` ! Happily IT dodaje nowy element do listy `a''` .  
  
 Jak rozwiązać ten problem w świecie rzeczywistym? Można również utworzyć kopię pierwotnej połączonej listy oraz zupełnie nową listę. Lub jeśli piszesz czysty kod, możesz znaleźć pierwszy element, dodać nowy element, a następnie dwukrotnie wykonać dwa razy na liście połączonej, przenosząc nad element, który właśnie został dodany.  
  
## <a name="adding-while-iterating"></a>Dodawanie podczas iteracji  
 Załóżmy na przykład, że chcesz napisać jakiś kod dla każdego elementu w drzewie, chcesz utworzyć zduplikowany element:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 Ten kod przechodzi do nieskończonej pętli. `foreach`Instrukcja iteruje przez `Elements()` oś, dodając nowe elementy do `doc` elementu. Zostanie ona zakończona również za pomocą elementów, które właśnie dodał. I ponieważ przydziela nowe obiekty do każdej iteracji pętli, ostatecznie zużywa całą dostępną pamięć.  
  
 Ten problem można rozwiązać, pobierając kolekcję do pamięci przy użyciu <xref:System.Linq.Enumerable.ToList%2A> standardowego operatora zapytania w następujący sposób:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
```  
  
 Teraz kod działa. Utworzone drzewo XML jest następujące:  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a>Usuwanie podczas iteracji  
 Jeśli chcesz usunąć wszystkie węzły na określonym poziomie, być może chcesz napisać kod podobny do poniższego:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 Nie jest to jednak wykonywane. W tej sytuacji po usunięciu pierwszego elementu, jest on usuwany z drzewa XML zawartego w katalogu głównym, a kod w metodzie element, który wykonuje iterację nie może znaleźć następnego elementu.  
  
 Poprzedni kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Rozwiązanie to ponownie wywołuje <xref:System.Linq.Enumerable.ToList%2A> zmaterializowania kolekcji w następujący sposób:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 Spowoduje to utworzenie następujących danych wyjściowych:  
  
```xml  
<Root />  
```  
  
 Alternatywnie można wyeliminować iterację całkowicie poprzez wywołanie <xref:System.Xml.Linq.XElement.RemoveAll%2A> elementu nadrzędnego:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Dlaczego nie można automatycznie obsłużyć LINQ?  
 Jednym z metod jest zawsze umieszczenie wszystkiego w pamięci zamiast oceny z opóźnieniem. Jest to jednak bardzo kosztowne pod względem wydajności i użycia pamięci. W rzeczywistości, jeśli LINQ i (LINQ to XML) miały przyjąć takie podejście, wystąpi niepowodzenie w rzeczywistych sytuacjach.  
  
 Innym możliwym podejściem jest umieszczenie w kodzie LINQ składni transakcji, a kompilator próbuje analizować kod i ustalić, czy jakakolwiek konkretna kolekcja jest wymagana do materiału. Jednak próba ustalenia całego kodu, który ma efekty uboczne, to niezwykle Complex. Spójrzmy na poniższy kod:  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Taki kod analizy musi analizować metody TestSomeCondition i DoMyProjection, a także wszystkie metody wywoływane przez te metody, aby określić, czy dowolny kod ma efekty uboczne. Jednak kod analizy nie może wyszukać żadnego kodu, który miał skutki uboczne. Należy wybrać tylko kod, który miał skutki uboczne w elementach podrzędnych `root` w tej sytuacji.  
  
 LINQ to XML nie próbuje wykonać żadnej takiej analizy.  
  
 Pozwala to uniknąć tych problemów.  
  
## <a name="guidance"></a>Wskazówki  
 Najpierw nie należy mieszać kodu deklaratywnego i bezwzględnego.  
  
 Nawet jeśli znasz dokładnie semantykę kolekcji i semantykę metod, które modyfikują drzewo XML, jeśli napiszesz jakiś kod sprytne, który pozwala uniknąć tych kategorii problemów, kod będzie musiał być obsługiwany przez innych deweloperów w przyszłości i mogą nie być jasne w przypadku problemów. Jeśli Mieszasz deklaratywne i bezwzględne style kodowania, kod będzie bardziej kruchy.  
  
 Jeśli napiszesz kod, który materializuje kolekcję, aby uniknąć tych problemów, zwróć uwagę na to, że komentarze są odpowiednie w kodzie, dzięki czemu programiści mogą zrozumieć problem.  
  
 Jeśli na przykład wydajność i inne zagadnienia są dozwolone, należy użyć tylko kodu deklaratywnego. Nie należy modyfikować istniejącego drzewa XML. Generuj nowy.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane programowanie LINQ to XML (Visual Basic)](advanced-linq-to-xml-programming.md)
