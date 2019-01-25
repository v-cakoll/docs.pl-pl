---
title: 'Instrukcje: Określ źródło przekształcenia przy użyciu wartości względnych'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 55007575435ada809b8fba43d08abdd2ce9ddd73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570619"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Instrukcje: Określ źródło przekształcenia przy użyciu wartości względnych
Ten przykład pokazuje, jak określić źródło przy użyciu wartości względnych <xref:System.Windows.UIElement.RenderTransform%2A> mający zastosowanie do <xref:System.Windows.FrameworkElement>.  
  
 Kiedy należy obrócić, skalowania lub pochylania <xref:System.Windows.FrameworkElement> przy użyciu <xref:System.Windows.UIElement.RenderTransform%2A> właściwość, domyślne ustawienie ma zastosowanie transformacji do lewego górnego rogu elementu. Jeśli chcesz obrócić, skalowania lub pochylić z Centrum elementu można kompensacji, ustawiając środek przekształcenia do środka elementu. Rozwiązanie wymaga jednak, że znasz rozmiar elementu. Łatwiejszy sposób stosowania transformacji do środka elementu jest określenie jego <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości (0,5, 0,5), zamiast ustawiać wartość center na przekształcenie, sam.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> wymienić <xref:System.Windows.Controls.Button> 45 stopni w prawo. Ponieważ przykładu nie określa Centrum, przycisk obraca się o punkt (0, 0), który jest jego lewego górnego rogu. <xref:System.Windows.Media.RotateTransform> Jest stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
 Poniższa ilustracja przedstawia wynik transformacji, na przykład, który następuje po.  
  
 ![Przekształcona przy użyciu RenderTransform przycisku](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
45 stopni obrót w prawo wokół przy użyciu RenderTransform właściwość  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 W poniższym przykładzie użyto również <xref:System.Windows.Media.RotateTransform> wymienić <xref:System.Windows.Controls.Button> 45 stopni zgodnie ze wskazówkami zegara, ale w tym przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> przycisku (0,5, 0,5). W rezultacie obrót zastosowano do środka przycisk, a nie do lewego górnego rogu.  
  
 Poniższa ilustracja przedstawia wynik transformacji, na przykład, który następuje po.  
  
 ![Przycisk przekształcony o jej środka](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
45 stopni przy użyciu RenderTransform właściwość RenderTransformOrigin z (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Aby uzyskać więcej informacji na temat przekształcania <xref:System.Windows.FrameworkElement> obiekty, zobacz [przekształca Przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Transform>
- [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
