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
ms.openlocfilehash: d739865a692fa5ef448eba91369015580e5eda97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916316"
---
# <a name="drawing-objects-overview"></a>Przegląd Rysowanie obiektów
W tym temacie <xref:System.Windows.Media.Drawing> przedstawiono obiekty i opisano sposób ich używania do wydajnego rysowania kształtów, map bitowych, tekstu i multimediów. Użyj <xref:System.Windows.Media.Drawing> obiektów podczas tworzenia obiektu clipart, maluj <xref:System.Windows.Media.DrawingBrush>z lub używaj <xref:System.Windows.Media.Visual> obiektów.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co to jest obiekt rysowania?  
 <xref:System.Windows.Media.Drawing> Obiekt opisuje widoczną zawartość, na przykład kształt, mapę bitową, wideo lub wiersz tekstu. Różne typy rysunków opisują różne typy zawartości. Poniżej znajduje się lista różnych typów obiektów rysowania.  
  
- <xref:System.Windows.Media.GeometryDrawing>— Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>— Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>— Rysuje tekst.  
  
- <xref:System.Windows.Media.VideoDrawing>— Odtwarza plik dźwiękowy lub wideo.  
  
- <xref:System.Windows.Media.DrawingGroup>— Rysuje inne rysunki. Użyj grupy rysowania, aby połączyć inne rysunki w pojedynczy rysunek złożony.  
  
 <xref:System.Windows.Media.Drawing>obiekty są uniwersalne; Istnieje wiele sposobów używania <xref:System.Windows.Media.Drawing> obiektu.  
  
- Można go wyświetlić jako obraz przy użyciu <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> kontrolki i.  
  
- Można go <xref:System.Windows.Media.DrawingBrush> użyć do malowania obiektu, takiego <xref:System.Windows.Controls.Page.Background%2A> jak <xref:System.Windows.Controls.Page>.  
  
- Można jej użyć do opisania wyglądu <xref:System.Windows.Media.DrawingVisual>.  
  
