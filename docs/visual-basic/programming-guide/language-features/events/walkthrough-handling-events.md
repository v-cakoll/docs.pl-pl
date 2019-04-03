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
ms.openlocfilehash: 2a8b515f500884d743b7dcca41ffe8c1607375a9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840929"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Przewodnik: Obsługa zdarzeń (Visual Basic)
Jest to drugi dwa tematy, które pokazują sposób pracy ze zdarzeniami. Pierwszy temat [instruktażu: Deklarujący i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), pokazuje, jak deklarować i wywoływać zdarzenia. Ta sekcja używa formularza i klasy z tego przewodnika, aby pokazują, jak obsługiwać zdarzenia w przypadku mogą mieć miejsce.  
  
 `Widget` Przykład klasy korzysta z tradycyjnych instrukcji obsługi zdarzeń. Visual Basic umożliwia innych technik do pracy ze zdarzeniami. W charakterze ćwiczenia, można zmodyfikować ten przykład, aby używał `AddHandler` i `Handles` instrukcji.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Aby obsłużyć zdarzenie PercentDone klasy elementu Widget  
  
1.  Umieść następujący kod w `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents` — Słowo kluczowe Określa, że zmienna `mWidget` służy do obsługi zdarzeń obiektu. Należy określić rodzaj obiektu, podając nazwę klasy, z którego obiekt zostanie utworzony.  
  
     Zmienna `mWidget` jest zadeklarowana w `Form1` ponieważ `WithEvents` zmienne muszą być na poziomie klasy. Ta zasada obowiązuje niezależnie od typu klasy, które można umieścić w.  
  
     Zmienna `mblnCancel` służy do anulowania `LongTask` metody.  
  
## <a name="writing-code-to-handle-an-event"></a>Pisanie kodu, aby obsłużyć zdarzenie  
 Jak najszybciej po zadeklarowaniu zmiennej za pomocą `WithEvents`, nazwa zmiennej jest wyświetlana na liście rozwijanej po lewej stronie klasy **Edytor kodu**. Po wybraniu `mWidget`, `Widget` klasy zdarzenia są wyświetlane w prawo rozwijanej listy. Wybranie event Wyświetla procedury odpowiednie zdarzenia z prefiksem `mWidget` i podkreślenia. Procedury zdarzeń skojarzonych z `WithEvents` zmiennej podano nazwę zmiennej jako prefiksu.  
  
#### <a name="to-handle-an-event"></a>Aby obsłużyć zdarzenie  
  
1.  Wybierz `mWidget` na liście rozwijanej po lewej stronie w **Edytor kodu**.  
  
2.  Wybierz `PercentDone` zdarzenie z listy po prawej listy rozwijanej. **Edytor kodu** otwiera `mWidget_PercentDone` procedury zdarzenia.  
  
    > [!NOTE]
    >  **Edytor kodu** jest przydatna, ale nie jest to wymagane, do wstawiania nowych programów obsługi zdarzeń. W tym instruktażu jest bardziej bezpośrednie, aby po prostu skopiować procedury obsługi zdarzeń bezpośrednio w kodzie.  
  
3.  Dodaj następujący kod do `mWidget_PercentDone` program obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Zawsze, gdy `PercentDone` zdarzenie jest zgłaszane, procedura zdarzenia Wyświetla procent wykonania w `Label` kontroli. `DoEvents` Metoda umożliwia etykiety do odświeżenia, a także zapewnia możliwość kliknij **anulować** przycisku.  
  
4.  Dodaj następujący kod do `Button2_Click` program obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Jeśli użytkownik kliknie **anulować** przycisk podczas `LongTask` jest uruchomiona, `Button2_Click` zdarzeń jest wykonywane tak szybko, jak `DoEvents` instrukcji umożliwia przetwarzanie zdarzeń, które wystąpią. Zmienna poziomu klasa `mblnCancel` jest ustawiona na `True`i `mWidget_PercentDone` zdarzeń następnie ją sprawdza i ustawia `ByRef Cancel` argument `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Łączenie zmiennej WithEvents do obiektu  
 `Form1` jest teraz skonfigurowane do obsługi `Widget` zdarzenia obiektu. Pozostaje tylko można znaleźć `Widget` gdzieś.  
  
 Kiedy Deklarujesz zmienną `WithEvents` w czasie projektowania, żaden obiekt nie jest skojarzony z nim. A `WithEvents` zmienna zachowuje się podobnie jak dowolnej zmiennej obiektu. Należy utworzyć obiekt i przypisać odwołanie do niej przy użyciu `WithEvents` zmiennej.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Aby utworzyć obiekt i przypisać odwołanie do niej  
  
1.  Wybierz **(formularz Form1 zdarzenia)** na liście rozwijanej po lewej stronie w **Edytor kodu**.  
  
2.  Wybierz `Load` zdarzenie z listy po prawej listy rozwijanej. **Edytor kodu** otwiera `Form1_Load` procedury zdarzenia.  
  
3.  Dodaj następujący kod do `Form1_Load` procedurę zdarzeń w celu utworzenia `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Gdy ten kod jest wykonywany, Visual Basic tworzy `Widget` obiektu i jego zdarzeń nawiązanie połączenia z procedur zdarzeń związanych z `mWidget`. Od tego punktu, gdy `Widget` wywołuje jego `PercentDone` zdarzenia `mWidget_PercentDone` zdarzeń procedura jest wykonywana.  
  
