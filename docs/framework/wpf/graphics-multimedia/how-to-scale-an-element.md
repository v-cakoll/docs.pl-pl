---
title: 'Instrukcje: Skalowanie elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 607b3a11085f746503c1b82552f1740b49d9ef5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131706"
---
# <a name="how-to-scale-an-element"></a>Instrukcje: Skalowanie elementu
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ScaleTransform> skalowania elementu.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości przez współczynnik określisz zmiany rozmiaru elementu. Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1.5 rozciąga elementu do 150 procent jego oryginalna szerokość. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> wartość 0,5 zmniejsza wysokość elementu o 50%.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> właściwości, aby określić punkt, który jest środek operacji skalowania. Domyślnie <xref:System.Windows.Media.ScaleTransform> skupia się w momencie (0,0), który odnosi się do lewego górnego rogu prostokąta. Ma to wpływ przenoszenia elementu, a także sprawia, że wyświetlane, ponieważ po zastosowaniu <xref:System.Windows.Media.Transform>, zmień przestrzeni współrzędnych, w której znajduje się obiekt.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ScaleTransform> dwukrotnie rozmiar 50 przez 50 <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Ma wartość 0 (domyślnie) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Zwykle ustawiasz <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do środka obiekt, który jest skalowany: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 W poniższym przykładzie pokazano inny <xref:System.Windows.Shapes.Rectangle> który podwaja się rozmiar jednak to <xref:System.Windows.Media.ScaleTransform> ma wartość 25 w obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, która odnosi się do Centrum prostokąta.  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Poniższa ilustracja przedstawia różnicę między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacji. Linia kropkowana pokazuje rozmiar i położenie prostokąta przed skalowaniem.  
  
 ![Skale x 2 z różnymi punktami](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dwie operacje ScaleTransform — za pomocą identycznych wartości ScaleX i ScaleY, ale różnych centrów  
  
 Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Przegląd Przekształcenia](transforms-overview.md)
- [— Tematy porad](transformations-how-to-topics.md)
