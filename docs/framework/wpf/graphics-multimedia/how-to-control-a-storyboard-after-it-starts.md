---
title: Jak kontrolować scenorys po uruchomieniu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 2407de5029007748de691a3020078b1241b02fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561465"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Jak kontrolować scenorys po uruchomieniu
W tym przykładzie przedstawiono użycie kodu w celu sterowania <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu. Aby kontrolować scenorysu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Trigger> i <xref:System.Windows.TriggerAction> obiektów, na przykład sprawdzić, [Użyj wyzwalacze zdarzeń, aby kontrolować scenorysu po jego uruchomieniu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Aby uruchomić scenorysu, należy użyć jego <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodę, która dystrybuuje scenorysu animacji właściwości animacji i uruchamia scenorysu.  
  
 Aby wprowadzić sterowane scenorysu, należy użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> — metoda i określ **true** jako drugiego parametru. Następnie można metody interakcyjne scenorysu wstrzymać, wznowić, wyszukiwanie, Zatrzymaj, przyspieszyć, lub spowolnić scenorysu lub jego dojściu do okresu. Oto lista metod interakcyjne scenorysu:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Wstrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Wznawia działanie wstrzymanej scenorysu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Ustawia szybkość interakcyjne scenorysu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Stara scenorysu określonej lokalizacji.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Stara scenorysu do określonej lokalizacji. W odróżnieniu od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody, ta operacja jest przetwarzana przed następnym znaczników.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Przesuwa scenorys z okresu, jeśli istnieje.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Przestaje scenorysu.  
  
 W poniższym przykładzie kilka metod scenorysu są używane do sterowania interaktywnego scenorysu.  
  
 **Uwaga:** aby zobaczyć przykładowy kontrolowanie scenorysu przy użyciu wyzwalaczy z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [wyzwalacze zdarzeń używana do sterowania scenorysu po jego uruchomieniu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
