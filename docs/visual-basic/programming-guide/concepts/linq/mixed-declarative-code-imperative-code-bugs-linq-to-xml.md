---
title: Mieszane usterki deklaratywne kodu Imperatywne kodu (LINQ do XML) (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d5d50b5444a9aca429eb5ddb682cd23c468a1e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Mieszane usterki kodu deklaratywne kodu/Imperatywne (LINQ do XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera różne metody, dzięki którym można bezpośrednio modyfikować drzewo XML. Można dodawać elementów, usuń elementy, zmienić zawartość elementu, dodać atrybuty i itd. Ten interfejs programowania jest opisany w [modyfikowanie drzew XML (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Jeśli użytkownik są iteracji w jednej osi, takie jak <xref:System.Xml.Linq.XContainer.Elements%2A>i modyfikujesz drzewa XML jako iterację osi, można na końcu niektóre dziwne usterki.  
  
 Ten problem jest czasami określany jako "Problemu Halloween".  
  
## <a name="definition-of-the-problem"></a>Definicja problemu  
 Podczas pisania kodu za pomocą LINQ, który iteruje po kolekcji deklaratywne styl pisania kodu. Jest więcej podobnie opisujące *co* ma, a nie że *jak* chcesz pobrać go wykonać. Podczas pisania kodu, który 1) jest pierwszym elementem, testy 2) dla niektórych warunku 3) modyfikuje go i 4) umieszcza je z powrotem do listy, a następnie będzie to konieczne kodu. Sprawi, że komputer *jak* zrobić, co ma gotowe.  
  
 Mieszanie te style kodu w tej samej operacji jest, co prowadzi do problemów. Rozważ następujące opcje:  
  
 Załóżmy, że masz listy połączonej z trzema elementami w nim (, b i c):  
  
 `a -> b -> c`  
  
 Załóżmy, że chcesz przenieść za pomocą listy połączonej, dodawania trzech nowych elementów (", b" i c'). Ma wynikowej listy połączonej, aby wyglądały następująco:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Tak pisania kodu, który iteruje po za pośrednictwem listy, a każdy element dodaje nowe prawo elementu po nim. Co się stanie, to najpierw zostanie wyświetlony kod `a` elementu i Wstaw `a'` po nim. Teraz, kodu przechodzi do następnego węzła na liście, który jest obecnie `a'`! Happily dodaje nowy element do listy, `a''`.  
  
 Jak będzie można rozwiązać ten problem w świecie rzeczywistym? Utwórz kopię oryginalnej listy połączonej i Utwórz całkowicie nową listę. Lub jeśli są pisanie kodu czysto konieczne może okazać się pierwszy element Dodaj nowy element, a następnie przejść dwa razy w listy połączonej, zaawansowane nad elementem, który właśnie został dodany.  
  
## <a name="adding-while-iterating"></a>Dodawanie podczas iteracja  
 Na przykład załóżmy, że chcesz pisania kodu dla każdego elementu w drzewie chcesz utworzyć zduplikowany element:  
  
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
  
 Ten kod przechodzi w pętli nieskończonej. `foreach` Iteruje po instrukcji `Elements()` osi, dodawanie nowych elementów do `doc` elementu. Kończy się ono również iteracja elementy, które go dodać. I ponieważ przydzielania nowych obiektów z każdej iteracji pętli, po pewnym czasie zużyje całą dostępną pamięć.  
  
 Można rozwiązać ten problem przez ściąganie kolekcji do pamięci przy użyciu <xref:System.Linq.Enumerable.ToList%2A> operator standardowej kwerendy, w następujący sposób:  
  
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
 Jeśli chcesz usunąć wszystkie węzły na określonym poziomie, może się wydawać do pisania kodu podobne do poniższych:  
  
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
  
 Jednak to nie chcesz. Po usunięciu elementu pierwszy, A, w takiej sytuacji jest usuwany z drzewa XML zawarte w katalogu głównym, a kod w metodzie elementy obsługującym iteracja nie można odnaleźć następnego elementu.  
  
 Poprzedni kod tworzy następujące dane wyjściowe:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Rozwiązanie to ponownie wywołać <xref:System.Linq.Enumerable.ToList%2A> do zmaterializowania kolekcji, w następujący sposób:  
  
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
  
 Alternatywnie można wyeliminować iteracji całkowicie przez wywołanie metody <xref:System.Xml.Linq.XElement.RemoveAll%2A> na element nadrzędny:  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a>Dlaczego nie LINQ automatycznie rozwiązać?  
 Jednym z podejść jest zawsze Przełącz wszystko do pamięci zamiast podczas oceny opóźnieniem. Jednakże może być bardzo kosztowna pod względem wydajności i użycia pamięci. W rzeczywistości gdyby LINQ i (LINQ do XML) o zastosowaniu takiego podejścia, spowoduje niepowodzenie w rzeczywistych sytuacji.  
  
 Innym rozwiązaniem możliwe będzie umieścić w jakieś składni transakcji do składnika LINQ i mieć kompilatora próba analiza kodu i określenia, czy żadnej określonej kolekcji jest wymagana można było zmaterializować. Jednak próby ustalenia całego kodu, który ma efekty uboczne jest niezwykle złożonych. Rozważmy następujący kod:  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Taki kod analizy należy przeanalizować metod TestSomeCondition i DoMyProjection i wszystkie metody, które wywołuje tych metod, aby określić, jeśli kod ma efekty uboczne. Jednak kod analizy nie można po prostu szukał kodu, który ma efekty uboczne. Będzie konieczne wybierz tylko kod, który ma efekty uboczne na elementy podrzędne `root` w takiej sytuacji.  
  
 LINQ do XML nie próbuje wykonać takie analizy.  
  
 Jest od użytkownika, aby uniknąć tych problemów.  
  
## <a name="guidance"></a>Wskazówki  
 Najpierw niemieszanie deklaratywne i bezwzględne kodu.  
  
 Nawet jeśli znasz dokładnie semantykę kolekcji i semantykę metod, które modyfikują drzewie XML podczas pisania niektórych inteligentne kod, który pozwala uniknąć problemów z tych kategorii kodu musi pozostać w przyszłości przez innych , a nie może być jako zwykły na problemy. Jeśli można mieszać deklaratywne i bezwzględne kodowania style, kod będzie bardziej łamliwa.  
  
 Podczas pisania kodu, który zostaje kolekcję tak, aby uniknąć tych problemów, należy pamiętać, go z komentarzami zgodnie z potrzebami w kodzie, dzięki czemu programistów konserwacji zostanie zrozumieć problem.  
  
 Po drugie Jeśli umożliwiają wydajności oraz inne kwestie, użyj tylko deklaratywne kodu. Nie należy modyfikować swoje istniejące drzewo XML. Wygenerować nowy.  
  
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
 [Zaawansowane LINQ do XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
