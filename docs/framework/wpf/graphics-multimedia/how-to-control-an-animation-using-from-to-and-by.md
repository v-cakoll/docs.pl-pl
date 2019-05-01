---
title: 'Instrukcje: Kontrolowanie animacji z użyciem elementów od, do i przez'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 56522ee5bd4391e43c261558b2fa622234c9ea3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008788"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Instrukcje: Kontrolowanie animacji z użyciem elementów od, do i przez
"Od/do/przez" lub "podstawowa Animacja" tworzy przejście między dwiema wartościami target (zobacz [Przegląd animacja](animation-overview.md) wprowadzenie do różnych rodzajów animacji). Aby ustawić wartości docelowe podstawowa Animacja, użyj jej <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.  W poniższej tabeli przedstawiono sposób, w jaki <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości, które mogą być używane razem lub oddzielnie, aby ustalić docelowy animacji wartości.  
  
|Określono właściwości|Wynikowe zachowania|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|W miarę animacji z wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości do podstawowej wartości właściwości, jest animowany lub poprzedniej animacji danych wyjściowych wartość, w zależności od sposobu skonfigurowania poprzedniej animacji.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|W miarę animacji z wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|W miarę animacji z wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość określoną przez sumę <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animacja w miarę od wartości bazowej animowany właściwości lub poprzedniej animacji danych wyjściowych wartość na wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|W miarę animacji z podstawową wartość właściwości jest animowany lub poprzedniej animacji danych wyjściowych wartość sumę wartości i wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.|  
  
> [!NOTE]
>  Nie należy ustawiać zarówno <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwość w tej samej animacji.  
  
 Aby skorzystać z innych metod interpolacji lub animować między więcej niż dwóch wartości docelowych, należy użyć animacji klatek kluczowych. Zobacz [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md) Aby uzyskać więcej informacji.  
  
 Aby dowiedzieć się, jak stosowanie wielu animacji do pojedynczej właściwości, zobacz [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).  
  
 W poniższym przykładzie pokazano różne efekty ustawienia <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości animacji.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Od, do i przez przykład wartości docelowej animacji](https://go.microsoft.com/fwlink/?LinkID=159988)
