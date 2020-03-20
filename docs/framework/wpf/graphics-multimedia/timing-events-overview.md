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
ms.openlocfilehash: ee45441e9ad09c60d8b61ecce4ef08b0027ce29e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145413"
---
# <a name="timing-events-overview"></a>Przegląd Zdarzenia chronometrażu
W tym temacie opisano sposób używania <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> pięciu zdarzeń chronometrażu dostępnych na i obiektów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zrozumieć, jak tworzyć i używać animacji. Aby rozpocząć pracę z animacją, zobacz [Omówienie animacji](animation-overview.md).  
  
 Właściwości programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **Korzystanie z obiektów scenorysu** (znaczników i kodu): Można używać <xref:System.Windows.Media.Animation.Storyboard> obiektów do rozmieszczenia i dystrybucji animacji do jednego lub więcej obiektów. Na przykład zobacz [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **Przy użyciu animacji lokalnych** (tylko <xref:System.Windows.Media.Animation.AnimationTimeline> kod): Można zastosować obiekty bezpośrednio do właściwości, które animują. Na przykład zobacz [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **Za pomocą zegarów** (tylko kod): Można jawnie zarządzać tworzenie zegara i dystrybuować zegary animacji samodzielnie.  Na przykład zobacz [Animowanie właściwości przy użyciu blokady animacji](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Ponieważ można ich używać w znacznikach i kod, <xref:System.Windows.Media.Animation.Storyboard> przykłady w tym przeglądzie używają obiektów. Jednak opisane pojęcia mogą być stosowane do innych metod animowania właściwości.  
  
### <a name="what-is-a-clock"></a>Co to jest zegar?  
 Sama oś czasu nie robi nic innego, jak opisać segment czasu. Jest to <xref:System.Windows.Media.Animation.Clock> obiekt osi czasu, który wykonuje rzeczywistą pracę: utrzymuje stan czasu związanych z czasem dla osi czasu. W większości przypadków, na przykład podczas korzystania z scenokomisją, zegar jest tworzony automatycznie dla osi czasu. Można również utworzyć <xref:System.Windows.Media.Animation.Clock> jawnie przy <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> użyciu metody. Aby uzyskać <xref:System.Windows.Media.Animation.Clock> więcej informacji o obiektach, zobacz [Omówienie systemu animacji i chronometrażu](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Dlaczego warto korzystać ze zdarzeń?  
 Z wyjątkiem jednego (seek wyrównane do ostatniego znacznika), wszystkie interaktywne operacje chronometrażu są asynchroniczne. Nie ma sposobu, aby dokładnie wiedzieć, kiedy będą wykonywane. To może być problem, gdy masz inny kod, który jest zależny od operacji chronometrażu. Załóżmy, że chcesz zatrzymać oś czasu, która animowała prostokąt. Po zatrzymaniu osi czasu zmieniasz kolor prostokąta.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 W poprzednim przykładzie drugi wiersz kodu może zostać wykonany przed zatrzymaniem scenorysu. To dlatego, że zatrzymanie jest operacją asynchroniką. Informowanie osi czasu lub zegara, aby zatrzymać tworzy "żądanie zatrzymania" rodzaju, który nie jest przetwarzany, dopóki aparat rozrządu następnego zaznaczenia.  
  
 Aby wykonać polecenia po zakończeniu osi czasu, należy użyć zdarzeń chronometrażu. W poniższym przykładzie program obsługi zdarzeń jest używany do zmiany koloru prostokąta po zakończeniu odtwarzania scenorysu.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [Odbieranie powiadomień po zmianie stanu zegara](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Zdarzenia publiczne  
 Klasy <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> i zapewniają pięć zdarzeń chronometrażu. W poniższej tabeli wymieniono te zdarzenia i warunki, które je wyzwalają.  
  
|Wydarzenie|Wyzwalanie operacji interaktywnej|Inne wyzwalacze|  
|-----------|--------------------------------------|--------------------|  
|**Zakończone**|Przejdź do wypełnienia|Zegar zostanie ukończony.|  
|**Currentglobalspeedinvalidated**|Pauza, wznowienie, poszukiwanie, ustawianie prędkości, pomijanie, aby wypełnić,|Zegar cofa się, przyspiesza, uruchamia lub zatrzymuje.|  
|**Currentstateinvalidated**|Rozpocznij, przejdź do wypełnienia, zatrzymaj|Zegar uruchamia się, zatrzymuje lub wypełnia.|  
|**CurrentTimeInvalidated (Wartość bieżącaczasowa)**|Rozpocznij, szukaj, przejdź do wypełnienia, zatrzymaj|Zegar postępuje.|  
|**UsuńZamiany**|Remove||  
  
## <a name="ticking-and-event-consolidation"></a>Tykanie i konsolidacja zdarzeń  
 Podczas animowania obiektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]w programie — aparat rozrządu zarządza animacjami. Aparat rozrządu śledzi postęp czasu i oblicza stan każdej animacji. To sprawia, że wiele takich ocen przechodzi w sekundę. Te przebiegi oceny są znane jako "kleszcze".  
  
 Podczas gdy kleszcze występują często, możliwe jest, że między kleszczami wiele rzeczy się wydarzy. Na przykład oś czasu może zostać zatrzymana, uruchomiona i zatrzymana ponownie, w którym to przypadku jej bieżący stan zmieni się trzy razy. Teoretycznie zdarzenie może być podniesione wiele razy w jednym kleszczu; jednak aparat rozrządu konsoliduje zdarzenia, dzięki czemu każde zdarzenie może być wywoływane co najwyżej raz na znacznik.  
  
## <a name="registering-for-events"></a>Rejestracja na wydarzenia  
 Istnieją dwa sposoby rejestrowania zdarzeń chronometrażu: można zarejestrować się na osi czasu lub z zegarem utworzonym z osi czasu. Rejestrowanie zdarzenia bezpośrednio z zegarem jest dość proste, chociaż można to zrobić tylko z kodu. Możesz zarejestrować się do zdarzeń z osią czasu z znaczników lub kodu. W następnej sekcji opisano sposób rejestrowania zdarzeń zegara z osią czasu.  
  
<a name="registeringforclockeventswithatimeline"></a>
## <a name="registering-for-clock-events-with-a-timeline"></a>Rejestrowanie zdarzeń zegara na osi czasu  
 Chociaż oś <xref:System.Windows.Media.Animation.Timeline.Completed>czasu <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated> <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> , i zdarzenia wydają się być skojarzone z osi czasu, <xref:System.Windows.Media.Animation.Clock> rejestrowanie dla tych zdarzeń faktycznie kojarzy program obsługi zdarzeń z utworzone dla osi czasu.  
  
 Podczas rejestrowania <xref:System.Windows.Media.Animation.Timeline.Completed> się do zdarzenia na osi czasu, na przykład, jesteś <xref:System.Windows.Media.Animation.Clock.Completed> rzeczywiście mówi system do zarejestrowania się dla zdarzenia każdego zegara, który jest tworzony dla osi czasu. W kodzie należy zarejestrować się <xref:System.Windows.Media.Animation.Clock> dla tego zdarzenia przed utworzeniem dla tej osi czasu; w przeciwnym razie nie otrzymasz powiadomienia. Dzieje się to [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]automatycznie w ; analizator automatycznie rejestruje zdarzenie przed utworzeniem. <xref:System.Windows.Media.Animation.Clock>  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja i system chronometrażu](animation-and-timing-system-overview.md)
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Zachowania chronometrażu](timing-behaviors-overview.md)
