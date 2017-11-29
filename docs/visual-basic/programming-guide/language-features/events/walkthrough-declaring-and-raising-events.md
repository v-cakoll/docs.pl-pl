---
title: "Deklarowanie i wywoływanie zdarzeń (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf75cfba5102be5d837af385e2d3578f78a03c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Wskazówki: deklarowanie i wywoływanie zdarzeń (Visual Basic)
W tym przewodniku pokazano, jak deklarowanie i wywoływanie zdarzeń klasy o nazwie `Widget`. Po wykonaniu kroków warto przeczytać temat Pomocnika [wskazówki: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), który wskazuje, jak używać zdarzeń z `Widget` obiektów, aby podać informacje o stanie w aplikacji.  
  
## <a name="the-widget-class"></a>Klasa widżetu  
 Załóżmy na chwilę, że masz `Widget` klasy. Twoje `Widget` klasa ma metodę, która może zająć dużo czasu na wykonanie i chcesz mieć możliwość wystawione określonego rodzaju zakończenia wskaźnika.  
  
 Oczywiście można utworzyć `Widget` obiektu Wyświetla okno dialogowe procent wykonania, ale następnie użytkownik będzie zablokowany z tego okna dialogowego w każdym projekcie, w którym jest używana `Widget` klasy. Dobrym zasada projektowania obiektu jest umożliwienie aplikacji, która używa dojścia obiektu interfejsu użytkownika — celem obiekt nie ma zarządzać formularza lub okna dialogowego.  
  
 Celem `Widget` jest wykonywanie innych zadań, dlatego zaleca się dodawania `PercentDone` zdarzeń i umożliwiają tej procedury, która wywołuje `Widget`do metod obsługi czy zdarzeń i wyświetlić stan aktualizacji. `PercentDone` Zdarzeń można też podać mechanizm anulowanie zadania.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Tworzenie, przykładów kodu dla tego tematu  
  
1.  Otwórz nowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplikacji systemu Windows projektu i tworzenie formularza o nazwie `Form1`.  
  
2.  Dodawanie dwóch przycisków i etykiet do `Form1`.  
  
3.  Nazwy obiektów, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Uruchom zadanie|  
    |`Button2`|`Text`|Anuluj|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Na **projektu** menu, wybierz **Dodaj klasę** Aby dodać klasę o nazwie `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Aby zadeklarować zdarzenia dla klasy widżetu  
  
-   Użyj `Event` — słowo kluczowe, aby zadeklarować zdarzenia w `Widget` klasy. Należy pamiętać, że zdarzenie może mieć `ByVal` i `ByRef` argumenty, jako `Widget`w `PercentDone` przedstawia zdarzenia:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Gdy obiekt wywołujący odbiera `PercentDone` zdarzenia `Percent` argument zawiera procent wykonania zadania. `Cancel` Argument może być ustawiony `True` anulować metodę, która wywołała zdarzenie.  
  
> [!NOTE]
>  Argumenty zdarzenia można zadeklarować tak samo, jak argumenty procedur z następującymi wyjątkami: zdarzenia nie mogą mieć `Optional` lub `ParamArray` argumentów i zdarzeń nie ma wartości zwracanych.  
  
 `PercentDone` Zdarzenie jest wywoływane przez `LongTask` metody `Widget` klasy. `LongTask`przyjmuje dwa argumenty: czas metody udaje do realizacji pracy i czas minimalny czas, przed `LongTask` pauzy podnieść `PercentDone` zdarzeń.  
  
#### <a name="to-raise-the-percentdone-event"></a>Aby zgłosić zdarzenie PercentDone  
  
1.  Aby uprościć dostęp do `Timer` Dodaj używane przez tę klasę, właściwości `Imports` instrukcji na początku sekcji deklaracji klasy modułu, powyżej `Class Widget` instrukcji.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Dodaj następujący kod do `Widget` klasy:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Jeśli aplikacja wymaga `LongTask` metody `Widget` klasy zgłasza `PercentDone` zdarzeń co `MinimumInterval` sekund. Po powrocie z zdarzenia `LongTask` sprawdza, czy `Cancel` ustawiono argument `True`.  
  
 W tym miejscu są niezbędne kilka zrzeczenie odpowiedzialności. Dla uproszczenia `LongTask` procedurze przyjęto założenie, musisz wiedzieć z wyprzedzeniem, jak długo trwa zadania. Prawie nigdy nie jest to możliwe. Dzielenie zadań na fragmentów parzystej rozmiar może być trudne i często przyjazny dla użytkowników jest po prostu ilość czasu, jaki upływa zanim uzyskają wskazanie, że coś jest przeprowadzana.  
  
 Inna wada może mieć wykrył w tym przykładzie. `Timer` Właściwość zwraca liczbę sekund, które zostały przekazane od północy; w związku z tym aplikacja zablokowała, jeśli zostanie uruchomiony bezpośrednio przed północy. Bardziej dokładne podejście do pomiaru czasu przenoszące warunków ograniczających, takich jak ta pod uwagę lub ich uniknięcie, takich jak przy użyciu właściwości `Now`.  
  
 Teraz, gdy `Widget` klasy może wywoływać zdarzenia, można przenieść do następnego wskazówki. [Wskazówki: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) przedstawiono sposób użycia `WithEvents` do skojarzenia z obsługi zdarzeń `PercentDone` zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [Wskazówki: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
