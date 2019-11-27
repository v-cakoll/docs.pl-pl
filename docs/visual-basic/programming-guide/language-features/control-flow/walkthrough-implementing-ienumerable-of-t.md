---
title: Implementowanie interfejsu IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f40fcf7e0724addc478b261dcd36d09e1d8a751a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333686"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Wskazówki: wdrażanie IEnumerable(Of T) w Visual Basic
Interfejs <xref:System.Collections.Generic.IEnumerable%601> jest implementowany przez klasy, które mogą zwracać sekwencję wartości po jednym elemencie naraz. Zaletą zwracania danych z jednego elementu jednocześnie jest to, że nie trzeba ładować kompletnego zestawu danych do pamięci, aby z niego korzystać. Wystarczy użyć wystarczającej ilości pamięci do załadowania pojedynczego elementu z danych. Klasy implementujące interfejs `IEnumerable(T)` mogą być używane z pętlą `For Each` lub kwerend LINQ.  
  
 Rozważmy na przykład aplikację, która musi odczytać duży plik tekstowy i zwrócić każdy wiersz z pliku zgodnego z określonymi kryteriami wyszukiwania. Aplikacja używa zapytania LINQ do zwracania wierszy z pliku, które pasują do określonych kryteriów. Aby zbadać zawartość pliku przy użyciu zapytania LINQ, aplikacja może załadować zawartość pliku do tablicy lub kolekcji. Jednak załadowanie całego pliku do tablicy lub kolekcji spowodowałoby dużo więcej pamięci niż jest to wymagane. Zapytanie LINQ mogło zamiast tego zbadać zawartość pliku przy użyciu klasy wyliczalnej, zwracając tylko wartości pasujące do kryteriów wyszukiwania. Zapytania, które zwracają tylko kilka pasujących wartości, zużywają znacznie mniej pamięci.  
  
 Można utworzyć klasę, która implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, aby uwidocznić dane źródłowe jako wyliczalne dane. Klasa implementująca interfejs `IEnumerable(T)` będzie wymagała innej klasy implementującej interfejs <xref:System.Collections.Generic.IEnumerator%601> do iteracji przez dane źródłowe. Te dwie klasy umożliwiają zwracanie elementów danych sekwencyjnie jako określonego typu.  
  
 W tym instruktażu utworzysz klasę, która implementuje interfejs `IEnumerable(Of String)` i klasę implementującą interfejs `IEnumerator(Of String)` do odczytywania pliku tekstowego po jednym wierszu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Tworzenie klasy wyliczalnej  
  
**Utwórz wyliczalny projekt klasy**

1. W Visual Basic w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.

1. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** . W okienku **Szablony** wybierz pozycję **Biblioteka klas** . W polu **Nazwa** wpisz `StreamReaderEnumerable`, a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Class1. vb i kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku na `StreamReaderEnumerable.vb` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy na `StreamReaderEnumerable`. Ta klasa spowoduje zaimplementowanie interfejsu `IEnumerable(Of String)`.

1. Kliknij prawym przyciskiem myszy projekt StreamReaderEnumerable, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**. Wybierz szablon **klasy** . W polu **Nazwa** wpisz `StreamReaderEnumerator.vb` i kliknij przycisk **OK**.

 Pierwsza klasa w tym projekcie jest klasą wyliczalną i implementuje interfejs `IEnumerable(Of String)`. Ten interfejs generyczny implementuje interfejs <xref:System.Collections.IEnumerable> i gwarantuje, że konsumenci tej klasy mogą uzyskać dostęp do wartości wpisanych jako `String`.  
  
**Dodaj kod w celu zaimplementowania interfejsu IEnumerable**

1. Otwórz plik StreamReaderEnumerable. vb.

2. W wierszu po `Public Class StreamReaderEnumerable`wpisz następujące polecenie i naciśnij klawisz ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic automatycznie wypełnia klasę elementami członkowskimi, które są wymagane przez interfejs `IEnumerable(Of String)`.
  
3. Ta klasa wyliczalna odczytaje wiersze z pliku tekstowego po jednym wierszu. Dodaj następujący kod do klasy, aby uwidocznić konstruktora publicznego, który Pobiera ścieżkę pliku jako parametr wejściowy.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Implementacja metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> interfejsu `IEnumerable(Of String)` zwróci nowe wystąpienie klasy `StreamReaderEnumerator`. Implementację metody `GetEnumerator` interfejsu `IEnumerable` można wykonać `Private`, ponieważ należy uwidocznić tylko elementy członkowskie interfejsu `IEnumerable(Of String)`. Zastąp kod, który Visual Basic wygenerowany dla metod `GetEnumerator`, przy użyciu następującego kodu.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Dodawanie kodu w celu zaimplementowania IEnumerator**

1. Otwórz plik StreamReaderEnumerator. vb.

2. W wierszu po `Public Class StreamReaderEnumerator`wpisz następujące polecenie i naciśnij klawisz ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic automatycznie wypełnia klasę elementami członkowskimi, które są wymagane przez interfejs `IEnumerator(Of String)`.

3. Klasa Enumerator otwiera plik tekstowy i wykonuje operacje we/wy pliku w celu odczytania wierszy z pliku. Dodaj następujący kod do klasy, aby uwidocznić konstruktora publicznego, który Pobiera ścieżkę pliku jako parametr wejściowy, i Otwórz plik tekstowy do odczytu.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Właściwości `Current` dla interfejsów `IEnumerator(Of String)` i `IEnumerator` zwracają bieżący element z pliku tekstowego jako `String`. Implementacja właściwości `Current` interfejsu `IEnumerator` można wykonać `Private`, ponieważ należy uwidocznić tylko elementy członkowskie interfejsu `IEnumerator(Of String)`. Zastąp kod, który Visual Basic wygenerowany dla właściwości `Current` przy użyciu następującego kodu.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. Metoda `MoveNext` interfejsu `IEnumerator` przechodzi do następnego elementu w pliku tekstowym i aktualizuje wartość zwracaną przez właściwość `Current`. Jeśli nie ma więcej elementów do odczytania, Metoda `MoveNext` zwraca `False`; w przeciwnym razie metoda `MoveNext` zwraca `True`. Dodaj następujący kod do metody `MoveNext`.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. Metoda `Reset` interfejsu `IEnumerator` kieruje iterator, aby wskazywał na początek pliku tekstowego i czyści bieżącą wartość elementu. Dodaj następujący kod do metody `Reset`.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. Metoda `Dispose` interfejsu `IEnumerator` gwarantuje, że wszystkie niezarządzane zasoby są wydawane przed zniszczeniem iteratora. Dojście do pliku, które jest używane przez obiekt `StreamReader`, jest zasobem niezarządzanym i musi zostać zamknięte przed zniszczeniem wystąpienia iteratora. Zastąp kod, który Visual Basic wygenerowany dla metody `Dispose`, przy użyciu następującego kodu.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>Użycie iteratora przykładowego

 Można użyć klasy wyliczalnej w kodzie wraz ze strukturami formantów wymagającymi obiektu, który implementuje `IEnumerable`, takich jak pętla `For Next` lub zapytanie LINQ. Poniższy przykład pokazuje `StreamReaderEnumerable` w kwerendzie LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
