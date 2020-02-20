---
title: Jak obrócić element w miejscu
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452795"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Jak obrócić element w miejscu
Ten przykład pokazuje, jak utworzyć element pokrętła przy użyciu <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Poniższy przykład stosuje <xref:System.Windows.Media.RotateTransform> do właściwości <xref:System.Windows.UIElement.RenderTransform%2A> elementu. W przykładzie zastosowano <xref:System.Windows.Media.Animation.DoubleAnimation>, aby animować <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>. Aby można było obrócić element, przykład ustawia właściwość <xref:System.Windows.UIElement.RenderTransformOrigin%2A> elementu na punkt (0,5, 0,5).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Aby uzyskać pełną próbkę, która zawiera więcej przykładów transformacji, zobacz przykład przekształceń [2-D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Zobacz też

- [Animacja — przegląd](animation-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
