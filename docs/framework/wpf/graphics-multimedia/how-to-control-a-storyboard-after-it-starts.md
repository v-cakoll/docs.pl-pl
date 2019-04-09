---
title: 'Instrukcje: Kontrolować Scenorys po uruchomieniu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161489"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Instrukcje: Kontrolować Scenorys po uruchomieniu
W tym przykładzie pokazano, jak używać kodu do kontroli <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu. Aby kontrolować scenorys w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Trigger> i <xref:System.Windows.TriggerAction> obiektów; Aby uzyskać przykład, zobacz [użyć wyzwalaczy zdarzeń, aby kontrolować Scenorys po uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Aby rozpocząć scenorysu, należy użyć jego <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody, która dystrybuuje animacjami scenorysu, właściwości, animowanie i uruchamia scenorysu.  
  
 Aby scenorysu sterowane, użyj <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody i określ **true** jako drugi parametr. Następnie można metod interakcyjnych scenorysu wstrzymać, wznowić, wyszukiwanie, Zatrzymaj, przyspieszyć, lub spowolnić scenorysu lub przejdź go do okresu wypełnienia. Oto lista metod interakcyjnych scenorysu:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Wstrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Wznawia działanie wstrzymanej scenorysu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Ustawia szybkość interaktywne scenorysu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Szuka scenorysu określonej lokalizacji.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Szuka scenorysu do określonej lokalizacji. W odróżnieniu od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody, ta operacja jest przetwarzana przed następnym znaczników.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Przesuwa scenorysu do okresu wypełnienia, jeśli taki istnieje.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zatrzymuje scenorysu.  
  
 W poniższym przykładzie kilka metod scenorysu są używane do interaktywnie kontrolować scenorys.  
  
 **Uwaga:** Aby zobaczyć przykład kontrolowanie scenorysu, za pomocą wyzwalaczy z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [użyć wyzwalaczy zdarzeń, aby kontrolować Scenorys po uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
