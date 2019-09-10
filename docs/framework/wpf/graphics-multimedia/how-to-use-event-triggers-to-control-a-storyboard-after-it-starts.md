---
title: 'Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855850"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń

Ten przykład pokazuje, <xref:System.Windows.Media.Animation.Storyboard> jak kontrolować po rozpoczęciu. Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> od przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programu, <xref:System.Windows.Media.Animation.BeginStoryboard>należy użyć, który dystrybuuje animacje do obiektów i właściwości, które są animowane, a następnie uruchamia scenorys. W przypadku nadania <xref:System.Windows.Media.Animation.BeginStoryboard> nazwy przez określenie jej <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości można ją przetworzyć w scenorysie. Następnie możesz interaktywnie kontrolować scenorys po jego uruchomieniu.

Użyj następujących działań scenorysu razem z <xref:System.Windows.EventTrigger> obiektami, aby sterować scenorysem.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorys.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia wstrzymanie scenorysu.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorys do końca jego okresu wypełniania, jeśli go zawiera.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Powoduje zatrzymanie scenorysu.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorys, zwalniając zasoby.

## <a name="example"></a>Przykład

W poniższym przykładzie są stosowane kontrolowane akcje scenorysu do interaktywnej kontroli scenorysu.

> [!NOTE]
> Aby zobaczyć przykład kontrolowania scenorysu przy użyciu kodu, zobacz [kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interaktywnych](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Więcej przykładów można znaleźć w [galerii przykładowej animacji](https://go.microsoft.com/fwlink/?LinkID=159969).

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
