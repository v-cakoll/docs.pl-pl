---
title: Implementacja interfejsu IEnumerable w języku Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4645153f9c830bc96b7ec55367f46f09098eb78d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Wskazówki: wdrażanie IEnumerable(Of T) w Visual Basic
<xref:System.Collections.Generic.IEnumerable%601> Interfejs jest implementowany przez klasy, które może zwracać sekwencję wartości jeden element w czasie. Zaletą przekazujących dane, które jest jeden element w czasie, że nie masz załadować pełny zestaw danych w pamięci, aby pracować z nim. Aby załadować jednego elementu danych z wystarczającą ilość pamięci tylko ma. Klasy, które implementują `IEnumerable(T)` interfejsu może być używany z `For Each` pętli lub zapytań LINQ.  
  
 Rozważmy na przykład aplikacja musi odczytywanie pliku tekstowego dużych i zwracać każdy wiersz z pliku, które spełniają kryteria wyszukiwania określonego. Aplikacja używa zapytania LINQ do zwrócenia wierszy z pliku, spełniających określone kryteria. Aby sprawdzić zawartość pliku za pomocą zapytania LINQ, aplikacji można załadować zawartość pliku do tablicy lub kolekcji. Jednakże ładowanie całego pliku do tablicą lub kolekcją będzie używać znacznie więcej pamięci niż jest to wymagane. Zapytania LINQ zamiast tego można zbadać zawartość pliku za pomocą klasy wyliczalny, zwracać tylko wartości spełniających kryteria wyszukiwania. Zapytań zwracających tylko kilka zgodne wartości będzie używać znacznie mniej pamięci.  
  
 Można utworzyć klasy, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs do udostępnienia danych źródłowych, jako wyliczalny danych. Klasy implementującej `IEnumerable(T)` wymaga innej klasy, która implementuje interfejs <xref:System.Collections.Generic.IEnumerator%601> interfejs do iteracji źródło danych. Te dwie klasy umożliwiają sekwencyjne jako określonego typu zwraca elementy danych.  
  
 W tym przewodniku utworzy klasę, która implementuje `IEnumerable(Of String)` interfejsu i klasy, która implementuje `IEnumerator(Of String)` interfejsu można odczytać pliku tekstowego jeden wiersz jednocześnie.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Tworzenie klasy Wyliczalny  
  
|Aby utworzyć projekt wyliczalny — klasa|  
|---|  
|1.  W języku Visual Basic na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.<br />2.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **biblioteki klas** w **szablony** okienka. W **nazwa** wpisz `StreamReaderEnumerable`, a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.<br />3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.vb i kliknij przycisk **zmienić**. Zmień nazwę pliku do `StreamReaderEnumerable.vb` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `StreamReaderEnumerable`. Ta klasa będzie implementowany `IEnumerable(Of String)` interfejsu.<br />4.  Kliknij prawym przyciskiem myszy projekt StreamReaderEnumerable, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **nowy element**. Wybierz **klasy** szablonu. W **nazwa** wpisz `StreamReaderEnumerator.vb` i kliknij przycisk **OK**.|  
  
 To pierwsza klasa w tym projekcie jest klasa wyliczalny i wdroży `IEnumerable(Of String)` interfejsu. Implementuje ten interfejs ogólny <xref:System.Collections.IEnumerable> interfejsu i gwarantuje, że konsumenci tej klasy mogą uzyskiwać dostęp do wartości wpisanych jako `String`.  
  
|Aby dodać kod do implementacji interfejsu IEnumerable|  
|---|  
|1.  Otwórz plik StreamReaderEnumerable.vb.<br />2.  W wierszu po `Public Class StreamReaderEnumerable`, wpisz następujące polecenie i naciśnij klawisz ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     Visual Basic automatycznie wypełni klasy z elementów członkowskich, które są wymagane przez `IEnumerable(Of String)` interfejsu.<br />3.  Ta klasa wyliczalny odczyta wierszy z pliku tekstowego jeden wiersz jednocześnie. Dodaj następujący kod do klasy do udostępnienia konstruktora publicznego, która przyjmuje ścieżkę pliku, jako parametr wejściowy.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Implementacji <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody `IEnumerable(Of String)` interfejsu zwraca nowe wystąpienie klasy `StreamReaderEnumerator` klasy. Implementacja `GetEnumerator` metody `IEnumerable` interfejsu może być utworzona `Private`, ponieważ ma zostać udostępniona tylko członkowie `IEnumerable(Of String)` interfejsu. Zastąp kod generowany dla języka Visual Basic `GetEnumerator` metody z następującym kodem.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|Aby dodać kod do implementacji IEnumerator|  
|---|  
|1.  Otwórz plik StreamReaderEnumerator.vb.<br />2.  W wierszu po `Public Class StreamReaderEnumerator`, wpisz następujące polecenie i naciśnij klawisz ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     Visual Basic automatycznie wypełni klasy z elementów członkowskich, które są wymagane przez `IEnumerator(Of String)` interfejsu.<br />3.  Klasa modułu wyliczającego otwiera plik tekstowy i wykonuje plik we/wy odczytać wierszy z pliku. Dodaj następujący kod do klasy można ujawniać publicznego konstruktora przyjmującego ścieżki pliku jako parametr wejściowy i Otwórz plik tekstowy do odczytu.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  `Current` Właściwości dla obu `IEnumerator(Of String)` i `IEnumerator` interfejsy zwracanie bieżącego elementu z pliku tekstowego jako `String`. Implementacja `Current` właściwość `IEnumerator` interfejsu może być utworzona `Private`, ponieważ ma zostać udostępniona tylko członkowie `IEnumerator(Of String)` interfejsu. Zastąp kod generowany dla języka Visual Basic `Current` właściwości z następującym kodem.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  `MoveNext` Metody `IEnumerator` interfejsu przechodzi do następnego elementu w pliku tekstowym i aktualizuje wartość, która jest zwracana w wyniku `Current` właściwości. Jeśli istnieje więcej elementów do odczytu, `MoveNext` metoda zwraca `False`; w przeciwnym razie `MoveNext` metoda zwraca `True`. Dodaj następujący kod do `MoveNext` metody.<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  `Reset` Metody `IEnumerator` interfejsu kieruje iteratora, aby wskazywały na początku pliku tekstowego i czyści wartość bieżącego elementu. Dodaj następujący kod do `Reset` metody.<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  `Dispose` Metody `IEnumerator` interfejsu gwarantuje, że wszystkie zasoby niezarządzane są wydawane przed iteratora. Dojście do pliku, który jest używany przez `StreamReader` obiekt jest niezarządzanym zasobem i muszą zostać zamknięte przed wystąpieniem iteratora. Zastąp kod generowany dla języka Visual Basic `Dispose` metodę z następującym kodem.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>Przy użyciu przykładowych iteratora  
 Można użyć klasy wyliczalny w kodzie wraz z struktury sterujące, które wymagają obiekt, który implementuje `IEnumerable`, takich jak `For Next` pętli lub zapytań LINQ. W poniższym przykładzie przedstawiono `StreamReaderEnumerable` w zapytaniu składnika LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
