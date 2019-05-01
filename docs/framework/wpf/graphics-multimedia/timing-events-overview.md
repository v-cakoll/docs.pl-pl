---
title: Przegląd Zdarzenia chronometrażu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: 91e335f4d5adaa5279fb16805604f2e2848eeb8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002394"
---
# <a name="timing-events-overview"></a>Przegląd Zdarzenia chronometrażu
W tym temacie opisano sposób używania pięciu zdarzenia chronometrażu dostępne na <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> obiektów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy wiedzieć, jak utworzyć i używać animacji. Aby rozpocząć pracę z animacji, zobacz [Przegląd animacja](animation-overview.md).  
  
 Istnieje wiele sposobów, aby animować właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **Używanie obiektów scenorysu** (znaczników i kodu): Możesz użyć <xref:System.Windows.Media.Animation.Storyboard> obiektów Rozmieść i rozpowszechniania animacji jeden lub więcej obiektów. Aby uzyskać przykład, zobacz [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **Za pomocą lokalnego animacji** (tylko kod): Można zastosować <xref:System.Windows.Media.Animation.AnimationTimeline> obiektów bezpośrednio do właściwości one animować. Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **Za pomocą zegary** (tylko kod): Można jawnie zarządzać zegara tworzenia i dystrybucji zegary animacji, samodzielnie.  Aby uzyskać przykład, zobacz [animować właściwość przy użyciu AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Ponieważ można ich używać w kodzie znaczników oraz kod, użyj na potrzeby przykładów w tym omówieniu <xref:System.Windows.Media.Animation.Storyboard> obiektów. Jednakże pojęcia opisane mogą dotyczyć innych metod animowanie właściwości.  
  
### <a name="what-is-a-clock"></a>Co to jest zegar?  
 Oś czasu, przez siebie, naprawdę nic nie robi innych niż opisują odcinek czasu. Jest oś czasu <xref:System.Windows.Media.Animation.Clock> obiekt, który wykonuje rzeczywistą pracę: Ta funkcja obsługuje związany stan czasu wykonywania dla osi czasu. W większości przypadków, takie jak kiedy przy użyciu scenorysy zegar jest tworzona automatycznie dla osi czasu. Można również utworzyć <xref:System.Windows.Media.Animation.Clock> jawnie przy użyciu <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metody. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Animation.Clock> obiekty, zobacz [Animacja i System chronometrażu w — Przegląd](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Dlaczego warto używać zdarzeń?  
 Z wyjątkiem jednego (wyszukiwanie wyrównane do ostatniej najmniejszej), wszystkie operacje interaktywne chronometrażu są asynchroniczne. Nie ma możliwości można dowiedzieć się, dokładnie gdy będą one wykonywanie. Może to stanowić problem w przypadku innego kodu, który jest zależny od czasu wykonania operacji. Załóżmy, że chcesz zatrzymać osi czasu, który animowane prostokąta. Po zatrzymaniu osi czasu, możesz zmienić kolor prostokąta.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 W poprzednim przykładzie drugi wiersz kodu może być wykonywany przed zatrzymaniem scenorysu. To, ponieważ zatrzymywanie jest operacją asynchroniczną. Informuje osi czasu lub zegara, aby zatrzymać tworzy "żądanie zatrzymania" przedstawię który nie jest przetwarzany aż do znaczników dalej aparatu chronometrażu.  
  
 Wykonywanie polecenia po ukończeniu osi czasu, należy użyć zdarzenia chronometrażu. W poniższym przykładzie program obsługi zdarzeń służy do po scenorysu zatrzymuje odtwarzanie, zmienić kolor prostokąta.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [zmiany stanu odbierania powiadomień podczas zegara](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Zdarzenia publiczne  
 <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> obu klas zapewnia pięć zdarzenia chronometrażu. W poniższej tabeli wymieniono te zdarzenia i ze zdarzeniami wyzwalającymi je.  
  
|Zdarzenie|Wyzwalanie operacji interaktywne|Inne wyzwalacze|  
|-----------|--------------------------------------|--------------------|  
|**Ukończone**|Przejdź do wypełnienia|Zegar zostanie ukończone.|  
|**CurrentGlobalSpeedInvalidated**|Wstrzymywanie, wznawianie, wyszukiwania, ustawić szybkość współczynnik, od razu przejść do wypełnienia, Zatrzymaj|Zegar odwraca, przyspieszają działanie, uruchomienia lub zatrzymania.|  
|**CurrentStateInvalidated**|Rozpocząć, przejdź do wypełnienia, Zatrzymaj|Zegar uruchamia, zatrzymuje, lub wypełnia.|  
|**CurrentTimeInvalidated**|Rozpocznij, wyszukiwania, przejdź do wypełnienia, Zatrzymaj|Przeprowadzaj zegara.|  
|**RemoveRequested**|Usuń||  
  
## <a name="ticking-and-event-consolidation"></a>Odliczania i konsolidacji zdarzeń  
 Gdy Animowanie obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jest aparat czas, który zarządza animacji. Aparat chronometrażu śledzi postęp w czasie i oblicza stan każdej animacji. Dzięki temu takich przebiegi wersji ewaluacyjnej na sekundę. Te subskrypcje oceny są określane jako "taktów."  
  
 Gdy impulsów występuje często, istnieje możliwość, że wiele rzeczy do wykonania między taktami. Na przykład oś czasu może można zatrzymana, pracę oraz zatrzymana ponownie, w którym to przypadku swojego bieżącego stanu będzie zostały zmienione trzy razy. Teoretycznie zdarzenie może zostać podniesiony wiele razy w jednym znaczników; jednak aparat chronometrażu konsoliduje zdarzenia, tak, aby każde zdarzenie można podniesione co najwyżej raz na jednostkę skali.  
  
## <a name="registering-for-events"></a>Rejestracja nasłuchiwania zdarzeń  
 Istnieją dwa sposoby rejestrowania dla zdarzenia chronometrażu: można zarejestrować za pomocą osi czasu lub za pomocą zegara, utworzony z osi czasu. Rejestrowanie zdarzeń bezpośrednio z zegara jest dość prosta, chociaż może być przeprowadzone wyłącznie z poziomu kodu. Możesz się zarejestrować zdarzenia za pomocą osi czasu z znaczników lub innego kodu. W następnej sekcji opisano sposób rejestrowania zdarzeń zegara za pomocą osi czasu.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Rejestracja nasłuchiwania zdarzeń zegara za pomocą osi czasu  
 Mimo, że oś czasu <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, i <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> zdarzenia są wyświetlane ma zostać skojarzony z osi czasu, rejestracja dla tych zdarzeń faktycznie kojarzy program obsługi zdarzeń za pomocą <xref:System.Windows.Media.Animation.Clock> utworzone dla osi czasu.  
  
 Podczas rejestrowania się <xref:System.Windows.Media.Animation.Timeline.Completed> zdarzeń na osi czasu, na przykład, możesz teraz faktycznie informuje system rejestracji <xref:System.Windows.Media.Animation.Clock.Completed> zdarzenia każdego zegara, który jest tworzony dla osi czasu. W kodzie, należy zarejestrować dla tego zdarzenia przed <xref:System.Windows.Media.Animation.Clock> jest tworzona dla tej osi czasu; w przeciwnym razie nie będziesz otrzymywać powiadomienia. Dzieje się to automatycznie w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; analizator automatycznie rejestruje zdarzenia przed <xref:System.Windows.Media.Animation.Clock> zostanie utworzony.  
  
## <a name="see-also"></a>Zobacz także

- [Animacja i system chronometrażu — przegląd](animation-and-timing-system-overview.md)
- [Animacja — przegląd](animation-overview.md)
- [Zachowania chronometrażu — przegląd](timing-behaviors-overview.md)
