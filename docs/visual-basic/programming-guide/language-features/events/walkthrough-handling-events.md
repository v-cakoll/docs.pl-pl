---
title: Obsługa zdarzeń
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: cb42f2e41e366cf8765cb9395d1a5641434bab40
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345083"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Wskazówki: obsługa zdarzeń (Visual Basic)
Jest to drugi z dwóch tematów, które pokazują, jak korzystać z zdarzeń. Pierwszy temat, [Przewodnik: deklarowanie i](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)wywoływanie zdarzeń, pokazuje sposób deklarowania i zgłaszania zdarzeń. Ta sekcja używa formularza i klasy z tego przewodnika, aby pokazać, jak obsługiwać zdarzenia po ich przejściu.  
  
 Przykład klasy `Widget` używa tradycyjnych instrukcji obsługi zdarzeń. Visual Basic zapewnia inne techniki pracy ze zdarzeniami. W ramach ćwiczenia można zmodyfikować ten przykład, aby użyć instrukcji `AddHandler` i `Handles`.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Aby obsłużyć zdarzenie PercentDone klasy widget  
  
1. Umieść następujący kod w `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     Słowo kluczowe `WithEvents` określa, że zmienna `mWidget` jest używana do obsługi zdarzeń obiektu. Należy określić rodzaj obiektu, dostarczając nazwę klasy, z której zostanie utworzony obiekt.  
  
     Zmienna `mWidget` jest zadeklarowana w `Form1`, ponieważ zmienne `WithEvents` muszą być na poziomie klasy. Ta wartość jest prawdziwa niezależnie od typu klasy, w której je umieszczasz.  
  
     Zmienna `mblnCancel` jest używana do anulowania metody `LongTask`.  
  
## <a name="writing-code-to-handle-an-event"></a>Pisanie kodu do obsługi zdarzenia  
 Gdy tylko zadeklarujesz zmienną przy użyciu `WithEvents`, nazwa zmiennej jest wyświetlana na liście rozwijanej w **edytorze kodu**klasy. Po wybraniu `mWidget`zdarzenia klasy `Widget` są wyświetlane na liście rozwijanej po prawej stronie. Wybranie zdarzenia powoduje wyświetlenie odpowiedniej procedury zdarzenia z prefiksem `mWidget` i podkreśleniem. Wszystkie procedury zdarzeń skojarzone z zmienną `WithEvents` są przydawane nazwie zmiennej jako prefiks.  
  
#### <a name="to-handle-an-event"></a>Aby obsłużyć zdarzenie  
  
1. Wybierz pozycję `mWidget` z listy rozwijanej po lewej stronie w **edytorze kodu**.  
  
2. Wybierz zdarzenie `PercentDone` z listy rozwijanej po prawej stronie. **Edytor kodu** otwiera procedurę zdarzenia `mWidget_PercentDone`.  
  
    > [!NOTE]
    > **Edytor kodu** jest przydatny, ale nie jest wymagany, do wstawiania nowych programów obsługi zdarzeń. W tym instruktażu bardziej bezpośrednim jest tylko kopiowanie programów obsługi zdarzeń bezpośrednio do kodu.  
  
3. Dodaj następujący kod do programu obsługi zdarzeń `mWidget_PercentDone`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Za każdym razem, gdy zostanie zgłoszone zdarzenie `PercentDone`, procedura zdarzenia wyświetla procent wykonania w kontrolce `Label`. Metoda `DoEvents` pozwala na odświeżenie etykiety, a także daje użytkownikowi możliwość kliknięcia przycisku **Anuluj** .  
  
4. Dodaj następujący kod dla programu obsługi zdarzeń `Button2_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Jeśli użytkownik kliknie przycisk **Anuluj** podczas `LongTask` jest uruchomiony, zdarzenie `Button2_Click` zostanie wykonane natychmiast, gdy instrukcja `DoEvents` umożliwia przetwarzanie zdarzeń. Zmienna na poziomie klasy `mblnCancel` jest ustawiona na `True`, a zdarzenie `mWidget_PercentDone` przetestuje je i ustawia argument `ByRef Cancel` na `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Łączenie zmiennej WithEvents z obiektem  
 `Form1` jest teraz skonfigurowany do obsługi zdarzeń `Widget` obiektu. To wszystko, co pozostało, aby znaleźć `Widget` w miejscu.  
  
 Kiedy deklarujesz zmienną `WithEvents` w czasie projektowania, żaden obiekt nie jest skojarzony z nim. Zmienna `WithEvents` jest taka sama jak jakakolwiek inna zmienna obiektu. Należy utworzyć obiekt i przypisać do niego odwołanie za pomocą zmiennej `WithEvents`.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Aby utworzyć obiekt i przypisać do niego odwołanie  
  
1. Wybierz pozycję **(zdarzenia Form1)** z listy rozwijanej po lewej stronie w **edytorze kodu**.  
  
2. Wybierz zdarzenie `Load` z listy rozwijanej po prawej stronie. **Edytor kodu** otwiera procedurę zdarzenia `Form1_Load`.  
  
3. Dodaj następujący kod dla procedury zdarzenia `Form1_Load`, aby utworzyć `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Gdy ten kod jest wykonywany, Visual Basic tworzy obiekt `Widget` i łączy jego zdarzenia z procedurami zdarzeń skojarzonymi z `mWidget`. Od tego momentu, gdy `Widget` zgłasza zdarzenie `PercentDone`, zostanie wykonana procedura zdarzenia `mWidget_PercentDone`.  
  
