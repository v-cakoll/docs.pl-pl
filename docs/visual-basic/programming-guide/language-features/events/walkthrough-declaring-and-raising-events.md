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
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345088"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Wskazówki: deklarowanie i wywoływanie zdarzeń (Visual Basic)
W tym instruktażu pokazano, jak zadeklarować i zgłosić zdarzenia dla klasy o nazwie `Widget`. Po wykonaniu kroków warto przeczytać temat pomocnika, [Przewodnik: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), który pokazuje, jak używać zdarzeń z `Widget` obiektów w celu zapewnienia informacji o stanie w aplikacji.  
  
## <a name="the-widget-class"></a>Klasa widget  
 Załóżmy, że masz już klasę `Widget`. Twoja Klasa `Widget` ma metodę, która może zająć dużo czasu, i chcesz, aby aplikacja mogła umieścić jakiś rodzaj wskaźnika uzupełniania.  
  
 Oczywiście można sprawić, aby obiekt `Widget` pokazywał okno dialogowe z wartością procentową, ale w każdym projekcie, w którym użyto klasy `Widget`, zostało zablokowane. Dobrą zasadą projektowania obiektów jest umożliwienie aplikacji, która używa obiektu obsługującego interfejs użytkownika — chyba że cały cel obiektu ma zarządzać formularzem lub oknem dialogowym.  
  
 Celem `Widget` jest wykonywanie innych zadań, dlatego lepiej jest dodać zdarzenie `PercentDone` i pozwolić procedurze wywołującej metody `Widget`obsłużyć to zdarzenie i wyświetlić aktualizacje stanu. Zdarzenie `PercentDone` może również dostarczyć mechanizm anulowania zadania.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Aby skompilować przykład kodu dla tego tematu  
  
1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows i Utwórz formularz o nazwie `Form1`.  
  
2. Dodaj dwa przyciski i etykietę do `Form1`.  
  
3. Nazwij obiekty, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Uruchom zadanie|  
    |`Button2`|`Text`|Cancel|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. W menu **projekt** wybierz polecenie **Dodaj klasę** , aby dodać klasę o nazwie `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Aby zadeklarować zdarzenie dla klasy widget  
  
- Użyj słowa kluczowego `Event`, aby zadeklarować zdarzenie w klasie `Widget`. Należy zauważyć, że zdarzenie może mieć `ByVal` i `ByRef` argumentów, ponieważ `PercentDone` zdarzenia `Widget`ilustruje:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Gdy wywołujący obiekt odbiera zdarzenie `PercentDone`, argument `Percent` zawiera wartość procentową wykonanego zadania. Argument `Cancel` można ustawić na `True`, aby anulować metodę, która wywołała zdarzenie.  
  
> [!NOTE]
> Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: zdarzenia nie mogą mieć `Optional` lub `ParamArray` argumentów, a zdarzenia nie mają zwracanych wartości.  
  
 Zdarzenie `PercentDone` jest zgłaszane przez metodę `LongTask` klasy `Widget`. `LongTask` przyjmuje dwa argumenty: czas, który ma być wykonywany przez metodę, oraz minimalny interwał czasu przed za`LongTask` wstrzymywaniem w celu podniesienia `PercentDone` zdarzenia.  
  
#### <a name="to-raise-the-percentdone-event"></a>Aby zgłosić zdarzenie PercentDone  
  
1. Aby uprościć dostęp do właściwości `Timer` używanej przez tę klasę, Dodaj instrukcję `Imports` do górnej części sekcji deklaracji w module klasy, powyżej instrukcji `Class Widget`.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Dodaj następujący kod do klasy `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Gdy aplikacja wywołuje metodę `LongTask`, Klasa `Widget` zgłasza zdarzenie `PercentDone` co `MinimumInterval` sekund. Po powrocie zdarzenia `LongTask` sprawdza, czy argument `Cancel` został ustawiony na `True`.  
  
 W tym miejscu należy wprowadzić kilka odrzutów. Dla uproszczenia w procedurze `LongTask` założono, że wiesz, jak długo zadanie będzie wykonywane. To prawie nigdy nie dotyczy. Dzielenie zadań na fragmenty nawet rozmiaru może być trudne, a często najważniejsze znaczenie dla użytkowników to po prostu ilość czasu, która jest przekazywana przed uzyskaniem wskazującego, że coś się dzieje.  
  
 W tym przykładzie może zostać wykorzystana inna luka. Właściwość `Timer` zwraca liczbę sekund, które upłynęły od północy; w związku z tym aplikacja zostanie zablokowana, jeśli zostanie uruchomiona tuż przed północy. Bardziej staranne podejście do mierzenia czasu będzie miało wpływ na warunki graniczne, takie jak to, lub uniknąć ich całkowitego, przy użyciu właściwości, takich jak `Now`.  
  
 Teraz, gdy Klasa `Widget` może zgłaszać zdarzenia, możesz przejść do następnego przewodnika. Wskazówki [: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) pokazuje, jak za pomocą `WithEvents` skojarzyć procedurę obsługi zdarzeń ze zdarzeniem `PercentDone`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Przewodnik: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
