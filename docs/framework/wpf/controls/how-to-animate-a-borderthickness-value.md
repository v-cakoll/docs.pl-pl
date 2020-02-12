---
title: Jak animować wartość BorderThickness
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124666"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Jak animować wartość BorderThickness
Ten przykład pokazuje, jak animować zmiany w grubości obramowania przy użyciu klasy <xref:System.Windows.Media.Animation.ThicknessAnimation>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia animowanie grubości obramowania przy użyciu <xref:System.Windows.Media.Animation.ThicknessAnimation>. W przykładzie zastosowano Właściwość <xref:System.Windows.Controls.Border.BorderThickness%2A> <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [Galeria przykładów animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Animacja — przegląd](../graphics-multimedia/animation-overview.md)
- [Animacja i chronometraż — Tematy porad](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animowanie grubości obramowania przy użyciu klatek kluczowych](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
