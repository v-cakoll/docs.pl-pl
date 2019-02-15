---
title: 'Instrukcje: Animuj wartość BorderThickness'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 96467fd013ddd2b2e215520384da2000aec68866
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304222"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Instrukcje: Animuj wartość BorderThickness
W tym przykładzie pokazano, jak animować zmiany grubości obramowania z wykorzystaniem <xref:System.Windows.Media.Animation.ThicknessAnimation> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje grubości obramowania przy użyciu <xref:System.Windows.Media.Animation.ThicknessAnimation>. W przykładzie użyto <xref:System.Windows.Controls.Border.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Animacja i chronometraż tematy porad](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animowanie grubości obramowania przy użyciu klatek kluczowych](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
