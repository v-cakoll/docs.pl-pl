---
title: 'Instrukcje: Obracanie elementu w miejscu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947256"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Instrukcje: Obracanie elementu w miejscu
Ten przykład pokazuje, jak do uczynienia elementu Uruchom za pomocą <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Następujący przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu. W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform>. Aby element pokrętła w miejscu, w przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość elementu w punkcie (0,5, 0,5).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Aby uzyskać pełny przykład, który zawiera więcej przykładów transformacji, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
