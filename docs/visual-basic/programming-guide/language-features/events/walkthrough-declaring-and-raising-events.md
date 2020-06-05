---
title: Deklarowanie i wywoływanie zdarzeń
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 3da60014d7ac95189c5d56c3e339ff1b054a40dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405096"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Wskazówki: deklarowanie i wywoływanie zdarzeń (Visual Basic)
W tym instruktażu pokazano, jak zadeklarować i zgłosić zdarzenia dla klasy o nazwie `Widget` . Po wykonaniu kroków warto przeczytać temat pomocnika, [Przewodnik: obsługa zdarzeń](walkthrough-handling-events.md), który pokazuje, jak używać zdarzeń z `Widget` obiektów w celu dostarczania informacji o stanie w aplikacji.  
  
## <a name="the-widget-class"></a>Klasa widget  
 Załóżmy dla momentu, gdy masz `Widget` klasę. Twoja `Widget` Klasa ma metodę, która może zająć dużo czasu, i chcesz, aby aplikacja mogła umieścić jakiś wskaźnik uzupełniania.  
  
 Oczywiście można sprawić, `Widget` Aby obiekt pokazywał okno dialogowe z wartością procentową, ale w każdym projekcie, w którym została użyta Klasa, zostało zablokowane `Widget` . Dobrą zasadą projektowania obiektów jest umożliwienie aplikacji, która używa obiektu obsługującego interfejs użytkownika — chyba że cały cel obiektu ma zarządzać formularzem lub oknem dialogowym.  
  
 Celem `Widget` jest wykonywanie innych zadań, dlatego lepszym rozwiązaniem jest dodanie `PercentDone` zdarzenia i poinformowanie procedury, która wywołuje `Widget` metody obsługi tego zdarzenia i wyświetla aktualizacje stanu. `PercentDone`Zdarzenie może również dostarczyć mechanizm anulowania zadania.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Aby skompilować przykład kodu dla tego tematu  
  
1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows i Utwórz formularz o nazwie `Form1` .  
  
2. Dodaj dwa przyciski i etykietę do `Form1` .  
  
3. Nazwij obiekty, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Uruchom zadanie|  
    |`Button2`|`Text`|Anuluj|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. W menu **projekt** wybierz polecenie **Dodaj klasę** , aby dodać klasę o nazwie `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Aby zadeklarować zdarzenie dla klasy widget  
  
- Użyj `Event` słowa kluczowego, aby zadeklarować zdarzenie w `Widget` klasie. Należy zauważyć, że zdarzenie może mieć `ByVal` i `ByRef` argumenty, `Widget` jako `PercentDone` zdarzenie:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Gdy wywołujący obiekt odbiera `PercentDone` zdarzenie, `Percent` argument zawiera procent wykonanego zadania. `Cancel`Argument może być ustawiony na `True` , aby anulować metodę, która wywołała zdarzenie.  
  
> [!NOTE]
> Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: zdarzenia nie mogą mieć `Optional` argumentów lub `ParamArray` , a zdarzenia nie mają zwracanych wartości.  
  
 `PercentDone`Zdarzenie jest wywoływane przez `LongTask` metodę `Widget` klasy. `LongTask`przyjmuje dwa argumenty: czas, który ma być wykonywany przez metodę, oraz minimalny interwał czasu przed `LongTask` zatrzymaniem `PercentDone` zdarzenia.  
  
#### <a name="to-raise-the-percentdone-event"></a>Aby zgłosić zdarzenie PercentDone  
  
1. Aby uprościć dostęp do `Timer` Właściwości używanej przez tę klasę, Dodaj `Imports` instrukcję do górnej części sekcji deklaracji w module klasy, powyżej `Class Widget` instrukcji.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Dodaj następujący kod do `Widget` klasy:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Gdy aplikacja wywołuje `LongTask` metodę, `Widget` Klasa zgłasza `PercentDone` zdarzenie co `MinimumInterval` kilka sekund. Po powrocie zdarzenia program `LongTask` sprawdza, czy `Cancel` argument został ustawiony na `True` .  
  
 W tym miejscu należy wprowadzić kilka odrzutów. Dla uproszczenia w `LongTask` procedurze założono, że wiesz, jak długo zadanie będzie wykonywane. To prawie nigdy nie dotyczy. Dzielenie zadań na fragmenty nawet rozmiaru może być trudne, a często najważniejsze znaczenie dla użytkowników to po prostu ilość czasu, która jest przekazywana przed uzyskaniem wskazującego, że coś się dzieje.  
  
 W tym przykładzie może zostać wykorzystana inna luka. `Timer`Właściwość zwraca liczbę sekund, które upłynęły od północy; w związku z tym aplikacja zostaje zablokowana, jeśli zostanie uruchomiona tuż przed północy. Bardziej staranne podejście do mierzenia czasu będzie miało wpływ na warunki graniczne, takie jak to, lub uniknąć ich całkowitego, przy użyciu właściwości, takich jak `Now` .  
  
 Teraz, gdy `Widget` Klasa może zgłaszać zdarzenia, możesz przejść do następnego przewodnika. [Przewodnik: obsługa zdarzeń](walkthrough-handling-events.md) pokazuje, jak używać `WithEvents` do kojarzenia procedury obsługi zdarzeń ze `PercentDone` zdarzeniem.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Przewodnik: obsługa zdarzeń](walkthrough-handling-events.md)
- [Zdarzenia](index.md)
