---
title: Jak obrócić element w miejscu
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112079"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Jak obrócić element w miejscu
W tym przykładzie pokazano, jak <xref:System.Windows.Media.RotateTransform> dokonać <xref:System.Windows.Media.Animation.DoubleAnimation>spin elementu przy użyciu a i a .  
  
 Poniższy przykład stosuje <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu. W przykładzie <xref:System.Windows.Media.Animation.DoubleAnimation> użyto a <xref:System.Windows.Media.RotateTransform.Angle%2A> do <xref:System.Windows.Media.RotateTransform>animowania pliku . Aby element obracać w miejscu, <xref:System.Windows.UIElement.RenderTransformOrigin%2A> w przykładzie ustawia właściwość elementu do punktu (0,5, 0,5).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Aby uzyskać pełną próbkę, która zawiera więcej przykładów transformacji, zobacz [Przykład przekształcania 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
