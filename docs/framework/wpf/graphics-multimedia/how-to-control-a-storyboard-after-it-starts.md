---
title: 'Instrukcje: Kontrolowanie scenorysu po rozpoczęciu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855866"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Instrukcje: Kontrolowanie scenorysu po rozpoczęciu

Ten przykład pokazuje, <xref:System.Windows.Media.Animation.Storyboard> jak używać kodu do sterowania po jego uruchomieniu. Aby kontrolować scenorys w programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Trigger> obiektów <xref:System.Windows.TriggerAction> i, aby zapoznać się z przykładem, zobacz [Używanie wyzwalaczy zdarzeń do kontrolowania scenorysu po jego uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

Aby uruchomić scenorys, należy użyć jego <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody, która dystrybuuje animacje scenorysu do właściwości, które są animowane i uruchamia scenorys.

Aby można było sterować scenorysem, należy użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody i określić **wartość true** jako drugi parametr. Następnie możesz użyć interaktywnych metod, aby wstrzymywać, wznawiać, wyszukiwać, zatrzymywać, przyspieszyć lub spowalniać scenorys lub przełączać się do jego okresu wypełniania. Poniżej znajduje się lista interaktywnych metod scenorysu:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Wstrzymuje scenorys.

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Wznawia wstrzymanie scenorysu.

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Ustawia szybkość interaktywną scenorysu.

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Wyszukuje scenorys w określonej lokalizacji.

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Szuka scenorysu do określonej lokalizacji. W przeciwieństwie <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> do metody, ta operacja jest przetwarzana przed następnym znacznikiem.

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Przesuwa scenorys do jego okresu wypełnienia, jeśli go zawiera.

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Powoduje zatrzymanie scenorysu.

W poniższym przykładzie kilka metod scenorysu służy do interaktywnego sterowania scenorysem.

> [!NOTE]
> Aby zobaczyć przykład kontrolowania scenorysu przy użyciu wyzwalaczy z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [Używanie wyzwalaczy zdarzeń do kontrolowania scenorysu po jego uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

## <a name="example"></a>Przykład

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>Zobacz także

- [Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
