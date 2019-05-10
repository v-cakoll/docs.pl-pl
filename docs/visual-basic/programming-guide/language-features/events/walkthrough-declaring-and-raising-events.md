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
ms.openlocfilehash: fe96e54e92c09cf65c312306214e4460550c685d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626445"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Przewodnik: Deklarowanie i wywoływanie zdarzeń (Visual Basic)
W tym instruktażu pokazano, jak deklarowanie i wywoływanie zdarzeń klasy o nazwie `Widget`. Po wykonaniu kroków, warto przeczytać temat Pomocnika [instruktażu: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), który pokazuje, jak używać zdarzeń z `Widget` obiektów, aby zapewnić informacje o stanie w aplikacji.  
  
## <a name="the-widget-class"></a>Klasa elementu Widget  
 Przyjęto założenie, do momentu, w którym masz `Widget` klasy. Twoje `Widget` klasa zawiera metody, która może zająć dużo czasu wykonania i chcesz, aby aplikację, aby można było oferowane pewnego rodzaju zakończenia wskaźnika.  
  
 Oczywiście można dokonać `Widget` obiektu Wyświetla okno dialogowe procent ukończenia, ale następnie może być zapoznaniu się z tego okna dialogowego każdego projektu, w którym użyto `Widget` klasy. Dobre zasada konstrukcja obiektu funkcyjnego jest umożliwienie aplikacji, która używa na uchwyt obiektu interfejsu użytkownika — chyba że całego obiektu ma na celu zarządzanie pole formularza lub okna dialogowego.  
  
 Celem `Widget` jest do innych zadań, aby go lepiej jest dodać `PercentDone` zdarzeń, dzięki czemu procedury, która wywołuje `Widget`jego metody obsługi, zdarzeń i wyświetlania stanu aktualizacji. `PercentDone` Zdarzenia może również udostępniać mechanizm anuluje zadanie.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Aby zbudować przykład kodu, w tym temacie  
  
1. Otwórz nowy projekt aplikacji Windows Visual Basic i Utwórz formularz o nazwie `Form1`.  
  
2. Dodawanie dwóch przycisków i etykiety w celu `Form1`.  
  
3. Nazwy obiektów, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Zadanie podrzędne uruchamiania|  
    |`Button2`|`Text`|Anuluj|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. Na **projektu** menu, wybierz **Dodaj klasę** można dodać klasę o nazwie `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Aby zadeklarować zdarzenia dla klasy elementu Widget  
  
- Użyj `Event` — słowo kluczowe, aby zadeklarować zdarzenia w `Widget` klasy. Należy zauważyć, że zdarzenie może mieć `ByVal` i `ByRef` argumentów, jako `Widget`firmy `PercentDone` pokazuje zdarzenia:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Gdy obiekt wywołujący odbiera `PercentDone` zdarzenia `Percent` argument zawiera procent wykonania zadania. `Cancel` Argument może być równa `True` anulować metodę, która wywołała zdarzenie.  
  
> [!NOTE]
>  Można zadeklarować argumenty zdarzenia, tak jak argumenty procedur z następującymi wyjątkami: Zdarzenia nie może mieć `Optional` lub `ParamArray` argumentów i zdarzenia nie mają zwracanych wartości.  
  
 `PercentDone` Wydarzenie jest podniesione przez `LongTask` metody `Widget` klasy. `LongTask` przyjmuje dwa argumenty: czas metody udaje się pracy, a minimalny interwał czasowy przed `LongTask` wstrzymuje działanie, aby podnieść `PercentDone` zdarzeń.  
  
#### <a name="to-raise-the-percentdone-event"></a>Aby zgłosić zdarzenie PercentDone  
  
1. Aby uprościć dostęp do `Timer` Dodaj właściwość używana przez tę klasę `Imports` instrukcji na górze sekcji deklaracji klasy modułu, powyżej `Class Widget` instrukcji.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Dodaj następujący kod do `Widget` klasy:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Gdy Twoja aplikacja wywołuje `LongTask` metody `Widget` klasy wywołuje `PercentDone` zdarzeń co `MinimumInterval` sekund. Po powrocie z zdarzenia `LongTask` sprawdza, czy `Cancel` argumentów została ustawiona na `True`.  
  
 Kilka zastrzeżenia są niezbędne, w tym miejscu. Dla uproszczenia `LongTask` procedurze przyjęto założenie, wcześniej wiadomo jak długo potrwa zadania. Prawie nigdy nie jest to możliwe. Podzielenie zadania na fragmenty o rozmiarze nawet może być trudne, a często najistotniejszych dla użytkowników jest po prostu ilość czasu, jaki upływa zanim staną się wskazanie, że coś, co dzieje się.  
  
 W tym przykładzie może mieć wykrył innego wady. `Timer` Właściwość zwraca liczbę sekund, które upłynęły od północy; w związku z tym, aplikacja zablokowania, gdy zostanie uruchomiona po prostu wcześniejszą niż północ. Bardziej dokładnej podejście do pomiaru czasu przenoszące warunków ograniczających, takie jak to pod uwagę lub uniknąć je całkowicie, przy użyciu właściwości, takich jak `Now`.  
  
 Teraz, gdy `Widget` klasy może wywoływać zdarzenia, można przenieść do poniższych wskazówek. [Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) pokazuje sposób użycia `WithEvents` skojarzyć program obsługi zdarzeń za pomocą `PercentDone` zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
