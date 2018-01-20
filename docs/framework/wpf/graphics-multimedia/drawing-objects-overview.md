---
title: "Przegląd Rysowanie obiektów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9b77b47a3f3ade27f2ba86304b1868a8d388482
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="drawing-objects-overview"></a>Przegląd Rysowanie obiektów
W tym temacie przedstawiono <xref:System.Windows.Media.Drawing> obiekty i opisuje sposób umożliwia wydajne Rysowanie kształtów, mapy bitowe, tekst i nośnika. Użyj <xref:System.Windows.Media.Drawing> malować obiekty podczas tworzenia obiektów graficznych, <xref:System.Windows.Media.DrawingBrush>, lub użyj <xref:System.Windows.Media.Visual> obiektów.  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co to jest obiekt rysunku?  
 A <xref:System.Windows.Media.Drawing> obiektu opisuje widocznej zawartości, takich jak kształtu, mapy bitowej, wideo lub wiersza tekstu. Różne typy rysunki opis różnych typów zawartości. Poniżej znajduje się lista różnych typów obiektów rysowania.  
  
-   <xref:System.Windows.Media.GeometryDrawing>— Rysuje kształt.  
  
-   <xref:System.Windows.Media.ImageDrawing>— Rysuje obraz.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>— Rysuje tekst.  
  
-   <xref:System.Windows.Media.VideoDrawing>— Odtwarza plik audio i wideo.  
  
-   <xref:System.Windows.Media.DrawingGroup>— Rysuje inne rysunki. Użyj grupy rysunku, aby połączyć inne rysunki w jeden złożonego.  
  
 <xref:System.Windows.Media.Drawing>obiekty są uniwersalne; istnieje wiele sposobów, można użyć <xref:System.Windows.Media.Drawing> obiektu.  
  
-   Można wyświetlić jako obraz za pomocą <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu.  
  
-   Użytkownik może być używany z <xref:System.Windows.Media.DrawingBrush> do rysowania obiektu, takie jak <xref:System.Windows.Controls.Page.Background%2A> z <xref:System.Windows.Controls.Page>.  
  
-   Służy do opisywania wygląd <xref:System.Windows.Media.DrawingVisual>.  
  