#### <a name="to-call-the-longtask-method"></a>Aby wywołać metodę LongTask  
  
- Dodaj następujący kod do programu obsługi zdarzeń `Button1_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Przed wywołaniem metody `LongTask`, etykieta, która wyświetla wartość procentową, musi zostać zainicjowana, a flaga `Boolean` na poziomie klasy dla anulowania metody musi być ustawiona na `False`.  
  
 `LongTask` jest wywoływana z czasem trwania zadania wynoszącym 12,2 sekund. Zdarzenie `PercentDone` jest zgłaszane raz w każdej jednej trzeciej części sekundy. Za każdym razem, gdy zdarzenie jest zgłaszane, wykonywana jest `mWidget_PercentDone` procedura zdarzenia.  
  
 Gdy `LongTask` jest wykonywane, `mblnCancel` jest testowana, aby sprawdzić, czy `LongTask` zakończyła się normalnie, lub jeśli została zatrzymana, ponieważ `mblnCancel` została ustawiona na `True`. Procent ukończenia jest aktualizowany tylko w poprzednim przypadku.  
  
#### <a name="to-run-the-program"></a>Aby uruchomić program  
  
1. Naciśnij klawisz F5, aby umieścić projekt w trybie uruchamiania.  
  
2. Kliknij przycisk **Rozpocznij zadanie** . Za każdym razem, gdy zdarzenie `PercentDone` zostanie wywołane, etykieta zostaje zaktualizowana o wartość procentową wykonanego zadania.  
  
3. Kliknij przycisk **Anuluj** , aby zatrzymać zadanie. Zauważ, że wygląd przycisku **Anuluj** nie zmienia się natychmiast po jego kliknięciu. Nie można wykonać zdarzenia `Click`, dopóki instrukcja `My.Application.DoEvents` nie zezwala na przetwarzanie zdarzeń.  
  
    > [!NOTE]
    > Metoda `My.Application.DoEvents` nie przetwarza zdarzeń w taki sam sposób jak w przypadku formularza. Na przykład w tym instruktażu należy kliknąć przycisk **Anuluj** dwa razy. Aby umożliwić bezpośrednie obsługiwanie zdarzeń przez formularz, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../../standard/threading/index.md).
  
 Może się pojawić monit o uruchomienie programu z użyciem klawisza F11 i przekroczenie kodu w wierszu. Można jasno zobaczyć, jak wykonywanie wprowadza `LongTask`, a następnie krótko wprowadzić ponownie `Form1` przy każdym wyjściu zdarzenia `PercentDone`.  
  
 Co się stanie, jeśli podczas wykonywania w kodzie `Form1`następuje ponowne wywołanie metody `LongTask`? W najgorszym przypadku może wystąpić przepełnienie stosu, jeśli `LongTask` były wywoływane za każdym razem, gdy zdarzenie zostało zgłoszone.  
  
 Można spowodować, że zmienna `mWidget` obsługiwać zdarzenia dla innego obiektu `Widget`, przypisując odwołanie do nowej `Widget` do `mWidget`. W rzeczywistości możesz wprowadzić kod w `Button1_Click` zrobić to za każdym razem, gdy klikniesz przycisk.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Aby obsłużyć zdarzenia dla innego widżetu  
  
- Dodaj następujący wiersz kodu do procedury `Button1_Click`, bezpośrednio poprzedzając wiersz, który odczytuje `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Powyższy kod tworzy nowy `Widget` przy każdym kliknięciu przycisku. Gdy tylko Metoda `LongTask` zostanie zakończona, odwołanie do `Widget` zostanie wydane, a `Widget` zostanie zniszczona.  
  
 Zmienna `WithEvents` może zawierać tylko jedno odwołanie do obiektu naraz, więc Jeśli przypiszesz inny obiekt `Widget` do `mWidget`, poprzednie zdarzenia `Widget`go obiektu nie będą już obsługiwane. Jeśli `mWidget` jest jedyną zmienną obiektu zawierającą odwołanie do starego `Widget`, obiekt zostanie zniszczony. Jeśli chcesz obsługiwać zdarzenia z kilku `Widget` obiektów, użyj instrukcji `AddHandler`, aby przetwarzać zdarzenia z poszczególnych obiektów osobno.  
  
> [!NOTE]
> W razie potrzeby można zadeklarować dowolną liczbę zmiennych `WithEvents`, ale tablice `WithEvents` zmiennych nie są obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
