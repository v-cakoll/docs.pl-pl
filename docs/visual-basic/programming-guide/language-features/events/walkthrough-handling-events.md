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
ms.openlocfilehash: 0ac3514505ca42870d77317feec30a27e4384e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a>Wskazówki: obsługa zdarzeń (Visual Basic)
Jest to drugi dwa tematy, które przedstawiają sposób pracy ze zdarzeniami. Pierwszym temacie [wskazówki: deklarujący i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), pokazuje, jak deklarowanie i wywoływanie zdarzeń. Ta sekcja używa formularza i klasy z tego przewodnika pokazanie sposobu obsługi zdarzenia, gdy ich została wykonana.  
  
 `Widget` Klasy przykładzie użyto tradycyjnych instrukcje obsługi zdarzeń. Visual Basic zapewnia innych technik do pracy ze zdarzeniami. Jako wykonywania można modyfikować w tym przykładzie, aby użyć `AddHandler` i `Handles` instrukcje.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Obsługa zdarzenia PercentDone klasy widżetu  
  
1.  Umieść następujący kod w `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents` — Słowo kluczowe Określa, że zmienna `mWidget` służy do obsługi zdarzeń obiektu. Należy określić rodzaj obiektu, podając nazwę klasy, z którego będzie można utworzyć obiektu.  
  
     Zmienna `mWidget` jest zadeklarowana w `Form1` ponieważ `WithEvents` zmienne musi być na poziomie klasy. Dotyczy to bez względu na typ klasy, która zostanie umieszczony w.  
  
     Zmienna `mblnCancel` jest używany do anulowania `LongTask` metody.  
  
## <a name="writing-code-to-handle-an-event"></a>Pisanie kodu do obsługi zdarzeń  
 Jak można zadeklarować zmiennej przy użyciu `WithEvents`, nazwa zmiennej jest wyświetlana na liście rozwijanej po lewej stronie klasy **edytora kodu**. Po wybraniu `mWidget`, `Widget` klasy zdarzenia są wyświetlane na liście po prawej listy rozwijanej. Wybranie zdarzenia zawiera procedury odpowiednie zdarzenia z prefiksem `mWidget` i podkreślenia. Procedur zdarzeń związanych z `WithEvents` zmiennej podano nazwę zmiennej jako prefiksu.  
  
#### <a name="to-handle-an-event"></a>Do obsługi zdarzeń  
  
1.  Wybierz `mWidget` z listy rozwijanej po lewej stronie **edytora kodu**.  
  
2.  Wybierz `PercentDone` zdarzenie na liście po prawej listy rozwijanej. **Edytora kodu** otwiera `mWidget_PercentDone` procedury zdarzenia.  
  
    > [!NOTE]
    >  **Edytora kodu** jest przydatne, ale nie jest to wymagane, wstawiania nowych programów obsługi zdarzeń. W tym przewodniku jest bardziej bezpośrednio po prostu skopiuj obsługi zdarzeń bezpośrednio w kodzie.  
  
3.  Dodaj następujący kod do `mWidget_PercentDone` obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     Zawsze, gdy `PercentDone` zdarzenie jest zgłaszane, procedura zdarzenia wyświetlane wykonano w `Label` formantu. `DoEvents` Metoda pozwala etykiety do odświeżenia, a także daje użytkownikowi możliwość kliknij **anulować** przycisk.  
  
4.  Dodaj następujący kod do `Button2_Click` obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 Gdy użytkownik kliknie **anulować** przycisk podczas `LongTask` jest uruchomiona, `Button2_Click` zdarzeń jest wykonywane tak szybko, jak `DoEvents` instrukcji umożliwia przetwarzanie zdarzenia występują. Zmienna poziomie klasy `mblnCancel` ustawiono `True`i `mWidget_PercentDone` zdarzeń następnie sprawdza ją i ustawia `ByRef Cancel` argument `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Łączenie do obiektu zmiennej WithEvents  
 `Form1` jest teraz skonfigurowane do obsługi `Widget` zdarzenia obiektu. Wszystkie opcje, które pozostaje jest znalezienie `Widget` innym.  
  
 Gdy zadeklarować zmiennej `WithEvents` w czasie projektowania, żaden obiekt jest skojarzony z nim. A `WithEvents` zmienna jest podobnie jak inne zmienna obiektu. Należy utworzyć obiekt i przypisać odwołanie do niej z `WithEvents` zmiennej.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Aby utworzyć obiekt i przypisać odwołanie do niej  
  
1.  Wybierz **(Form1 zdarzeń)** z listy rozwijanej po lewej stronie **edytora kodu**.  
  
2.  Wybierz `Load` zdarzenie na liście po prawej listy rozwijanej. **Edytora kodu** otwiera `Form1_Load` procedury zdarzenia.  
  
3.  Dodaj następujący kod do `Form1_Load` procedury zdarzenia można utworzyć `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 Podczas tego kodu, Visual Basic tworzy `Widget` obiektu i jego zdarzeń nawiązanie połączenia procedur zdarzeń związanych z `mWidget`. Od tego punktu, gdy `Widget` zgłasza jego `PercentDone` zdarzenia `mWidget_PercentDone` zdarzeń procedura jest wykonywana.  
  
