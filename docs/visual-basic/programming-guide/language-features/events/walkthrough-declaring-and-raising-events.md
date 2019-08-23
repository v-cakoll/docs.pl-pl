---
title: Deklarowanie i wywoływanie zdarzeń (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956335"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Przewodnik: Deklarowanie i wywoływanie zdarzeń (Visual Basic)
W tym instruktażu pokazano, jak zadeklarować i zgłosić zdarzenia dla `Widget`klasy o nazwie. Po wykonaniu kroków warto przeczytać temat pomocnika, [Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), które pokazują, jak używać zdarzeń z `Widget` obiektów w celu dostarczania informacji o stanie w aplikacji.  
  
## <a name="the-widget-class"></a>Klasa widget  
 Załóżmy dla momentu, gdy masz `Widget` klasę. Twoja `Widget` Klasa ma metodę, która może zająć dużo czasu, i chcesz, aby aplikacja mogła umieścić jakiś wskaźnik uzupełniania.  
  
 Oczywiście można sprawić `Widget` , aby obiekt pokazywał okno dialogowe z wartością procentową, ale w każdym projekcie, w którym została `Widget` użyta Klasa, zostało zablokowane. Dobrą zasadą projektowania obiektów jest umożliwienie aplikacji, która używa obiektu obsługującego interfejs użytkownika — chyba że cały cel obiektu ma zarządzać formularzem lub oknem dialogowym.  
  
 Celem `Widget` jest wykonywanie innych zadań, dlatego lepszym rozwiązaniem jest `PercentDone` dodanie zdarzenia i poinformowanie procedury, która wywołuje `Widget`metody obsługi tego zdarzenia i wyświetla aktualizacje stanu. `PercentDone` Zdarzenie może również dostarczyć mechanizm anulowania zadania.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Aby skompilować przykład kodu dla tego tematu  
  
1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows i Utwórz formularz o nazwie `Form1`.  
  
2. Dodaj dwa przyciski i etykietę do `Form1`.  
  
3. Nazwij obiekty, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Uruchom zadanie|  
    |`Button2`|`Text`|Anuluj|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. W menu **projekt** wybierz polecenie **Dodaj klasę** , aby dodać klasę o nazwie `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Aby zadeklarować zdarzenie dla klasy widget  
  
- Użyj słowa `Event` kluczowego, aby zadeklarować zdarzenie `Widget` w klasie. Należy zauważyć, że zdarzenie może `ByVal` mieć `ByRef` i argumenty, `Widget`jako `PercentDone` zdarzenie:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Gdy wywołujący obiekt odbiera `PercentDone` zdarzenie `Percent` , argument zawiera procent wykonanego zadania. Argument może być ustawiony na `True` , aby anulować metodę, która wywołała zdarzenie. `Cancel`  
  
> [!NOTE]
> Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: Zdarzenia nie mogą `Optional` mieć `ParamArray` argumentów lub, a zdarzenia nie mają zwracanych wartości.  
  
 Zdarzenie jest wywoływane `LongTask` przez metodę `Widget` klasy. `PercentDone` `LongTask`przyjmuje dwa argumenty: czas, który ma być wykonywany przez metodę, oraz minimalny interwał czasu przed `LongTask` zatrzymaniem `PercentDone` zdarzenia.  
  
#### <a name="to-raise-the-percentdone-event"></a>Aby zgłosić zdarzenie PercentDone  
  
1. Aby uprościć dostęp do `Timer` właściwości używanej przez tę klasę, `Imports` Dodaj instrukcję do górnej części sekcji deklaracji w module `Class Widget` klasy, powyżej instrukcji.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Dodaj następujący kod do `Widget` klasy:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Gdy aplikacja wywołuje `LongTask` metodę `Widget` , Klasa zgłasza `PercentDone` zdarzenie co `MinimumInterval` kilka sekund. Po powrocie zdarzenia program `LongTask` sprawdza, `Cancel` czy argument został ustawiony na `True`.  
  
 W tym miejscu należy wprowadzić kilka odrzutów. Dla uproszczenia w `LongTask` procedurze założono, że wiesz, jak długo zadanie będzie wykonywane. To prawie nigdy nie dotyczy. Dzielenie zadań na fragmenty nawet rozmiaru może być trudne, a często najważniejsze znaczenie dla użytkowników to po prostu ilość czasu, która jest przekazywana przed uzyskaniem wskazującego, że coś się dzieje.  
  
 W tym przykładzie może zostać wykorzystana inna luka. `Timer` Właściwość zwraca liczbę sekund, które upłynęły od północy; w związku z tym aplikacja zostaje zablokowana, jeśli zostanie uruchomiona tuż przed północy. Bardziej staranne podejście do mierzenia czasu będzie miało wpływ na warunki graniczne, takie jak to, lub uniknąć ich całkowitego, przy `Now`użyciu właściwości, takich jak.  
  
 Teraz, gdy `Widget` Klasa może zgłaszać zdarzenia, możesz przejść do następnego przewodnika. [Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) pokazuje `WithEvents` ,`PercentDone` jak używać do kojarzenia procedury obsługi zdarzeń ze zdarzeniem.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
