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
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186541"
---
# <a name="drawing-objects-overview"></a>Przegląd Rysowanie obiektów
W tym <xref:System.Windows.Media.Drawing> temacie przedstawiono obiekty i opisano sposób ich efektywnego rysowania kształtów, map bitowych, tekstu i nośników. Obiekty <xref:System.Windows.Media.Drawing> są używane podczas tworzenia obiektów <xref:System.Windows.Media.DrawingBrush>clipart, malowania obiektami lub używania <xref:System.Windows.Media.Visual> obiektów.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Co to jest obiekt rysunkowy?  
 Obiekt <xref:System.Windows.Media.Drawing> opisuje widoczną zawartość, taką jak kształt, mapa bitowa, wideo lub wiersz tekstu. Różne typy rysunków opisują różne typy zawartości. Poniżej znajduje się lista różnych typów obiektów rysunkowych.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>– Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Rysuje tekst.  
  
- <xref:System.Windows.Media.VideoDrawing>– Odtwarza plik audio lub wideo.  
  
- <xref:System.Windows.Media.DrawingGroup>– Rysuje inne rysunki. Grupa rysunków służy do łączenia innych rysunków w pojedynczy rysunek złożony.  
  
 <xref:System.Windows.Media.Drawing>obiekty są wszechstronne; istnieje wiele sposobów użycia <xref:System.Windows.Media.Drawing> obiektu.  
  
- Można go wyświetlić jako obraz <xref:System.Windows.Media.DrawingImage> za <xref:System.Windows.Controls.Image> pomocą i formantu.  
  
- Można go użyć <xref:System.Windows.Media.DrawingBrush> z a do malowania <xref:System.Windows.Controls.Page.Background%2A> obiektu, takiego jak . <xref:System.Windows.Controls.Page>  
  
- Można go użyć do opisania <xref:System.Windows.Media.DrawingVisual>wyglądu pliku .  
  
