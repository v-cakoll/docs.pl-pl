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
ms.openlocfilehash: 29d878afbe3669fc88e62b1fec98b306918c303d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405083"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Wskazówki: obsługa zdarzeń (Visual Basic)
Jest to drugi z dwóch tematów, które pokazują, jak korzystać z zdarzeń. Pierwszy temat, [Przewodnik: deklarowanie i](walkthrough-declaring-and-raising-events.md)wywoływanie zdarzeń, pokazuje sposób deklarowania i zgłaszania zdarzeń. Ta sekcja używa formularza i klasy z tego przewodnika, aby pokazać, jak obsługiwać zdarzenia po ich przejściu.  
  
 W `Widget` przykładzie klasy są stosowane tradycyjne instrukcje obsługi zdarzeń. Visual Basic zapewnia inne techniki pracy ze zdarzeniami. W ramach ćwiczenia można zmodyfikować ten przykład, aby użyć `AddHandler` `Handles` instrukcji i.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Aby obsłużyć zdarzenie PercentDone klasy widget  
  
1. Umieść następujący kod w `Form1` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`Słowo kluczowe Określa, że zmienna `mWidget` jest używana do obsługi zdarzeń obiektu. Należy określić rodzaj obiektu, dostarczając nazwę klasy, z której zostanie utworzony obiekt.  
  
     Zmienna `mWidget` jest zadeklarowana w, `Form1` ponieważ `WithEvents` zmienne muszą być na poziomie klasy. Ta wartość jest prawdziwa niezależnie od typu klasy, w której je umieszczasz.  
  
     Zmienna służy `mblnCancel` do anulowania `LongTask` metody.  
  
## <a name="writing-code-to-handle-an-event"></a>Pisanie kodu do obsługi zdarzenia  
 Po zadeklarowaniu zmiennej przy użyciu `WithEvents` , nazwa zmiennej jest wyświetlana na liście rozwijanej w **edytorze kodu**klasy. Po wybraniu `mWidget` `Widget` zdarzenia klasy są wyświetlane na liście rozwijanej po prawej stronie. Wybranie zdarzenia powoduje wyświetlenie odpowiedniej procedury zdarzenia z prefiksem `mWidget` i podkreśleniem. Wszystkie procedury zdarzeń skojarzone ze `WithEvents` zmienną otrzymują nazwę zmiennej jako prefiks.  
  
#### <a name="to-handle-an-event"></a>Aby obsłużyć zdarzenie  
  
1. Wybierz `mWidget` z listy rozwijanej po lewej stronie w **edytorze kodu**.  
  
2. Wybierz `PercentDone` zdarzenie z listy rozwijanej po prawej stronie. **Edytor kodu** otwiera `mWidget_PercentDone` procedurę zdarzenia.  
  
    > [!NOTE]
    > **Edytor kodu** jest przydatny, ale nie jest wymagany, do wstawiania nowych programów obsługi zdarzeń. W tym instruktażu bardziej bezpośrednim jest tylko kopiowanie programów obsługi zdarzeń bezpośrednio do kodu.  
  
3. Dodaj następujący kod do `mWidget_PercentDone` programu obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Za każdym razem `PercentDone` , gdy zdarzenie jest zgłaszane, procedura zdarzenia wyświetla procent wykonania w `Label` kontrolce. `DoEvents`Metoda pozwala na odświeżenie etykiety, a także pozwala użytkownikowi kliknąć przycisk **Anuluj** .  
  
4. Dodaj następujący kod dla `Button2_Click` programu obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Jeśli użytkownik kliknie przycisk **Anuluj** w trakcie `LongTask` działania, `Button2_Click` zdarzenie jest wykonywane zaraz po tym, jak `DoEvents` instrukcja zezwala na przetwarzanie zdarzeń. Zmienna na poziomie klasy `mblnCancel` jest ustawiana na `True` , a `mWidget_PercentDone` następnie zdarzenie sprawdza i ustawia `ByRef Cancel` argument na `True` .  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Łączenie zmiennej WithEvents z obiektem  
 `Form1`jest teraz skonfigurowany do obsługi `Widget` zdarzeń obiektu. To wszystko, co pozostało, aby znaleźć `Widget` gdzieś.  
  
 Po zadeklarowaniu zmiennej `WithEvents` w czasie projektowania, żaden obiekt nie jest skojarzony z nim. `WithEvents`Zmienna jest tak samo jak jakakolwiek inna zmienna obiektu. Należy utworzyć obiekt i przypisać do niego odwołanie przy użyciu `WithEvents` zmiennej.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Aby utworzyć obiekt i przypisać do niego odwołanie  
  
1. Wybierz pozycję **(zdarzenia Form1)** z listy rozwijanej po lewej stronie w **edytorze kodu**.  
  
2. Wybierz `Load` zdarzenie z listy rozwijanej po prawej stronie. **Edytor kodu** otwiera `Form1_Load` procedurę zdarzenia.  
  
3. Dodaj następujący kod dla `Form1_Load` procedury zdarzenia, aby utworzyć `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Gdy ten kod jest wykonywany, Visual Basic tworzy `Widget` obiekt i łączy jego zdarzenia z procedurami zdarzeń skojarzonymi z `mWidget` . Od tego momentu, gdy `Widget` wywołuje `PercentDone` zdarzenie, `mWidget_PercentDone` procedura zdarzenia jest wykonywana.  
  
