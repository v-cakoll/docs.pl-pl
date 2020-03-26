---
title: Jak obrócić obiekt
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112066"
---
# <a name="how-to-rotate-an-object"></a>Jak obrócić obiekt
W tym przykładzie pokazano, jak obrócić obiekt. Przykład najpierw tworzy <xref:System.Windows.Media.RotateTransform> a, a <xref:System.Windows.Media.RotateTransform.Angle%2A> następnie określa jego w stopniach.  
  
 Poniższy przykład obraca <xref:System.Windows.Shapes.Polyline> obiekt o 45 stopni w lewym górnym rogu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 Właściwości <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> i właściwości <xref:System.Windows.Media.RotateTransform> określić punkt, o którym obiekt jest obrócony. Ten punkt środkowy jest wyrażony w przestrzeni współrzędnych elementu, który jest przekształcany. Domyślnie obrót jest stosowany do (0,0), który jest lewym górnym rogu obiektu do przekształcenia.  
  
 W następnym przykładzie <xref:System.Windows.Shapes.Polyline> obróci obiekt zgodnie z ruchem wskazówek zegara o 45 stopni względem punktu (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.Transform> wyniki stosowania a do dwóch obiektów.  
  
 ![Obrót 45 stopni z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dwa obiekty obracające się o 45 stopni z różnych centrów obrotowych  
  
 W <xref:System.Windows.Shapes.Polyline> poprzednich przykładach jest <xref:System.Windows.UIElement>. Po zastosowaniu <xref:System.Windows.Media.Transform> <xref:System.Windows.UIElement.RenderTransform%2A> a do <xref:System.Windows.UIElement>właściwości , można <xref:System.Windows.UIElement.RenderTransformOrigin%2A> użyć właściwości, aby <xref:System.Windows.Media.Transform> określić początek dla każdego, który stosuje się do elementu. Ponieważ <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość używa współrzędnych względnych, można zastosować przekształcenie do środka elementu, nawet jeśli nie znasz jego rozmiaru. Aby uzyskać więcej informacji i na przykład, zobacz [Określanie pochodzenia transformacji przy użyciu wartości względnych](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Transform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy in jakże](transformations-how-to-topics.md)
