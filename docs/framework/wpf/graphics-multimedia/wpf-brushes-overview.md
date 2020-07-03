---
title: Omówienie pędzli
description: Odkryj, jak zilustrować koncepcje, malując przy użyciu prostych, pełnych kolorów za pomocą gradientów i wzorców w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 9bfd702d7a5a9d807e2b922874119c2bb2e68f39
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853725"
---
# <a name="wpf-brushes-overview"></a>Przegląd Pędzle WPF
Wszystko widoczne na ekranie jest widoczne, ponieważ zostało narysowane przez pędzel. Na przykład Pędzel służy do opisywania tła przycisku, pierwszego planu tekstu i wypełnienia kształtu. W tym temacie przedstawiono koncepcje rysowania przy użyciu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pędzli i przedstawiono przykłady. Pędzle umożliwiają malowanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obiektów ze wszystkimi elementami od prostych, pełnych kolorów do złożonych zestawów wzorców i obrazów.  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>Malowanie przy użyciu pędzla  
 <xref:System.Windows.Media.Brush>"Maluje" obszar z danymi wyjściowymi. Różne pędzle mają różne typy danych wyjściowych. Niektóre pędzle malują obszar z pełnymi kolorami, innymi z gradientem, wzorcem, obrazem lub rysowaniem. Na poniższej ilustracji przedstawiono przykłady poszczególnych <xref:System.Windows.Media.Brush> typów.  
  
 ![Typy pędzli](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Przykłady pędzla  
  
 Większość obiektów wizualnych umożliwia określenie sposobu, w jaki są rysowane. W poniższej tabeli wymieniono niektóre typowe obiekty i właściwości, których można użyć <xref:System.Windows.Media.Brush> .  
  
|Klasa|Właściwości pędzla|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 W poniższych sekcjach opisano różne <xref:System.Windows.Media.Brush> typy i przedstawiono przykład każdego z nich.  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>Maluj z pełnym kolorem  
 <xref:System.Windows.Media.SolidColorBrush>Maluje obszar z pełnymi <xref:System.Windows.Media.Color> . Istnieją różne sposoby określania typu <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> : można na przykład określić kanały alfa, czerwonego, niebieskiego i zielonego, lub użyć jednego ze wstępnie zdefiniowanego koloru dostarczonego przez <xref:System.Windows.Media.Colors> klasę.  
  
 Poniższy przykład używa <xref:System.Windows.Media.SolidColorBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> . Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Prostokąt malowany przy użyciu SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Aby uzyskać więcej informacji o <xref:System.Windows.Media.SolidColorBrush> klasie, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>Maluj z gradientem liniowym  
 <xref:System.Windows.Media.LinearGradientBrush>Maluje obszar z gradientem liniowym. Gradient liniowy miesza dwa lub więcej kolorów w wierszu, oś gradientu. <xref:System.Windows.Media.GradientStop>Obiekty są używane do określania kolorów w gradiencie i ich położenia.  
  
 Poniższy przykład używa <xref:System.Windows.Media.LinearGradientBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> . Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Prostokąt malowany przy użyciu LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji o <xref:System.Windows.Media.LinearGradientBrush> klasie, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>Maluj z gradientem promieniowym  
 <xref:System.Windows.Media.RadialGradientBrush>Maluje obszar z gradientem promieniowym. Gradient promieniowy miesza dwa lub więcej kolorów w okręgu. Podobnie jak w przypadku <xref:System.Windows.Media.LinearGradientBrush> klasy, należy użyć <xref:System.Windows.Media.GradientStop> obiektów do określenia kolorów w gradiencie i ich położenia.  
  
 Poniższy przykład używa <xref:System.Windows.Media.RadialGradientBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> . Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Prostokąt malowany przy użyciu RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji o <xref:System.Windows.Media.RadialGradientBrush> klasie, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>Malowanie przy użyciu obrazu  
 <xref:System.Windows.Media.ImageBrush>Maluje obszar za pomocą <xref:System.Windows.Media.ImageSource> .  
  
 Poniższy przykład używa <xref:System.Windows.Media.ImageBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> . Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przez ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Prostokąt malowany przy użyciu obrazu  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> klasy, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>Malowanie przy użyciu rysowania  
 <xref:System.Windows.Media.DrawingBrush>Maluje obszar za pomocą <xref:System.Windows.Media.Drawing> . <xref:System.Windows.Media.Drawing>Może zawierać kształty, obrazy, tekst i multimedia.  
  
 Poniższy przykład używa <xref:System.Windows.Media.DrawingBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> . Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Prostokąt malowany przy użyciu DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush> klasy, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>Maluj przy użyciu wizualizacji  
 <xref:System.Windows.Media.VisualBrush>Maluje obszar z <xref:System.Windows.Media.Visual> obiektem. Przykłady obiektów wizualnych obejmują <xref:System.Windows.Controls.Button> , <xref:System.Windows.Controls.Page> , i <xref:System.Windows.Controls.MediaElement> . <xref:System.Windows.Media.VisualBrush>Pozwala również na tworzenie projektów zawartości z jednej części aplikacji w innym obszarze — jest to bardzo przydatne do tworzenia efektów odbicia i powiększania części ekranu.  
  
 Poniższy przykład używa <xref:System.Windows.Media.VisualBrush> do malowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> . Na poniższej ilustracji przedstawiono prostokąt malowany.  
  
 ![Prostokąt malowany przy użyciu VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Prostokąt malowany przy użyciu VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.VisualBrush> klasy, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>Malowanie przy użyciu wstępnie zdefiniowanych i pędzli systemowych  
 Dla wygody Windows Presentation Foundation (WPF) zawiera zestaw wstępnie zdefiniowanych i pędzli systemowych, których można użyć do malowania obiektów.  
  
- Aby uzyskać listę dostępnych wstępnie zdefiniowanych pędzli, zobacz <xref:System.Windows.Media.Brushes> Klasa. Aby zapoznać się z przykładem, jak używać wstępnie zdefiniowanego pędzla, zobacz [malowanie obszaru za pomocą pełnego koloru](how-to-paint-an-area-with-a-solid-color.md).  
  
- Aby zapoznać się z listą dostępnych pędzli systemowych, zapoznaj się z <xref:System.Windows.SystemColors> klasą. Aby zapoznać się z przykładem, zobacz [malowanie obszaru za pomocą pędzla systemu](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>Typowe funkcje pędzla  
 <xref:System.Windows.Media.Brush>obiekty zapewniają <xref:System.Windows.Media.Brush.Opacity%2A> Właściwość, która może służyć do przezroczystego lub częściowo przezroczystego pędzla. <xref:System.Windows.Media.Brush.Opacity%2A>Wartość 0 powoduje, że pędzel całkowicie przezroczysty, a <xref:System.Windows.Media.Brush.Opacity%2A> wartość 1 sprawia, że pędzel całkowicie nieprzezroczysty. W poniższym przykładzie użyta jest <xref:System.Windows.Media.Brush.Opacity%2A> Właściwość, aby zwiększyć <xref:System.Windows.Media.SolidColorBrush> nieprzezroczystość na 25 procent.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Jeśli pędzel zawiera kolory, które są częściowo przezroczyste, wartość przezroczystości koloru jest połączona za pomocą mnożenia z wartością nieprzezroczystość pędzla. Na przykład, jeśli Pędzel ma wartość nieprzezroczystości 0,5, a kolor używany w pędzlu ma również wartość nieprzezroczystości 0,5, kolor wyjściowy ma wartość nieprzezroczystości równą 0,25.  
  
> [!NOTE]
> To bardziej wydajne, aby zmienić wartość nieprzezroczystości pędzla, niż pozwala zmienić nieprzezroczystość całego elementu przy użyciu jego <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> właściwości.  
  
 Można obrócić, skalować, pochylić i przetłumaczyć zawartość pędzla przy użyciu jego <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości lub. Aby uzyskać więcej informacji, zobacz [Omówienie transformacji pędzla](brush-transformation-overview.md).  
  
 Ponieważ są <xref:System.Windows.Media.Animation.Animatable> obiektami, <xref:System.Windows.Media.Brush> obiekty mogą być animowane. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy z <xref:System.Windows.Freezable> klasy, <xref:System.Windows.Media.Brush> Klasa zawiera kilka specjalnych funkcji: <xref:System.Windows.Media.Brush> obiekty mogą być deklarowane jako [zasoby](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współdzielone między wiele obiektów i klonowane. Ponadto wszystkie <xref:System.Windows.Media.Brush> typy z wyjątkiem <xref:System.Windows.Media.VisualBrush> mogą być tylko do odczytu w celu zwiększenia wydajności i zapewnienia bezpieczeństwa wątkowego.  
  
 Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiekty, zobacz [Freezable obiektów — Omówienie](../advanced/freezable-objects-overview.md).  
  
 Aby uzyskać więcej informacji na temat powodów, dla których <xref:System.Windows.Media.VisualBrush> nie można zablokować obiektów, zobacz <xref:System.Windows.Media.VisualBrush> stronę typ.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
- [Przykładowe pędzle](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [Przykład ImageBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Przykład VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [— Tematy porad](brushes-how-to-topics.md)
- [Inne zalecenia dotyczące wydajności](../advanced/optimizing-performance-other-recommendations.md)
