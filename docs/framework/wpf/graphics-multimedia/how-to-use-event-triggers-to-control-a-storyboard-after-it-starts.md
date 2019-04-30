---
title: 'Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d444349f8bc9236e1d15f484f35b1326c77e2425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769294"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń
W tym przykładzie pokazano, jak kontrolować <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu. Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard>, która dystrybuuje animacji do obiektów i właściwości, animować, a następnie uruchamia scenorysu. Jeśli nadasz <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę, określając jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, możesz obejrzeć sterowane scenorysu. Możesz następnie interaktywnie kontrolować scenorys po uruchomieniu.  
  
 Użyj następujących akcji scenorysu w połączeniu z <xref:System.Windows.EventTrigger> obiektów, aby kontrolować scenorys.  
  
- <xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorysu.  
  
- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.  
  
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.  
  
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorysu do końca okresu wypełnienia, jeśli taki istnieje.  
  
- <xref:System.Windows.Media.Animation.StopStoryboard>: Zatrzymuje scenorysu.  
  
- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu zwalnianiu zasobów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto akcji musi scenorysu, aby interaktywnie kontrolować scenorys.  
  
 **Uwaga:** Aby zapoznać się przykładem kontrolowanie scenorysu przy użyciu kodu, zobacz [kontrolować Scenorys po jego rozpoczyna się przy użyciu jego metod interakcyjnych](how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Aby uzyskać więcej przykładów, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interakcyjnych](how-to-control-a-storyboard-after-it-starts.md)
- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
