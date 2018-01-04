---
title: "Przegląd Zdarzenia chronometrażu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79669bdc4b5f9cfb8bdac92efa07e932cc14ac57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="timing-events-overview"></a>Przegląd Zdarzenia chronometrażu
W tym temacie opisano sposób używania pięciu zdarzenia czasowe na <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> obiektów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy wiedzieć, jak utworzyć i użyć animacji. Aby rozpocząć pracę z animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Istnieje wiele sposobów w celu animowania właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **Przy użyciu obiektów scenorysu** (znaczników i kodu): można użyć <xref:System.Windows.Media.Animation.Storyboard> obiektów rozmieszczania i rozpowszechniania animacji co najmniej jeden obiekt. Na przykład zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Przy użyciu lokalnego animacje** (tylko kod): można zastosować <xref:System.Windows.Media.Animation.AnimationTimeline> bezpośrednio na ich animowania właściwości obiektów. Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **Przy użyciu zegary** (tylko kod): jawnie można zarządzać zegara tworzenia i rozpowszechniania zegary animacji samodzielnie.  Na przykład zobacz [animować właściwości przy użyciu AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Ponieważ mogą ich używać w kodzie znaczników oraz kod, użyj przykłady w tym omówieniu <xref:System.Windows.Media.Animation.Storyboard> obiektów. Jednak pojęcia opisane może odnosić się do innych metod animowania właściwości.  
  
### <a name="what-is-a-clock"></a>Co to jest zegar?  
 Oś czasu, przez siebie, faktycznie nic nie robi innych niż opisano segment czasu. Jest na osi czasu <xref:System.Windows.Media.Animation.Clock> obiekt, który wykonuje rzeczywistą pracę: Ta funkcja obsługuje związany z czasem stan czasu wykonywania dla osi czasu. W większości przypadków, np. po użyciu scenorys zegar jest tworzona automatycznie dla osi czasu. Można również utworzyć <xref:System.Windows.Media.Animation.Clock> jawnie przy użyciu <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metody. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Animation.Clock> obiekty, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Dlaczego warto używać zdarzenia?  
 Z wyjątkiem jednego (wyszukiwanie wyrównany do ostatniego znaczników), wszystkie operacje interaktywne chronometrażu są asynchroniczne. Nie istnieje sposób można dowiedzieć dokładnie gdy będą one wykonywanie. Jeśli masz innego kodu, który jest zależny od czasu operacji, które może być problem. Załóżmy, że chcesz zatrzymać osi czasu, który animowany prostokąta. Po zatrzymaniu osi czasu, można zmienić kolor prostokąta.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 W poprzednim przykładzie drugi wiersz kodu może wykonać przed zatrzymaniem scenorysu. To, ponieważ operacja asynchroniczna jest zatrzymywana. Informuje osi czasu lub zegara, aby zatrzymać tworzy "żądanie zatrzymania" typu nie jest przetwarzany do aparatu chronometrażu dalej znaczników.  
  
 Do wykonania polecenia, po zakończeniu osi czasu, użyj zdarzenia czasowe. W poniższym przykładzie program obsługi zdarzeń służy do po scenorysu zatrzymuje odtwarzanie zmienić kolor prostokąta.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Aby uzyskać bardziej szczegółowy przykład, zobacz [zmian stanu odbierania powiadomień po na zegarze](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Zdarzenia publiczne  
 <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> klasy zarówno Podaj pięć zdarzenia czasowe. W poniższej tabeli wymieniono te zdarzeń i warunków, które mogą powodować ich.  
  
|Zdarzenie|Wyzwalanie operacji interakcyjne|Inne wyzwalacze|  
|-----------|--------------------------------------|--------------------|  
|**Ukończone**|Przejdź do wypełnienia|Zegar zostanie ukończone.|  
|**CurrentGlobalSpeedInvalidated**|Wstrzymać, wznowić, wyszukiwania, ustaw stosunek szybkości, przejdź do wypełnienia, Zatrzymaj|Zegar odwraca, przyspiesza, uruchomienia lub zatrzymania.|  
|**CurrentStateInvalidated**|Rozpocząć, przejdź do wypełnienia, Zatrzymaj|Zegar uruchamia, zatrzymuje, lub wypełnia.|  
|**CurrentTimeInvalidated**|Rozpocznij, wyszukiwania, przejdź do wypełnienia, Zatrzymaj|Realizowany zegara.|  
|**RemoveRequested**|Usuń||  
  
## <a name="ticking-and-event-consolidation"></a>Materacy i zdarzenia konsolidacji  
 Gdy Animowanie obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], to aparat czasu, która zarządza animacji. Aparat chronometrażu śledzi postępu czasu i oblicza stan każdego animacji. Takie przebiegów obliczania pozwala na sekundę. Te przebiegów obliczania są określane jako "znaczników."  
  
 Gdy znaczniki występuje często, istnieje możliwość, że wiele różnych czynności między taktami. Na przykład osi czasu może być zatrzymana, uruchamiania i zatrzymywania ponownie, w takim przypadku swojego bieżącego stanu będzie zostały zmienione trzy razy. Teoretycznie może być zdarzenia wiele razy w jednym znaczników; jednak aparat chronometrażu konsoliduje zdarzenia, tak aby każdego zdarzenia można uruchamiany co najwyżej raz na osi.  
  
## <a name="registering-for-events"></a>Rejestracja nasłuchiwania zdarzeń  
 Istnieją dwa sposoby, aby zarejestrować dla zdarzenia czasowe: możesz zarejestrować z osi czasu lub z zegarem utworzone na podstawie na osi czasu. Rejestrowanie na potrzeby zdarzenia bezpośrednio z zegarem jest bardzo prosta, chociaż można wykonać tylko z kodu. Możesz rejestrować zdarzeń o osi czasu z kodu znaczników lub kodu. W następnej sekcji opisano sposób rejestrowania zdarzeń zegara o osi czasu.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Rejestrowanie zdarzeń zegara o osi czasu  
 Mimo że osi czasu <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, i <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> zdarzeń mogą być skojarzone z osi czasu, rejestracja dla tych zdarzeń faktycznie skojarzony program obsługi zdarzeń z <xref:System.Windows.Media.Animation.Clock> utworzone dla osi czasu.  
  
 Gdy zarejestrujesz <xref:System.Windows.Media.Animation.Timeline.Completed> zdarzeń na osi czasu, na przykład możesz jest rzeczywiście informuje system, można zarejestrować na potrzeby <xref:System.Windows.Media.Animation.Clock.Completed> zdarzenia każdego zegara, który jest tworzony dla osi czasu. W kodzie, należy zarejestrować dla tego zdarzenia przed <xref:System.Windows.Media.Animation.Clock> jest tworzona dla tej osi czasu; w przeciwnym razie nie będzie otrzymywać powiadomienia. Dzieje się to automatycznie w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; analizator automatycznie rejestruje zdarzenia przed <xref:System.Windows.Media.Animation.Clock> jest tworzony.  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja i system chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Zachowania chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