#### <a name="to-call-the-longtask-method"></a>Aby wywołać metodę LongTask  
  
-   Dodaj następujący kod do `Button1_Click` obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 Przed `LongTask` metoda jest wywoływana etykiety wyświetla procentu ukończenia musi zostać zainicjowany i poziomie klasy `Boolean` Flaga anulowanie metoda musi mieć ustawioną `False`.  
  
 `LongTask` jest wywoływana z czas trwania zadania 12.2 sekund. `PercentDone` Zdarzenie jest wywoływane po każdym jedna trzecia sekundy. Zawsze zdarzenie jest zgłaszane, `mWidget_PercentDone` zdarzeń procedura jest wykonywana.  
  
 Podczas `LongTask` jest wykonywana, `mblnCancel` jest testowany, aby sprawdzić, czy `LongTask` zakończone normalnie, lub jeśli zatrzymana, ponieważ `mblnCancel` ustawiono `True`. Procent wykonania jest aktualizowany tylko w pierwszym przypadku.  
  
#### <a name="to-run-the-program"></a>Aby uruchomić program  
  
1.  Naciśnij klawisz F5, aby umieścić projektu w trybie uruchamiania.  
  
2.  Kliknij przycisk **Rozpocznij zadanie** przycisku. Zawsze `PercentDone` zdarzenie jest zgłaszane, etykiety został zaktualizowany o procent wykonania zadania.  
  
3.  Kliknij przycisk **anulować** przycisk, aby zatrzymać zadanie. Zwróć uwagę, że wygląd **anulować** natychmiast po kliknięciu przycisku nie ulega zmianie. `Click` Zdarzeń nie może mieć miejsce, do `My.Application.DoEvents` instrukcji umożliwia przetwarzanie zdarzenia.  
  
    > [!NOTE]
    >  `My.Application.DoEvents` — Metoda nie przetwarza zdarzenia w taki sam sposób jak w formularzu. Na przykład, w tym przewodniku muszą kliknij **anulować** dwa razy przycisk. Aby zezwolić na formularzu, aby obsługiwać zdarzenia bezpośrednio, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz [wątki](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
 Może być istotne, aby uruchomić program z F11 i krokowo kodu wiersza w czasie. Wyraźnie widać, jak wykonanie wprowadza `LongTask`i następnie krótko ponownie wprowadzenia `Form1` zawsze `PercentDone` zdarzenia.  
  
 Co się stanie, jeśli podczas wykonywania ponownie kod `Form1`, `LongTask` metody wywołane ponownie? W najgorszym przepełnienie stosu może wystąpić, jeśli `LongTask` były nazywane za każdym razem, gdy wywołano zdarzenie.  
  
 Zmienna może spowodować `mWidget` do obsługi zdarzeń dla innej `Widget` obiektu przypisując odwołanie do nowego `Widget` do `mWidget`. W rzeczywistości wprowadzisz kod w `Button1_Click` to zrobić, za każdym razem, kliknij przycisk.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Do obsługi zdarzeń dla różnych widżetu  
  
-   Dodaj następujący wiersz kodu w celu `Button1_Click` procedura bezpośrednio po wierszu `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 Powyższy kod tworzy nową `Widget` każdym kliknięciu przycisku. Jak najszybciej `LongTask` metody zakończeniu odwołanie do `Widget` wydaniu i `Widget` zostanie zniszczony.  
  
 A `WithEvents` zmienna może zawierać tylko jeden obiekt odniesienia w czasie, tak więc jeśli możesz przypisać inną `Widget` do obiektu `mWidget`, poprzedniej `Widget` zdarzeń obiektu będzie już obsługiwany. Jeśli `mWidget` jest tylko zmienna obiektu zawierające odwołania do starego `Widget`, obiekt zostanie zniszczony. Jeśli chcesz obsługiwać zdarzenia z kilku `Widget` obiektów, użyj `AddHandler` instrukcji przetwarzania zdarzeń z każdego obiektu osobno.  
  
> [!NOTE]
>  Można zadeklarować tyle `WithEvents` muszą zmienne jako użytkownik, ale tablice `WithEvents` zmienne nie są obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
