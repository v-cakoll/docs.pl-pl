---
title: 'Instrukcje: Otrzymaj powiadomienie po zmianie stanu zegara'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: dc3fffb88ce59ceb908d6febd2f078820513b641
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363140"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a>Instrukcje: Otrzymaj powiadomienie po zmianie stanu zegara
Zegar <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> wystąpi zdarzenie po jego <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> staje się nieprawidłowy, np. gdy zegar uruchomienia lub zatrzymania. Możesz zarejestrować dla tego zdarzenia z bezpośrednio przy użyciu <xref:System.Windows.Media.Animation.Clock>, możesz także zarejestrować przy użyciu <xref:System.Windows.Media.Animation.Timeline>.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> oraz dwóch <xref:System.Windows.Media.Animation.DoubleAnimation> obiekty służą do animować szerokość dwoma prostokątami. <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Zdarzeń służy do nasłuchiwania zmian stanu zegara.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 Na poniższej ilustracji przedstawiono różne stany animacji wprowadzili nadrzędnej osi czasu (*scenorysu*) w miarę.  
  
 ![Zegar stanów dla serii ujęć z animacjami dwóch](./media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 W poniższej tabeli przedstawiono sytuacje, w którym *Animation1*firmy <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> generowane zdarzenie:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Czas (w sekundach)|1|10|19|21|30|39|  
|Stan|Aktywne|Aktywne|Zatrzymany|Aktywne|Aktywne|Zatrzymany|  
  
 W poniższej tabeli przedstawiono sytuacje, w którym *Animation2*firmy <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> generowane zdarzenie:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Czas (w sekundach)|1|9|11|19|21|29|31|39|  
|Stan|Aktywne|Wypełnianie|Aktywne|Zatrzymany|Aktywne|Wypełnianie|Aktywne|Zatrzymany|  
  
 Należy zauważyć, że *Animation1*firmy <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> zdarzenia generowane na 10 sekund, mimo że jego stan pozostaje <xref:System.Windows.Media.Animation.ClockState.Active>. To, że jego stan jest zmieniany na 10 sekund, ale zmieniła się z <xref:System.Windows.Media.Animation.ClockState.Active> do <xref:System.Windows.Media.Animation.ClockState.Filling> , a następnie ponownie do <xref:System.Windows.Media.Animation.ClockState.Active> w tej samej osi.
