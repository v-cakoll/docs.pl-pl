---
title: Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186701"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu

W tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> pokazano, jak kontrolować po jego uruchomieniu. Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> za [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pomocą <xref:System.Windows.Media.Animation.BeginStoryboard>, użyj , który rozprowadza animacje do obiektów i właściwości, które animują, a następnie uruchamia scenorysu. Jeśli nadasz <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę, określając <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> jej właściwość, można uczynić ją kontrolowalnym scenorysu. Następnie można interaktywnie sterować scenorysu po jego uruchomieniu.

Użyj następujących akcji scenorysu wraz z <xref:System.Windows.EventTrigger> obiektami, aby kontrolować scenorys.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorys.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia wstrzymany scenorys.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorys do końca okresu wypełnienia, jeśli go ma.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Zatrzymuje scenorys.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorys, zwalniając zasoby.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto kontrolalnych akcji scenorysu do interaktywnego sterowania scenorysu.

> [!NOTE]
> Aby wyświetlić przykład kontrolowania scenorysu przy użyciu kodu, zobacz [Sterowanie scenorysem po uruchomieniu przy użyciu metod interaktywnych.](how-to-control-a-storyboard-after-it-starts.md)

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Aby uzyskać dodatkowe przykłady, zobacz [Przykładowa galeria animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interakcyjnych](how-to-control-a-storyboard-after-it-starts.md)
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Scenorysy](storyboards-overview.md)
