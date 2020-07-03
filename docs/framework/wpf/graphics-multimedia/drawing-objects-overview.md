---
title: Przegląd Rysowanie obiektów
description: Zapoznaj się z obiektami i sposobami korzystania z nich w celu wydajnego rysowania kształtów, map bitowych, tekstu i multimediów w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: f00a59cd6e799e57f238c5f9b72ecc48e8445475
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853833"
---
# <a name="drawing-objects-overview"></a>Przegląd Rysowanie obiektów
W tym temacie przedstawiono <xref:System.Windows.Media.Drawing> obiekty i opisano sposób ich używania do wydajnego rysowania kształtów, map bitowych, tekstu i multimediów. Użyj <xref:System.Windows.Media.Drawing> obiektów podczas tworzenia obiektu clipart, maluj z <xref:System.Windows.Media.DrawingBrush> lub używaj <xref:System.Windows.Media.Visual> obiektów.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Co to jest obiekt rysowania?  
 <xref:System.Windows.Media.Drawing>Obiekt opisuje widoczną zawartość, na przykład kształt, mapę bitową, wideo lub wiersz tekstu. Różne typy rysunków opisują różne typy zawartości. Poniżej znajduje się lista różnych typów obiektów rysowania.  
  
- <xref:System.Windows.Media.GeometryDrawing>— Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>— Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>— Rysuje tekst.  
  
- <xref:System.Windows.Media.VideoDrawing>— Odtwarza plik dźwiękowy lub wideo.  
  
- <xref:System.Windows.Media.DrawingGroup>— Rysuje inne rysunki. Użyj grupy rysowania, aby połączyć inne rysunki w pojedynczy rysunek złożony.  
  
 <xref:System.Windows.Media.Drawing>obiekty są uniwersalne; Istnieje wiele sposobów używania <xref:System.Windows.Media.Drawing> obiektu.  
  
- Można go wyświetlić jako obraz przy użyciu <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> kontrolki i.  
  
- Można go użyć <xref:System.Windows.Media.DrawingBrush> do malowania obiektu, takiego jak <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page> .  
  
- Można jej użyć do opisania wyglądu <xref:System.Windows.Media.DrawingVisual> .  
  
