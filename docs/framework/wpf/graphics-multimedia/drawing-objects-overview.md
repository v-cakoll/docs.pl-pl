---
title: Przegląd Rysowanie obiektów
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: edbb5521069caaa83dc24ca03af510d8e12f1b11
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836529"
---
# <a name="drawing-objects-overview"></a>Przegląd Rysowanie obiektów
W tym temacie przedstawiono <xref:System.Windows.Media.Drawing> obiektów oraz opisano, jak za ich pomocą efektywnie Rysowanie kształtów, mapy bitowe, tekstu i media. Użyj <xref:System.Windows.Media.Drawing> obiektów podczas tworzenia obiektu clipart malować <xref:System.Windows.Media.DrawingBrush>, lub użyj <xref:System.Windows.Media.Visual> obiektów.  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co to jest obiekt rysowania?  
 A <xref:System.Windows.Media.Drawing> obiekt w tym artykule opisano widoczne zawartości, takiej jak kształt, mapy bitowej, wideo lub wiersza tekstu. Różne rodzaje rysunki opis różnych typów zawartości. Oto lista różne rodzaje Rysowanie obiektów.  
  
-   <xref:System.Windows.Media.GeometryDrawing> — Rysuje kształt.  
  
-   <xref:System.Windows.Media.ImageDrawing> — Rysuje obraz.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> — Rysuje tekst.  
  
-   <xref:System.Windows.Media.VideoDrawing> — Odtwarza plik audio lub wideo.  
  
-   <xref:System.Windows.Media.DrawingGroup> — Rysuje inne rysunki. Aby połączyć inne rysunki w jeden złożony, należy użyć rysowania grupy.  
  
 <xref:System.Windows.Media.Drawing> obiekty są uniwersalne; istnieje wiele sposobów, możesz użyć <xref:System.Windows.Media.Drawing> obiektu.  
  
-   Wyświetl jako obraz przy użyciu <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> kontroli.  
  
-   Można ją za pomocą <xref:System.Windows.Media.DrawingBrush> namalować obiektu, takie jak <xref:System.Windows.Controls.Page.Background%2A> z <xref:System.Windows.Controls.Page>.  
  
-   Służy do opisywania wygląd <xref:System.Windows.Media.DrawingVisual>.  
  
