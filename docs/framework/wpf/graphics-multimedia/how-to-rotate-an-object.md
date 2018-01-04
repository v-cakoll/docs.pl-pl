---
title: "Jak obrócić obiekt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b356ef1782ec5bba4f7288644a0802f029456bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object"></a>Jak obrócić obiekt
W tym przykładzie pokazano, jak obiektu. Najpierw tworzony <xref:System.Windows.Media.RotateTransform> , a następnie określa jego <xref:System.Windows.Media.RotateTransform.Angle%2A> stopni.  
  
 Poniższy przykład obraca <xref:System.Windows.Shapes.Polyline> obiekt o 45 stopni, o jego lewym górnym rogu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> Określ punkt o tym, które jest obracana obiektu. Tego punktu centralnego jest wyrażona w układzie współrzędnych elementu, który jest przekształcany. Domyślnie obrót jest stosowany do (0,0), który jest lewego górnego rogu obiektu do przekształcania.  
  
 Obraca się w następnym przykładzie <xref:System.Windows.Shapes.Polyline> obiekt zegara 45 stopni informacje o punkcie (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Na poniższej ilustracji przedstawiono wyniki zastosowania <xref:System.Windows.Media.Transform> do dwóch obiektów.  
  
 ![obrotów 45 stopni z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dwa obiekty, które Obrót o 45 stopni z różnych obrotowej Wyśrodkowuje  
  
 <xref:System.Windows.Shapes.Polyline> w poprzednich przykładach jest <xref:System.Windows.UIElement>. Po zastosowaniu <xref:System.Windows.Media.Transform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.UIElement>, można użyć <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości w celu określenia źródła dla każdej <xref:System.Windows.Media.Transform> przeznaczonych do elementu. Ponieważ <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość używa współrzędnych względnych, możesz zastosować transformację do Centrum elementu, nawet jeśli nie znasz jego rozmiaru. Aby uzyskać więcej informacji oraz przykładem, zobacz [Określ punkt początkowy transformacji przy użyciu względne wartości](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