- Można go użyć do wyliczenia <xref:System.Windows.Media.Visual>zawartości pliku .  
  
 WPF WPF udostępnia inne typy obiektów, które są zdolne do rysowania kształtów, bitmap, tekstu i nośnika. Na przykład można również <xref:System.Windows.Shapes.Shape> użyć obiektów do rysowania kształtów, a <xref:System.Windows.Controls.MediaElement> formant zapewnia inny sposób dodawania wideo do aplikacji. Więc kiedy należy <xref:System.Windows.Media.Drawing> używać obiektów? Kiedy można poświęcić funkcje na poziomie struktury, aby uzyskać korzyści z wydajności lub gdy potrzebujesz <xref:System.Windows.Freezable> funkcji. Ponieważ <xref:System.Windows.Media.Drawing> obiekty nie obsługują [układu,](../advanced/layout.md)danych wejściowych i fokusowych, zapewniają one korzyści z wydajności, które <xref:System.Windows.Media.Visual> czynią je idealnymi do opisywania tła, obiektów clipart i do rysowania niskopoziomowego z obiektami.  
  
 Ponieważ są one <xref:System.Windows.Freezable> obiektem typu, <xref:System.Windows.Media.Drawing> obiekty uzyskują kilka specjalnych funkcji, które obejmują następujące: mogą być zadeklarowane jako [zasoby,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)współużytkowane przez wiele obiektów, wykonane tylko do odczytu w celu zwiększenia wydajności, sklonowane i wykonane wątku bezpieczne. Aby uzyskać więcej informacji na <xref:System.Windows.Freezable> temat różnych funkcji udostępnianych przez obiekty, zobacz [Omówienie obiektów freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Rysowanie kształtu  
 Aby narysować kształt, <xref:System.Windows.Media.GeometryDrawing>należy użyć pliku . <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Właściwość rysunku geometrii opisuje kształt do <xref:System.Windows.Media.GeometryDrawing.Brush%2A> rysowania, jego właściwość opisuje sposób malowania wnętrza kształtu, a jego <xref:System.Windows.Media.GeometryDrawing.Pen%2A> właściwość opisuje sposób rysowania jego konturu.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.GeometryDrawing> do narysowania kształtu. Kształt jest opisany przez <xref:System.Windows.Media.GeometryGroup> a <xref:System.Windows.Media.EllipseGeometry> i dwa obiekty. Wnętrze kształtu jest pomalowane <xref:System.Windows.Media.LinearGradientBrush> a, a jego <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>kontur jest rysowany za pomocą .  
  
 W tym przykładzie tworzy się następujące <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometriaDrawing dwóch elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
A GeometriaDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Aby uzyskać pełny przykład, zobacz [Tworzenie geometriiDrawing](how-to-create-a-geometrydrawing.md).  
  
 Inne <xref:System.Windows.Media.Geometry> klasy, <xref:System.Windows.Media.PathGeometry> takie jak umożliwia tworzenie bardziej złożonych kształtów przez tworzenie krzywych i łuków. Aby uzyskać <xref:System.Windows.Media.Geometry> więcej informacji o obiektach, zobacz [Omówienie geometrii](geometry-overview.md).  
  
 Aby uzyskać więcej informacji na temat innych sposobów <xref:System.Windows.Media.Drawing> rysowania kształtów, które nie używają obiektów, zobacz [Kształty i Rysunek podstawowy w przeglądzie WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Rysowanie obrazu  
 Aby narysować obraz, <xref:System.Windows.Media.ImageDrawing>należy użyć pliku . Właściwość <xref:System.Windows.Media.ImageDrawing> obiektu opisuje obraz do rysowania, a jego <xref:System.Windows.Media.ImageDrawing.Rect%2A> właściwość definiuje region, w którym jest rysowany obraz. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A>  
  
 Poniższy przykład rysuje obraz do prostokąta znajdującego się w (75,75), który jest 100 na 100 pikseli. Na poniższej <xref:System.Windows.Media.ImageDrawing> ilustracji przedstawiono utworzone przez przykład. Dodano szare obramowanie, aby <xref:System.Windows.Media.ImageDrawing>pokazać granice pliku .  
  
 ![A 100 na 100 ImageDrawing sporządzone na &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 na 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Aby uzyskać więcej informacji o obrazach, zobacz [Omówienie obrazowania](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Odtwarzanie multimediów (tylko kod)  
  
> [!NOTE]
> Chociaż można <xref:System.Windows.Media.VideoDrawing> zadeklarować [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]w , można tylko załadować i odtworzyć jego nośnika przy użyciu kodu. Aby odtworzyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]wideo <xref:System.Windows.Controls.MediaElement> w , użyj zamiast tego.  
  
 Aby odtworzyć plik audio lub <xref:System.Windows.Media.VideoDrawing> wideo, <xref:System.Windows.Media.MediaPlayer>należy użyć a i . Istnieją dwa sposoby ładowania i odtwarzania multimediów. Pierwszym z nich <xref:System.Windows.Media.MediaPlayer> jest <xref:System.Windows.Media.VideoDrawing> użycie i a przez siebie, a <xref:System.Windows.Media.MediaTimeline> drugim sposobem <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>jest stworzenie własnego do wykorzystania z i .  
  
> [!NOTE]
> Podczas dystrybucji multimediów z aplikacją nie można używać pliku multimedialnego jako zasobu projektu, tak jak obraz. W pliku projektu należy zamiast tego ustawić `Content` typ `CopyToOutputDirectory` nośnika i ustawić na `PreserveNewest` lub . `Always`  
  
 Aby odtwarzać multimedia bez <xref:System.Windows.Media.MediaTimeline>tworzenia własnych , wykonaj następujące kroki.  
  
1. Utwórz <xref:System.Windows.Media.MediaPlayer> obiekt.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Użyj <xref:System.Windows.Media.MediaPlayer.Open%2A> metody, aby załadować plik multimedialny.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.VideoDrawing>plik .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Określ rozmiar i lokalizację, aby <xref:System.Windows.Media.VideoDrawing.Rect%2A> narysować <xref:System.Windows.Media.VideoDrawing>nośnik, ustawiając właściwość pliku .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Ustaw <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwość <xref:System.Windows.Media.VideoDrawing> utworzonego utworu. <xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Użyj <xref:System.Windows.Media.MediaPlayer.Play%2A> metody, <xref:System.Windows.Media.MediaPlayer> aby rozpocząć odtwarzanie multimediów.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.VideoDrawing> i a <xref:System.Windows.Media.MediaPlayer> do jednorazowego odtwo wyświetlenia pliku wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkową kontrolę czasu nad <xref:System.Windows.Media.MediaTimeline> nośnikiem, należy użyć a z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów. Umożliwia <xref:System.Windows.Media.MediaTimeline> określenie, czy film ma się powtarzać. Aby użyć <xref:System.Windows.Media.MediaTimeline> a <xref:System.Windows.Media.VideoDrawing>z , należy wykonać następujące kroki:  
  
1. Zadeklarować <xref:System.Windows.Media.MediaTimeline> i ustawić jego zachowania chronometrażu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Utwórz <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline>pliku .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.MediaClock> użyj, <xref:System.Windows.Media.MediaPlayer.Clock%2A> aby ustawić jego właściwość.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Utworzyć <xref:System.Windows.Media.VideoDrawing> i przypisać <xref:System.Windows.Media.MediaPlayer> do <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwości <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 W poniższym przykładzie <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> użyto <xref:System.Windows.Media.VideoDrawing> a i a do wielokrotnego odtwarzania wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy zauważyć, że <xref:System.Windows.Media.MediaTimeline>podczas korzystania z <xref:System.Windows.Media.Animation.ClockController> programu <xref:System.Windows.Media.Animation.Clock.Controller%2A> , użyjesz interaktywnej zwracanej z <xref:System.Windows.Media.MediaClock> właściwości <xref:System.Windows.Media.MediaPlayer>do sterowania odtwarzaniem multimediów zamiast interaktywnych metod .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Rysowanie tekstu  
 Aby narysować tekst, <xref:System.Windows.Media.GlyphRunDrawing> należy <xref:System.Windows.Media.GlyphRun>użyć a i . W poniższym przykładzie użyto a <xref:System.Windows.Media.GlyphRunDrawing> do narysowania tekstu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> jest obiektem niskiego poziomu przeznaczonym do użytku z prezentacją dokumentu o stałym formacie i scenariuszami drukowania. Prostszym sposobem rysowania tekstu na ekranie <xref:System.Windows.Controls.TextBlock>jest użycie przycisku <xref:System.Windows.Controls.Label> lub . Aby uzyskać <xref:System.Windows.Media.GlyphRun>więcej informacji na temat , zobacz [Wprowadzenie do obiektu glifów i glify element](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) omówienia.  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Rysunki kompozytowe  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia łączenie wielu rysunków w jeden rysunek złożony. Za pomocą <xref:System.Windows.Media.DrawingGroup>programu , można łączyć kształty, <xref:System.Windows.Media.Drawing> obrazy i tekst w jeden obiekt.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.DrawingGroup> do połączenia dwóch <xref:System.Windows.Media.GeometryDrawing> obiektów i obiektu. <xref:System.Windows.Media.ImageDrawing> W tym przykładzie daje następujące dane wyjściowe.  
  
 ![Grupa rysunków z wieloma rysunkami](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Rysunek złożony  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia również stosowanie masek krycia, przekształceń, efektów bitmapowych i innych operacji do jego zawartości. <xref:System.Windows.Media.DrawingGroup>operacje są stosowane w następującej <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>kolejności: , <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Na poniższej ilustracji <xref:System.Windows.Media.DrawingGroup> przedstawiono kolejność, w jakiej są stosowane operacje.  
  
 ![Kolejność operacji grupy rysunkowej](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji grupy rysunkowej  
  
 W poniższej tabeli opisano właściwości, których <xref:System.Windows.Media.DrawingGroup> można używać do manipulowania zawartością obiektu.  
  
|Właściwość|Opis|Ilustracji|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Zmienia krycie wybranych części <xref:System.Windows.Media.DrawingGroup> zawartości. Na przykład zobacz [Jak: Sterowanie kryciem rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Grupa rysunkowa z maską krycia](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Jednolicie zmienia krycie <xref:System.Windows.Media.DrawingGroup> zawartości. Ta właściwość służy <xref:System.Windows.Media.Drawing> do przezroczystego lub częściowo przezroczystego. Na przykład zobacz [Jak: Stosowanie maski krycia do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Grupy rysunku z różnymi ustawieniami krycia](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Stosuje a <xref:System.Windows.Media.Effects.BitmapEffect> do <xref:System.Windows.Media.DrawingGroup> zawartości. Na przykład zobacz [Jak: Stosowanie bitmapowego efektu do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Grupa rysunku z efektem BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Przycina <xref:System.Windows.Media.DrawingGroup> zawartość do regionu opisanego za pomocą pliku <xref:System.Windows.Media.Geometry>. Na przykład zobacz [Jak: Przycinanie rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Grupa rysunku ze zdefiniowanym regionem klipu](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Przyciąga piksele niezależne od urządzenia do pikseli urządzenia zgodnie z określonymi wytycznymi. Ta właściwość jest przydatna do zapewnienia, że precyzyjnie szczegółowe grafiki renderowania ostro na wyświetlaczach o niskiej rozdzielczości DPI. Na przykład zobacz [Stosowanie zestawu wytycznych do rysunku](how-to-apply-a-guidelineset-to-a-drawing.md).|![Grupa rysunkowa z zestawem wytycznych i bez niego](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Przekształca <xref:System.Windows.Media.DrawingGroup> zawartość. Na przykład zobacz [Jak: Stosowanie przekłęce do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Grupa rysunku obrócona](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Wyświetlanie rysunku jako obrazu  
 Aby wyświetlić <xref:System.Windows.Controls.Image> z formantem, <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Image.Source%2A> <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingImage> użyj jako formantu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> i ustaw właściwość <xref:System.Windows.Media.DrawingImage> obiektu na rysunek, który ma być wyświetlany.  
  
 W poniższym przykładzie <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> użyto formantu i formantu do wyświetlenia pliku <xref:System.Windows.Media.GeometryDrawing>. W tym przykładzie daje następujące dane wyjściowe.  
  
 ![GeometriaDrawing dwóch elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
A DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Malowanie obiektu rysunkiem  
 A <xref:System.Windows.Media.DrawingBrush> jest typem pędzla, który maluje obszar za pomocą obiektu rysunkowego. Można go użyć do malowania prawie każdego obiektu graficznego rysunkiem. Właściwość <xref:System.Windows.Media.Drawing> a <xref:System.Windows.Media.DrawingBrush> opisuje <xref:System.Windows.Media.DrawingBrush.Drawing%2A>jego . Aby renderować <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush>za pomocą programu , dodaj go <xref:System.Windows.Media.Drawing> do pędzla za pomocą właściwości pędzla i użyj pędzla do malowania obiektu graficznego, takiego jak formant lub panel.  
  
 Poniższe przykłady używa <xref:System.Windows.Media.DrawingBrush> do <xref:System.Windows.Shapes.Shape.Fill%2A> malowania <xref:System.Windows.Shapes.Rectangle> wzoru utworzonego <xref:System.Windows.Media.GeometryDrawing>na podstawie . W tym przykładzie daje następujące dane wyjściowe.  
  
 ![Szczotka do rysowania w kafelkach](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
A GeometryDrawing używany z DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 Klasa <xref:System.Windows.Media.DrawingBrush> zawiera wiele opcji rozciągania i układania kafli jego zawartości. Aby uzyskać <xref:System.Windows.Media.DrawingBrush>więcej informacji na temat , zobacz [Malowanie obrazami, rysunkami i wizualizacjami.](painting-with-images-drawings-and-visuals.md)  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Renderowanie rysunku za pomocą wizualizacji  
 A <xref:System.Windows.Media.DrawingVisual> jest typem obiektu wizualnego przeznaczonego do renderowania rysunku. Praca bezpośrednio w warstwie wizualnej jest opcją dla deweloperów, którzy chcą zbudować wysoce dostosowane środowisko graficzne i nie jest opisana w tym przeglądzie. Aby uzyskać więcej informacji, zobacz [using DrawingVisual Objects](using-drawingvisual-objects.md) overview.  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>DrawingContext Obiekty  
 Klasa <xref:System.Windows.Media.DrawingContext> umożliwia wypełnianie zawartości <xref:System.Windows.Media.Visual> wizualnej <xref:System.Windows.Media.Drawing> lub a. Wiele takich obiektów graficznych <xref:System.Windows.Media.DrawingContext> niższego poziomu używa, ponieważ bardzo efektywnie opisuje zawartość graficzną.  
  
 Chociaż <xref:System.Windows.Media.DrawingContext> metody rysowania są podobne do <xref:System.Drawing.Graphics?displayProperty=nameWithType> metod rysowania typu, w rzeczywistości są one bardzo różne. <xref:System.Windows.Media.DrawingContext>jest używany z systemem graficznym w <xref:System.Drawing.Graphics?displayProperty=nameWithType> trybie zachowanym, podczas gdy typ jest używany z systemem graficznym w trybie natychmiastowym. Podczas korzystania <xref:System.Windows.Media.DrawingContext> z poleceń rysowania obiektu, są rzeczywiście przechowywania zestaw instrukcji renderowania (chociaż dokładny mechanizm przechowywania zależy <xref:System.Windows.Media.DrawingContext>od typu obiektu, który dostarcza ), który będzie później używany przez system graficzny; nie rysujesz na ekranie w czasie rzeczywistym. Aby uzyskać więcej informacji na temat działania systemu graficznego Windows Presentation Foundation (WPF), zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).  
  
 Nigdy nie bezpośrednio utworzyć <xref:System.Windows.Media.DrawingContext>wystąpienia; można jednak uzyskać kontekst rysunkowy z niektórych <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>metod, takich jak i .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Wyliczanie zawartości wizualizacji  
 Oprócz innych zastosowań obiekty <xref:System.Windows.Media.Drawing> zapewniają również model obiektów do wyliczania <xref:System.Windows.Media.Visual>zawartości programu .  
  
 W poniższym przykładzie <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> użyto <xref:System.Windows.Media.DrawingGroup> metody do <xref:System.Windows.Media.Visual> pobrania wartości a i wyliczyć go.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przegląd Geometria](geometry-overview.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
- [Tematy in jakże](drawings-how-to-topics.md)
