---
title: Mieszany kod deklaracyjnej usterki kodu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 30760999a264c81e16104c0c9b112d442ce66121
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591624"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Mieszany kod deklaratywny/niezbędny kod (LINQ to XMLC#) ()
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera różne metody, które umożliwiają bezpośrednie modyfikowanie drzewa XML. Możesz dodać elementy, usunąć elementy, zmienić zawartość elementu, dodać atrybuty i tak dalej. Ten interfejs programowania został opisany w temacie [Modyfikowanie drzew XML (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md). Jeśli dokonujesz iteracji przez jedną z osi, na <xref:System.Xml.Linq.XContainer.Elements%2A>przykład, i modyfikujesz drzewo XML podczas iteracji przez oś, możesz zakończyć z niektórymi niektórymi usterkami.  
  
 Ten problem jest czasami znany jako "problem z Halloween".  
  
## <a name="definition-of-the-problem"></a>Definicja problemu  
 Podczas pisania kodu przy użyciu LINQ, który wykonuje iterację kolekcji, piszesz kod w stylu deklaratywnym. Więcej informacji o tym, *co* chcesz zrobić, jest bardziej zbliżone, a tym samym, *jak* chcesz go wykonać. Jeśli napiszesz kod, który 1) pobierze pierwszy element, 2) testuje go w pewnym stanie, 3) modyfikuje go, a 4) umieszcza go z powrotem na liście, wówczas będzie to kod zapasowy. Poinformujesz o tym, *jak* to zrobić.  
  
 Mieszanie tych stylów kodu w tej samej operacji polega na tym, co prowadzi do problemów. Rozważ następujące opcje:  
  
 Załóżmy, że masz połączoną listę z trzema elementami (a, b i c):  
  
 `a -> b -> c`  
  
 Teraz Załóżmy, że chcesz przejść przez połączoną listę, dodając trzy nowe elementy (a ", b" i c "). Chcesz, aby połączona lista wyglądała następująco:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Dlatego Napisz kod, który wykonuje iterację na liście, i dla każdego elementu, dodaje nowy element po nim. Co się dzieje, gdy Twój kod będzie najpierw widział `a` element i Wstaw `a'` po nim. Teraz kod zostanie przeniesiony do następnego węzła na liście, który jest teraz `a'`! Happily IT dodaje nowy element do listy `a''`.  
  
 Jak rozwiązać ten problem w świecie rzeczywistym? Można również utworzyć kopię pierwotnej połączonej listy oraz zupełnie nową listę. Lub jeśli piszesz czysty kod, możesz znaleźć pierwszy element, dodać nowy element, a następnie dwukrotnie wykonać dwa razy na liście połączonej, przenosząc nad element, który właśnie został dodany.  
  
## <a name="adding-while-iterating"></a>Dodawanie podczas iteracji  
 Załóżmy na przykład, że chcesz napisać jakiś kod dla każdego elementu w drzewie, chcesz utworzyć zduplikowany element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Ten kod przechodzi do nieskończonej pętli. Instrukcja iteruje `Elements()` przez oś, `doc` dodając nowe elementy do elementu. `foreach` Zostanie ona zakończona również za pomocą elementów, które właśnie dodał. I ponieważ przydziela nowe obiekty do każdej iteracji pętli, ostatecznie zużywa całą dostępną pamięć.  
  
 Ten problem można rozwiązać, pobierając kolekcję do pamięci przy użyciu <xref:System.Linq.Enumerable.ToList%2A> standardowego operatora zapytania w następujący sposób:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
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
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
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
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Spowoduje to utworzenie następujących danych wyjściowych:  
  
```xml  
<Root />  
```  
  
 Alternatywnie można wyeliminować iterację całkowicie poprzez wywołanie <xref:System.Xml.Linq.XElement.RemoveAll%2A> elementu nadrzędnego:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Dlaczego nie można automatycznie obsłużyć LINQ?  
 Jednym z metod jest zawsze umieszczenie wszystkiego w pamięci zamiast oceny z opóźnieniem. Jest to jednak bardzo kosztowne pod względem wydajności i użycia pamięci. W rzeczywistości, jeśli LINQ i (LINQ to XML) miały przyjąć takie podejście, wystąpi niepowodzenie w rzeczywistych sytuacjach.  
  
 Innym możliwym podejściem jest umieszczenie w kodzie LINQ składni transakcji, a kompilator próbuje analizować kod i ustalić, czy jakakolwiek konkretna kolekcja jest wymagana do materiału. Jednak próba ustalenia całego kodu, który ma efekty uboczne, to niezwykle Complex. Rozważmy następujący kod:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Taki kod analizy musi analizować metody TestSomeCondition i DoMyProjection, a także wszystkie metody wywoływane przez te metody, aby określić, czy dowolny kod ma efekty uboczne. Jednak kod analizy nie może wyszukać żadnego kodu, który miał skutki uboczne. Należy wybrać tylko kod, który miał skutki uboczne w elementach `root` podrzędnych w tej sytuacji.  
  
 LINQ to XML nie próbuje wykonać żadnej takiej analizy.  
  
 Pozwala to uniknąć tych problemów.  
  
## <a name="guidance"></a>Wskazówki  
 Najpierw nie należy mieszać kodu deklaratywnego i bezwzględnego.  
  
 Nawet jeśli znasz dokładnie semantykę kolekcji i semantykę metod, które modyfikują drzewo XML, jeśli piszesz jakiś kod sprytne, który pozwala uniknąć tych kategorii problemów, kod będzie musiał być obsługiwany przez innych deweloperów w przyszłości. i mogą nie być jasne w przypadku problemów. Jeśli Mieszasz deklaratywne i bezwzględne style kodowania, kod będzie bardziej kruchy.  
  
 Jeśli napiszesz kod, który materializuje kolekcję, aby uniknąć tych problemów, zwróć uwagę na to, że komentarze są odpowiednie w kodzie, dzięki czemu programiści mogą zrozumieć problem.  
  
 Jeśli na przykład wydajność i inne zagadnienia są dozwolone, należy użyć tylko kodu deklaratywnego. Nie należy modyfikować istniejącego drzewa XML. Generuj nowy.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
 