-   Służy do analizy zawartości <xref:System.Windows.Media.Visual>.  
  
 WPF zawiera inne typy obiektów, które obsługują rysowanie kształtów, mapy bitowe, tekst i nośnika. Na przykład umożliwia także <xref:System.Windows.Shapes.Shape> obiektów rysowanie kształtów i <xref:System.Windows.Controls.MediaElement> kontrola zapewnia inny sposób dodawania wideo do aplikacji. Dlatego kiedy korzystać z <xref:System.Windows.Media.Drawing> obiektów? Gdy pochodzących z poziomu funkcji framework do korzyści wydajności lub należy <xref:System.Windows.Freezable> funkcji. Ponieważ <xref:System.Windows.Media.Drawing> obiektów nie obsługują [układu](../../../../docs/framework/wpf/advanced/layout.md)należy wprowadzić i skoncentrować się, zapewniają korzyści wydajności, które były nadaje się doskonale dla opisujący tło, grafikę klip i niskiego poziomu rysunku z <xref:System.Windows.Media.Visual> obiektów.  
  
 Ponieważ są one typu <xref:System.Windows.Freezable> obiektu <xref:System.Windows.Media.Drawing> obiektów uzyskać kilka specjalne funkcje, takie jak: mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md)współużytkowanych przez wiele obiektów, aby poprawić jest tylko do odczytu wydajność, sklonowany, a wprowadzone wątkowo. Aby uzyskać więcej informacji o różnych funkcjach dostarczonych przez <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Rysuj kształt  
 Rysuj kształt, należy użyć <xref:System.Windows.Media.GeometryDrawing>. Na rysunku geometrii <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> właściwości opisującą kształt do rysowania, jego <xref:System.Windows.Media.GeometryDrawing.Brush%2A> właściwość opisuje, jak jest rysowane wewnątrz kształtu i jego <xref:System.Windows.Media.GeometryDrawing.Pen%2A> właściwość opisuje, jak powinien być rysowany konturu jej.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> Aby narysować kształt. Kształt jest opisane przez <xref:System.Windows.Media.GeometryGroup> i dwa <xref:System.Windows.Media.EllipseGeometry> obiektów. Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej jest rysowany z <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 W tym przykładzie tworzy następujące <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing zawierający dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Obiekt GeometryDrawing zawierający  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Aby uzyskać pełny przykład, zobacz [Utwórz obiekt GeometryDrawing zawierający](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 Inne <xref:System.Windows.Media.Geometry> klas, takich jak <xref:System.Windows.Media.PathGeometry> umożliwiają tworzenie bardziej złożonych kształtów tworząc krzywych i łuków. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Geometry> obiekty, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Aby uzyskać więcej informacji na temat innych sposobów Rysowanie kształtów, które nie używają <xref:System.Windows.Media.Drawing> obiekty, zobacz [kształtów i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Rysowanie obrazów  
 Aby narysować obrazu, należy użyć <xref:System.Windows.Media.ImageDrawing>. <xref:System.Windows.Media.ImageDrawing> Obiektu <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> właściwość opisuje obrazu do rysowania, a jego <xref:System.Windows.Media.ImageDrawing.Rect%2A> właściwość definiuje region, gdzie jest rysowany obrazu.  
  
 Poniższy przykład Rysuje obraz do prostokąta znajduje się w punkcie (75,75) czyli 100 x 100 pikseli. Na poniższej ilustracji pokazano <xref:System.Windows.Media.ImageDrawing> powstały w przykładzie. Dodano szarego obramowania pokazanie granice <xref:System.Windows.Media.ImageDrawing>.  
  
 ![100 x 100 Obiekt ImageDrawing o rozmiarze rysowane &#40; 75,75 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
Obiekt ImageDrawing o rozmiarze 100 na 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Aby uzyskać więcej informacji na temat obrazów, zobacz [Imaging omówienie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Odtwarzanie multimediów (tylko kod)  
  
> [!NOTE]
>  Mimo że można zadeklarować <xref:System.Windows.Media.VideoDrawing> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można tylko załadowanie i odtworzenie jej nośnika przy użyciu kodu. Do odtwarzania wideo w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], użyj <xref:System.Windows.Controls.MediaElement> zamiast tego.  
  
 Do odtwarzania pliku audio i wideo, użyj <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>. Istnieją dwa sposoby do ładowania i odtwarzanie multimediów. Pierwsza to użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi sposób polega na utworzeniu własnych <xref:System.Windows.Media.MediaTimeline> do użycia z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Do rozpowszechniania nośnika z aplikacji, nie można użyć pliku multimedialnego jako zasób projektu, jak w przypadku obrazu. W pliku projektu, należy zamiast tego ustawić typ nośnika `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.  
  
 Do odtwarzania multimediów bez tworzenia własnego <xref:System.Windows.Media.MediaTimeline>, wykonaj następujące kroki.  
  
1.  Utwórz <xref:System.Windows.Media.MediaPlayer> obiektu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Użyj <xref:System.Windows.Media.MediaPlayer.Open%2A> metodę, aby załadować plik nośnika.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Utwórz <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Określ rozmiar i położenie do rysowania nośnika przez ustawienie <xref:System.Windows.Media.VideoDrawing.Rect%2A> właściwość <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Ustaw <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwość <xref:System.Windows.Media.VideoDrawing> z <xref:System.Windows.Media.MediaPlayer> utworzony.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Użyj <xref:System.Windows.Media.MediaPlayer.Play%2A> metody <xref:System.Windows.Media.MediaPlayer> aby rozpocząć odtwarzanie nośnika.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania plików wideo raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkowe chronometrażu kontrolę nad nośnik, użyj <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline> Umożliwia określenie, czy należy powtórzyć wideo. Aby użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.VideoDrawing>, wykonaj następujące czynności:  
  
1.  Deklarowanie <xref:System.Windows.Media.MediaTimeline> i ustaw jego zachowania chronometrażu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Utwórz <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Utwórz <xref:System.Windows.Media.MediaPlayer> i użyj <xref:System.Windows.Media.MediaClock> można ustawić jej <xref:System.Windows.Media.MediaPlayer.Clock%2A> właściwości.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Utwórz <xref:System.Windows.Media.VideoDrawing> i przypisz <xref:System.Windows.Media.MediaPlayer> do <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwość <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> powtarzanie odtwarzania wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy zauważyć, że gdy używasz <xref:System.Windows.Media.MediaTimeline>, możesz użyć interakcyjnego <xref:System.Windows.Media.Animation.ClockController> zwrócony z <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.MediaClock> odtwarzanie multimediów formantu zamiast metody interakcyjne <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Rysowanie tekstu  
 Rysowanie tekstu, należy użyć <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.GlyphRun>. W poniższym przykładzie użyto <xref:System.Windows.Media.GlyphRunDrawing> pisania tekstu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> jest obiektem niskiego poziomu przeznaczony do użycia w ustalonym formacie dokumentu prezentacji i scenariusze drukowania. Rysowanie tekstu na ekranie prostszy sposób jest użycie <xref:System.Windows.Controls.Label> lub <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.GlyphRun>, zobacz [wprowadzenie do obiektu GlyphRun obiektu i symboli](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) omówienie.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Rysunki złożone  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia łączenie wielu rysunków w jeden złożonego. Za pomocą <xref:System.Windows.Media.DrawingGroup>, można łączyć kształty, obrazy i tekst w pojedynczy <xref:System.Windows.Media.Drawing> obiektu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingGroup> do łączenia dwóch <xref:System.Windows.Media.GeometryDrawing> obiektów i <xref:System.Windows.Media.ImageDrawing> obiektu. W tym przykładzie tworzy następujące dane wyjściowe.  
  
 ![Obiekt DrawingGroup z wielu rysunków](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Rysowanie złożone  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia także zastosowanie nieprzezroczystość maski, transformacje efekty mapy bitowej i innych operacji do jego zawartości. <xref:System.Windows.Media.DrawingGroup>operacje są stosowane w następującej kolejności: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Na poniższej ilustracji przedstawiono kolejność, w którym <xref:System.Windows.Media.DrawingGroup> operacji są stosowane.  
  
 ![Kolejność operacji obiektu DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji DrawingGroup  
  
 W poniższej tabeli opisano właściwości można użyć do manipulowania <xref:System.Windows.Media.DrawingGroup> zawartości obiektu.  
  
|Właściwość|Opis|Illustration|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Zmienia nieprzezroczystość zaznaczonych części <xref:System.Windows.Media.DrawingGroup> zawartość. Na przykład zobacz [porady: kontrolowanie przezroczystości rysunku](http://msdn.microsoft.com/library/68580652-7d32-4d27-93cc-a5148cf4d5ee).|![Obiekt DrawingGroup z maskę przezroczystości](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Zmienia jednolicie nieprzezroczystość <xref:System.Windows.Media.DrawingGroup> zawartość. Używaj tej właściwości umożliwia <xref:System.Windows.Media.Drawing> przezroczystego lub częściowo przezroczysty. Na przykład, zobacz [porady: stosowanie maskę przezroczystości do rysunku](http://msdn.microsoft.com/library/d77b420b-9be2-479c-a45e-82f4da30eb9f).|![Obiekty DrawingGroup z różnymi ustawieniami nieprzezroczystości](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Stosuje <xref:System.Windows.Media.Effects.BitmapEffect> do <xref:System.Windows.Media.DrawingGroup> zawartość. Na przykład, zobacz [porady: stosowanie właściwości BitmapEffect do rysunku](http://msdn.microsoft.com/library/c5b1de83-8d09-47fb-96db-5f174471f4b5).|![DrawingGroup z obiektem BlurBitmapEffect](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Klipy <xref:System.Windows.Media.DrawingGroup> zawartość w regionie opisywane przy użyciu <xref:System.Windows.Media.Geometry>. Na przykład zobacz [porady: obcina rysunku](http://msdn.microsoft.com/library/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058) .|![DrawingGroup ze zdefiniowanym obszarem przycinania](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Przyciąganie pikselach niezależnych od urządzenia na urządzeniu pikseli wzdłuż określonych wytycznych. Ta właściwość jest przydatne w celu znacznie renderowania grafiki precyzyjne szczegółowe na ekranach niskiej rozdzielczości. Na przykład zobacz [dotyczą właściwością GuidelineSet rysunku](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).|![Obiekt DrawingGroup z włączonymi i wyłączonymi właściwością GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Przekształca <xref:System.Windows.Media.DrawingGroup> zawartość. Na przykład zobacz [porady: zastosowanie transformacji do rysunku](http://msdn.microsoft.com/library/0d525f2b-682d-4d67-9660-cf46929fbabd).|![A obracać DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Wyświetl rysunku jako obrazu  
 Aby wyświetlić <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Controls.Image> kontrolować, użyj <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> formantu <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwości do rysunku mają być wyświetlane.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu, aby wyświetlić <xref:System.Windows.Media.GeometryDrawing>. W tym przykładzie tworzy następujące dane wyjściowe.  
  
 ![GeometryDrawing zawierający dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Malowanie obiektu z rysunkiem  
 A <xref:System.Windows.Media.DrawingBrush> jest typu pędzla rysujący obszar rysowania obiektu. Służy on o niemal dowolnym obiektu graficznego do rysunku. <xref:System.Windows.Media.Drawing> Właściwość <xref:System.Windows.Media.DrawingBrush> opisuje jego <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Do renderowania <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Media.DrawingBrush>, dodaj go do pędzla przy użyciu pędzla <xref:System.Windows.Media.Drawing> właściwości i używanie pędzla do rysowania graficznego obiektów, takich jak kontrola lub panelu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> z wzorcem utworzone na podstawie <xref:System.Windows.Media.GeometryDrawing>. W tym przykładzie tworzy następujące dane wyjściowe.  
  
 ![A rozmieszczany pędzla](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
Obiekt GeometryDrawing zawierający używane z DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Klasa udostępnia szereg opcji rozciąganie i ustawianie widoku kafelków jego zawartości. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush>, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md) omówienie.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Renderowanie rysunku z element wizualny  
 A <xref:System.Windows.Media.DrawingVisual> jest typem obiektu visual przeznaczone do renderowania rysunku. Praca bezpośrednio w warstwie visual jest opcją dla deweloperów, którzy chcą tworzyć wysoce dostosowane środowisko graficznego i nie została opisana w tym omówieniu. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md) omówienie.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Obiekty klasy DrawingContext  
 <xref:System.Windows.Media.DrawingContext> Klasa umożliwia wypełnienie <xref:System.Windows.Media.Visual> lub <xref:System.Windows.Media.Drawing> z zawartością visual. Użyj takich obiektów grafiki niższego poziomu <xref:System.Windows.Media.DrawingContext> ponieważ opisuje zawartość graficzną bardzo wydajnie.  
  
 Mimo że <xref:System.Windows.Media.DrawingContext> metody rysowania wyglądać podobnie do metody rysowania <xref:System.Drawing.Graphics?displayProperty=nameWithType> typu są faktycznie bardzo różnią się. <xref:System.Windows.Media.DrawingContext>jest używany z systemu grafiki zachowanych trybie, podczas gdy <xref:System.Drawing.Graphics?displayProperty=nameWithType> typ jest używany z systemem grafiki w trybie natychmiastowym. Jeśli używasz <xref:System.Windows.Media.DrawingContext> polecenia rysowania obiektu, zestaw instrukcji renderowania faktycznie są przechowywane (chociaż mechanizmu magazynowania dokładne zależy od typu obiektu, który dostarcza <xref:System.Windows.Media.DrawingContext>) który później będzie używany przez grafiki systemu; nie pobierają do ekranu w czasie rzeczywistym. Aby uzyskać więcej informacji na temat sposobu [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] grafiki systemu znaleźć [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Użytkownik nigdy nie bezpośrednio utworzyć wystąpienia <xref:System.Windows.Media.DrawingContext>; można jednak uzyskać rysowania kontekstu z niektórych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Wyliczanie zawartości obiektu Visual  
 Oprócz ich zastosowań <xref:System.Windows.Media.Drawing> obiekty także dostarczają model obiektowy wyliczania zawartość <xref:System.Windows.Media.Visual>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pobierania <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i jej wyliczyć.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)
