---
title: Omówienie pędzli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186577"
---
# <a name="wpf-brushes-overview"></a>Przegląd Pędzle WPF
Wszystko widoczne na ekranie jest widoczne, ponieważ zostało pomalowane pędzlem. Na przykład pędzel jest używany do opisywania tła przycisku, pierwszego planu tekstu i wypełnienia kształtu. W tym temacie przedstawiono pojęcia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] malowania pędzlami i podano przykłady. Pędzle umożliwiają malowanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obiektów wszystkim, od prostych, jednolitych kolorów po złożone zestawy wzorów i obrazów.  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>Malowanie pędzlem  
 "Farby" <xref:System.Windows.Media.Brush> obszar z jego wyjściem. Różne pędzle mają różne typy danych wyjściowych. Niektóre pędzle malują obszar w jednolitym kolorze, inne gradientem, wzorkiem, obrazem lub rysunkiem. Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.Brush> przykłady każdego z różnych typów.  
  
 ![Typy pędzli](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Przykłady pędzla  
  
 Większość obiektów wizualnych umożliwia określenie sposobu ich malowania. W poniższej tabeli wymieniono niektóre typowe obiekty <xref:System.Windows.Media.Brush>i właściwości, z którymi można użyć pliku .  
  
|Klasa|Właściwości pędzla|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 W poniższych sekcjach <xref:System.Windows.Media.Brush> opisano różne typy i podać przykład każdego z nich.  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>Malowanie jednolitym kolorem  
 A <xref:System.Windows.Media.SolidColorBrush> maluje obszar z <xref:System.Windows.Media.Color>bryłą . Istnieje wiele sposobów, aby określić <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush>a : na przykład można określić jego kanały alfa, czerwony, niebieski i zielony <xref:System.Windows.Media.Colors> lub użyć jednego z predefiniowanych kolorów dostarczonych przez klasę.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.SolidColorBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> pliku <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowany prostokąt.  
  
 ![Prostokąt namalowany za pomocą pędzla SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Prostokąt namalowany za pomocą pędzla SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.SolidColorBrush> informacji na temat klasy, zobacz [Malowanie za pomocą jednolitych kolorów i gradientów Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>Malowanie gradientem liniowym  
 A <xref:System.Windows.Media.LinearGradientBrush> maluje obszar gradientem liniowym. Gradient liniowy miesza dwa lub więcej kolorów między linią, oś gradientu. Obiekty <xref:System.Windows.Media.GradientStop> są używane do określania kolorów gradientu i ich położenia.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.LinearGradientBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> pliku <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowany prostokąt.  
  
 ![Prostokąt namalowany za pomocą pędzla liniowego](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Prostokąt namalowany za pomocą pędzla liniowego  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.LinearGradientBrush> informacji na temat klasy, zobacz [Malowanie za pomocą jednolitych kolorów i gradientów Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>Malowanie gradientem promieniowym  
 A <xref:System.Windows.Media.RadialGradientBrush> maluje obszar gradientem promieniowym. Gradient promieniowy miesza dwa lub więcej kolorów w okręgu. Podobnie jak <xref:System.Windows.Media.LinearGradientBrush> w przypadku <xref:System.Windows.Media.GradientStop> klasy, obiekty są używane do określania kolorów gradientu i ich położenia.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.RadialGradientBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> pliku <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowany prostokąt.  
  
 ![Prostokąt namalowany za pomocą pędzla RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Prostokąt namalowany za pomocą pędzla PromieniowegoGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.RadialGradientBrush> informacji na temat klasy, zobacz [Malowanie za pomocą jednolitych kolorów i gradientów Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>Malowanie obrazem  
 Malowanie <xref:System.Windows.Media.ImageBrush> obszaru za <xref:System.Windows.Media.ImageSource>pomocą pliku .  
  
 W poniższym przykładzie <xref:System.Windows.Media.ImageBrush> użyto do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> pliku <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowany prostokąt.  
  
 ![Prostokąt namalowany pędzlem imagebrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Prostokąt namalowany przy użyciu obrazu  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.ImageBrush> informacji na temat klasy, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>Malowanie rysunkiem  
 A <xref:System.Windows.Media.DrawingBrush> maluje obszar <xref:System.Windows.Media.Drawing>za pomocą pliku . A <xref:System.Windows.Media.Drawing> może zawierać kształty, obrazy, tekst i multimedia.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.DrawingBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> pliku <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowany prostokąt.  
  
 ![Prostokąt namalowany za pomocą pędzla DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Prostokąt namalowany za pomocą pędzla DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.DrawingBrush> informacji na temat klasy, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>Malowanie za pomocą wizualizacji  
 A <xref:System.Windows.Media.VisualBrush> maluje obszar <xref:System.Windows.Media.Visual> za pomocą obiektu. Przykłady obiektów wizualnych <xref:System.Windows.Controls.Page>obejmują <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.Button>, i . A <xref:System.Windows.Media.VisualBrush> umożliwia również wyświetlanie zawartości z jednej części aplikacji do innego obszaru; jest to bardzo przydatne do tworzenia efektów odbicia i powiększania części ekranu.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.VisualBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> pliku <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowany prostokąt.  
  
 ![Prostokąt namalowany za pomocą pędzla VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Prostokąt namalowany za pomocą pędzla VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.VisualBrush> informacji na temat klasy, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>Malowanie przy użyciu wstępnie zdefiniowanych i pędzli systemowych  
 Dla wygody program Windows Presentation Foundation (WPF) udostępnia zestaw wstępnie zdefiniowanych i systemowych pędzli, których można używać do malowania obiektów.  
  
- Aby uzyskać listę dostępnych wstępnie zdefiniowanych pędzli, zobacz <xref:System.Windows.Media.Brushes> klasę. Aby zapoznać się z przykładem przedstawiającym sposób używania wstępnie zdefiniowanego pędzla, zobacz [Malowanie obszaru jednolitym kolorem](how-to-paint-an-area-with-a-solid-color.md).  
  
- Aby uzyskać listę dostępnych pędzli <xref:System.Windows.SystemColors> systemowych, zobacz klasę. Na przykład zobacz [Malowanie obszaru pędzlem systemowym](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>Typowe funkcje pędzla  
 <xref:System.Windows.Media.Brush>obiekty zapewniają <xref:System.Windows.Media.Brush.Opacity%2A> właściwość, która może służyć do pędzla przezroczyste lub częściowo przezroczyste. Wartość <xref:System.Windows.Media.Brush.Opacity%2A> 0 sprawia, że pędzel <xref:System.Windows.Media.Brush.Opacity%2A> jest całkowicie przezroczysty, podczas gdy wartość 1 sprawia, że pędzel jest całkowicie nieprzezroczysty. W poniższym przykładzie <xref:System.Windows.Media.Brush.Opacity%2A> użyto <xref:System.Windows.Media.SolidColorBrush> właściwości do 25 procent nieprzezroczyste.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Jeśli pędzel zawiera kolory, które są częściowo przezroczyste, wartość krycia koloru jest łączona przez mnożenie z wartością krycia pędzla. Na przykład jeśli pędzel ma wartość krycia 0,5 i kolor używany w pędzlu ma również wartość krycia 0,5, kolor wyjściowy ma wartość krycia 0,25.  
  
> [!NOTE]
> Jest bardziej efektywne, aby zmienić wartość krycia pędzla niż jest, aby zmienić krycie całego elementu przy użyciu jego <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> właściwości.  
  
 Zawartość pędzla można obracać, skalować, pochylać i <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> tłumaczyć za pomocą jego właściwości. Aby uzyskać więcej informacji, zobacz [Omówienie transformacji pędzla](brush-transformation-overview.md).  
  
 Ponieważ są <xref:System.Windows.Media.Animation.Animatable> to <xref:System.Windows.Media.Brush> obiekty, obiekty mogą być animowane. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Freezable Funkcje  
 Ponieważ dziedziczy z <xref:System.Windows.Freezable> klasy, <xref:System.Windows.Media.Brush> klasa zawiera kilka <xref:System.Windows.Media.Brush> funkcji specjalnych: obiekty mogą być zadeklarowane jako [zasoby,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)współużytkowane przez wiele obiektów i sklonowane. Ponadto wszystkie typy <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.VisualBrush> z wyjątkiem mogą być tylko do odczytu w celu zwiększenia wydajności i wykonane wątku bezpieczne.  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Freezable> temat różnych funkcji udostępnianych przez obiekty, zobacz [Omówienie obiektów freezable](../advanced/freezable-objects-overview.md).  
  
 Aby uzyskać więcej <xref:System.Windows.Media.VisualBrush> informacji na temat <xref:System.Windows.Media.VisualBrush> dlaczego obiekty nie mogą być zablokowane, zobacz stronę tekstu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
- [Próbka pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Przykład pędzla Wizualnego](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [Tematy in jakże](brushes-how-to-topics.md)
- [Inne zalecenia dotyczące wydajności](../advanced/optimizing-performance-other-recommendations.md)