- Można jej użyć do wyliczenia zawartości <xref:System.Windows.Media.Visual> .  
  
 WPF udostępnia inne typy obiektów, które umożliwiają rysowanie kształtów, map bitowych, tekstu i multimediów. Można na przykład użyć <xref:System.Windows.Shapes.Shape> obiektów do rysowania kształtów, a <xref:System.Windows.Controls.MediaElement> formant zapewnia inny sposób dodawania wideo do aplikacji. Tak więc kiedy należy używać <xref:System.Windows.Media.Drawing> obiektów? Aby wymusić funkcje poziomu platformy w celu uzyskania korzyści z wydajności lub korzystania z <xref:System.Windows.Freezable> funkcji. Ponieważ <xref:System.Windows.Media.Drawing> obiekty nie obsługują [układu](../advanced/layout.md), wejścia i koncentracji, zapewniają korzyści z wydajności, które są idealnym rozwiązaniem do opisywania tła, grafiki artystycznej i dla rysowania niskiego poziomu z <xref:System.Windows.Media.Visual> obiektami.  
  
 Ponieważ są one <xref:System.Windows.Freezable> obiektem typu, <xref:System.Windows.Media.Drawing> obiekty uzyskują kilka specjalnych funkcji, które obejmują następujące: mogą być deklarowane jako [zasoby](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współużytkowane przez wiele obiektów, wykonywane tylko do odczytu w celu poprawy wydajności, klonowania i zapewnienia bezpiecznego wątkowo. Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiekty, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Rysowanie kształtu  
 Aby narysować kształt, użyj <xref:System.Windows.Media.GeometryDrawing> . Właściwość rysowania geometrii <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> zawiera opis kształtu do rysowania, jego <xref:System.Windows.Media.GeometryDrawing.Brush%2A> Właściwość opisuje sposób malowania wnętrza kształtu, a jego <xref:System.Windows.Media.GeometryDrawing.Pen%2A> Właściwość opisuje sposób rysowania konturów.  
  
 Poniższy przykład używa <xref:System.Windows.Media.GeometryDrawing> do rysowania kształtu. Kształt jest opisywany przez <xref:System.Windows.Media.GeometryGroup> i dwa <xref:System.Windows.Media.EllipseGeometry> obiekty. Wnętrze kształtu jest rysowane z <xref:System.Windows.Media.LinearGradientBrush> i jego kontur jest rysowany przy użyciu <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> .  
  
 Ten przykład tworzy następujące elementy <xref:System.Windows.Media.GeometryDrawing> .  
  
 ![GeometryDrawing dwie wielokropek](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Pełny przykład można znaleźć w temacie [Create a GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Inne <xref:System.Windows.Media.Geometry> klasy, takie jak <xref:System.Windows.Media.PathGeometry> umożliwienie tworzenia bardziej złożonych kształtów przez tworzenie krzywych i łuków. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Geometry> obiektów, zobacz [Omówienie geometrii](geometry-overview.md).  
  
 Aby uzyskać więcej informacji na temat innych sposobów rysowania kształtów, które nie używają <xref:System.Windows.Media.Drawing> obiektów, zobacz [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Rysowanie obrazu  
 Aby narysować obraz, użyj <xref:System.Windows.Media.ImageDrawing> . <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> Właściwość obiektu zawiera opis obrazu do rysowania, a jego <xref:System.Windows.Media.ImageDrawing.Rect%2A> Właściwość definiuje region, w którym jest rysowany obraz.  
  
 Poniższy przykład rysuje obraz do prostokąta znajdującego się w (75, 75), który jest 100 o 100 pikseli. Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.ImageDrawing> Tworzenie przez przykład. Dodano szare obramowanie, aby pokazać granice elementu <xref:System.Windows.Media.ImageDrawing> .  
  
 ![100 100 ImageDrawing &#40;75, 75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 o 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Aby uzyskać więcej informacji o obrazach, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Odtwórz multimedia (tylko kod)  
  
> [!NOTE]
> Chociaż można zadeklarować <xref:System.Windows.Media.VideoDrawing> w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , można ładować i odtwarzać multimedia tylko przy użyciu kodu. Aby odtworzyć wideo w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , użyj <xref:System.Windows.Controls.MediaElement> zamiast niego.  
  
 Aby odtworzyć plik audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> . Istnieją dwa sposoby ładowania i odtwarzania multimediów. Pierwszym sposobem jest użycie i a <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi — tworzenie własnych <xref:System.Windows.Media.MediaTimeline> do użycia z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> .  
  
> [!NOTE]
> Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu, takiego jak obraz. W pliku projektu należy zamiast tego ustawić typ nośnika na `Content` i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always` .  
  
 Aby odtwarzać multimedia bez tworzenia własnych <xref:System.Windows.Media.MediaTimeline> , wykonaj następujące czynności.  
  
1. Utwórz <xref:System.Windows.Media.MediaPlayer> obiekt.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Użyj <xref:System.Windows.Media.MediaPlayer.Open%2A> metody, aby załadować plik multimedialny.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Określ rozmiar i lokalizację, aby narysować nośnik przez ustawienie <xref:System.Windows.Media.VideoDrawing.Rect%2A> właściwości <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Ustaw <xref:System.Windows.Media.VideoDrawing.Player%2A> Właściwość <xref:System.Windows.Media.VideoDrawing> z <xref:System.Windows.Media.MediaPlayer> utworzonym elementem.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Użyj <xref:System.Windows.Media.MediaPlayer.Play%2A> metody, <xref:System.Windows.Media.MediaPlayer> Aby rozpocząć odtwarzanie nośnika.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Poniższy przykład używa i, <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> Aby odtworzyć plik wideo jeden raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkową kontrolę czasu na nośniku, użyj <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline>Pozwala określić, czy film wideo powinien być powtarzany. Aby użyć programu <xref:System.Windows.Media.MediaTimeline> z programem <xref:System.Windows.Media.VideoDrawing> , należy wykonać następujące czynności:  
  
1. Zadeklaruj <xref:System.Windows.Media.MediaTimeline> i ustaw jego zachowania chronometrażu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Utwórz <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Utwórz <xref:System.Windows.Media.MediaPlayer> i Użyj, <xref:System.Windows.Media.MediaClock> Aby ustawić jego <xref:System.Windows.Media.MediaPlayer.Clock%2A> Właściwość.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Utwórz <xref:System.Windows.Media.VideoDrawing> i przypisz <xref:System.Windows.Media.MediaPlayer> do <xref:System.Windows.Media.VideoDrawing.Player%2A> właściwości <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Poniższy przykład używa, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> a i a, <xref:System.Windows.Media.VideoDrawing> Aby odtwarzać wideo wielokrotnie.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy pamiętać, że w przypadku korzystania z programu <xref:System.Windows.Media.MediaTimeline> można użyć interaktywnego powrotu <xref:System.Windows.Media.Animation.ClockController> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwości <xref:System.Windows.Media.MediaClock> do sterowania odtwarzaniem multimediów zamiast interaktywnych metod <xref:System.Windows.Media.MediaPlayer> .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Rysuj tekst  
 Aby narysować tekst, użyj <xref:System.Windows.Media.GlyphRunDrawing> i <xref:System.Windows.Media.GlyphRun> . Poniższy przykład używa <xref:System.Windows.Media.GlyphRunDrawing> do rysowania tekstu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> jest obiektem niskiego poziomu, który jest przeznaczony do użycia w przypadku prezentacji dokumentów o stałym formacie i scenariuszy drukowania. Łatwiejszym sposobem rysowania tekstu na ekranie jest użycie <xref:System.Windows.Controls.Label> lub <xref:System.Windows.Controls.TextBlock> . Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.GlyphRun> , zobacz [wprowadzenie do obiektu GlyphRun i elementów glifs](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) przegląd.  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Rysunki złożone  
 A <xref:System.Windows.Media.DrawingGroup> umożliwia łączenie wielu rysunków w pojedynczy rysunek złożony. Za pomocą <xref:System.Windows.Media.DrawingGroup> , można połączyć kształty, obrazy i tekst w jeden <xref:System.Windows.Media.Drawing> obiekt.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingGroup> do łączenia dwóch <xref:System.Windows.Media.GeometryDrawing> obiektów i <xref:System.Windows.Media.ImageDrawing> obiektu. Ten przykład generuje następujące dane wyjściowe.  
  
 ![Obiekt do rysowania z wieloma rysunkami](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Rysunek złożony  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup>Ponadto umożliwia zastosowanie masek kryjących, transformacji, efektów mapy bitowej i innych operacji do jej zawartości. <xref:System.Windows.Media.DrawingGroup>operacje są stosowane w następującej kolejności: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> ,,,, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> , i <xref:System.Windows.Media.DrawingGroup.Transform%2A> .  
  
 Na poniższej ilustracji przedstawiono kolejność, w której <xref:System.Windows.Media.DrawingGroup> są stosowane operacje.  
  
 ![Kolejność operacji na rysunku](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji na obiektach do rysowania  
  
 W poniższej tabeli opisano właściwości, których można użyć do manipulowania <xref:System.Windows.Media.DrawingGroup> zawartością obiektu.  
  
|Właściwość|Opis|Ilustracji|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Zmienia nieprzezroczystość wybranych części <xref:System.Windows.Media.DrawingGroup> zawartości. Aby zapoznać się z przykładem, zobacz [jak: kontrolowanie nieprzezroczystości rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Obiekt typu rysowanie z maską nieprzezroczystości](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Jednorodnie zmienia nieprzezroczystość <xref:System.Windows.Media.DrawingGroup> zawartości. Użyj tej właściwości, aby uczynić <xref:System.Windows.Media.Drawing> przezroczystą lub częściowo przezroczystą. Aby zapoznać się z przykładem, zobacz [jak: zastosować maskę nieprzezroczystość do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups z różnymi ustawieniami nieprzezroczystości](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Stosuje <xref:System.Windows.Media.Effects.BitmapEffect> do <xref:System.Windows.Media.DrawingGroup> zawartości. Aby zapoznać się z przykładem, zobacz [jak: stosowanie efektu bitmapy do rysunku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Rysowanie z BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Przycina <xref:System.Windows.Media.DrawingGroup> zawartość do regionu, który jest opisywany przy użyciu <xref:System.Windows.Media.Geometry> . Aby zapoznać się z przykładem, zobacz [How to: cliping rysowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Rysowanie ze zdefiniowanym regionem przycinania](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Przyciąga niezależne od urządzenia piksele do pikseli urządzenia zgodnie z określonymi wskazówkami. Ta właściwość jest przydatna do zapewnienia, że dokładniej szczegółowe renderowanie grafiki na wyświetlaczach o niskiej rozdzielczości DPI. Aby zapoznać się z przykładem, zobacz temat [stosowanie GuidelineSet do rysunku](how-to-apply-a-guidelineset-to-a-drawing.md).|![Obiekt do rysowania z i bez GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Przekształca <xref:System.Windows.Media.DrawingGroup> zawartość. Aby zapoznać się z przykładem, zobacz [How to: Apply a Transform for a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Obrócona przerysowanie](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Wyświetlanie rysunku jako obrazu  
 Aby wyświetlić <xref:System.Windows.Media.Drawing> <xref:System.Windows.Controls.Image> formant z kontrolką, użyj <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> kontrolki <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwość obiektu na rysunek, który chcesz wyświetlić.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> kontrolki do wyświetlenia <xref:System.Windows.Media.GeometryDrawing> . Ten przykład generuje następujące dane wyjściowe.  
  
 ![GeometryDrawing dwie wielokropek](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Malowanie obiektu za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> to typ pędzla, który maluje obszar z obiektem rysunkowym. Można jej użyć do malowania tylko dowolnego obiektu graficznego z rysunkiem. <xref:System.Windows.Media.Drawing>Właściwość klasy <xref:System.Windows.Media.DrawingBrush> opisuje <xref:System.Windows.Media.DrawingBrush.Drawing%2A> . Aby renderować a <xref:System.Windows.Media.Drawing> za pomocą <xref:System.Windows.Media.DrawingBrush> , Dodaj go do pędzla przy użyciu właściwości pędzla <xref:System.Windows.Media.Drawing> i użyj pędzla do malowania obiektu graficznego, takiego jak kontrolka lub panel.  
  
 W poniższych przykładach używa <xref:System.Windows.Media.DrawingBrush> się do malowania elementu <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> z wzorcem utworzonym na podstawie <xref:System.Windows.Media.GeometryDrawing> . Ten przykład generuje następujące dane wyjściowe.  
  
 ![DrawingBrush z sąsiadującą](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing używany z DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush>Klasa zawiera różne opcje rozciągania i rozmieszczania zawartości. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush> , zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Renderowanie rysunku przy użyciu wizualizacji  
 A <xref:System.Windows.Media.DrawingVisual> jest typem obiektu wizualizacji zaprojektowanego do renderowania rysunku. Praca bezpośrednio w warstwie wizualnej jest opcją dla deweloperów, którzy chcą utworzyć wysoce dostosowane środowisko graficzne i nie jest opisana w tym omówieniu. Aby uzyskać więcej informacji, zobacz temat [Korzystanie z użycie DrawingVisual obiektów](using-drawingvisual-objects.md) — Omówienie.  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>DrawingContext — obiekty  
 <xref:System.Windows.Media.DrawingContext>Klasa umożliwia wypełnienie <xref:System.Windows.Media.Visual> lub <xref:System.Windows.Media.Drawing> z zawartością wizualną. Wiele takich obiektów grafiki niższego poziomu używa, <xref:System.Windows.Media.DrawingContext> ponieważ opisuje ona zawartość graficzną bardzo wydajnie.  
  
 Chociaż <xref:System.Windows.Media.DrawingContext> metody rysowania wyglądają podobnie jak metody rysowania <xref:System.Drawing.Graphics?displayProperty=nameWithType> typu, są one bardzo różne. <xref:System.Windows.Media.DrawingContext>jest używany z systemem grafiki trybu zachowywania, podczas gdy <xref:System.Drawing.Graphics?displayProperty=nameWithType> Typ jest używany z systemem graficznym trybu natychmiastowego. W przypadku korzystania z <xref:System.Windows.Media.DrawingContext> poleceń rysowania obiektu w rzeczywistości przechowujesz zestaw instrukcji renderowania (Chociaż dokładny mechanizm magazynowania zależy od typu obiektu, który dostarcza <xref:System.Windows.Media.DrawingContext> ), który będzie później używany przez system grafiki. nie można narysować na ekranie w czasie rzeczywistym. Aby uzyskać więcej informacji na temat działania systemu grafiki Windows Presentation Foundation (WPF), zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).  
  
 Nigdy nie tworzysz bezpośrednio wystąpienia <xref:System.Windows.Media.DrawingContext> . Możesz jednak uzyskać kontekst rysowania z określonych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Wyliczanie zawartości wizualizacji  
 Oprócz innych <xref:System.Windows.Media.Drawing> obiektów, obiekty również udostępniają model obiektów do wyliczania zawartości <xref:System.Windows.Media.Visual> .  
  
 W poniższym przykładzie zastosowano <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, aby pobrać <xref:System.Windows.Media.DrawingGroup> wartość a <xref:System.Windows.Media.Visual> i wyliczyć ją.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md)
- [Przegląd Geometria](geometry-overview.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
- [— Tematy porad](drawings-how-to-topics.md)
