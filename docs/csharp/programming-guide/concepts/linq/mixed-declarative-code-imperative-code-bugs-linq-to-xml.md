---
title: Mieszane błędy kod deklaratywny kodu i Imperatywnego (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 56d8140613f3dae7f99c1374634dbd8bdf094a7c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585801"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Mieszane błędy kodu deklaratywnego/Imperatywne (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera różne metody, które umożliwiają modyfikowanie drzewa XML bezpośrednio. Można dodać elementy, usuwanie elementów, zmienić zawartość elementu, dodawanie atrybutów i tak dalej. Ten interfejs programowania jest opisana w [modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Jeśli użytkownik są iteracji w jednej osi, takie jak <xref:System.Xml.Linq.XContainer.Elements%2A>i są modyfikowanie drzewa XML jako iterację osi, użytkownik może wystąpić pewne błędy otrzymano nieoczekiwany.  
  
 Ten problem jest czasami określany jako "Halloween Problem".  
  
## <a name="definition-of-the-problem"></a>Definicja problemu  
 Podczas pisania kodu za pomocą LINQ, który iteruje po kolekcji pisania kodu w stylu deklaratywnego. Jest więcej podobnie opisujące *co* chcesz, a które *jak* chcesz wykonywania pracy. Jeśli piszesz kod, który (1) pierwszego elementu, 2) testy dla jakiś warunek 3) modyfikuje je i 4) umieszcza go z powrotem do listy, a następnie będzie to kodu imperatywnego. Sprawi, że komputer *jak* zrobić lepiej będzie gotowe.  
  
 Mieszanie te style kodu w tej samej operacji jest o tym, co prowadzi do problemów. Rozważ następujące opcje:  
  
 Załóżmy, że masz listę połączoną z trzema elementami w nim (, b i c):  
  
 `a -> b -> c`  
  
 Załóżmy, że chcesz przenieść za pośrednictwem połączonej listy dodawania trzech nowych elementów (", b", a c "). Chcesz, aby wynikowe listy dwukierunkowej, aby wyglądał następująco:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Dlatego napisać kod, który wykonuje iterację na liście, a następnie dla każdego elementu dodaje nowe uprawnienie elementu po nim. Co się stanie, to najpierw zostanie wyświetlony kod `a` elementu i Wstaw `a'` po nim. Teraz kod przejdzie do kolejnego węzła na liście, która jest teraz `a'`! Trafem korzysta dodaje nowy element do listy, `a''`.  
  
 Jak będzie można rozwiązać ten problem w rzeczywistych warunkach? Dobrze Utwórz kopię oryginalnego połączonej listy i Utwórz całkowicie nową listę. Lub jeśli piszesz kodu czysto imperatywnego, może się okazać, pierwszy element, Dodaj nowy element, a następnie przejdź dwa razy na liście połączonej, przesuwania nad elementem, który właśnie został dodany.  
  
## <a name="adding-while-iterating"></a>Dodawanie podczas iteracja  
 Na przykład załóżmy, że chcesz pisanie kodu dla każdego elementu w drzewie chcesz utworzyć zduplikowany element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Ten kod przechodzi w pętli nieskończonej. `foreach` Iteruje po instrukcji `Elements()` osi, dodawanie nowych elementów do `doc` elementu. Kończy się ono również iteracji na elementach, który właśnie został dodany. A ponieważ są przydzielane nowych obiektów wraz z każdą iteracją pętli, po pewnym czasie zużyje całą dostępną pamięć.  
  
 Możesz rozwiązać ten problem przez pobieranie kolekcji w pamięci, używając <xref:System.Linq.Enumerable.ToList%2A> standardowego operatora zapytania, w następujący sposób:  
  
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
  
 Teraz kod działa. Wynikowe drzewo składni XML jest następująca:  
  
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
  
## <a name="deleting-while-iterating"></a>Usuwanie podczas iteracja  
 Jeśli chcesz usunąć wszystkie węzły, na pewnym etapie, możesz chcieć wykorzystać do pisania kodu, jak pokazano poniżej:  
  
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
  
 Jednak to nie należy. W takiej sytuacji po usunięciu pierwszy element, A, zostanie on usunięty z drzewa XML znajdujących się w katalogu głównym, a kod w metodzie elementów, który wykonuje iteracja nie można odnaleźć następnego elementu.  
  
 Powyższy kod generuje następujące wyniki:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 To rozwiązanie jest ponownie wywołanie <xref:System.Linq.Enumerable.ToList%2A> do zmaterializowania kolekcji, w następujący sposób:  
  
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
  
 To generuje następujące wyniki:  
  
```xml  
<Root />  
```  
  
 Alternatywnie, można wyeliminować iteracji całkowicie przez wywołanie metody <xref:System.Xml.Linq.XElement.RemoveAll%2A> elementu nadrzędnego:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Dlaczego nie mogę LINQ automatycznie obsługiwać to?  
 Jedno z podejść jest zawsze Przenieś wszystko do pamięci, zamiast wykonywania obliczanie z opóźnieniem. Jednakże może być bardzo kosztowna pod względem wydajności i użycia pamięci. W rzeczywistości gdyby LINQ i (LINQ to XML) do zastosowania tego podejścia, przestaną działać w rzeczywistych warunkach.  
  
 Innym podejściem możliwe będzie umieścić w jakieś składni transakcji na składnika LINQ i mają kompilatora próba przeanalizowania kodu i określenia, czy żadnej określonej kolekcji jest wymagana do być zmaterializowany. Próba ustalenia cały kod, który ma efekty uboczne jest jednak bardzo złożone. Rozważmy poniższy kod:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Taki kod analizy należałoby analizowanie metod TestSomeCondition i DoMyProjection i wszystkie metody, które wywołały tych metod, aby określić, jeśli dowolny kod ma efekty uboczne. Jednak kod analizy nie można po prostu szukać wszelki kod, który ma efekty uboczne. Należałoby w celu wybrania tylko kod, który ma efekty uboczne na elementy podrzędne `root` w takiej sytuacji.  
  
 LINQ to XML nie próbuje wykonywać takie analizę.  
  
 Jest on do Ciebie, aby uniknąć tych problemów.  
  
## <a name="guidance"></a>Wskazówki  
 Po pierwsze nie należy mieszać kodu deklaratywnego i imperatywnego.  
  
 Nawet wtedy, gdy znasz dokładnie semantyki kolekcji i semantyka metody, które modyfikowanie drzewa XML, jeśli piszesz niektóre inteligentne kod, który pozwala uniknąć tych kategorii problemów, Twój kod będzie muszą być przechowywane przez innych programistów w przyszłości , i nie może być jako zwykły na problemy. Po przemieszaniu deklaratywnego i imperatywnego kodowania style, Twój kod będzie bardziej kruchy.  
  
 Jeśli piszesz kod, który materializuje kolekcji, tak aby uniknąć tych problemów, należy pamiętać, go z komentarzami, zgodnie z potrzebami w swoim kodzie, aby programiści obsługi będzie zrozumiałe dla problemu.  
  
 Po drugie jeśli zezwala na wydajność i innych zagadnień, należy użyć tylko kod deklaratywny. Nie należy modyfikować swoje istniejące drzewa XML. Generuj nowe hasło.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane LINQ to XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
