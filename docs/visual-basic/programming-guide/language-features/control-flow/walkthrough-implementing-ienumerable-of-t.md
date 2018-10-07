---
title: Implementowanie interfejsu IEnumerable w języku Visual Basic
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: be2eefdc52d38df3071d457b7a71dbac6eaa2657
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837001"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Wskazówki: wdrażanie IEnumerable(Of T) w Visual Basic
<xref:System.Collections.Generic.IEnumerable%601> Interfejs jest implementowany przez klasy, które mogą zwracać sekwencję wartości jeden element w danym momencie. Zaletą zwracający dane, jeden element w danym momencie to, że nie masz załadować kompletny zestaw danych do pamięci z nią pracować. Musisz użyć wystarczającą ilość pamięci do załadowania pojedynczy element z danych. Klasy, które implementują `IEnumerable(T)` interfejsu może być używany z `For Each` pętli lub zapytań LINQ.  
  
 Na przykład rozważmy aplikację, która musi odczytywanie pliku tekstowego duże i zwracać każdy wiersz z pliku, który pasuje do kryteriów wyszukiwania określonego. Aplikacja używa zapytania LINQ do zwrócenia wierszy z pliku, który spełniających określone kryteria. Aby zbadać zawartość pliku za pomocą zapytań LINQ, aplikacja może ładować zawartość pliku do tablicy lub kolekcji. Jednak ładowanie całego pliku do tablicy lub kolekcji będzie zużywać znacznie więcej pamięci niż jest to wymagane. Zapytania LINQ zamiast tego można zbadać zawartość pliku przy użyciu klasy wyliczalny, zwracając tylko te wartości, które spełniają kryteria wyszukiwania. Zapytania, które zwracają tylko kilka pasujących wartości będą zużywać znacznie mniej pamięci.  
  
 Można utworzyć klasę, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu, aby uwidocznić źródło danych, jako wyliczalny dane. Swojej klasie, która implementuje `IEnumerable(T)` interfejsu będzie wymagać innej klasy, która implementuje <xref:System.Collections.Generic.IEnumerator%601> interfejsu do iteracji przez źródło danych. Te dwie klasy umożliwiają zwracają elementy danych po kolei jako określonego typu.  
  
 W tym instruktażu utworzysz klasę, która implementuje `IEnumerable(Of String)` interfejsu i klasę, która implementuje `IEnumerator(Of String)` interfejsu można odczytać tekstu jeden wiersz pliku naraz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Tworzenie klasy Wyliczalny  
  
**Utwórz projekt wyliczalny klas**

1.  W języku Visual Basic na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.

1.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **biblioteki klas** w **szablony** okienka. W **nazwa** wpisz `StreamReaderEnumerable`, a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.vb i kliknij przycisk **Zmień nazwę**. Zmień nazwę pliku do `StreamReaderEnumerable.vb` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `StreamReaderEnumerable`. Ta klasa wdroży `IEnumerable(Of String)` interfejsu.

1.  Kliknij prawym przyciskiem myszy projekt StreamReaderEnumerable, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element**. Wybierz **klasy** szablonu. W **nazwa** wpisz `StreamReaderEnumerator.vb` i kliknij przycisk **OK**.

 Pierwszą klasą w tym projekcie jest klasą wyliczalny i wdroży `IEnumerable(Of String)` interfejsu. Implementuje ten interfejs ogólny <xref:System.Collections.IEnumerable> interfejsu i gwarantuje, że osoby korzystające z tej klasy mają dostęp do wartości wpisanych jako `String`.  
  
**Dodaj kod do implementacji interfejsu IEnumerable**

1. Otwórz plik StreamReaderEnumerable.vb.

2. W wierszu po `Public Class StreamReaderEnumerable`, wpisz następujące polecenie i naciśnij klawisz ENTER.

   [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]

   Visual Basic automatycznie wypełnia klasę za pomocą elementów członkowskich, które są wymagane przez `IEnumerable(Of String)` interfejsu.
  
3. Ta klasa wyliczalny odczyta wiersze z jeden wiersz pliku tekstowego w danym momencie. Dodaj następujący kod do klasy w celu udostępnienia publicznego konstruktora, która przyjmuje ścieżkę do pliku jako parametr wejściowy.

   [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]

4. Implementacja <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody `IEnumerable(Of String)` interfejsu spowoduje zwrócenie nowego wystąpienia `StreamReaderEnumerator` klasy. Implementacja `GetEnumerator` metody `IEnumerable` może pracować z interfejsem `Private`, ponieważ musisz udostępnić tylko członkowie `IEnumerable(Of String)` interfejsu. Zastąp kod, który języka Visual Basic wygenerowany dla `GetEnumerator` metody z następującym kodem.

   [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]  
  
**Dodaj kod implementacji IEnumerator**

1. Otwórz plik StreamReaderEnumerator.vb.

2. W wierszu po `Public Class StreamReaderEnumerator`, wpisz następujące polecenie i naciśnij klawisz ENTER.

   [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]

   Visual Basic automatycznie wypełnia klasę za pomocą elementów członkowskich, które są wymagane przez `IEnumerator(Of String)` interfejsu.

3. Klasa modułu wyliczającego otwiera plik tekstowy i wykonuje plik We/Wy odczytu wiersze z pliku. Dodaj następujący kod do klasy w celu udostępnienia publicznego konstruktora, która przyjmuje ścieżkę do pliku jako parametr wejściowy, a następnie otwórz plik tekstowy do odczytu.

   [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]

4. `Current` Właściwości dla obu `IEnumerator(Of String)` i `IEnumerator` interfejsów zwracanie bieżącego elementu z pliku tekstowego jako `String`. Implementacja `Current` właściwość `IEnumerator` może pracować z interfejsem `Private`, ponieważ musisz udostępnić tylko członkowie `IEnumerator(Of String)` interfejsu. Zastąp kod, który języka Visual Basic wygenerowany dla `Current` właściwości z następującym kodem.

   [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]

5. `MoveNext` Metody `IEnumerator` interfejsu przechodzi do następnego elementu w pliku tekstowym i aktualizuje wartość, która jest zwracana przez `Current` właściwości. Jeśli istnieje więcej elementów do odczytu, `MoveNext` metoda zwraca `False`; w przeciwnym razie `MoveNext` metoda zwraca `True`. Dodaj następujący kod do `MoveNext` metody.

   [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]

6. `Reset` Metody `IEnumerator` interfejsu kieruje iteratora, aby wskazywała na początku pliku tekstowego i wyczyści bieżącą wartość elementu. Dodaj następujący kod do `Reset` metody.

   [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]

7. `Dispose` Metody `IEnumerator` interfejsu gwarantuje, że wszystkie zasoby niezarządzane są zwalniane, przed iteratora jest niszczony. Dojście do pliku, który jest używany przez `StreamReader` obiekt został niezarządzany zasób i muszą zostać zamknięte przed wystąpieniem iteratora. Zastąp kod, który języka Visual Basic wygenerowany dla `Dispose` metoda następującym kodem.

   [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)] 
  
## <a name="using-the-sample-iterator"></a>Używając iteratora próbki

 Można użyć wyliczalny klasy w kodzie oraz struktur sterujących, które wymagają obiekt, który implementuje `IEnumerable`, takich jak `For Next` pętli lub kwerendę LINQ. W poniższym przykładzie przedstawiono `StreamReaderEnumerable` w zapytaniu programu LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