- Można jej użyć do wyliczenia zawartości <xref:System.Windows.Media.Visual>.  
  
 WPF udostępnia inne typy obiektów, które umożliwiają rysowanie kształtów, map bitowych, tekstu i multimediów. Można na przykład użyć <xref:System.Windows.Shapes.Shape> obiektów do rysowania kształtów, <xref:System.Windows.Controls.MediaElement> a formant zapewnia inny sposób dodawania wideo do aplikacji. Tak więc kiedy należy używać <xref:System.Windows.Media.Drawing> obiektów? Aby wymusić <xref:System.Windows.Freezable> funkcje poziomu platformy w celu uzyskania korzyści z wydajności lub korzystania z funkcji. Ponieważ <xref:System.Windows.Media.Drawing> obiekty nie obsługują [układu](../advanced/layout.md), wejścia i koncentracji, zapewniają korzyści z wydajności, które są idealnym rozwiązaniem do opisywania tła, grafiki artystycznej i dla rysowania niskiego poziomu <xref:System.Windows.Media.Visual> z obiektami.  
  
 Ponieważ są one obiektem <xref:System.Windows.Freezable> typu, <xref:System.Windows.Media.Drawing> obiekty uzyskują kilka specjalnych funkcji, które obejmują następujące: mogą być deklarowane jako [zasoby](../advanced/xaml-resources.md), współużytkowane przez wiele obiektów, wykonywane tylko do odczytu w celu poprawy wydajności, klonowania i bezpieczny wątkowo. Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiekty, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Rysowanie kształtu  
 Aby narysować kształt, użyj <xref:System.Windows.Media.GeometryDrawing>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Właściwość rysowania geometrii zawiera opis kształtu do rysowania, jego <xref:System.Windows.Media.GeometryDrawing.Brush%2A> Właściwość opisuje sposób malowania wnętrza kształtu, a jego <xref:System.Windows.Media.GeometryDrawing.Pen%2A> Właściwość opisuje sposób rysowania konturów.  
  
 Poniższy przykład używa <xref:System.Windows.Media.GeometryDrawing> do rysowania kształtu. Kształt jest opisywany przez <xref:System.Windows.Media.GeometryGroup> i dwa <xref:System.Windows.Media.EllipseGeometry> obiekty. Wnętrze kształtu jest rysowane z <xref:System.Windows.Media.LinearGradientBrush> i jego kontur jest rysowany <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>przy użyciu.  
  
 Ten przykład tworzy następujące elementy <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dwie wielokropek](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Pełny przykład można znaleźć w temacie [Create a GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Inne <xref:System.Windows.Media.Geometry> klasy, takie jak <xref:System.Windows.Media.PathGeometry> umożliwienie tworzenia bardziej złożonych kształtów przez tworzenie krzywych i łuków. Aby uzyskać więcej informacji <xref:System.Windows.Media.Geometry> na temat obiektów, zobacz [Omówienie geometrii](geometry-overview.md).  
  
 Aby uzyskać więcej informacji na temat innych sposobów rysowania kształtów, które <xref:System.Windows.Media.Drawing> nie używają obiektów, zobacz [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Rysowanie obrazu  
 Aby narysować obraz, użyj <xref:System.Windows.Media.ImageDrawing>. Właściwość obiektu zawiera opis obrazu do rysowania, a jego <xref:System.Windows.Media.ImageDrawing.Rect%2A> Właściwość definiuje region, w którym jest rysowany obraz. <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.ImageDrawing.ImageSource%2A>  
  
 Poniższy przykład rysuje obraz do prostokąta znajdującego się w (75, 75), który jest 100 o 100 pikseli. Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.ImageDrawing> tworzenie przez przykład. Dodano szare obramowanie, aby pokazać granice elementu <xref:System.Windows.Media.ImageDrawing>.  
  
 ![A 100 do 100 ImageDrawing narysowana &#40;na 75,&#41; 75](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 o 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Aby uzyskać więcej informacji o obrazach, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Odtwórz multimedia (tylko kod)  
  
> [!NOTE]
> Chociaż można zadeklarować <xref:System.Windows.Media.VideoDrawing> w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można ładować i odtwarzać multimedia tylko przy użyciu kodu. Aby odtworzyć wideo w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], <xref:System.Windows.Controls.MediaElement> Użyj zamiast niego.  
  
 Aby odtworzyć plik audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>i. Istnieją dwa sposoby ładowania i odtwarzania multimediów. Pierwszym sposobem <xref:System.Windows.Media.MediaPlayer> jest użycie <xref:System.Windows.Media.VideoDrawing> i a przez siebie, a drugi — tworzenie <xref:System.Windows.Media.MediaPlayer> własnych <xref:System.Windows.Media.MediaTimeline> do użycia z i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu, takiego jak obraz. W pliku projektu należy zamiast tego ustawić `Content` typ nośnika na i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always`.  
  
 Aby odtwarzać multimedia bez tworzenia własnych <xref:System.Windows.Media.MediaTimeline>, wykonaj następujące czynności.  
  
1. Tworzy obiekt <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Użyj metody <xref:System.Windows.Media.MediaPlayer.Open%2A> , aby załadować plik multimedialny.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Określ rozmiar i lokalizację, aby narysować nośnik przez ustawienie <xref:System.Windows.Media.VideoDrawing.Rect%2A> właściwości. <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. <xref:System.Windows.Media.VideoDrawing.Player%2A> Ustaw właściwość <xref:System.Windows.Media.VideoDrawing> z utworzonym elementem <xref:System.Windows.Media.MediaPlayer> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Użyj metody, <xref:System.Windows.Media.MediaPlayer> aby rozpocząć odtwarzanie nośnika. <xref:System.Windows.Media.MediaPlayer.Play%2A>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Poniższy przykład używa <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> i, aby odtworzyć plik wideo jeden raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkową kontrolę czasu na nośniku, użyj <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> z i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline> Pozwala określić, czy film wideo powinien być powtarzany. Aby użyć programu <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.VideoDrawing>z programem, należy wykonać następujące czynności:  
  
1. Zadeklaruj <xref:System.Windows.Media.MediaTimeline> i ustaw jego zachowania chronometrażu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaClock> Utwórz<xref:System.Windows.Media.MediaTimeline>z.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Utwórz i Użyj, <xref:System.Windows.Media.MediaClock> aby ustawić jego <xref:System.Windows.Media.MediaPlayer.Clock%2A> właściwość. <xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. <xref:System.Windows.Media.VideoDrawing> Utwórz i <xref:System.Windows.Media.MediaPlayer> Przypisz do<xref:System.Windows.Media.VideoDrawing.Player%2A>Właściwości .<xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Poniższy przykład używa, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> a i <xref:System.Windows.Media.VideoDrawing> a, aby odtwarzać wideo wielokrotnie.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy pamiętać, że w przypadku korzystania <xref:System.Windows.Media.MediaTimeline>z programu można użyć interaktywnego <xref:System.Windows.Media.Animation.ClockController> powrotu <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwości do sterowania odtwarzaniem multimediów zamiast interaktywnych metod <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Rysuj tekst  
 Aby narysować tekst, użyj <xref:System.Windows.Media.GlyphRunDrawing> <xref:System.Windows.Media.GlyphRun>i. Poniższy przykład używa <xref:System.Windows.Media.GlyphRunDrawing> do rysowania tekstu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> jest obiektem niskiego poziomu, który jest przeznaczony do użycia w przypadku prezentacji dokumentów o stałym formacie i scenariuszy drukowania. Łatwiejszym sposobem rysowania tekstu na ekranie jest użycie <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>lub. Aby uzyskać więcej informacji <xref:System.Windows.Media.GlyphRun>na temat, zobacz [wprowadzenie do obiektu GlyphRun i elementów glifs](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) przegląd.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Rysunki złożone  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia łączenie wielu rysunków w pojedynczy rysunek złożony. Za pomocą <xref:System.Windows.Media.DrawingGroup>, można połączyć kształty, obrazy i tekst w jeden <xref:System.Windows.Media.Drawing> obiekt.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingGroup> do łączenia dwóch <xref:System.Windows.Media.GeometryDrawing> obiektów i <xref:System.Windows.Media.ImageDrawing> obiektu. Ten przykład generuje następujące dane wyjściowe.  
  
 ![Obiekt do rysowania z wieloma rysunkami](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Rysunek złożony  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup> Ponadto umożliwia zastosowanie masek kryjących, transformacji, efektów mapy bitowej i innych operacji do jej zawartości. <xref:System.Windows.Media.DrawingGroup>operacje są stosowane w następującej kolejności: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>,,, i <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Na poniższej ilustracji przedstawiono kolejność, w której <xref:System.Windows.Media.DrawingGroup> są stosowane operacje.  
  
 ![Kolejność operacji na rysunku](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji na obiektach do rysowania  
  
 W poniższej tabeli opisano właściwości, których można użyć do manipulowania <xref:System.Windows.Media.DrawingGroup> zawartością obiektu.  
  
|Właściwość|Opis|Ilustracji|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Zmienia nieprzezroczystość wybranych części <xref:System.Windows.Media.DrawingGroup> zawartości. Aby zapoznać się z przykładem, zobacz [How to: Kontroluj nieprzezroczystość rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Obiekt typu rysowanie z maską] nieprzezroczystości (./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Jednorodnie zmienia nieprzezroczystość <xref:System.Windows.Media.DrawingGroup> zawartości. Użyj tej właściwości, aby uczynić <xref:System.Windows.Media.Drawing> przezroczystą lub częściowo przezroczystą. Aby zapoznać się z przykładem, zobacz [How to: Zastosuj maskę nieprzezroczystość do](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))rysunku.|![DrawingGroups z różnymi ustawieniami] nieprzezroczystości (./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|<xref:System.Windows.Media.Effects.BitmapEffect> Stosuje<xref:System.Windows.Media.DrawingGroup> do zawartości. Aby zapoznać się z przykładem, zobacz [How to: Zastosuj efektu bitmapy do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Rysowanie z BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Przycina zawartość do regionu, który jest opisywany <xref:System.Windows.Media.Geometry>przy użyciu. <xref:System.Windows.Media.DrawingGroup> Aby zapoznać się z przykładem, zobacz [How to: Przytnij rysunek](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Rysowanie ze zdefiniowanym regionem przycinania](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Przyciąga niezależne od urządzenia piksele do pikseli urządzenia zgodnie z określonymi wskazówkami. Ta właściwość jest przydatna do zapewnienia, że dokładniej szczegółowe renderowanie grafiki na wyświetlaczach o niskiej rozdzielczości DPI. Aby zapoznać się z przykładem, zobacz temat [stosowanie GuidelineSet do rysunku](how-to-apply-a-guidelineset-to-a-drawing.md).|![Obiekt do rysowania z i bez GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Przekształca <xref:System.Windows.Media.DrawingGroup> zawartość. Aby zapoznać się z przykładem, zobacz [How to: Zastosuj transformację do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Obrócona przerysowanie](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Wyświetlanie rysunku jako obrazu  
 Aby <xref:System.Windows.Media.Drawing> wyświetlić <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image.Source%2A> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> formant z kontrolką<xref:System.Windows.Controls.Image> , Użyj jako kontrolki i ustaw właściwość obiektu na rysunek, który chcesz wyświetlić. <xref:System.Windows.Controls.Image>  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> i kontrolki do wyświetlenia <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![GeometryDrawing dwie wielokropek](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Malowanie obiektu za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> to typ pędzla, który maluje obszar z obiektem rysunkowym. Można jej użyć do malowania tylko dowolnego obiektu graficznego z rysunkiem. <xref:System.Windows.Media.Drawing> Właściwość<xref:System.Windows.Media.DrawingBrush> klasy opisuje .<xref:System.Windows.Media.DrawingBrush.Drawing%2A> Aby renderować a <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush>za pomocą, Dodaj go do <xref:System.Windows.Media.Drawing> pędzla przy użyciu właściwości pędzla i użyj pędzla do malowania obiektu graficznego, takiego jak kontrolka lub panel.  
  
 W poniższych przykładach używa <xref:System.Windows.Media.DrawingBrush> się do <xref:System.Windows.Shapes.Shape.Fill%2A> malowania <xref:System.Windows.Shapes.Rectangle> elementu z wzorcem utworzonym na <xref:System.Windows.Media.GeometryDrawing>podstawie. Ten przykład generuje następujące dane wyjściowe.  
  
 ![DrawingBrush z sąsiadującą](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing używany z DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Klasa zawiera różne opcje rozciągania i rozmieszczania zawartości. Aby uzyskać więcej informacji <xref:System.Windows.Media.DrawingBrush>na temat, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Renderowanie rysunku przy użyciu wizualizacji  
 A <xref:System.Windows.Media.DrawingVisual> jest typem obiektu wizualizacji zaprojektowanego do renderowania rysunku. Praca bezpośrednio w warstwie wizualnej jest opcją dla deweloperów, którzy chcą utworzyć wysoce dostosowane środowisko graficzne i nie jest opisana w tym omówieniu. Aby uzyskać więcej informacji, zobacz temat [Korzystanie z użycie DrawingVisual obiektów](using-drawingvisual-objects.md) — Omówienie.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext — obiekty  
 Klasa umożliwia <xref:System.Windows.Media.Visual> wypełnienie lub<xref:System.Windows.Media.Drawing> z zawartością wizualną. <xref:System.Windows.Media.DrawingContext> Wiele takich obiektów grafiki niższego poziomu używa, <xref:System.Windows.Media.DrawingContext> ponieważ opisuje ona zawartość graficzną bardzo wydajnie.  
  
 Chociaż metody <xref:System.Drawing.Graphics?displayProperty=nameWithType> rysowania wyglądają podobnie jak metody rysowania typu, są one bardzo różne. <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingContext>jest używany z systemem grafiki trybu zachowywania, podczas gdy <xref:System.Drawing.Graphics?displayProperty=nameWithType> typ jest używany z systemem graficznym trybu natychmiastowego. Gdy używasz <xref:System.Windows.Media.DrawingContext> poleceń rysowania obiektu, w rzeczywistości zapisujesz zestaw instrukcji renderowania (Chociaż dokładny mechanizm magazynowania zależy od typu obiektu, który <xref:System.Windows.Media.DrawingContext>dostarcza), który będzie później używany przez system grafiki. nie są rysowane na ekranie w czasie rzeczywistym. Aby uzyskać więcej informacji na temat działania systemu grafiki Windows Presentation Foundation (WPF), zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).  
  
 Nigdy nie tworzysz bezpośrednio wystąpienia <xref:System.Windows.Media.DrawingContext>. Możesz jednak uzyskać kontekst rysowania z określonych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Wyliczanie zawartości wizualizacji  
 Oprócz innych obiektów, <xref:System.Windows.Media.Drawing> obiekty również udostępniają model obiektów do wyliczania zawartości. <xref:System.Windows.Media.Visual>  
  
 W poniższym przykładzie zastosowano <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, aby <xref:System.Windows.Media.DrawingGroup> pobrać wartość <xref:System.Windows.Media.Visual> a i wyliczyć ją.  
  
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
