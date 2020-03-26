---
title: Jak pochylić element
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112027"
---
# <a name="how-to-skew-an-element"></a>Jak pochylić element
W tym przykładzie <xref:System.Windows.Media.SkewTransform> pokazano, jak użyć a pochylić element. Pochylenie, które jest również znane jako ścinanie, jest transformacją, która rozciąga przestrzeń współrzędnych w sposób nieujemny. Jednym z typowych zastosowań <xref:System.Windows.Media.SkewTransform> jest symulowanie głębi 3D w obiektach 2D.  
  
 Użyj <xref:System.Windows.Media.SkewTransform.CenterX%2A> właściwości <xref:System.Windows.Media.SkewTransform.CenterY%2A> i, aby określić <xref:System.Windows.Media.SkewTransform>punkt środkowy .  
  
 Użyj <xref:System.Windows.Media.SkewTransform.AngleX%2A> właściwości <xref:System.Windows.Media.SkewTransform.AngleY%2A> i, aby określić kąt pochylenia osi x i osi y oraz pochylić bieżący układ współrzędnych wzdłuż tych osi.  
  
 Aby przewidzieć efekt transformacji pochylenia, należy wziąć pod uwagę, że <xref:System.Windows.Media.SkewTransform.AngleX%2A> pochyla wartości osi x względem oryginalnego układu współrzędnych. W związku z <xref:System.Windows.Media.SkewTransform.AngleX%2A> tym dla osi y y obraca się o 30 stopni przez początek układu współrzędnych i pochyla wartości w x- o 30 stopni od tego początku. Podobnie, <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 pochyla wartości y kształtu o 30 stopni od początku układu współrzędnych. Należy zauważyć, że nie jest to ten sam efekt, co tłumaczenie (przenoszenie) układu współrzędnych o 30 stopni w x- lub y-.  
  
 W poniższym przykładzie stosuje się pochylenie poziome o 45 stopni do <xref:System.Windows.Shapes.Rectangle> punktu środkowego (0,0).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 W poniższym przykładzie stosuje się pochylenie poziome o 45 stopni do <xref:System.Windows.Shapes.Rectangle> punktu środkowego (25,25).  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 W poniższym przykładzie stosuje się pochylenie pionowe o 45 stopni do <xref:System.Windows.Shapes.Rectangle> punktu środkowego (25,25).  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Na poniższej ilustracji przedstawiono różne pochylenia, które są używane w tym przykładzie.  
  
 ![Przykłady skewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Trzy przykłady SkewTransform zilustrowane  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy in jakże](transformations-how-to-topics.md)
