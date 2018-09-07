---
title: Jak skalować element
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 44c638b58d828e5beb0b9de5c7bb0b67c8e82d87
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097437"
---
# <a name="how-to-scale-an-element"></a>Jak skalować element
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ScaleTransform> skalowania elementu.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości przez współczynnik określisz zmiany rozmiaru elementu. Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1.5 rozciąga elementu do 150 procent jego oryginalna szerokość. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> wartość 0,5 zmniejsza wysokość elementu o 50%.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> właściwości, aby określić punkt, który jest środek operacji skalowania. Domyślnie <xref:System.Windows.Media.ScaleTransform> skupia się w momencie (0,0), który odnosi się do lewego górnego rogu prostokąta. Ma to wpływ przenoszenia elementu, a także sprawia, że wyświetlane, ponieważ po zastosowaniu <xref:System.Windows.Media.Transform>, zmień przestrzeni współrzędnych, w której znajduje się obiekt.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ScaleTransform> dwukrotnie rozmiar 50 przez 50 <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Ma wartość 0 (domyślnie) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Zwykle ustawiasz <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do środka obiekt, który jest skalowany: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 W poniższym przykładzie pokazano inny <xref:System.Windows.Shapes.Rectangle> który podwaja się rozmiar jednak to <xref:System.Windows.Media.ScaleTransform> ma wartość 25 w obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, która odnosi się do Centrum prostokąta.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Poniższa ilustracja przedstawia różnicę między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacji. Linia kropkowana pokazuje rozmiar i położenie prostokąta przed skalowaniem.  
  
 ![Skale x 2 z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dwie operacje ScaleTransform — za pomocą identycznych wartości ScaleX i ScaleY, ale różnych centrów  
  
 Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
