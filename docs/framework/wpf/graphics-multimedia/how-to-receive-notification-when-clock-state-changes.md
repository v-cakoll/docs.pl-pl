---
title: 'Porady: otrzymywać powiadomienie, gdy zegar&#39;s zmiany stanu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: d0eaca4d2a05d01e686efc15dfceebb6de4f4b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a>Porady: otrzymywać powiadomienie, gdy zegar&#39;s zmiany stanu
Zegar <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzenie po jego <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> staje się nieprawidłowy, np. gdy zegar uruchomienia lub zatrzymania. Możesz zarejestrować dla tego zdarzenia z bezpośrednio za pomocą <xref:System.Windows.Media.Animation.Clock>, lub możesz zarejestrować za pomocą <xref:System.Windows.Media.Animation.Timeline>.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> i dwa <xref:System.Windows.Media.Animation.DoubleAnimation> obiekty służą do animowania szerokość dwóch prostokątów. <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Zdarzeń służy do nasłuchiwania zmian stanu zegara.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 Na poniższej ilustracji przedstawiono różne stany animacji wprowadzili nadrzędnej osi czasu (*scenorysu*) realizowany.  
  
 ![Zegar stanów dla scenorysu z dwóch animacje](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 W poniższej tabeli przedstawiono czas, w którym *Animation1*w <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> generowane zdarzenie:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Czas (w sekundach)|1|10|19|21|30|39|  
|Stan|Aktywne|Aktywne|Zatrzymany|Aktywne|Aktywne|Zatrzymany|  
  
 W poniższej tabeli przedstawiono czas, w którym *Animation2*w <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> generowane zdarzenie:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Czas (w sekundach)|1|9|11|19|21|29|31|39|  
|Stan|Aktywne|Wypełnianie|Aktywne|Zatrzymany|Aktywne|Wypełnianie|Aktywne|Zatrzymany|  
  
 Zwróć uwagę, że *Animation1*w <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> zdarzenia generowane na 10 sekund, mimo że jego stan pozostaje <xref:System.Windows.Media.Animation.ClockState.Active>. Jest to spowodowane jego stan zmienił się na 10 sekund, ale zmieniła się z tym <xref:System.Windows.Media.Animation.ClockState.Active> do <xref:System.Windows.Media.Animation.ClockState.Filling> , a następnie z powrotem do <xref:System.Windows.Media.Animation.ClockState.Active> w tej samej osi.
