---
title: 'Instrukcje: Określanie, czy oś czasu ma być automatycznie odtwarzana od końca'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024667"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="f0aa0-102">Instrukcje: Określanie, czy oś czasu ma być automatycznie odtwarzana od końca</span><span class="sxs-lookup"><span data-stu-id="f0aa0-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="f0aa0-103">Oś czasu <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość określa, czy odtwarzany w odwrotnej kolejności po jej zakończeniu iteracji do przodu.</span><span class="sxs-lookup"><span data-stu-id="f0aa0-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="f0aa0-104">W poniższym przykładzie pokazano kilka animacji przy użyciu identycznych czas trwania i wartości docelowych, ale z różnymi <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f0aa0-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="f0aa0-105">Aby zademonstrować sposób, w jaki <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość zachowuje się z różnymi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ustawienia, niektórych animacji są skonfigurowane do powtarzania.</span><span class="sxs-lookup"><span data-stu-id="f0aa0-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="f0aa0-106">Ostatnie pokazuje animacji jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość pracuje zagnieżdżonych osi czasu.</span><span class="sxs-lookup"><span data-stu-id="f0aa0-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0aa0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0aa0-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
