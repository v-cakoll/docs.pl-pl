---
title: TileBrush — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187097"
---
# <a name="tilebrush-overview"></a>TileBrush — Przegląd
<xref:System.Windows.Media.TileBrush>obiekty zapewniają dużą kontrolę nad tym, jak obszar jest malowany <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.Visual>obrazem, lub . W tym temacie <xref:System.Windows.Media.TileBrush> opisano sposób używania funkcji <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>w <xref:System.Windows.Media.VisualBrush> celu uzyskania większej kontroli nad tym, jak obszar jest malowany lub malowany.  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, warto zrozumieć, jak korzystać <xref:System.Windows.Media.ImageBrush>z <xref:System.Windows.Media.DrawingBrush>podstawowych funkcji programu , lub <xref:System.Windows.Media.VisualBrush> klasy. Aby zapoznać się z wprowadzeniem do tych typów, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>Malowanie obszaru kafelkami  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>są <xref:System.Windows.Media.VisualBrush> typami <xref:System.Windows.Media.TileBrush> obiektów. Pędzle kafelków zapewniają dużą kontrolę nad tym, jak obszar jest malowany obrazem, rysunkiem lub wizualizacją. Na przykład zamiast malować obszar pojedynczym rozciągniętym obrazem, można namalować obszar serią kafelków obrazów, które tworzą wzór.  
  
 Malowanie obszaru pędzlem do płytek obejmuje trzy składniki: zawartość, płytkę bazową i obszar wyjściowy.  
  
 ![Elementy tileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki tileBrush z pojedynczą płytką  
  
 ![Składniki płytki wyłożonej kafelkamiBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki tileBrush z TileMode płytki  
  
 Obszar wyjściowy jest obszarem malowanym, <xref:System.Windows.Shapes.Shape.Fill%2A> takim <xref:System.Windows.Shapes.Ellipse> jak <xref:System.Windows.Controls.Control.Background%2A> obszar <xref:System.Windows.Controls.Button>lub . W następnych sekcjach opisano pozostałe <xref:System.Windows.Media.TileBrush>dwa składniki programu .  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>Zawartość pędzla  
 Istnieją trzy różne <xref:System.Windows.Media.TileBrush> typy i każdy farby z innego rodzaju zawartości.  
  
- Jeśli pędzel <xref:System.Windows.Media.ImageBrush>jest , ta zawartość <xref:System.Windows.Media.ImageBrush.ImageSource%2A> jest obrazem Właściwość określa zawartość . <xref:System.Windows.Media.ImageBrush>  
  
- Jeśli pędzel <xref:System.Windows.Media.DrawingBrush>jest , ta zawartość jest rysunkiem. Właściwość <xref:System.Windows.Media.DrawingBrush.Drawing%2A> określa zawartość . <xref:System.Windows.Media.DrawingBrush>.  
  
- Jeśli pędzel <xref:System.Windows.Media.VisualBrush>jest , ta zawartość jest wizualizacją. Właściwość <xref:System.Windows.Media.VisualBrush.Visual%2A> określa zawartość . <xref:System.Windows.Media.VisualBrush>.  
  
 Można określić położenie i <xref:System.Windows.Media.TileBrush> wymiary <xref:System.Windows.Media.TileBrush.Viewbox%2A> zawartości przy użyciu właściwości, <xref:System.Windows.Media.TileBrush.Viewbox%2A> chociaż jest to typowe, aby pozostawić zestaw do wartości domyślnej. Domyślnie <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest skonfigurowany tak, aby całkowicie zawierał zawartość pędzla. Aby uzyskać więcej informacji <xref:System.Windows.Controls.Viewbox>na <xref:System.Windows.Controls.Viewbox> temat konfigurowania strony właściwości.  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>Płytka bazowa  
 A <xref:System.Windows.Media.TileBrush> wyświetla jego zawartość na kafelku podstawowym. Właściwość <xref:System.Windows.Media.TileBrush.Stretch%2A> określa <xref:System.Windows.Media.TileBrush> sposób rozciągnięcia zawartości w celu wypełnienia kafelka podstawowego. Właściwość <xref:System.Windows.Media.TileBrush.Stretch%2A> akceptuje następujące wartości, zdefiniowane przez wyliczenie: <xref:System.Windows.Media.Stretch>  
  
- <xref:System.Windows.Media.Stretch.None>: Zawartość pędzla nie jest rozciągnięta, aby wypełnić płytkę.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Zawartość pędzla jest skalowana w celu dopasowania do kafelka. Ponieważ wysokość i szerokość zawartości są skalowane niezależnie, oryginalny współczynnik proporcji zawartości może nie zostać zachowany. Oznacza to, że zawartość pędzla może być wypaczony w celu całkowitego wypełnienia kafelka wyjściowego.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Zawartość pędzla jest skalowana w taki sposób, aby całkowicie mieściła się w kafelku. Proporcje zawartości są zachowywane.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Zawartość pędzla jest skalowana w taki sposób, aby całkowicie wypełniała obszar wyjściowy przy zachowaniu oryginalnego współczynnika proporcji zawartości.  
  
 Na poniższej ilustracji <xref:System.Windows.Media.TileBrush.Stretch%2A> przedstawiono różne ustawienia.  
  
 ![Różne ustawienia rozciągania pędzla płytki](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 W poniższym przykładzie zawartość <xref:System.Windows.Media.ImageBrush> jest ustawiona tak, aby nie rozciągała się, aby wypełnić obszar wyjściowy.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Domyślnie a <xref:System.Windows.Media.TileBrush> generuje pojedynczy kafelek (kafelek podstawowy) i rozciąga ten kafelek, aby całkowicie wypełnić obszar wyjściowy. Można zmienić rozmiar i położenie kafelka <xref:System.Windows.Media.TileBrush.Viewport%2A> bazowego, ustawiając właściwości i. <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>Rozmiar kafelka bazowego  
 Właściwość <xref:System.Windows.Media.TileBrush.Viewport%2A> określa rozmiar i położenie kafelka podstawowego, a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość określa, czy jest określony przy użyciu współrzędnych bezwzględnych lub względnych. Jeśli współrzędne są względne, są one względem wielkości obszaru wyjściowego. Punkt (0,0) reprezentuje lewy górny róg obszaru wyjściowego i (1,1) reprezentuje prawy dolny róg obszaru wyjściowego. Aby określić, że <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość używa <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> współrzędnych bezwzględnych, ustaw właściwość na <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.TileBrush> różnicę w <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>danych wyjściowych między z względną a bezwzględną . Należy zauważyć, że ilustracje każdy pokazuje wzór kafelkowy; w następnej sekcji opisano sposób określania desenia kafelków.  
  
 ![Bezwzględne i względne jednostki rzutni](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 W poniższym przykładzie obraz jest używany do tworzenia kafelka o szerokości i wysokości 50%. Płytka bazowa znajduje się na (0,0) obszaru wyjściowego.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 W następnym przykładzie ustawia <xref:System.Windows.Media.ImageBrush> kafelki pikseli niezależnych od urządzenia o rozmiarze 25 na 25. Ponieważ <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> są bezwzględne, <xref:System.Windows.Media.ImageBrush> płytki są zawsze 25 na 25 pikseli, niezależnie od rozmiaru obszaru malowanego.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>Zachowanie kafli  
 A <xref:System.Windows.Media.TileBrush> tworzy desematowany deseń, gdy jego kafelek bazowy nie <xref:System.Windows.Media.TileMode.None> wypełnia całkowicie obszaru wyjściowego i określa tryb kafli inny. Gdy kafelek pędzla kafelka nie wypełnia całkowicie <xref:System.Windows.Media.TileBrush.TileMode%2A> obszaru wyjściowego, jego właściwość określa, czy kafelek bazowy powinien być duplikowany w celu wypełnienia obszaru wyjściowego, a jeśli tak, to jak należy zduplikować kafelek bazowy. Właściwość <xref:System.Windows.Media.TileBrush.TileMode%2A> akceptuje następujące wartości, zdefiniowane przez wyliczenie: <xref:System.Windows.Media.TileMode>  
  
- <xref:System.Windows.Media.TileMode.None>: Rysowany jest tylko płytka bazowa.  
  
- <xref:System.Windows.Media.TileMode.Tile>: Płytka bazowa jest rysowana, a pozostały obszar jest wypełniany przez powtórzenie kafelka bazowego w taki sposób, że prawa krawędź jednego kafelka przylega do lewej krawędzi następnego, podobnie jak na dole i na górze.  
  
- <xref:System.Windows.Media.TileMode.FlipX>: Tak <xref:System.Windows.Media.TileMode.Tile>samo jak , ale alternatywne kolumny płytek są przerzucane w poziomie.  
  
- <xref:System.Windows.Media.TileMode.FlipY>: Tak <xref:System.Windows.Media.TileMode.Tile>samo jak , ale alternatywne rzędy płytek są odwrócone pionowo.  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: Połączenie <xref:System.Windows.Media.TileMode.FlipX> i <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Na poniższej ilustracji przedstawiono różne tryby tworzenia kafelków.  
  
 ![Różne ustawienia tileBrush TileMode](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 W poniższym przykładzie obraz jest używany do malowania prostokąta o szerokości 100 pikseli i wysokości 100 pikseli. Po ustawieniu pędzla <xref:System.Windows.Media.TileBrush.Viewport%2A> został ustawiony na 0,0,0.25,0.25, płytka bazowa pędzla jest wykonana na 1/4 obszaru wyjściowego. Pędzel <xref:System.Windows.Media.TileBrush.TileMode%2A> jest ustawiony <xref:System.Windows.Media.TileMode.FlipXY>na . tak, aby wypełnił prostokąt rzędami płytek.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Tematy in jakże](brushes-how-to-topics.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
- [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Przykład pędzla Wizualnego](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
