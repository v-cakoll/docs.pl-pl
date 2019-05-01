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
ms.openlocfilehash: a610acfef416a978ab8ecd9a561a135ecf3611cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973753"
---
# <a name="tilebrush-overview"></a>TileBrush — Przegląd
<xref:System.Windows.Media.TileBrush> obiekty umożliwiają z dużym stopniem kontrolę nad jak obszar jest malowane z obrazem, <xref:System.Windows.Media.Drawing>, lub <xref:System.Windows.Media.Visual>. W tym temacie opisano sposób użycia <xref:System.Windows.Media.TileBrush> funkcje, aby uzyskać większą kontrolę nad jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, lub <xref:System.Windows.Media.VisualBrush> Malowanie obszaru.  

<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, warto zrozumieć sposób korzystania z podstawowych funkcji <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, lub <xref:System.Windows.Media.VisualBrush> klasy. Aby zapoznać się z wprowadzeniem do tych typów, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Malowanie obszaru za pomocą kafelków  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, są <xref:System.Windows.Media.VisualBrush> typów <xref:System.Windows.Media.TileBrush> obiektów. Pędzle kafelka zapewnia dużą kontrolę nad jak obszar jest malowany obrazów, rysowania lub wizualizacji danych. Na przykład zamiast tylko Malowanie obszaru za pomocą pojedynczego obrazu rozciągnięty, można malować obszar za pomocą szeregu Kafelki obrazów, tworzące wzorzec.  
  
 Malowanie obszaru za pomocą pędzla wzoru obejmuje trzy składniki: zawartość, podstawowy Kafelek i obszaru wyjściowego.  
  
 ![Składniki TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki TileBrush z jednym kafelkiem  
  
 ![Składniki fragmentacji TileBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki TileBrush z TileMode kafelka  
  
 Obszar danych wyjściowych to obszar, jest malowane, takich jak <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> lub <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. W kolejnych sekcjach opisano dwa składniki programu <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>Zawartość pędzla  
 Istnieją trzy różne rodzaje <xref:System.Windows.Media.TileBrush> i maluje każdej z innym typem zawartości.  
  
- Jeśli jest pędzel <xref:System.Windows.Media.ImageBrush>, ta zawartość jest obrazem <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwość określa zawartości <xref:System.Windows.Media.ImageBrush>.  
  
- Jeśli jest pędzel <xref:System.Windows.Media.DrawingBrush>, ta zawartość jest rysowania. <xref:System.Windows.Media.DrawingBrush.Drawing%2A> Właściwość określa zawartości <xref:System.Windows.Media.DrawingBrush>.  
  
- Jeśli jest pędzel <xref:System.Windows.Media.VisualBrush>, ta zawartość jest wizualizacji. <xref:System.Windows.Media.VisualBrush.Visual%2A> Właściwość określa zawartości <xref:System.Windows.Media.VisualBrush>.  
  
 Można określić położenie i wymiary <xref:System.Windows.Media.TileBrush> zawartości przy użyciu <xref:System.Windows.Media.TileBrush.Viewbox%2A> właściwości, mimo że często, aby pozostawić <xref:System.Windows.Media.TileBrush.Viewbox%2A> ustawiony na wartość domyślną. Domyślnie <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest skonfigurowany do całkowicie zawierają zawartość pędzla. Aby uzyskać więcej informacji o konfigurowaniu <xref:System.Windows.Controls.Viewbox>, zobacz <xref:System.Windows.Controls.Viewbox> stronę właściwości.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>Podstawowy Kafelek  
 A <xref:System.Windows.Media.TileBrush> projektów jego zawartość na podstawowy Kafelek. <xref:System.Windows.Media.TileBrush.Stretch%2A> Właściwości kontrolki jak <xref:System.Windows.Media.TileBrush> zawartości jest rozciągany tak, aby wypełnić podstawowy Kafelek. <xref:System.Windows.Media.TileBrush.Stretch%2A> Właściwość akceptuje następujące wartości, zdefiniowane przez <xref:System.Windows.Media.Stretch> wyliczenia:  
  
- <xref:System.Windows.Media.Stretch.None>: Pędzel zawartość nie jest rozciągana do wypełnienia kafelka.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Pędzel zawartość jest skalowana do rozmiaru kafelka. Ponieważ wysokość i szerokość zawartość jest skalowana niezależnie, oryginalny współczynnik proporcji zawartości mogą nie zostać zachowane. Oznacza to, że zawartość pędzla może zniekształcenia Aby całkowicie wypełnić kafelka dane wyjściowe.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Pędzel zawartość jest skalowana tak, aby zmieścił się całkowicie we fragmencie. Zawartość proporcje są zachowywane.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Pędzel zawartość jest skalowana tak, aby całkowicie wypełnia obszar wyjściowy przy jednoczesnym zapewnieniu właściwej zawartości oryginalnego współczynnika proporcji.  
  
 Na poniższym obrazie przedstawiono poszczególne <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienia.  
  
 ![Different TileBrush Stretch settings](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 W poniższym przykładzie zawartość <xref:System.Windows.Media.ImageBrush> jest ustawiony tak, aby nie dopasowuje się do wypełnienia obszaru wyjściowego.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Domyślnie <xref:System.Windows.Media.TileBrush> generuje pojedynczego kafelka (podstawowy Kafelek) i rozciąga tego kafelka, aby całkowicie wypełnić obszaru wyjściowego. Można zmienić rozmiar i położenie podstawowy Kafelek, ustawiając <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Rozmiar fragmentu podstawowy  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Właściwość określa rozmiar i położenie podstawowy Kafelek i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwość określa, czy <xref:System.Windows.Media.TileBrush.Viewport%2A> jest określona za pomocą współrzędnych bezwzględny lub względny. Jeśli współrzędne względne, są one względem rozmiar obszaru danych wyjściowych. Reprezentuje punkt (0,0) lewym górnym rogu obszaru danych wyjściowych i (1,1) reprezentuje dolnym rogu obszaru wyjściowego. Aby określić, że <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość używa współrzędne bezwzględne, ustaw <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwość <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Na poniższej ilustracji przedstawiono różnice w danych wyjściowych między <xref:System.Windows.Media.TileBrush> z względne i bezwzględne <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Należy zauważyć, że każdy posiadającym fragmentacji wzorca; w następnej sekcji opisano sposób określania wzorzec kafelka.  
  
 ![Bezwzględna i jednostkach względnych okienka ekranu](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 W poniższym przykładzie obraz jest używany do utworzenia kafelka, który ma szerokości i wysokości 50%. Podstawowy Kafelek znajduje się w (0,0) obszaru wyjściowego.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 W następnym przykładzie kafelkach <xref:System.Windows.Media.ImageBrush> na pikselach niezależnych od urządzenia 25 o 25. Ponieważ <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> są bezwzględne, <xref:System.Windows.Media.ImageBrush> Kafelki są zawsze 25 o 25 pikseli, bez względu na rozmiar obszaru są rysowane.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Zachowanie fragmentacji  
 A <xref:System.Windows.Media.TileBrush> generuje wzorzec fragmentacji, podczas jego podstawowy Kafelek nie wypełnia całkowicie obszaru wyjściowego i tryb fragmentacji innych następnie <xref:System.Windows.Media.TileMode.None> jest określony. Gdy Kafelek pędzla kafelków nie wypełnia całkowicie obszaru wyjściowego jego <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość określa, czy powinny zostać zduplikowane podstawowy Kafelek, aby wypełnił obszar danych wyjściowych, a jeśli tak, jak podstawowy Kafelek powinny zostać zduplikowane. <xref:System.Windows.Media.TileBrush.TileMode%2A> Właściwość akceptuje następujące wartości, zdefiniowane przez <xref:System.Windows.Media.TileMode> wyliczenia:  
  
- <xref:System.Windows.Media.TileMode.None>: Podstawowy Kafelek jest rysowane.  
  
- <xref:System.Windows.Media.TileMode.Tile>: Podstawowy Kafelek jest rysowana, a pozostałe obszar zostanie wypełniony przez powtarzanie podstawowy Kafelek taki sposób, że prawą krawędzią jeden Kafelek jest przyległa do lewej krawędzi następnego i podobnie dla dołu i od góry.  
  
- <xref:System.Windows.Media.TileMode.FlipX>: Taka sama jak <xref:System.Windows.Media.TileMode.Tile>, ale kolumn alternatywnego Kafelki są przerzucane poziomo.  
  
- <xref:System.Windows.Media.TileMode.FlipY>: Taka sama jak <xref:System.Windows.Media.TileMode.Tile>, ale naprzemienne wiersze Kafelki są przerzucane w pionie.  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: Kombinacji <xref:System.Windows.Media.TileMode.FlipX> i <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Na poniższym obrazie przedstawiono tryby różnych fragmentacji.  
  
 ![Different TileBrush TileMode settings](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 W poniższym przykładzie obraz jest używany do malowania prostokąt, 100 pikseli szerokości i 100 pikseli wysokości. Ustawiając pędzla <xref:System.Windows.Media.TileBrush.Viewport%2A> została ustawiona do 0,0,0.25,0.25, podstawowy Kafelek pędzla dokonuje się za 1/4 obszaru wyjściowego. Pędzel <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawiono <xref:System.Windows.Media.TileMode.FlipXY>. tak, aby wypełnił prostokąt z wierszami kafelków.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Tematy z instrukcjami](brushes-how-to-topics.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [Przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049)
