---
title: 'Instrukcje: Animowanie położenia obiektu przy użyciu elementu PointAnimation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 1ef3f77e551affaa7e61d2aabf95f10c29275417
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111309"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Instrukcje: Animowanie położenia obiektu przy użyciu elementu PointAnimation
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.PointAnimation> klasy, aby animować obiekt <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje przeniesienie elipsę <xref:System.Windows.Shapes.Path> z jednego miejsca na ekranie do innego. Przykład animuje położenie <xref:System.Windows.Media.EllipseGeometry> przy użyciu <xref:System.Windows.Media.Animation.PointAnimation> animować <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [Animacja — przegląd](animation-overview.md)
- [Grafika i multimedia](index.md)
- [Grafika tematy porad](graphics-how-to-topics.md)
- [Animacja i chronometraż tematy porad](animation-and-timing-how-to-topics.md)
