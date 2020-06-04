---
title: Implementowanie interfejsu IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 582957c91eac63cf7f72dd2f6c0cf40e627be686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402034"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Wskazówki: wdrażanie IEnumerable(Of T) w Visual Basic
<xref:System.Collections.Generic.IEnumerable%601>Interfejs jest implementowany przez klasy, które mogą zwracać sekwencję wartości po jednym elemencie naraz. Zaletą zwracania danych z jednego elementu jednocześnie jest to, że nie trzeba ładować kompletnego zestawu danych do pamięci, aby z niego korzystać. Wystarczy użyć wystarczającej ilości pamięci do załadowania pojedynczego elementu z danych. Klasy implementujące `IEnumerable(T)` interfejs mogą być używane z `For Each` pętlami lub kwerendami LINQ.  
  
 Rozważmy na przykład aplikację, która musi odczytać duży plik tekstowy i zwrócić każdy wiersz z pliku zgodnego z określonymi kryteriami wyszukiwania. Aplikacja używa zapytania LINQ do zwracania wierszy z pliku, które pasują do określonych kryteriów. Aby zbadać zawartość pliku przy użyciu zapytania LINQ, aplikacja może załadować zawartość pliku do tablicy lub kolekcji. Jednak załadowanie całego pliku do tablicy lub kolekcji spowodowałoby dużo więcej pamięci niż jest to wymagane. Zapytanie LINQ mogło zamiast tego zbadać zawartość pliku przy użyciu klasy wyliczalnej, zwracając tylko wartości pasujące do kryteriów wyszukiwania. Zapytania, które zwracają tylko kilka pasujących wartości, zużywają znacznie mniej pamięci.  
  
 Można utworzyć klasę, która implementuje interfejs, <xref:System.Collections.Generic.IEnumerable%601> Aby udostępnić dane źródłowe jako wyliczalne dane. Klasa implementująca `IEnumerable(T)` interfejs będzie wymagała innej klasy implementującej <xref:System.Collections.Generic.IEnumerator%601> interfejs do iteracji przez dane źródłowe. Te dwie klasy umożliwiają zwracanie elementów danych sekwencyjnie jako określonego typu.  
  
 W tym instruktażu utworzysz klasę, która implementuje `IEnumerable(Of String)` interfejs i klasę, która implementuje `IEnumerator(Of String)` interfejs do odczytywania pliku tekstowego po jednym wierszu naraz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Tworzenie klasy wyliczalnej  
  
**Utwórz wyliczalny projekt klasy**

1. W Visual Basic w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.

1. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** . W okienku **Szablony** wybierz pozycję **Biblioteka klas** . W polu **Nazwa** wpisz `StreamReaderEnumerable` , a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Class1. vb i kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku na `StreamReaderEnumerable.vb` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy na `StreamReaderEnumerable` . Ta klasa będzie implementować `IEnumerable(Of String)` interfejs.

1. Kliknij prawym przyciskiem myszy projekt StreamReaderEnumerable, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**. Wybierz szablon **klasy** . W polu **Nazwa** wpisz `StreamReaderEnumerator.vb` i kliknij przycisk **OK**.

 Pierwsza klasa w tym projekcie jest klasą wyliczalną i implementuje `IEnumerable(Of String)` interfejs. Ten interfejs generyczny implementuje <xref:System.Collections.IEnumerable> interfejs i gwarantuje, że konsumenci tej klasy mogą uzyskać dostęp do wartości wpisanych jako `String` .  
  
**Dodaj kod w celu zaimplementowania interfejsu IEnumerable**

1. Otwórz plik StreamReaderEnumerable. vb.

2. W wierszu po `Public Class StreamReaderEnumerable` wpisz następujące polecenie i naciśnij klawisz ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic automatycznie wypełnia klasę elementami członkowskimi, które są wymagane przez `IEnumerable(Of String)` interfejs.
  
3. Ta klasa wyliczalna odczytaje wiersze z pliku tekstowego po jednym wierszu. Dodaj następujący kod do klasy, aby uwidocznić konstruktora publicznego, który Pobiera ścieżkę pliku jako parametr wejściowy.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Twoja implementacja <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody `IEnumerable(Of String)` interfejsu zwróci nowe wystąpienie `StreamReaderEnumerator` klasy. Można wprowadzić implementację `GetEnumerator` metody `IEnumerable` interfejsu `Private` , ponieważ trzeba uwidocznić tylko elementy członkowskie `IEnumerable(Of String)` interfejsu. Zastąp kod, który Visual Basic wygenerowany dla `GetEnumerator` metod przy użyciu następującego kodu.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Dodawanie kodu w celu zaimplementowania IEnumerator**

1. Otwórz plik StreamReaderEnumerator. vb.

2. W wierszu po `Public Class StreamReaderEnumerator` wpisz następujące polecenie i naciśnij klawisz ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic automatycznie wypełnia klasę elementami członkowskimi, które są wymagane przez `IEnumerator(Of String)` interfejs.

3. Klasa Enumerator otwiera plik tekstowy i wykonuje operacje we/wy pliku w celu odczytania wierszy z pliku. Dodaj następujący kod do klasy, aby uwidocznić konstruktora publicznego, który Pobiera ścieżkę pliku jako parametr wejściowy, i Otwórz plik tekstowy do odczytu.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`Właściwości obu `IEnumerator(Of String)` `IEnumerator` interfejsów i zwracają bieżący element z pliku tekstowego jako `String` . Można wprowadzić implementację `Current` właściwości `IEnumerator` interfejsu `Private` , ponieważ trzeba uwidocznić tylko elementy członkowskie `IEnumerator(Of String)` interfejsu. Zastąp kod, który Visual Basic wygenerowany dla `Current` właściwości przy użyciu następującego kodu.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext`Metoda `IEnumerator` interfejsu przechodzi do następnego elementu w pliku tekstowym i aktualizuje wartość zwracaną przez `Current` Właściwość. Jeśli nie ma więcej elementów do odczytania, `MoveNext` Metoda zwraca `False` ; w przeciwnym razie `MoveNext` Metoda zwraca `True` . Dodaj następujący kod do metody `MoveNext`:

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`Metoda `IEnumerator` interfejsu kieruje iterator, aby wskazać początek pliku tekstowego i czyści bieżącą wartość elementu. Dodaj następujący kod do metody `Reset`:

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`Metoda `IEnumerator` interfejsu gwarantuje, że wszystkie niezarządzane zasoby są uwalniane przed zniszczeniem iteratora. Dojście do pliku używane przez `StreamReader` obiekt jest zasobem niezarządzanym i musi zostać zamknięte przed zniszczeniem wystąpienia iteratora. Zastąp kod, który Visual Basic wygenerowany dla `Dispose` metody przy użyciu następującego kodu.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Użycie iteratora przykładowego

 Można użyć klasy wyliczalnej w kodzie wraz ze strukturami formantów, które wymagają obiektu, który implementuje `IEnumerable` , takich jak `For Next` Pętla lub zapytanie LINQ. Poniższy przykład przedstawia `StreamReaderEnumerable` w kwerendzie LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md)
- [Przepływ sterowania](index.md)
- [Struktury pętli](loop-structures.md)
- [For Each...Next, instrukcja](../../../language-reference/statements/for-each-next-statement.md)
