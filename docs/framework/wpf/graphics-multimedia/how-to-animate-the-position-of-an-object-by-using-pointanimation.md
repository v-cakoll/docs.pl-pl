---
title: 'Instrukcje: Animuj położenie obiektu z wykorzystaniem PointAnimation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: db0551ba7c22e6c13ef2875e5f4ba681fc6df14d
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304794"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Instrukcje: Animuj położenie obiektu z wykorzystaniem PointAnimation
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.PointAnimation> klasy, aby animować obiekt <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje przeniesienie elipsę <xref:System.Windows.Shapes.Path> z jednego miejsca na ekranie do innego. Przykład animuje położenie <xref:System.Windows.Media.EllipseGeometry> przy użyciu <xref:System.Windows.Media.Animation.PointAnimation> animować <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Grafika tematy porad](graphics-how-to-topics.md)
- [Animacja i chronometraż tematy porad](animation-and-timing-how-to-topics.md)
