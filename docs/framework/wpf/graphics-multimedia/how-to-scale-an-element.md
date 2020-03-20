---
title: Jak skalować element
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187435"
---
# <a name="how-to-scale-an-element"></a>Jak skalować element
W tym przykładzie <xref:System.Windows.Media.ScaleTransform> pokazano, jak użyć a do skalowania elementu.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> i, aby zmienić rozmiar elementu według określonego współczynnika. Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1,5 rozciąga element do 150 procent jego pierwotnej szerokości. Wartość <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 zmniejsza wysokość elementu o 50 procent.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> właściwości <xref:System.Windows.Media.ScaleTransform.CenterY%2A> i, aby określić punkt, który jest środkiem operacji skalowania. Domyślnie a <xref:System.Windows.Media.ScaleTransform> jest wyśrodkowany w punkcie (0,0), co odpowiada lewemu górnemu rogu prostokąta. Ma to wpływ na przenoszenie elementu, a także na jego <xref:System.Windows.Media.Transform>powiększanie, ponieważ po zastosowaniu elementu , należy zmienić przestrzeń współrzędnych, w której znajduje się obiekt.  
  
 W poniższym przykładzie <xref:System.Windows.Media.ScaleTransform> użyto do podwojenia rozmiaru 50 <xref:System.Windows.Shapes.Rectangle>na 50 . Wartość <xref:System.Windows.Media.ScaleTransform> 0 (domyślna) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>i .  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> Zazwyczaj ustawia się <xref:System.Windows.Media.ScaleTransform.CenterY%2A> i na środku obiektu, który jest<xref:System.Windows.FrameworkElement.Width%2A>skalowany: <xref:System.Windows.FrameworkElement.Height%2A>( /2, /2).  
  
 W poniższym <xref:System.Windows.Shapes.Rectangle> przykładzie pokazano inny, który jest podwojony rozmiar; jednak ma <xref:System.Windows.Media.ScaleTransform> to wartość 25 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> dla <xref:System.Windows.Media.ScaleTransform.CenterY%2A>obu i , która odpowiada środkowi prostokąta.  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Na poniższej ilustracji przedstawiono różnicę między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacjami. Linia kropkowana pokazuje rozmiar i położenie prostokąta przed skalowaniem.  
  
 ![2x wagi z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dwie operacje ScaleTransform z identycznymi wartościami ScaleX i ScaleY, ale z różnymi centrami  
  
 Aby uzyskać pełną próbkę, zobacz [przykład przekształca 2-W](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy in jakże](transformations-how-to-topics.md)
