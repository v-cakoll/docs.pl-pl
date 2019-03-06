---
title: 'Instrukcje: Utwórz złożony rysunek'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: ec71fb3e2f92444d33e15da38f0c88acc715c46d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374144"
---
# <a name="how-to-create-a-composite-drawing"></a>Instrukcje: Utwórz złożony rysunek
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
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
