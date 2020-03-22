---
title: Wdrażanie IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266914"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Wskazówki: wdrażanie IEnumerable(Of T) w Visual Basic
Interfejs <xref:System.Collections.Generic.IEnumerable%601> jest implementowany przez klasy, które mogą zwracać sekwencję wartości po jednym elemencie naraz. Zaletą zwracania danych jeden element naraz jest, że nie trzeba załadować pełny zestaw danych do pamięci, aby pracować z nim. Wystarczy użyć wystarczającej ilości pamięci, aby załadować pojedynczy element z danych. Klasy, które `IEnumerable(T)` implementują interfejs `For Each` może służyć z pętli lub zapytań LINQ.  
  
 Rozważmy na przykład aplikację, która musi odczytać duży plik tekstowy i zwrócić każdy wiersz z pliku, który spełnia określone kryteria wyszukiwania. Aplikacja używa kwerendy LINQ do zwracania wierszy z pliku, które odpowiadają określonym kryteriom. Aby zbadać zawartość pliku przy użyciu kwerendy LINQ, aplikacja może załadować zawartość pliku do tablicy lub kolekcji. Jednak ładowanie całego pliku do tablicy lub kolekcji zużywa znacznie więcej pamięci niż jest to wymagane. Kwerenda LINQ zamiast tego kwerendy zawartości pliku przy użyciu klasy wyliczalne, zwracając tylko wartości, które odpowiadają kryteriom wyszukiwania. Kwerendy, które zwracają tylko kilka pasujących wartości zużywa znacznie mniej pamięci.  
  
 Można utworzyć klasę, która <xref:System.Collections.Generic.IEnumerable%601> implementuje interfejs, aby udostępnić dane źródłowe jako wyliczalne dane. Klasa, która implementuje `IEnumerable(T)` interfejs będzie wymagać <xref:System.Collections.Generic.IEnumerator%601> innej klasy, która implementuje interfejs do iteracji za pośrednictwem danych źródłowych. Te dwie klasy umożliwiają zwracanie elementów danych sekwencyjnie jako określonego typu.  
  
 W tym instruktażu utworzysz klasę, `IEnumerable(Of String)` która implementuje interfejs `IEnumerator(Of String)` i klasę, która implementuje interfejs do odczytu pliku tekstowego po jednym wierszu naraz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Tworzenie klasy wyliczalnej  
  
**Tworzenie projektu klasy wyliczalnej**

1. W języku Visual Basic w menu **Plik** wskaż polecenie **Nowy,** a następnie kliknij polecenie **Projekt**.

1. W oknie dialogowym **Nowy projekt** w okienku **Typy projektów** upewnij się, że system **Windows** jest zaznaczony. Wybierz **bibliotekę klas** w okienku **Szablony.** W polu **Nazwa** `StreamReaderEnumerable`wpisz , a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik Class1.vb i kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku `StreamReaderEnumerable.vb` na i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę `StreamReaderEnumerable`nazwy klasy na . Ta klasa zaimplementuje `IEnumerable(Of String)` interfejs.

1. Kliknij prawym przyciskiem myszy projekt StreamReaderEnumerable, wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Nowy element**. Wybierz szablon **Klasa.** W polu **Nazwa** `StreamReaderEnumerator.vb` wpisz i kliknij przycisk **OK**.

 Pierwsza klasa w tym projekcie jest klasą wyliczalną i zaimplementuje `IEnumerable(Of String)` interfejs. Ten ogólny interfejs <xref:System.Collections.IEnumerable> implementuje interfejs i gwarantuje, że konsumenci tej `String`klasy mogą uzyskiwać dostęp do wartości wpisanych jako .  
  
**Dodaj kod do zaimplementowania IEnumerable**

1. Otwórz plik StreamReaderEnumerable.vb.

2. W wierszu `Public Class StreamReaderEnumerable`po wpisz następujące polecenie i naciśnij klawisz ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic automatycznie wypełnia klasę członkami, które są wymagane `IEnumerable(Of String)` przez interfejs.
  
3. Ta klasa wyliczalna będzie odczytywać wiersze z pliku tekstowego po jednym wierszu naraz. Dodaj następujący kod do klasy, aby udostępnić konstruktora publicznego, który przyjmuje ścieżkę pliku jako parametr wejściowy.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Implementacja <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody `IEnumerable(Of String)` interfejsu zwróci nowe wystąpienie `StreamReaderEnumerator` klasy. Implementacja `GetEnumerator` metody `IEnumerable` interfejsu może być `Private`wykonana , ponieważ trzeba udostępnić `IEnumerable(Of String)` tylko elementy członkowskie interfejsu. Zastąp kod wygenerowany `GetEnumerator` przez program Visual Basic dla metod następującym kodem.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Dodaj kod do zaimplementowania IEnumerator**

1. Otwórz plik StreamReaderEnumerator.vb.

2. W wierszu `Public Class StreamReaderEnumerator`po wpisz następujące polecenie i naciśnij klawisz ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic automatycznie wypełnia klasę członkami, które są wymagane `IEnumerator(Of String)` przez interfejs.

3. Klasa wyliczania otwiera plik tekstowy i wykonuje we/wy pliku, aby odczytać wiersze z pliku. Dodaj następujący kod do klasy, aby udostępnić konstruktora publicznego, który przyjmuje ścieżkę pliku jako parametr wejściowy i otwórz plik tekstowy do odczytu.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current` Właściwości zarówno dla `IEnumerator(Of String)` i `IEnumerator` interfejsów zwracają bieżący element z `String`pliku tekstowego jako . Implementacja `Current` właściwości `IEnumerator` interfejsu mogą być `Private`wykonane, ponieważ trzeba udostępnić `IEnumerator(Of String)` tylko elementy członkowskie interfejsu. Zastąp kod wygenerowany `Current` przez program Visual Basic dla właściwości następującym kodem.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. Metoda `MoveNext` `IEnumerator` interfejsu przechodzi do następnego elementu w pliku tekstowym i aktualizuje `Current` wartość zwracaną przez właściwość. Jeśli nie ma więcej elementów `MoveNext` do `False`odczytu, metoda zwraca ; w `MoveNext` przeciwnym `True`razie metoda zwraca . Dodaj następujący kod do metody `MoveNext`:

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. Metoda `Reset` `IEnumerator` interfejsu kieruje iteratora do punktu początkowego pliku tekstowego i czyści bieżącą wartość elementu. Dodaj następujący kod do metody `Reset`:

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. Metoda `Dispose` `IEnumerator` interfejsu gwarantuje, że wszystkie zasoby niezarządzane są zwalniane przed zniszczeniem iteratora. Dojście do pliku, `StreamReader` który jest używany przez obiekt jest zasobem niezarządzanym i musi zostać zamknięty przed zniszczeniem wystąpienia iteratora. Zastąp kod wygenerowany `Dispose` przez program Visual Basic dla metody następującym kodem.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Korzystanie z przykładowego iteratora

 Można użyć klasy wyliczalnej w kodzie wraz ze strukturami `IEnumerable`kontroli, które `For Next` wymagają obiektu, który implementuje , takich jak pętla lub kwerenda LINQ. Poniższy przykład `StreamReaderEnumerable` pokazuje w kwerendzie LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
