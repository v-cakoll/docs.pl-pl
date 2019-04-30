---
title: 'Instrukcje: Animowanie właściwości przy użyciu elementu AnimationClock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 4fa9efc593461d26eabaee5e2f62c1a17da1b543
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761016"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Instrukcje: Animowanie właściwości przy użyciu elementu AnimationClock
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.Clock> obiektów, aby animować właściwości.  
  
 Istnieją trzy sposoby, aby animować właściwości zależności:  
  
- Tworzenie <xref:System.Windows.Media.Animation.AnimationTimeline> i skojarz go z tej właściwości przy użyciu <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Użyj obiektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody do stosowania pojedynczej <xref:System.Windows.Media.Animation.AnimationTimeline> do właściwości docelowej.  
  
- Tworzenie <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> i zastosować je do właściwości.  
  
 <xref:System.Windows.Media.Animation.Storyboard> obiekty i <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody umożliwiają animować właściwości bez bezpośrednio tworzenie i rozpowszechnianie zegary (przykłady można znaleźć [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md) i [animować właściwości bez Za pomocą scenorysu](how-to-animate-a-property-without-using-a-storyboard.md)); zegary są tworzone i dystrybucji dla Ciebie automatycznie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do dwóch podobnych właściwości.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Aby uzyskać przykład pokazujący sposób interaktywnie kontrolować <xref:System.Windows.Media.Animation.Clock> po jego uruchomieniu, zobacz [interaktywnie kontrolować zegar](how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md)
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