#### <a name="to-call-the-longtask-method"></a>Aby wywołać metodę LongTask  
  
- Dodaj następujący kod do `Button1_Click` programu obsługi zdarzeń:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Przed `LongTask` wywołaniem metody, etykieta, w której jest wyświetlany procent wykonania, musi zostać zainicjowana, a flaga poziomu klasy `Boolean` dla anulowania metody musi być ustawiona na `False` .  
  
 `LongTask`jest wywoływana z czasem trwania zadania wynoszącym 12,2 sekund. `PercentDone`Zdarzenie jest zgłaszane raz w jednej trzeciej części sekundy. Za każdym razem, gdy zdarzenie jest zgłaszane, `mWidget_PercentDone` wykonywana jest procedura zdarzenia.  
  
 Gdy `LongTask` to zrobisz, `mblnCancel` zostanie przetestowany w celu sprawdzenia `LongTask` , czy zakończono normalne działanie, czy został zatrzymany, ponieważ `mblnCancel` został ustawiony na `True` . Procent ukończenia jest aktualizowany tylko w poprzednim przypadku.  
  
#### <a name="to-run-the-program"></a>Aby uruchomić program  
  
1. Naciśnij klawisz F5, aby umieścić projekt w trybie uruchamiania.  
  
2. Kliknij przycisk **Rozpocznij zadanie** . Za każdym razem `PercentDone` , gdy zdarzenie jest zgłaszane, etykieta zostaje zaktualizowana o wartość procentową wykonanego zadania.  
  
3. Kliknij przycisk **Anuluj** , aby zatrzymać zadanie. Zauważ, że wygląd przycisku **Anuluj** nie zmienia się natychmiast po jego kliknięciu. `Click`Zdarzenie nie może wystąpić, dopóki `My.Application.DoEvents` instrukcja nie zezwala na przetwarzanie zdarzeń.  
  
    > [!NOTE]
    > `My.Application.DoEvents`Metoda nie przetwarza zdarzeń w taki sam sposób jak w przypadku formularza. Na przykład w tym instruktażu należy kliknąć przycisk **Anuluj** dwa razy. Aby umożliwić bezpośrednie obsługiwanie zdarzeń przez formularz, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../../standard/threading/index.md).
  
 Może się pojawić monit o uruchomienie programu z użyciem klawisza F11 i przekroczenie kodu w wierszu. Można jasno zobaczyć, jak działa wprowadzanie `LongTask` , a następnie krótko wprowadzić ponownie `Form1` przy każdym `PercentDone` wywołaniu zdarzenia.  
  
 Co się stanie, jeśli podczas wykonywania z powrotem w kodzie `Form1` , `LongTask` Metoda została wywołana ponownie? W najgorszym przypadku mogą wystąpić przeciążenia stosu, jeśli `LongTask` zostały wywołane za każdym razem, gdy zdarzenie zostało zgłoszone.  
  
 Można spowodować, aby zmienna `mWidget` obsługiwała zdarzenia dla innego `Widget` obiektu przez przypisanie odwołania do nowego elementu `Widget` do `mWidget` . W rzeczywistości kod można wykonać za `Button1_Click` każdym razem, gdy klikniesz przycisk.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Aby obsłużyć zdarzenia dla innego widżetu  
  
- Dodaj następujący wiersz kodu do `Button1_Click` procedury bezpośrednio przed wierszem, który odczytuje `mWidget.LongTask(12.2, 0.33)` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Powyższy kod tworzy nowy za `Widget` każdym razem, gdy przycisk zostanie kliknięty. Gdy tylko Metoda zostanie `LongTask` zakończona, odwołanie do `Widget` zostanie wydane i `Widget` zostanie zniszczone.  
  
 `WithEvents`Zmienna może zawierać tylko jedno odwołanie do obiektu, więc Jeśli przypiszesz inny `Widget` obiekt do `mWidget` , `Widget` zdarzenia poprzedniego obiektu nie będą już obsługiwane. Jeśli `mWidget` jest jedyną zmienną obiektu zawierającą odwołanie do starego `Widget` , obiekt zostanie zniszczony. Jeśli chcesz obsługiwać zdarzenia z kilku `Widget` obiektów, użyj `AddHandler` instrukcji, aby przetwarzać zdarzenia z poszczególnych obiektów osobno.  
  
> [!NOTE]
> W razie potrzeby można zadeklarować dowolną liczbę `WithEvents` zmiennych, ale tablice `WithEvents` zmiennych nie są obsługiwane.  
  
## <a name="see-also"></a>Zobacz też

- [Wskazówki: deklarowanie i wywoływanie zdarzeń](walkthrough-declaring-and-raising-events.md)
- [Zdarzenia](index.md)
