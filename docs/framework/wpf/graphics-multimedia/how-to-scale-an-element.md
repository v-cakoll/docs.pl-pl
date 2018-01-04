---
title: "Jak skalować element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2bff810dc9b44b25db93c8565da27acc4f0ccc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scale-an-element"></a>Jak skalować element
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ScaleTransform> skalowania elementu.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości przez współczynnik określisz zmiany rozmiaru elementu. Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1.5 rozciąga się do 150 procent oryginalną szerokość elementu. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> wartość 0,5 zmniejsza wysokość elementu 50 procent.  
  
 Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> właściwości, aby określić punkt, który jest Centrum operacji skalowania. Domyślnie <xref:System.Windows.Media.ScaleTransform> skupia się w punkcie (0,0), która odpowiada górnego lewego rogu prostokąta. Ma to wpływ przenoszenia elementu, a także sprawia, że są większe, ponieważ po zastosowaniu <xref:System.Windows.Media.Transform>, można zmienić przestrzeni współrzędnych, w której znajduje się obiekt.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ScaleTransform> podwojenia rozmiaru 50 przez 50 <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Ma wartość 0 (wartość domyślna) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Zwykle ustawić <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do Centrum obiektu, który ma: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 W poniższym przykładzie przedstawiono innego <xref:System.Windows.Shapes.Rectangle> który jest podwójny rozmiar; jednak to <xref:System.Windows.Media.ScaleTransform> ma wartość 25 dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, które odpowiada Centrum prostokąta.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Na poniższej ilustracji przedstawiono różnice między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacji. Linia kropkowana pokazuje rozmiar i położenie okna przed skalowania.  
  
 ![Skale x 2 z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dwie operacje ScaleTransform z identycznymi wartościami ScaleX i ScaleY, ale różnych centrów  
  
 Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
