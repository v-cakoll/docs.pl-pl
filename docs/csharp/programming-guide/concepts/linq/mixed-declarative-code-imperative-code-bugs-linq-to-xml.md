---
title: Mieszane deklaratywne błędy kodu imperatywnego (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 76a9bb5abf6ce2700a2a0698ebc109f65e2b7eb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168352"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Mieszane deklaratywne błędy kodu/kodu imperatywnego (LINQ do XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera różne metody, które umożliwiają bezpośrednią modyfikację drzewa XML. Można dodawać elementy, usuwać elementy, zmieniać zawartość elementu, dodawać atrybuty itd. Ten interfejs programowania jest opisany w [modyfikowaniu drzew XML (LINQ do XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md). Jeśli iteracji przez jedną z osi, <xref:System.Xml.Linq.XContainer.Elements%2A>takich jak , i modyfikujesz drzewo XML podczas iteracji przez oś, można skończyć z dziwnych błędów.  
  
 Ten problem jest czasami znany jako "Halloween Problem".  
  
## <a name="definition-of-the-problem"></a>Definicja problemu  
 Podczas pisania kodu przy użyciu LINQ, który iteruje za pośrednictwem kolekcji, piszesz kod w stylu deklaratywnym. Jest to bardziej podobne do opisywania *tego, co* chcesz, a raczej, że *jak* chcesz to zrobić. Jeśli piszesz kod, który 1) pobiera pierwszy element, 2) testuje go dla pewnego warunku, 3) modyfikuje go i 4) umieszcza go z powrotem na liście, a następnie byłoby to kod imperatyw. Mówisz *komputerowi, jak* robić to, co chcesz zrobić.  
  
 Mieszanie tych stylów kodu w tej samej operacji jest to, co prowadzi do problemów. Rozważ następujące źródła:  
  
 Załóżmy, że masz połączoną listę z trzema elementami (a, b i c):  
  
 `a -> b -> c`  
  
 Teraz załóżmy, że chcesz przejść przez połączoną listę, dodając trzy nowe elementy (a', b', i c'). Chcesz, aby wynikowa lista połączona wyglądała tak:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Więc napisać kod, który iteruje przez listę i dla każdego elementu, dodaje nowy element zaraz po nim. Co się stanie, że kod `a` najpierw zobaczy element i wstaw i wstaw `a'` po nim. Teraz twój kod zostanie przesuniesię do następnego `a'`węzła na liście, który jest teraz! Szczęśliwie dodaje nowy element do `a''`listy, .  
  
 Jak rozwiązać ten problem w prawdziwym świecie? Cóż, możesz utworzyć kopię oryginalnej listy połączonej i utworzyć zupełnie nową listę. Lub jeśli piszesz kod czysto imperatywny, może znaleźć pierwszy element, dodać nowy element, a następnie przejść dwa razy na liście połączone, postępy nad elementem, który właśnie dodał.  
  
## <a name="adding-while-iterating"></a>Dodawanie podczas iteracji  
 Załóżmy na przykład, że chcesz napisać kod, który dla każdego elementu w drzewie chcesz utworzyć zduplikowany element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Ten kod przechodzi w nieskończoną pętlę. Instrukcja `foreach` iteruje `Elements()` przez oś, dodając `doc` nowe elementy do elementu. Kończy się iteracji również poprzez elementy to właśnie dodał. A ponieważ przydziela nowe obiekty z każdą iteracją pętli, ostatecznie zużywa całą dostępną pamięć.  
  
 Ten problem można rozwiązać, ściągając kolekcję do pamięci przy użyciu standardowego <xref:System.Linq.Enumerable.ToList%2A> operatora zapytania w następujący sposób:  
  
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
  
 Teraz kod działa. Wynikowe drzewo XML jest następujące:  
  
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
 Jeśli chcesz usunąć wszystkie węzły na pewnym poziomie, możesz ulec pokusie, aby napisać kod w następujący sposób:  
  
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
  
 Jednak to nie robi, co chcesz. W tej sytuacji po usunięciu pierwszego elementu, A, jest usuwany z drzewa XML zawarte w katalogu głównym, a kod w Elements metody, która wykonuje iteracji nie można znaleźć następnego elementu.  
  
 Poprzedni kod daje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Rozwiązaniem jest ponowne <xref:System.Linq.Enumerable.ToList%2A> wywołanie urzeczywistnienia kolekcji w następujący sposób:  
  
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
  
 Daje to następujące dane wyjściowe:  
  
```xml  
<Root />  
```  
  
 Alternatywnie można całkowicie wyeliminować iterację, <xref:System.Xml.Linq.XElement.RemoveAll%2A> wywołując element nadrzędny:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Dlaczego linq nie może automatycznie sobie z tym poradzić?  
 Jednym z podejść byłoby zawsze przynieść wszystko do pamięci, a nie robi leniwy oceny. Jednak byłoby to bardzo kosztowne pod względem wydajności i wykorzystania pamięci. W rzeczywistości, jeśli LINQ i (LINQ do XML) miałyby przyjąć takie podejście, nie powiodłoby się w rzeczywistych sytuacjach.  
  
 Innym możliwym podejściem byłoby umieścić w jakiejś składni transakcji w LINQ i mieć próby kompilatora do analizy kodu i ustalić, czy jakakolwiek konkretna kolekcja musi być zmaterializowane. Jednak, próby określenia całego kodu, który ma skutki uboczne jest niezwykle skomplikowane. Spójrzmy na poniższy kod:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Taki kod analizy musiałby przeanalizować metody TestSomeCondition i DoMyProjection i wszystkie metody, które te metody o nazwie, aby ustalić, czy kod miał skutki uboczne. Ale kod analizy nie mógł po prostu szukać kodu, który miał skutki uboczne. Musiałby wybrać tylko kod, który miał skutki uboczne dla `root` elementów podrzędnych w tej sytuacji.  
  
 LINQ do XML nie próbuje wykonać żadnej takiej analizy.  
  
 To do Ciebie, aby uniknąć tych problemów.  
  
## <a name="guidance"></a>Wskazówki  
 Po pierwsze, nie należy mieszać deklaratywny i imperatywny kod.  
  
 Nawet jeśli wiesz dokładnie semantyki kolekcji i semantyki metod, które modyfikują drzewo XML, jeśli napiszesz jakiś sprytny kod, który unika tych kategorii problemów, kod będzie musiał być utrzymywany przez innych deweloperów w przyszłości i mogą nie być tak jasne w kwestiach. Jeśli połączysz deklaratywne i imperatywne style kodowania, kod będzie bardziej kruchy.  
  
 Jeśli piszesz kod, który materializuje kolekcji, tak aby uniknąć tych problemów, należy pamiętać, że z komentarzami, jak odpowiednio w kodzie, tak, że programiści konserwacji zrozumie problem.  
  
 Po drugie, jeśli wydajność i inne zagadnienia pozwalają, należy użyć tylko kod deklaratywny. Nie należy modyfikować istniejącego drzewa XML. Wygeneruj nowy.  
  
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
