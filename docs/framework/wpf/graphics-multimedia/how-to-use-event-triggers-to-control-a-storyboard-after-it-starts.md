---
title: Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: f31b1233f00147fdccde5e0816fa4839ae33d549
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183541"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu
W tym przykładzie pokazano, jak kontrolować <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu. Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard>, która dystrybuuje animacji do obiektów i właściwości, animować, a następnie uruchamia scenorysu. Jeśli nadasz <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę, określając jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, możesz obejrzeć sterowane scenorysu. Możesz następnie interaktywnie kontrolować scenorys po uruchomieniu.  
  
 Użyj następujących akcji scenorysu w połączeniu z <xref:System.Windows.EventTrigger> obiektów, aby kontrolować scenorys.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Zatrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Prowadzi scenorysu do końca okresu wypełnienia, jeśli taki istnieje.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Zatrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu zwalnianiu zasobów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto akcji musi scenorysu, aby interaktywnie kontrolować scenorys.  
  
 **Uwaga:** aby zobaczyć przykład kontrolowanie scenorysu przy użyciu kodu, zobacz [kontrolować Scenorys po jego rozpoczyna się przy użyciu jego metod interakcyjnych](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Aby uzyskać więcej przykładów, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [Kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interakcyjnych](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
