---
title: Jak kontrolować animację z użyciem od, do i przez
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: b06df97dc57c58a01f30be2d70bfeebf104521ad
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451788"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Jak kontrolować animację z użyciem od, do i przez
"Od/do/przez" lub "podstawowa animacja" tworzy przejście między dwiema wartościami docelowymi (zobacz [Omówienie animacji](animation-overview.md) dla wprowadzenia do różnych typów animacji). Aby ustawić wartości docelowe animacji podstawowej, użyj właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  W poniższej tabeli zestawiono, jak właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> mogą być używane razem lub oddzielnie, aby określić wartości docelowe animacji.  
  
|Określone właściwości|Zachowanie rezultatowe|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animacja postępuje z wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> do wartości podstawowej animowanej właściwości lub poprzedniej wartości wyjściowej animacji, w zależności od sposobu skonfigurowania poprzedniej animacji.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animacja postępuje z wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> do wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animacja postępuje z wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> do wartości określonej przez sumę właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animacja postępuje z wartości podstawowej animowanej właściwości lub poprzedniej wartości wyjściowej animacji do wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animacja postępuje z wartości podstawowej animowanej właściwości lub poprzedniej wartości wyjściowej animacji do sumy tej wartości i wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
  
> [!NOTE]
> Nie ustawiaj właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> na tej samej animacji.  
  
 Aby użyć innych metod interpolacji lub animować między więcej niż dwoma wartościami docelowymi, należy użyć animacji klatek kluczowych. Aby uzyskać więcej informacji, zobacz [Omówienie animacji klatek kluczowych](key-frame-animations-overview.md) .  
  
 Aby uzyskać informacje o stosowaniu wielu animacji do pojedynczej właściwości, zobacz [animacje kluczowych klatek — Omówienie](key-frame-animations-overview.md).  
  
 W poniższym przykładzie przedstawiono różne efekty ustawiania właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na animacjach.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Animacja — przegląd](animation-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Przykładowe wartości docelowe od, do i według animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
