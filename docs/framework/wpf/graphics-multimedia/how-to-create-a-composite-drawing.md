---
title: 'Instrukcje: Tworzenie złożonego rysunku'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132473"
---
# <a name="how-to-create-a-composite-drawing"></a>Instrukcje: Tworzenie złożonego rysunku
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingGroup> do tworzenia złożonych rysunków, łącząc wiele <xref:System.Windows.Media.Drawing> obiekty w jeden złożony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingGroup> do utworzenia złożonego rysunku <xref:System.Windows.Media.GeometryDrawing> i <xref:System.Windows.Media.ImageDrawing> obiektów. Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.  
  
 ![DrawingGroup przy użyciu wielu rysunków](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Złożony rysunek, która jest tworzona przy użyciu DrawingGroup  
  
 Należy pamiętać, szare obramowanie granice rysunku przedstawiono.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Możesz użyć <xref:System.Windows.Media.DrawingGroup> do zastosowania <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ustawienie <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, lub <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> rysunkach zawiera. Ponieważ <xref:System.Windows.Media.DrawingGroup> jest również <xref:System.Windows.Media.Drawing>, może zawierać inne <xref:System.Windows.Media.DrawingGroup> obiektów.  
  
 Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa dodatkowe <xref:System.Windows.Media.DrawingGroup> obiektów do i stosować w efektów mapy bitowej maski krycia niektóre z jego rysunki. Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.  
  
 ![DrawingGroup przy użyciu wielu rysunków](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
Złożonego rysowania, który ma wiele DrawingGroup — obiekty  
  
 Należy pamiętać, szare obramowanie granice rysunku przedstawiono.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](drawing-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [Przegląd Rysowanie obiektów](drawing-objects-overview.md)
