---
title: Przegląd Pędzle WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 8a1d05ad48ce75ce67d21d5a4d508015fea879b2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458627"
---
# <a name="wpf-brushes-overview"></a>Przegląd Pędzle WPF
Wszystko widoczne na ekranie jest widoczne, ponieważ zostało narysowane przez pędzel. Na przykład Pędzel służy do opisywania tła przycisku, pierwszego planu tekstu i wypełnienia kształtu. W tym temacie przedstawiono koncepcje rysowania przy użyciu pędzli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i przedstawiono przykłady. Pędzle umożliwiają malowanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obiektów ze wszystkimi elementami od prostych, pełnych kolorów do złożonych zestawów wzorców i obrazów.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Malowanie przy użyciu pędzla  
 <xref:System.Windows.Media.Brush> "maluje" obszar z danymi wyjściowymi. Różne pędzle mają różne typy danych wyjściowych. Niektóre pędzle malują obszar z pełnymi kolorami, innymi z gradientem, wzorcem, obrazem lub rysowaniem. Na poniższej ilustracji przedstawiono przykłady poszczególnych typów <xref:System.Windows.Media.Brush>.  
  
 ![Typy pędzli](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Przykłady pędzla  
  
 Większość obiektów wizualnych umożliwia określenie sposobu, w jaki są rysowane. W poniższej tabeli wymieniono niektóre typowe obiekty i właściwości, których można użyć <xref:System.Windows.Media.Brush>.  
  
|Class|Właściwości pędzla|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 W poniższych sekcjach opisano różne typy <xref:System.Windows.Media.Brush> i przedstawiono przykład każdego z nich.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Maluj z pełnym kolorem  
 <xref:System.Windows.Media.SolidColorBrush> maluje obszar z pełnymi <xref:System.Windows.Media.Color>. Istnieją różne sposoby określania <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush>: można na przykład określić kanały alfa, czerwone, niebieskie i zielone, lub użyć jednego ze wstępnie zdefiniowanego koloru dostarczonego przez klasę <xref:System.Windows.Media.Colors>.  
  
 Poniższy przykład używa <xref:System.Windows.Media.SolidColorBrush>, aby malować <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Prostokąt malowany przy użyciu SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.Media.SolidColorBrush>, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Maluj z gradientem liniowym  
 <xref:System.Windows.Media.LinearGradientBrush> maluje obszar z gradientem liniowym. Gradient liniowy miesza dwa lub więcej kolorów w wierszu, oś gradientu. Użyj <xref:System.Windows.Media.GradientStop> obiektów, aby określić kolory w gradiencie i ich położenia.  
  
 Poniższy przykład używa <xref:System.Windows.Media.LinearGradientBrush>, aby malować <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Prostokąt malowany przy użyciu LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.Media.LinearGradientBrush>, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Maluj z gradientem promieniowym  
 <xref:System.Windows.Media.RadialGradientBrush> maluje obszar z gradientem promieniowym. Gradient promieniowy miesza dwa lub więcej kolorów w okręgu. Podobnie jak w przypadku klasy <xref:System.Windows.Media.LinearGradientBrush>, można użyć obiektów <xref:System.Windows.Media.GradientStop> do określenia kolorów gradientu i ich pozycji.  
  
 Poniższy przykład używa <xref:System.Windows.Media.RadialGradientBrush>, aby malować <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Prostokąt malowany przy użyciu RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.Media.RadialGradientBrush>, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Malowanie przy użyciu obrazu  
 <xref:System.Windows.Media.ImageBrush> maluje obszar z <xref:System.Windows.Media.ImageSource>.  
  
 Poniższy przykład używa <xref:System.Windows.Media.ImageBrush>, aby malować <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przez ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Prostokąt malowany przy użyciu obrazu  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.Media.ImageBrush>, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Malowanie przy użyciu rysowania  
 <xref:System.Windows.Media.DrawingBrush> maluje obszar z <xref:System.Windows.Media.Drawing>. <xref:System.Windows.Media.Drawing> może zawierać kształty, obrazy, teksty i multimedia.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingBrush>, aby malować <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Prostokąt malowany przy użyciu DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.Media.DrawingBrush>, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Maluj przy użyciu wizualizacji  
 <xref:System.Windows.Media.VisualBrush> maluje obszar z obiektem <xref:System.Windows.Media.Visual>. Przykłady obiektów wizualnych obejmują <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>i <xref:System.Windows.Controls.MediaElement>. <xref:System.Windows.Media.VisualBrush> umożliwia również projektować zawartość z jednej części aplikacji w innym obszarze; jest to bardzo przydatne w przypadku tworzenia efektów odbicia i powiększania części ekranu.  
  
 Poniższy przykład używa <xref:System.Windows.Media.VisualBrush>, aby malować <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Prostokąt malowany przy użyciu VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.Media.VisualBrush>, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Malowanie przy użyciu wstępnie zdefiniowanych i pędzli systemowych  
 Dla wygody Windows Presentation Foundation (WPF) zawiera zestaw wstępnie zdefiniowanych i pędzli systemowych, których można użyć do malowania obiektów.  
  
- Aby uzyskać listę dostępnych wstępnie zdefiniowanych pędzli, zobacz Klasa <xref:System.Windows.Media.Brushes>. Aby zapoznać się z przykładem, jak używać wstępnie zdefiniowanego pędzla, zobacz [malowanie obszaru za pomocą pełnego koloru](how-to-paint-an-area-with-a-solid-color.md).  
  
- Aby uzyskać listę dostępnych pędzli systemowych, zapoznaj się z klasą <xref:System.Windows.SystemColors>. Aby zapoznać się z przykładem, zobacz [malowanie obszaru za pomocą pędzla systemu](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Typowe funkcje pędzla  
 obiekty <xref:System.Windows.Media.Brush> zapewniają Właściwość <xref:System.Windows.Media.Brush.Opacity%2A>, która może służyć do przezroczystego lub częściowo przezroczystego pędzla. <xref:System.Windows.Media.Brush.Opacity%2A> wartość 0 sprawia, że pędzel całkowicie przezroczysty, a <xref:System.Windows.Media.Brush.Opacity%2A> wartość 1 sprawia, że pędzel całkowicie nieprzezroczysty. Poniższy przykład używa właściwości <xref:System.Windows.Media.Brush.Opacity%2A>, aby <xref:System.Windows.Media.SolidColorBrush> 25 procent nieprzezroczystości.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Jeśli pędzel zawiera kolory, które są częściowo przezroczyste, wartość przezroczystości koloru jest połączona za pomocą mnożenia z wartością nieprzezroczystość pędzla. Na przykład, jeśli Pędzel ma wartość nieprzezroczystości 0,5, a kolor używany w pędzlu ma również wartość nieprzezroczystości 0,5, kolor wyjściowy ma wartość nieprzezroczystości równą 0,25.  
  
> [!NOTE]
> Aby zmienić wartość nieprzezroczystości pędzla, należy zmienić nieprzezroczystość całego elementu przy użyciu jego właściwości <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>.  
  
 Można obrócić, skalować, pochylić i przetłumaczyć zawartość pędzla przy użyciu jego właściwości <xref:System.Windows.Media.Brush.Transform%2A> lub <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Aby uzyskać więcej informacji, zobacz [Omówienie transformacji pędzla](brush-transformation-overview.md).  
  
 Ponieważ są one <xref:System.Windows.Media.Animation.Animatable> obiektami, obiekty <xref:System.Windows.Media.Brush> mogą być animowane. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy on z klasy <xref:System.Windows.Freezable>, Klasa <xref:System.Windows.Media.Brush> udostępnia kilka specjalnych funkcji: obiekty <xref:System.Windows.Media.Brush> mogą być deklarowane jako [zasoby](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współdzielone przez wiele obiektów i klonowane. Ponadto wszystkie typy <xref:System.Windows.Media.Brush> z wyjątkiem <xref:System.Windows.Media.VisualBrush> mogą być tylko do odczytu, aby zwiększyć wydajność i zapewnić bezpieczną obsługę wątków.  
  
 Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiektów, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
 Aby uzyskać więcej informacji na temat tego, dlaczego <xref:System.Windows.Media.VisualBrush> obiektów nie można zamrozić, zapoznaj się ze stroną typu <xref:System.Windows.Media.VisualBrush>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [Przykładowe pędzle](https://go.microsoft.com/fwlink/?LinkID=159973)
- [Przykład ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [Przykład VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
- [Tematy z instrukcjami](brushes-how-to-topics.md)
- [Inne zalecenia dotyczące wydajności](../advanced/optimizing-performance-other-recommendations.md)