-   Służy do wyliczenia zawartości <xref:System.Windows.Media.Visual>.  
  
 WPF zapewnia inne typy obiektów, które są zdolne do rysowania kształtów, mapy bitowe, tekstu i media. Na przykład, można również użyć <xref:System.Windows.Shapes.Shape> obiekty do rysowania kształtów, a <xref:System.Windows.Controls.MediaElement> kontroli udostępnia inny sposób dodać wideo do swojej aplikacji. Dlatego kiedy należy używać <xref:System.Windows.Media.Drawing> obiektów? Gdy pochodzących z poziomu funkcji framework korzyści w wydajności lub gdy potrzebujesz <xref:System.Windows.Freezable> funkcji. Ponieważ <xref:System.Windows.Media.Drawing> obiektów nie obsługują [układ](../../../../docs/framework/wpf/advanced/layout.md), dane wejściowe i skoncentrować się, zapewniają korzyści wydajności, które były idealne do opisywania tła, clipart oraz Rysowanie niskiego poziomu <xref:System.Windows.Media.Visual> obiektów.  
  
 Ponieważ są one typu <xref:System.Windows.Freezable> obiektu, <xref:System.Windows.Media.Drawing> obiektów uzyskać kilka specjalne funkcje, które obejmują następujące elementy: mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md), udostępnione wśród wielu obiektów, aby poprawić jest tylko do odczytu wydajność, sklonować i wprowadzone metodą o bezpiecznych wątkach. Aby uzyskać więcej informacji na temat różnych funkcji oferowanych przez <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Rysowanie kształtu  
 Aby narysować kształt, należy użyć <xref:System.Windows.Media.GeometryDrawing>. Na rysunku geometrii <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> właściwość opisuje kształtu, aby narysować, jego <xref:System.Windows.Media.GeometryDrawing.Brush%2A> właściwość opisuje, jak być rysowane wewnątrz kształtu i jego <xref:System.Windows.Media.GeometryDrawing.Pen%2A> właściwość opisuje, jak ma być rysowany konturu jej.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> Aby narysować kształt. Kształt jest opisana przez <xref:System.Windows.Media.GeometryGroup> oraz dwóch <xref:System.Windows.Media.EllipseGeometry> obiektów. Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej rysowania za pomocą <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 W tym przykładzie tworzy następujące <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Aby uzyskać kompletny przykład, zobacz [tworzenie GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 Inne <xref:System.Windows.Media.Geometry> klasy, takie jak <xref:System.Windows.Media.PathGeometry> umożliwiają tworzenie bardziej złożonych kształtów, tworząc, krzywych i łuki. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Geometry> obiekty, zobacz [Przegląd Geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Aby uzyskać więcej informacji o innych sposobach Rysowanie kształtów, które nie używają <xref:System.Windows.Media.Drawing> obiekty, zobacz [kształty i podstawowe Rysowanie w WPF — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Rysowanie obrazu  
 Aby narysować obrazu, należy użyć <xref:System.Windows.Media.ImageDrawing>. <xref:System.Windows.Media.ImageDrawing> Obiektu <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> właściwość opisuje obrazu do rysowania i jego <xref:System.Windows.Media.ImageDrawing.Rect%2A> właściwość definiuje region, w którym narysowaniem obrazu.  
  
 Poniższy przykład pobiera obraz do prostokąta znajduje się w punkcie (75,75) oznacza to 100 x 100 pikseli. Poniższa ilustracja przedstawia <xref:System.Windows.Media.ImageDrawing> utworzone przez w przykładzie. Szare obramowanie został dodany do wyświetlenia granice <xref:System.Windows.Media.ImageDrawing>.  
  
 ![100 x 100 ImageDrawing rysowany w &#40;75,75&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
ImageDrawing 100 x 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Aby uzyskać więcej informacji o obrazach, zobacz [Przegląd obrazowanie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Odtwórz z nośnika (tylko kod)  
  
> [!NOTE]
>  Mimo że można zadeklarować <xref:System.Windows.Media.VideoDrawing> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można tylko obciążenia i odtwarzanie multimediów za pomocą kodu. Aby odtworzyć wideo w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], użyj <xref:System.Windows.Controls.MediaElement> zamiast tego.  
  
 Odtwarzanie pliku audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>. Istnieją dwa sposoby, aby załadować i odtwarzanie multimediów. Pierwsza to użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi ze sposobów jest utworzenie własnych <xref:System.Windows.Media.MediaTimeline> za pomocą <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Podczas dystrybucji multimediów za pomocą aplikacji, nie można użyć pliku multimedialnego jako zasób projektu, tak jak w przypadku obrazu. W pliku projektu, należy zamiast tego ustawić typ nośnika na `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.  
  
 Odtwarzanie multimediów bez konieczności tworzenia własnych <xref:System.Windows.Media.MediaTimeline>, wykonaj następujące kroki.  
  
1.  Tworzy obiekt <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Użyj <xref:System.Windows.Media.MediaPlayer.Open%2A> metodę, aby załadować plik nośnika.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Utwórz <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Określ rozmiar i lokalizację, aby narysować nośnika przez ustawienie <xref:System.Windows.Media.VideoDrawing.Rect%2A> właściwość <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Ustaw <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwość <xref:System.Windows.Media.VideoDrawing> z <xref:System.Windows.Media.MediaPlayer> został utworzony.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Użyj <xref:System.Windows.Media.MediaPlayer.Play%2A> metody <xref:System.Windows.Media.MediaPlayer> rozpoczęcie odtwarzania nośnika.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania pliku wideo, jeden raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkowe chronometrażu kontrolę nad nośnika, należy użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline> Umożliwia określenie, czy należy powtórzyć filmu wideo. Aby użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.VideoDrawing>, wykonaj następujące czynności:  
  
1.  Zadeklaruj <xref:System.Windows.Media.MediaTimeline> i ustaw jego zachowania chronometrażu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Tworzenie <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Tworzenie <xref:System.Windows.Media.MediaPlayer> i użyj <xref:System.Windows.Media.MediaClock> można ustawić jego <xref:System.Windows.Media.MediaPlayer.Clock%2A> właściwości.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Tworzenie <xref:System.Windows.Media.VideoDrawing> i przypisać <xref:System.Windows.Media.MediaPlayer> do <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwość <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> powtarzanie odtwarzania filmu wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy zauważyć, że gdy używasz <xref:System.Windows.Media.MediaTimeline>, możesz użyć interakcyjnego <xref:System.Windows.Media.Animation.ClockController> zwróciło <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.MediaClock> Aby kontrolować odtwarzanie multimediów zamiast metod interaktywnych <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Rysowanie tekstu  
 Rysowanie tekstu, należy użyć <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.GlyphRun>. W poniższym przykładzie użyto <xref:System.Windows.Media.GlyphRunDrawing> ma zostać narysowany tekst "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Element <xref:System.Windows.Media.GlyphRun> jest obiektem niskiego poziomu, przeznaczony do użytku z dokumentów o stałym formacie prezentacji i scenariusze drukowania. Rysowanie tekstu na ekranie prostszy sposób jest użycie <xref:System.Windows.Controls.Label> lub <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.GlyphRun>, zobacz [wprowadzenie do obiektu GlyphRun i elementu glifu](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) Przegląd.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Rysunki złożone  
 A <xref:System.Windows.Media.DrawingGroup> pozwala połączyć wiele rysunków w jeden złożony. Za pomocą <xref:System.Windows.Media.DrawingGroup>, można połączyć kształty, obrazów i tekstu, które znajdują się w pojedynczej <xref:System.Windows.Media.Drawing> obiektu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingGroup> połączyć dwa <xref:System.Windows.Media.GeometryDrawing> obiektów i <xref:System.Windows.Media.ImageDrawing> obiektu. Ten przykład generuje następujące dane wyjściowe.  
  
 ![DrawingGroup przy użyciu wielu rysunków](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Złożony rysunek  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia także zastosowanie maski krycia, przekształcenia, efekty bitmapowe i inne operacje do jego zawartości. <xref:System.Windows.Media.DrawingGroup> operacje są stosowane w następującej kolejności: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Poniższa ilustracja przedstawia kolejność, w którym <xref:System.Windows.Media.DrawingGroup> operacji są stosowane.  
  
 ![DrawingGroup — kolejność operacji](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji DrawingGroup  
  
 W poniższej tabeli opisano właściwości można używać do manipulowania <xref:System.Windows.Media.DrawingGroup> zawartości obiektu.  
  
|Właściwość|Opis|Ilustracja|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Zmienia nieprzezroczystość zaznaczonych części <xref:System.Windows.Media.DrawingGroup> zawartość. Aby uzyskać przykład, zobacz [jak: Kontrolowanie nieprzezroczystość rysowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![DrawingGroup za pomocą maski krycia](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Równomiernie zmienia nieprzezroczystość <xref:System.Windows.Media.DrawingGroup> zawartość. Ta właściwość służy do upewnij <xref:System.Windows.Media.Drawing> obszarów przezroczystych lub częściowo przezroczyste. Aby uzyskać przykład, zobacz [jak: Zastosuj maski krycia do rysowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Obiekty DrawingGroup z różnymi ustawieniami nieprzezroczystości](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Stosuje <xref:System.Windows.Media.Effects.BitmapEffect> do <xref:System.Windows.Media.DrawingGroup> zawartość. Aby uzyskać przykład, zobacz [jak: Zastosowanie efektu bitmapy do rysowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup z obiektem BlurBitmapEffect](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Klipy <xref:System.Windows.Media.DrawingGroup> zawartość do regionu opisywane przy użyciu <xref:System.Windows.Media.Geometry>. Aby uzyskać przykład, zobacz [jak: Przytnij rysowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![DrawingGroup — z regionem zdefiniowanych klip](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Przyciąga pikselach niezależnych od urządzenia na urządzeniu pikseli wzdłuż określonych wytycznych. Ta właściwość jest przydatne w celu zminimalizowania gwałtownie renderowania grafiki precyzyjnie szczegółowe na ekranach o niskiej rozdzielczości DPI. Aby uzyskać przykład, zobacz [stosowanie elementu GuidelineSet do rysowania](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup z lub bez GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Przekształca <xref:System.Windows.Media.DrawingGroup> zawartość. Aby uzyskać przykład, zobacz [jak: Zastosuj przekształcenie do rysowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![A obracać DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Rysowania są wyświetlane jako obraz  
 Do wyświetlenia <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Controls.Image> kontrolować, należy użyć <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> kontrolki <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwości do rysunku, którą chcesz wyświetlić.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu, aby wyświetlić <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![GeometryDrawing dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Malowanie obiektu za pomocą rysowania  
 Element <xref:System.Windows.Media.DrawingBrush> jest typu pędzla, który umożliwia malowanie obszaru za pomocą rysowania obiektu. Służy on do malowania o niemal dowolnym graficznego obiektu za pomocą rysowania. <xref:System.Windows.Media.Drawing> Właściwość <xref:System.Windows.Media.DrawingBrush> opisano jego <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Do renderowania <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Media.DrawingBrush>, dodaj go do pędzla przy użyciu pędzli <xref:System.Windows.Media.Drawing> właściwość i użyj pędzla do rysowania graficznego obiektu, takie jak formant lub panelu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> z wzorcem utworzone na podstawie <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![A sąsiadująco DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing używane z DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Klasa oferuje różnorodne opcje rozciąganie i fragmentacji jego zawartości. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush>, zobacz [malowanie obrazami, rysowaniem i Visual](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md) Przegląd.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Renderowanie rysowania za pomocą wizualizacji  
 Element <xref:System.Windows.Media.DrawingVisual> jest typem obiektu visual przeznaczone do renderowania rysowania. Praca bezpośrednio w warstwie visual jest dostępny dla deweloperów, którzy chcą tworzyć wysoce dostosowane środowisko graficznego i nie została opisana w tym omówieniu. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md) Przegląd.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Obiekty DrawingContext  
 <xref:System.Windows.Media.DrawingContext> Klasy pozwala wypełnić <xref:System.Windows.Media.Visual> lub <xref:System.Windows.Media.Drawing> o zawartości wizualnej. Użyj takich obiektów grafiki niższego poziomu <xref:System.Windows.Media.DrawingContext> ponieważ opisuje zawartość graficzną bardzo wydajny sposób.  
  
 Mimo że <xref:System.Windows.Media.DrawingContext> metody rysowania wyglądać podobnie do metody rysowania <xref:System.Drawing.Graphics?displayProperty=nameWithType> typu, różnią się one naprawdę bardzo. <xref:System.Windows.Media.DrawingContext> jest używany w systemie grafiki zachowanej trybu, podczas gdy <xref:System.Drawing.Graphics?displayProperty=nameWithType> typ jest używany z systemem grafiki w trybie natychmiastowym. Zastosowania <xref:System.Windows.Media.DrawingContext> obiektu rysowanie poleceń, faktycznie przechowujesz zestaw instrukcji renderowania (ale mechanizm dokładnie magazynu zależy od typu obiektu, który dostarcza <xref:System.Windows.Media.DrawingContext>) który będzie później używany przez grafiki systemu; nie są rysunku na ekranie w czasie rzeczywistym. Aby uzyskać więcej informacji o tym, jak działa system grafiki Windows Presentation Foundation (WPF), zobacz [Przegląd Renderowanie grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Możesz nigdy nie bezpośrednio utworzyć wystąpienia <xref:System.Windows.Media.DrawingContext>; można jednak uzyskać rysowania kontekstu z niektórych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Wyliczanie zawartości Visual  
 Oprócz ich zastosowań <xref:System.Windows.Media.Drawing> obiektów również zapewnić model obiektu wyliczanie zawartości <xref:System.Windows.Media.Visual>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, która pobierze <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i ją wyliczanie.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)
