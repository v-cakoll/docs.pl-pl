---
title: 'Instrukcje: Kontrolowanie animacji z użyciem elementów od, do i przez'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 812217a2905671567271687b974a435dd85cea47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930084"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Instrukcje: Kontrolowanie animacji z użyciem elementów od, do i przez
"Od/do/przez" lub "podstawowa animacja" tworzy przejście między dwiema wartościami docelowymi (zobacz [Omówienie animacji](animation-overview.md) dla wprowadzenia do różnych typów animacji). Aby ustawić wartości docelowe animacji podstawowej, użyj <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>właściwości, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .  W poniższej tabeli zestawiono <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, jak właściwości, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> mogą być używane razem lub oddzielnie, aby określić wartości docelowe animacji.  
  
|Określone właściwości|Zachowanie rezultatowe|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animacja postępuje z wartości określonej przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość do wartości podstawowej animowanej właściwości lub poprzedniej wartości wyjściowej animacji, w zależności od sposobu skonfigurowania poprzedniej animacji.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animacja postępuje z wartości określonej przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość do wartości określonej <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> przez właściwość.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animacja postępuje z wartości określonej przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość do wartości określonej przez sumę <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animacja postępuje z wartości podstawowej animowanej właściwości lub poprzedniej wartości wyjściowej animacji do wartości określonej przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwość.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animacja postępuje z wartości podstawowej animowanej właściwości lub poprzedniej wartości wyjściowej animacji do sumy tej wartości i wartości określonej przez <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwość.|  
  
> [!NOTE]
> Nie ustawiaj <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> i właściwości dla tej samej animacji.  
  
 Aby użyć innych metod interpolacji lub animować między więcej niż dwoma wartościami docelowymi, należy użyć animacji klatek kluczowych. Aby uzyskać więcej informacji, zobacz [Omówienie animacji klatek kluczowych](key-frame-animations-overview.md) .  
  
 Aby uzyskać informacje o stosowaniu wielu animacji do pojedynczej właściwości, zobacz [animacje kluczowych klatek — Omówienie](key-frame-animations-overview.md).  
  
 W poniższym przykładzie przedstawiono różne efekty ustawienia <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości animacji.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Przykładowe wartości docelowe od, do i według animacji](https://go.microsoft.com/fwlink/?LinkID=159988)
