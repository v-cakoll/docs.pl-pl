---
title: Obsługa zdarzeń (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 12267e0a70419298bc581421c4f3a220088d205f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956311"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Przewodnik: Obsługa zdarzeń (Visual Basic)
Jest to drugi z dwóch tematów, które pokazują, jak korzystać z zdarzeń. Pierwszy temat, [Przewodnik: Deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), pokazuje sposób deklarowania i zgłaszania zdarzeń. Ta sekcja używa formularza i klasy z tego przewodnika, aby pokazać, jak obsługiwać zdarzenia po ich przejściu.  
  
 W `Widget` przykładzie klasy są stosowane tradycyjne instrukcje obsługi zdarzeń. Visual Basic zapewnia inne techniki pracy ze zdarzeniami. W ramach ćwiczenia można zmodyfikować ten przykład, aby użyć `AddHandler` instrukcji i. `Handles`  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Aby obsłużyć zdarzenie PercentDone klasy widget  
  
1. Umieść następujący kod w `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     Słowo kluczowe Określa, że zmienna `mWidget` jest używana do obsługi zdarzeń obiektu. `WithEvents` Należy określić rodzaj obiektu, dostarczając nazwę klasy, z której zostanie utworzony obiekt.  
  
     Zmienna `mWidget` jest zadeklarowana w `Form1` , `WithEvents` ponieważ zmienne muszą być na poziomie klasy. Ta wartość jest prawdziwa niezależnie od typu klasy, w której je umieszczasz.  
  
     Zmienna `mblnCancel` służy do `LongTask` anulowania metody.  
  
## <a name="writing-code-to-handle-an-event"></a>Pisanie kodu do obsługi zdarzenia  
 Po zadeklarowaniu zmiennej przy użyciu `WithEvents`, nazwa zmiennej jest wyświetlana na liście rozwijanej w **edytorze kodu**klasy. Po wybraniu `mWidget` `Widget` zdarzenia klasy są wyświetlane na liście rozwijanej po prawej stronie. Wybranie zdarzenia powoduje wyświetlenie odpowiedniej procedury zdarzenia z prefiksem `mWidget` i podkreśleniem. Wszystkie procedury zdarzeń skojarzone ze `WithEvents` zmienną otrzymują nazwę zmiennej jako prefiks.  
  
#### <a name="to-handle-an-event"></a>Aby obsłużyć zdarzenie  
  
1. Wybierz `mWidget` z listy rozwijanej po lewej stronie w **edytorze kodu**.  
  
2. `PercentDone` Wybierz zdarzenie z listy rozwijanej po prawej stronie. **Edytor kodu** otwiera `mWidget_PercentDone` procedurę zdarzenia.  
  
    > [!NOTE]
    > **Edytor kodu** jest przydatny, ale nie jest wymagany, do wstawiania nowych programów obsługi zdarzeń. W tym instruktażu bardziej bezpośrednim jest tylko kopiowanie programów obsługi zdarzeń bezpośrednio do kodu.  
  
3. Dodaj następujący kod do `mWidget_PercentDone` programu obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Za każdym razem, gdy `Label` zdarzeniejestzgłaszane,procedurazdarzeniawyświetlaprocentwykonaniawkontrolce.`PercentDone` Metoda pozwala na odświeżenie etykiety, a także pozwala użytkownikowi kliknąć przycisk **Anuluj.** `DoEvents`  
  
4. Dodaj następujący kod dla `Button2_Click` programu obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Jeśli użytkownik kliknie przycisk **Anuluj** w trakcie `LongTask` działania, `Button2_Click` zdarzenie jest wykonywane zaraz po tym `DoEvents` , jak instrukcja zezwala na przetwarzanie zdarzeń. Zmienna `mblnCancel` na poziomie klasy jest ustawiana na `True`, a `mWidget_PercentDone` następnie zdarzenie sprawdza i ustawia `ByRef Cancel` argument na `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Łączenie zmiennej WithEvents z obiektem  
 `Form1`jest teraz skonfigurowany do obsługi `Widget` zdarzeń obiektu. To wszystko, co pozostało `Widget` , aby znaleźć gdzieś.  
  
 Po zadeklarowaniu zmiennej `WithEvents` w czasie projektowania, żaden obiekt nie jest skojarzony z nim. `WithEvents` Zmienna jest tak samo jak jakakolwiek inna zmienna obiektu. Należy utworzyć obiekt i przypisać do niego odwołanie przy użyciu `WithEvents` zmiennej.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Aby utworzyć obiekt i przypisać do niego odwołanie  
  
1. Wybierz pozycję **(zdarzenia Form1)** z listy rozwijanej po lewej stronie w **edytorze kodu**.  
  
2. `Load` Wybierz zdarzenie z listy rozwijanej po prawej stronie. **Edytor kodu** otwiera `Form1_Load` procedurę zdarzenia.  
  
3. Dodaj następujący kod dla `Form1_Load` procedury zdarzenia, aby `Widget`utworzyć:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Gdy ten kod jest wykonywany, Visual Basic tworzy `Widget` obiekt i łączy jego zdarzenia z procedurami zdarzeń skojarzonymi `mWidget`z. Od tego momentu, gdy `Widget` `PercentDone` wywołuje zdarzenie, `mWidget_PercentDone` procedura zdarzenia jest wykonywana.  
  
#### <a name="to-call-the-longtask-method"></a>Aby wywołać metodę LongTask  
  
- Dodaj następujący kod do `Button1_Click` programu obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Przed wywołaniem `Boolean`metody, etykieta, w której jest wyświetlany procent wykonania, musi zostać zainicjowana, a flaga poziomu klasy dla anulowania metody musi być ustawiona na `False`. `LongTask`  
  
 `LongTask`jest wywoływana z czasem trwania zadania wynoszącym 12,2 sekund. `PercentDone` Zdarzenie jest zgłaszane raz w jednej trzeciej części sekundy. Za `mWidget_PercentDone` każdym razem, gdy zdarzenie jest zgłaszane, wykonywana jest procedura zdarzenia.  
  
 Gdy `LongTask` to zrobisz, `mblnCancel` zostanie przetestowany w `LongTask` celu sprawdzenia, czy zakończono normalne działanie `mblnCancel` , czy został `True`zatrzymany, ponieważ został ustawiony na. Procent ukończenia jest aktualizowany tylko w poprzednim przypadku.  
  
#### <a name="to-run-the-program"></a>Aby uruchomić program  
  
1. Naciśnij klawisz F5, aby umieścić projekt w trybie uruchamiania.  
  
2. Kliknij przycisk **Rozpocznij zadanie** . Za każdym razem `PercentDone` , gdy zdarzenie jest zgłaszane, etykieta zostaje zaktualizowana o wartość procentową wykonanego zadania.  
  
3. Kliknij przycisk **Anuluj** , aby zatrzymać zadanie. Zauważ, że wygląd przycisku **Anuluj** nie zmienia się natychmiast po jego kliknięciu. Zdarzenie nie może wystąpić, dopóki `My.Application.DoEvents` instrukcja nie zezwala na przetwarzanie zdarzeń. `Click`  
  
    > [!NOTE]
    > `My.Application.DoEvents` Metoda nie przetwarza zdarzeń w taki sam sposób jak w przypadku formularza. Na przykład w tym instruktażu należy kliknąć przycisk **Anuluj** dwa razy. Aby umożliwić bezpośrednie obsługiwanie zdarzeń przez formularz, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../../standard/threading/index.md).
  
 Może się pojawić monit o uruchomienie programu z użyciem klawisza F11 i przekroczenie kodu w wierszu. Można jasno zobaczyć, jak działa wprowadzanie `LongTask`, a następnie krótko wprowadzić ponownie `Form1` przy `PercentDone` każdym wywołaniu zdarzenia.  
  
 Co się stanie, jeśli podczas wykonywania z powrotem w kodzie `Form1` `LongTask` , metoda została wywołana ponownie? W najgorszym przypadku mogą wystąpić przeciążenia stosu `LongTask` , jeśli zostały wywołane za każdym razem, gdy zdarzenie zostało zgłoszone.  
  
 Można spowodować, aby zmienna `mWidget` obsługiwała zdarzenia dla innego `Widget` obiektu przez przypisanie odwołania do nowego `Widget` elementu do `mWidget`. W rzeczywistości kod można wykonać za `Button1_Click` każdym razem, gdy klikniesz przycisk.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Aby obsłużyć zdarzenia dla innego widżetu  
  
- Dodaj następujący wiersz kodu do `Button1_Click` procedury bezpośrednio przed wierszem, który odczytuje: `mWidget.LongTask(12.2, 0.33)`  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Powyższy kod tworzy nowy `Widget` za każdym razem, gdy przycisk zostanie kliknięty. Gdy tylko `LongTask` Metoda zostanie zakończona, odwołanie `Widget` do `Widget` zostanie wydane i zostanie zniszczone.  
  
 Zmienna może zawierać tylko jedno odwołanie do obiektu, więc Jeśli przypiszesz inny `Widget` obiekt do `mWidget`, zdarzenia poprzedniego `Widget` obiektu nie będą już obsługiwane. `WithEvents` Jeśli `mWidget` jest jedyną zmienną obiektu zawierającą odwołanie do starego `Widget`, obiekt zostanie zniszczony. Jeśli chcesz obsługiwać zdarzenia z kilku `Widget` obiektów, `AddHandler` Użyj instrukcji, aby przetwarzać zdarzenia z poszczególnych obiektów osobno.  
  
> [!NOTE]
> W razie potrzeby można zadeklarować dowolną liczbę `WithEvents` zmiennych, ale `WithEvents` tablice zmiennych nie są obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
