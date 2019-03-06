---
title: 'Instrukcje: Obróć obiekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 49de419f22980ab9101c388079e0348b4c1113f4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360371"
---
# <a name="how-to-rotate-an-object"></a>Instrukcje: Obróć obiekt
Ten przykład pokazuje, jak obrócić obiekt. W przykładzie najpierw jest tworzony <xref:System.Windows.Media.RotateTransform> , a następnie określa jego <xref:System.Windows.Media.RotateTransform.Angle%2A> w stopniach.  
  
 Poniższy przykład obraca <xref:System.Windows.Shapes.Polyline> obiektu 45 stopni, o jego lewego górnego rogu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> Określ punkt o tym, które obrotu obiektu. Ten punkt środkowy jest wyrażona w układzie współrzędnych elementu, który jest przekształcany. Domyślnie obrót jest stosowany do (0,0), czyli lewego górnego rogu obiektu do przekształcenia.  
  
 Obraca się w następnym przykładzie <xref:System.Windows.Shapes.Polyline> obiektu do ruchu wskazówek zegara 45 stopni, o punkt (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Na poniższej ilustracji przedstawiono wyniki zastosowania <xref:System.Windows.Media.Transform> do dwóch obiektów.  
  
 ![Obroty 45 stopni z różnymi punktami](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dwa obiekty, które Obrót o 45 stopni za pośrednictwem różnych obrotowych centrów  
  
 <xref:System.Windows.Shapes.Polyline> w poprzednich przykładach <xref:System.Windows.UIElement>. Po zastosowaniu <xref:System.Windows.Media.Transform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.UIElement>, możesz użyć <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości w celu określenia początek dla każdego <xref:System.Windows.Media.Transform> przeznaczonych do elementu. Ponieważ <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość używa współrzędnych względnych, można zastosować przekształcenie do środka elementu, nawet jeśli nie znasz jego rozmiaru. Aby uzyskać więcej informacji i przykład zobacz [Określ źródło przekształcenia przy użyciu wartości względnych](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Transform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy z instrukcjami](transformations-how-to-topics.md)
