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
ms.openlocfilehash: d4527c331308ff6cd517705212e09428216d2378
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459730"
---
# <a name="drawing-objects-overview"></a>Przegląd Rysowanie obiektów
W tym temacie przedstawiono <xref:System.Windows.Media.Drawing> obiektów i opisano sposób ich użycia w celu wydajnego rysowania kształtów, map bitowych, tekstu i multimediów. Użyj <xref:System.Windows.Media.Drawing> obiektów podczas tworzenia clipart, maluj przy użyciu <xref:System.Windows.Media.DrawingBrush>lub Użyj obiektów <xref:System.Windows.Media.Visual>.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co to jest obiekt rysowania?  
 Obiekt <xref:System.Windows.Media.Drawing> opisuje widoczną zawartość, na przykład kształt, mapę bitową, wideo lub wiersz tekstu. Różne typy rysunków opisują różne typy zawartości. Poniżej znajduje się lista różnych typów obiektów rysowania.  
  
- <xref:System.Windows.Media.GeometryDrawing> — rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing> — rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> — rysuje tekst.  
  
- <xref:System.Windows.Media.VideoDrawing> — odtwarza plik audio lub wideo.  
  
- <xref:System.Windows.Media.DrawingGroup> — rysuje inne rysunki. Użyj grupy rysowania, aby połączyć inne rysunki w pojedynczy rysunek złożony.  
  
 obiekty <xref:System.Windows.Media.Drawing> są uniwersalne; Istnieje wiele sposobów użycia obiektu <xref:System.Windows.Media.Drawing>.  
  
- Można go wyświetlić jako obraz przy użyciu <xref:System.Windows.Media.DrawingImage> i kontrolki <xref:System.Windows.Controls.Image>.  
  
- Można go użyć z <xref:System.Windows.Media.DrawingBrush> do malowania obiektu, takiego jak <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page>.  
  
- Można jej użyć do opisania wyglądu <xref:System.Windows.Media.DrawingVisual>.  
  