#### <a name="to-call-the-longtask-method"></a>Aby wywołać metodę LongTask  
  
-   Dodaj następujący kod do `Button1_Click` program obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Przed `LongTask` metoda jest wywoływana, etykieta Wyświetla procent ukończenia musi zostać zainicjowany i poziomu klasa `Boolean` Flaga dla anulowanie metody musi być równa `False`.  
  
 `LongTask` jest wywoływana z czas trwania zadania 12.2 sekund. `PercentDone` Zdarzenie jest wywoływane po każdym jednej trzeciej części sekundy. Każdorazowo, zdarzenie jest wywoływane, `mWidget_PercentDone` zdarzeń procedura jest wykonywana.  
  
 Gdy `LongTask` zostanie to zrobione, `mblnCancel` jest testowany, aby sprawdzić, czy `LongTask` zakończył się normalnie, czy zatrzymane, ponieważ `mblnCancel` została ustawiona na `True`. Procent wykonania jest aktualizowany tylko w przypadku poprzedniej wersji portalu.  
  
#### <a name="to-run-the-program"></a>Aby uruchomić program  
  
1.  Naciśnij klawisz F5, aby przełączyć projekt w trybie uruchamiania.  
  
2.  Kliknij przycisk **Rozpocznij zadanie** przycisku. Każdorazowo `PercentDone` zdarzenie jest zgłaszane, etykieta zostanie zaktualizowana przy użyciu procent wykonania zadania.  
  
3.  Kliknij przycisk **anulować** przycisk, aby zatrzymać zadanie. Należy zauważyć, że wygląd **anulować** natychmiast po kliknięciu przycisku nie powoduje zmiany. `Click` Zdarzeń nie może się zdarzyć, dopóki `My.Application.DoEvents` instrukcji umożliwia przetwarzanie zdarzeń.  
  
    > [!NOTE]
    >  `My.Application.DoEvents` Metody nie przetwarza zdarzeń w taki sam sposób jak formularz. Na przykład, w tym przewodniku należy kliknij **anulować** podwójnie. Aby zezwolić na formularzu do obsługi zdarzeń bezpośrednio, możesz użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość](../../../../standard/threading/index.md).
  
 Może okazać się istotne, aby uruchomić program za pomocą F11 i przejść przez kod linię w danym momencie. Wyraźnie widać, jak wykonanie wprowadza `LongTask`i następnie krótko ponownie wprowadza `Form1` każdorazowo `PercentDone` zdarzenie jest wywoływane.  
  
 Co się stanie, jeśli podczas wykonywania w kodzie `Form1`, `LongTask` metoda była nazywana ponownie? W najgorszym przypadku może wystąpić przepełnienie stosu, jeśli `LongTask` były wywoływane za każdym razem, gdy zdarzenia zostało podniesione.  
  
 Może spowodować zmiennej `mWidget` do obsługi zdarzeń dla innego `Widget` obiektu przez przypisywanie odwołania do nowego `Widget` do `mWidget`. W rzeczywistości, można wprowadzić kod w `Button1_Click` to zrobić, za każdym razem, gdy klikniesz przycisk.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Do obsługi zdarzeń dla innego elementu widget  
  
-   Dodaj następujący wiersz kodu w celu `Button1_Click` procedury bezpośrednio poprzedzający wiersz zawierający ciąg `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Powyższy kod tworzy nową `Widget` każdym kliknięciu przycisku. Jak najszybciej `LongTask` metoda zakończeniu odwołanie do `Widget` wydaniu i `Widget` zostanie zniszczony.  
  
 A `WithEvents` zmienna może zawierać tylko jeden obiekt odwołania w czasie, więc Jeśli przypiszesz inną `Widget` obiekt `mWidget`, poprzedni `Widget` zdarzenia obiektu będzie już obsługiwana. Jeśli `mWidget` jest tylko zmienna obiekt zawierający odniesienia do starego `Widget`, obiekt zostanie zniszczony. Jeśli chcesz obsługiwać zdarzenia z kilku `Widget` obiekty, używają `AddHandler` instrukcję, aby oddzielnie przetwarzania zdarzeń pochodzących z każdego obiektu.  
  
> [!NOTE]
>  Można zadeklarować dowolną liczbę `WithEvents` zmiennych, jak należy, ale tablic `WithEvents` zmienne nie są obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
