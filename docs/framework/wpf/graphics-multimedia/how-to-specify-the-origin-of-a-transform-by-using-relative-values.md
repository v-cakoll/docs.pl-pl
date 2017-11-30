---
title: "Jak określić źródło przekształcenia przy użyciu wartości względnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec61fdedc78b785dccf2c235cd17fd20b6d5abc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Jak określić źródło przekształcenia przy użyciu wartości względnych
W tym przykładzie pokazano, jak Użyj względne wartości w celu określenia pochodzenia <xref:System.Windows.UIElement.RenderTransform%2A> do zastosowano <xref:System.Windows.FrameworkElement>.  
  
 Gdy można obracanie, skalowanie i pochylanie <xref:System.Windows.FrameworkElement> przy użyciu <xref:System.Windows.UIElement.RenderTransform%2A> właściwość, domyślne ustawienie jest stosowana transformacja lewego górnego rogu elementu. Jeśli chcesz obracanie, skalowanie i pochylanie z Centrum elementu można kompensacji ustawiając Centrum przekształcenie Centrum elementu. Rozwiązania wymaga jednak, że znasz rozmiar elementu. Prostszy sposób stosowania przekształcenia do Centrum elementu jest określenie jego <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości (0,5, 0,5), zamiast ustawiania wartości center na transformacji samego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> obracania <xref:System.Windows.Controls.Button> 45 stopni w prawo. Ponieważ przykładzie nie określa Centrum, przycisk obraca informacje o punkcie (0, 0), który jest jego lewym górnym rogu. <xref:System.Windows.Media.RotateTransform> Jest stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
 Na poniższej ilustracji przedstawiono wynik transformacji, na przykład, który jest zgodny.  
  
 ![Przycisk przekształcony przy użyciu właściwości RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Obrót w prawo 45 stopni przy użyciu właściwości RenderTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 W poniższym przykładzie również użyto <xref:System.Windows.Media.RotateTransform> obracania <xref:System.Windows.Controls.Button> 45 stopni w prawo, jednak w tym przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> przycisku (0,5, 0,5). W związku z tym obrót jest stosowany do Centrum przycisku zamiast do lewego górnego rogu.  
  
 Na poniższej ilustracji przedstawiono wynik transformacji, na przykład, który jest zgodny.  
  
 ![Przycisk przekształcony o jego center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
45 stopni przy użyciu właściwości RenderTransform RenderTransformOrigin z (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Aby uzyskać więcej informacji na temat przekształcania <xref:System.Windows.FrameworkElement> obiekty, zobacz [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 [Przekształca — omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