- Można jej użyć do wyliczenia zawartości <xref:System.Windows.Media.Visual>.  
  
 WPF udostępnia inne typy obiektów, które umożliwiają rysowanie kształtów, map bitowych, tekstu i multimediów. Można na przykład użyć obiektów <xref:System.Windows.Shapes.Shape> do rysowania kształtów, a kontrolka <xref:System.Windows.Controls.MediaElement> zapewnia inny sposób dodawania wideo do aplikacji. Tak więc kiedy należy używać <xref:System.Windows.Media.Drawing> obiektów? Gdy można wymusić funkcje poziomu platformy w celu uzyskania korzyści z wydajności lub gdy potrzebujesz <xref:System.Windows.Freezable> funkcji. Ponieważ obiekty <xref:System.Windows.Media.Drawing> nie obsługują [układu](../advanced/layout.md), wejścia i koncentracji, zapewniają korzyści z wydajności, które są idealnym rozwiązaniem do opisywania tła, grafiki artystycznej i dla rysowania niskiego poziomu z obiektami <xref:System.Windows.Media.Visual>.  
  
 Ponieważ są one typu <xref:System.Windows.Freezable> obiektu, obiekty <xref:System.Windows.Media.Drawing> oferują kilka specjalnych funkcji, takich jak: mogą być deklarowane jako [zasoby](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współużytkowane przez wiele obiektów, przeznaczone tylko do odczytu w celu poprawy wydajności, klonowania i wykonania bezpieczny wątkowo. Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiektów, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Rysowanie kształtu  
 Aby narysować kształt, użyj <xref:System.Windows.Media.GeometryDrawing>. Właściwość <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> rysowania geometrii zawiera opis kształtu do rysowania, jego właściwość <xref:System.Windows.Media.GeometryDrawing.Brush%2A> opisuje sposób malowania wnętrza kształtu, a jej Właściwość <xref:System.Windows.Media.GeometryDrawing.Pen%2A> opisuje sposób rysowania konturów.  
  
 Poniższy przykład używa <xref:System.Windows.Media.GeometryDrawing> do rysowania kształtu. Kształt jest opisywany przez <xref:System.Windows.Media.GeometryGroup> i dwa obiekty <xref:System.Windows.Media.EllipseGeometry>. Wnętrze kształtu jest rysowane <xref:System.Windows.Media.LinearGradientBrush>, a jego kontur jest rysowany z <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Ten przykład tworzy następujące <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dwie wielokropek](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Pełny przykład można znaleźć w temacie [Create a GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Inne klasy <xref:System.Windows.Media.Geometry>, takie jak <xref:System.Windows.Media.PathGeometry> umożliwiają tworzenie bardziej złożonych kształtów przez tworzenie krzywych i łuków. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Geometry> obiektów, zobacz [Omówienie geometrii](geometry-overview.md).  
  
 Aby uzyskać więcej informacji na temat innych sposobów rysowania kształtów, które nie używają <xref:System.Windows.Media.Drawing> obiektów, zobacz [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Rysowanie obrazu  
 Aby narysować obraz, użyj <xref:System.Windows.Media.ImageDrawing>. Właściwość <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> obiektu <xref:System.Windows.Media.ImageDrawing> opisuje obraz do rysowania, a jego właściwość <xref:System.Windows.Media.ImageDrawing.Rect%2A> definiuje region, w którym jest rysowany obraz.  
  
 Poniższy przykład rysuje obraz do prostokąta znajdującego się w (75, 75), który jest 100 o 100 pikseli. Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.ImageDrawing> utworzone przez przykład. Dodano szare obramowanie, aby pokazać granice <xref:System.Windows.Media.ImageDrawing>.  
  
 ![A 100 do 100 ImageDrawing narysowana &#40;na 75, 75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 o 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Aby uzyskać więcej informacji o obrazach, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Odtwórz multimedia (tylko kod)  
  
> [!NOTE]
> Chociaż można zadeklarować <xref:System.Windows.Media.VideoDrawing> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można załadować i odtworzyć multimedia przy użyciu kodu. Aby odtworzyć wideo w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], użyj <xref:System.Windows.Controls.MediaElement> zamiast tego.  
  
 Aby odtworzyć plik audio lub wideo, użyj <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>. Istnieją dwa sposoby ładowania i odtwarzania multimediów. Pierwszym sposobem jest użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> samodzielnie, a drugi — tworzenie własnych <xref:System.Windows.Media.MediaTimeline> do użycia z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu, takiego jak obraz. W pliku projektu należy zamiast tego ustawić typ nośnika na `Content` i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always`.  
  
 Aby odtwarzać multimedia bez tworzenia własnych <xref:System.Windows.Media.MediaTimeline>, wykonaj następujące czynności.  
  
1. Utwórz obiekt <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Użyj metody <xref:System.Windows.Media.MediaPlayer.Open%2A>, aby załadować plik multimedialny.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Określ rozmiar i lokalizację, aby narysować nośnik przez ustawienie właściwości <xref:System.Windows.Media.VideoDrawing.Rect%2A> <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Ustaw właściwość <xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing> za pomocą utworzonego <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Użyj metody <xref:System.Windows.Media.MediaPlayer.Play%2A> <xref:System.Windows.Media.MediaPlayer>, aby rozpocząć odtwarzanie nośnika.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Poniższy przykład używa <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania pliku wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkową kontrolę czasu na nośniku, użyj <xref:System.Windows.Media.MediaTimeline> z obiektami <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>. <xref:System.Windows.Media.MediaTimeline> pozwala określić, czy film wideo powinien być powtarzany. Aby użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.VideoDrawing>, wykonaj następujące czynności:  
  
1. Zadeklaruj <xref:System.Windows.Media.MediaTimeline> i ustaw jego zachowania chronometrażu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Utwórz <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.MediaPlayer> i użyj <xref:System.Windows.Media.MediaClock>, aby ustawić jej Właściwość <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Utwórz <xref:System.Windows.Media.VideoDrawing> i przypisz <xref:System.Windows.Media.MediaPlayer> do właściwości <xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Poniższy przykład używa <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>, aby kilkukrotnie odtworzyć film wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy pamiętać, że w przypadku korzystania z <xref:System.Windows.Media.MediaTimeline>interaktywny <xref:System.Windows.Media.Animation.ClockController> zwrócony z właściwości <xref:System.Windows.Media.Animation.Clock.Controller%2A> <xref:System.Windows.Media.MediaClock> do sterowania odtwarzaniem multimediów zamiast interaktywnych metod <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Rysuj tekst  
 Aby narysować tekst, użyj <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.GlyphRun>. Poniższy przykład używa <xref:System.Windows.Media.GlyphRunDrawing> do rysowania tekstu "Hello world".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun> jest obiektem niskiego poziomu, który jest przeznaczony do użytku z prezentacją dokumentu o stałym formacie i scenariusze drukowania. Łatwiejszym sposobem rysowania tekstu na ekranie jest użycie <xref:System.Windows.Controls.Label> lub <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.GlyphRun>, zobacz [wprowadzenie do obiektu GlyphRun i elementów glifs](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) przegląd.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Rysunki złożone  
 <xref:System.Windows.Media.DrawingGroup> umożliwia łączenie wielu rysunków w pojedynczy rysunek złożony. Za pomocą <xref:System.Windows.Media.DrawingGroup>można łączyć kształty, obrazy i tekst w jeden obiekt <xref:System.Windows.Media.Drawing>.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingGroup> do łączenia dwóch obiektów <xref:System.Windows.Media.GeometryDrawing> i obiektu <xref:System.Windows.Media.ImageDrawing>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![Obiekt do rysowania z wieloma rysunkami](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Rysunek złożony  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup> umożliwia również stosowanie masek nieprzezroczystości, transformacji, efektów mapy bitowej i innych operacji do jej zawartości. operacje <xref:System.Windows.Media.DrawingGroup> są stosowane w następującej kolejności: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Na poniższej ilustracji przedstawiono kolejność stosowania <xref:System.Windows.Media.DrawingGroup> operacji.  
  
 ![Kolejność operacji na rysunku](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji na obiektach do rysowania  
  
 W poniższej tabeli opisano właściwości, których można użyć do manipulowania zawartością obiektu <xref:System.Windows.Media.DrawingGroup>.  
  
|Właściwość|Opis|Ilustracji|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Zmienia nieprzezroczystość wybranych fragmentów zawartości <xref:System.Windows.Media.DrawingGroup>. Aby zapoznać się z przykładem, zobacz [jak: kontrolowanie nieprzezroczystości rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Obiekt typu rysowanie z maską nieprzezroczystości](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Jednorodnie zmienia nieprzezroczystość zawartości <xref:System.Windows.Media.DrawingGroup>. Użyj tej właściwości, aby uczynić <xref:System.Windows.Media.Drawing> przezroczystą lub częściowo przezroczystą. Aby zapoznać się z przykładem, zobacz [jak: zastosować maskę nieprzezroczystość do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups z różnymi ustawieniami nieprzezroczystości](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Stosuje <xref:System.Windows.Media.Effects.BitmapEffect> do zawartości <xref:System.Windows.Media.DrawingGroup>. Aby zapoznać się z przykładem, zobacz [jak: stosowanie efektu bitmapy do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Rysowanie z BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Przycina <xref:System.Windows.Media.DrawingGroup> zawartość do regionu, który można opisać przy użyciu <xref:System.Windows.Media.Geometry>. Aby zapoznać się z przykładem, zobacz [How to: cliping rysowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Rysowanie ze zdefiniowanym regionem przycinania](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Przyciąga niezależne od urządzenia piksele do pikseli urządzenia zgodnie z określonymi wskazówkami. Ta właściwość jest przydatna do zapewnienia, że dokładniej szczegółowe renderowanie grafiki na wyświetlaczach o niskiej rozdzielczości DPI. Aby zapoznać się z przykładem, zobacz temat [stosowanie GuidelineSet do rysunku](how-to-apply-a-guidelineset-to-a-drawing.md).|![Obiekt do rysowania z i bez GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Przekształca zawartość <xref:System.Windows.Media.DrawingGroup>. Aby zapoznać się z przykładem, zobacz [How to: Apply a Transform for a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Obrócona przerysowanie](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Wyświetlanie rysunku jako obrazu  
 Aby wyświetlić <xref:System.Windows.Media.Drawing> z kontrolką <xref:System.Windows.Controls.Image>, użyj <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image.Source%2A> kontrolki <xref:System.Windows.Controls.Image> i ustaw właściwość <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> na rysunek, który chcesz wyświetlić.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingImage> i kontrolki <xref:System.Windows.Controls.Image> do wyświetlania <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![GeometryDrawing dwie wielokropek](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Malowanie obiektu za pomocą rysowania  
 <xref:System.Windows.Media.DrawingBrush> to typ pędzla, który maluje obszar z obiektem rysunkowym. Można jej użyć do malowania tylko dowolnego obiektu graficznego z rysunkiem. <xref:System.Windows.Media.Drawing> Właściwość <xref:System.Windows.Media.DrawingBrush> opisuje jej <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Aby renderować <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Media.DrawingBrush>, Dodaj go do pędzla przy użyciu właściwości <xref:System.Windows.Media.Drawing> pędzla i użyj pędzla do malowania obiektu graficznego, takiego jak kontrolka lub panel.  
  
 Poniższe przykłady używają <xref:System.Windows.Media.DrawingBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> ze wzorcem utworzonym na podstawie <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![DrawingBrush z sąsiadującą](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing używany z DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 Klasa <xref:System.Windows.Media.DrawingBrush> udostępnia różne opcje rozciągania i rozmieszczania zawartości. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush>, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Renderowanie rysunku przy użyciu wizualizacji  
 <xref:System.Windows.Media.DrawingVisual> jest typem obiektu wizualizacji zaprojektowanego do renderowania rysunku. Praca bezpośrednio w warstwie wizualnej jest opcją dla deweloperów, którzy chcą utworzyć wysoce dostosowane środowisko graficzne i nie jest opisana w tym omówieniu. Aby uzyskać więcej informacji, zobacz temat [Korzystanie z użycie DrawingVisual obiektów](using-drawingvisual-objects.md) — Omówienie.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext — obiekty  
 Klasa <xref:System.Windows.Media.DrawingContext> umożliwia wypełnienie <xref:System.Windows.Media.Visual> lub <xref:System.Windows.Media.Drawing> z zawartością wizualną. Wiele takich obiektów graficznych na niższym poziomie używa <xref:System.Windows.Media.DrawingContext>, ponieważ opisuje ona zawartość graficzną bardzo wydajnie.  
  
 Mimo że metody rysowania <xref:System.Windows.Media.DrawingContext> wyglądają podobnie jak metody rysowania typu <xref:System.Drawing.Graphics?displayProperty=nameWithType>, są one bardzo różne. <xref:System.Windows.Media.DrawingContext> jest używany z systemem grafiki trybu zachowywania, podczas gdy typ <xref:System.Drawing.Graphics?displayProperty=nameWithType> jest używany z systemem graficznym trybu natychmiastowego. W przypadku korzystania z poleceń rysowania obiektu <xref:System.Windows.Media.DrawingContext>, w rzeczywistości przechowujesz zestaw instrukcji renderowania (Chociaż dokładny mechanizm magazynowania zależy od typu obiektu, który dostarcza <xref:System.Windows.Media.DrawingContext>), który będzie później używany przez system grafiki; nie rysujesz na ekranie w czasie rzeczywistym. Aby uzyskać więcej informacji na temat działania systemu grafiki Windows Presentation Foundation (WPF), zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).  
  
 Nie można bezpośrednio utworzyć wystąpienia <xref:System.Windows.Media.DrawingContext>; można jednak uzyskać kontekst rysowania z pewnych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Wyliczanie zawartości wizualizacji  
 Oprócz innych celów, obiekty <xref:System.Windows.Media.Drawing> udostępniają również model obiektów do wyliczania zawartości <xref:System.Windows.Media.Visual>.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>, aby pobrać <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i wyliczyć ją.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Geometria — przegląd](geometry-overview.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [Tematy z instrukcjami](drawings-how-to-topics.md)
