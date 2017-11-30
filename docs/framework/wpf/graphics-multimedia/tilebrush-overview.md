---
title: "TileBrush — Przegląd"
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
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f759a56233e8cf2b1c1d39862706be518fefe43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="tilebrush-overview"></a>TileBrush — Przegląd
<xref:System.Windows.Media.TileBrush>obiekty umożliwiają z dużym stopniem kontrolę nad jak obszar jest rysowane przy użyciu obrazu <xref:System.Windows.Media.Drawing>, lub <xref:System.Windows.Media.Visual>. W tym temacie opisano sposób użycia <xref:System.Windows.Media.TileBrush> funkcji, aby uzyskać większą kontrolę nad jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, lub <xref:System.Windows.Media.VisualBrush> rysują obszaru.  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy zrozumieć, jak używać podstawowych funkcji <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, lub <xref:System.Windows.Media.VisualBrush> klasy. Aby obejrzeć wprowadzenie do tych typów, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Malowanie obszar o kafelków  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, są <xref:System.Windows.Media.VisualBrush> typów <xref:System.Windows.Media.TileBrush> obiektów. Pędzle kafelków umożliwiają z dużym stopniem kontrolę nad jak obszar jest rysowane przy użyciu obrazu, rysunku lub visual. Na przykład zamiast tylko malowanie obszar o jeden obraz rozciągnięty, można malować obszar o serię kafelków obrazu, tworzące wzorzec.  
  
 Malowanie obszar o pędzla kafelka obejmuje trzy składniki: zawartość, podstawowy Kafelek i do obszaru wyjściowego.  
  
 ![Składniki TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki TileBrush z jednego kafelka  
  
 ![Składniki sąsiadującym TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki TileBrush z TileMode kafelków  
  
 Obszar wyjściowy jest obszaru są rysowane, takich jak <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> lub <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Kolejne sekcje opisują dwa składniki programu <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>Pędzel zawartości  
 Istnieją trzy różne typy <xref:System.Windows.Media.TileBrush> i maluje każdego z innym typem zawartości.  
  
-   Jeśli jest pędzla <xref:System.Windows.Media.ImageBrush>, ta zawartość jest obrazem <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwość określa zawartość <xref:System.Windows.Media.ImageBrush>.  
  
-   Jeśli jest pędzla <xref:System.Windows.Media.DrawingBrush>, ta zawartość jest rysunku. <xref:System.Windows.Media.DrawingBrush.Drawing%2A> Właściwość określa zawartość <xref:System.Windows.Media.DrawingBrush>.  
  
-   Jeśli jest pędzla <xref:System.Windows.Media.VisualBrush>, ta zawartość jest element wizualny. <xref:System.Windows.Media.VisualBrush.Visual%2A> Właściwość określa zawartość <xref:System.Windows.Media.VisualBrush>.  
  
 Można określić pozycji i wymiary <xref:System.Windows.Media.TileBrush> zawartości przy użyciu <xref:System.Windows.Media.TileBrush.Viewbox%2A> właściwości, chociaż często pozostaw <xref:System.Windows.Media.TileBrush.Viewbox%2A> ustawioną wartość domyślną. Domyślnie <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest skonfigurowany do przechowywania całkowicie zawartość pędzla. Aby uzyskać więcej informacji o konfigurowaniu <xref:System.Windows.Controls.Viewbox>, zobacz <xref:System.Windows.Controls.Viewbox> strony właściwości.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>Podstawowy Kafelek  
 A <xref:System.Windows.Media.TileBrush> projekty na podstawowy Kafelek jego zawartości. <xref:System.Windows.Media.TileBrush.Stretch%2A> Formantów właściwości jak <xref:System.Windows.Media.TileBrush> zawartości jest rozciągany tak, aby wypełnić podstawowy Kafelek. <xref:System.Windows.Media.TileBrush.Stretch%2A> Właściwość przyjmuje następujące wartości zdefiniowane przez <xref:System.Windows.Media.Stretch> wyliczenie:  
  
-   <xref:System.Windows.Media.Stretch.None>Pędzla zawartości nie jest rozciągany tak, aby wypełnić kafelka.  
  
-   <xref:System.Windows.Media.Stretch.Fill>Zawartość pędzla jest skalowane w celu dopasowania kafelka. Ponieważ zawartość wysokość i szerokość są skalowane niezależnie, jego oryginalny współczynnik proporcji zawartości mogą nie zostać zachowane. Oznacza to, że zawartość pędzla może wypaczenia aby wypełnić fragment danych wyjściowych.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>Tak, aby zmieścił się całkowicie w kafelku skalowania zawartości pędzla. Zawartość współczynnik proporcji jest zachowywany.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>Zawartość pędzla skalowania, aby całkowicie wypełnia obszaru wyjściowego przy zachowaniu zawartości oryginalnego współczynnika proporcji.  
  
 Na poniższym obrazie przedstawiono różne <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienia.  
  
 ![Różne ustawienia TileBrush Stretch](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 W poniższym przykładzie zawartość <xref:System.Windows.Media.ImageBrush> ustawiono tak, aby nie stretch aby wypełnił obszar danych wyjściowych.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Domyślnie <xref:System.Windows.Media.TileBrush> generuje pojedynczy fragment (podstawowy Kafelek) i rozciąga się tego kafelka, aby wypełnić obszaru wyjściowego. Przez ustawienie można zmienić rozmiar i położenie podstawowy Kafelek <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Rozmiar kafelka podstawowej  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Właściwość określa rozmiar i położenie podstawowy Kafelek i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwość określa, czy <xref:System.Windows.Media.TileBrush.Viewport%2A> jest określona za pomocą współrzędnych bezwzględny lub względny. Jeśli współrzędnych względnych, są one względem rozmiar obszaru danych wyjściowych. Reprezentuje punkt (0,0) lewym górnym rogu obszaru wyjściowego i (1,1) reprezentuje dolnej prawym narożniku obszaru wyjściowego. Aby określić, że <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość używa współrzędne bezwzględne, ustaw <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Na poniższej ilustracji przedstawiono różnice w danych wyjściowych między <xref:System.Windows.Media.TileBrush> z względna lub bezwzględna <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Zwróć uwagę, że na ilustracjach każdego przedstawiono sąsiadującym wzorzec; w następnej sekcji opisano sposób określania wzorca kafelka.  
  
 ![Bezwzględny i jednostkach względnych okienka ekranu](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 W poniższym przykładzie obraz służy do tworzenia kafelka, który ma szerokości i wysokości 50%. Podstawowy Kafelek znajduje się pod adresem (0,0) obszaru wyjściowego.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 W następnym przykładzie fragmentów <xref:System.Windows.Media.ImageBrush> do 25 o 25 pikselach niezależnych od urządzenia. Ponieważ <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> są bezwzględne, <xref:System.Windows.Media.ImageBrush> Kafelki są zawsze 25 o 25 pikseli, niezależnie od rozmiaru obszaru są rysowane.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Zachowanie kafelków  
 A <xref:System.Windows.Media.TileBrush> tworzy sąsiadującym wzorzec podczas jego podstawowy Kafelek nie wypełnia całkowicie obszaru wyjściowego i tryb kafelków innych następnie <xref:System.Windows.Media.TileMode.None> jest określona. Gdy kafelka pędzla kafelka nie wypełnia całkowicie obszar wyjściowy jego <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość określa, czy powinny zostać zduplikowane podstawowy Kafelek, aby wypełnił obszar danych wyjściowych, a jeśli tak, jak Kafelek podstawowym powinny zostać zduplikowane. <xref:System.Windows.Media.TileBrush.TileMode%2A> Właściwość przyjmuje następujące wartości zdefiniowane przez <xref:System.Windows.Media.TileMode> wyliczenie:  
  
-   <xref:System.Windows.Media.TileMode.None>: Tylko podstawowy Kafelek jest rysowane.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: Podstawowy Kafelek ma zostać narysowana i pozostałe obszar jest wypełniony, powtarzając podstawowy Kafelek tak, aby był przylegające do lewej krawędzi następnej i prawej krawędzi jednego kafelka podobnie do dołu i z góry.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: Taki sam jak <xref:System.Windows.Media.TileMode.Tile>, ale alternatywny kolumn fragmentów są przerzucane poziomo.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: Taki sam jak <xref:System.Windows.Media.TileMode.Tile>, ale Kafelki wiersze są przerzucane pionowo.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Kombinację <xref:System.Windows.Media.TileMode.FlipX> i <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Na poniższym obrazie przedstawiono kafelków różne tryby.  
  
 ![Różne ustawienia TileBrush TileMode](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 W poniższym przykładzie jest używany obraz do malowania prostokąt 100 pikseli szerokości i wysokości 100 pikseli. Przez ustawienie pędzla <xref:System.Windows.Media.TileBrush.Viewport%2A> została ustawiona na 0,0,0.25,0.25, pędzla podstawowy Kafelek ma zostać za 1/4 obszaru wyjściowego. Pędzel <xref:System.Windows.Media.TileBrush.TileMode%2A> ma ustawioną wartość <xref:System.Windows.Media.TileMode.FlipXY>. tak, aby wypełnił prostokąt z wierszami kafelków.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [Malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Przykładowe ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Przykładowe VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)
