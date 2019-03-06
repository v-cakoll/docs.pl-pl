---
title: Przegląd Pędzle WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 12671c62a887f863bfb423cf67d7a25eed4118b2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362607"
---
# <a name="wpf-brushes-overview"></a>Przegląd Pędzle WPF
Wszystko, co jest widoczne na ekranie jest widoczny, ponieważ został on malowane przez pędzla. Na przykład jest używany pędzel opisujący tło przycisku, tekst pierwszego planu i wypełnienie kształtu. W tym temacie przedstawiono koncepcję malowanie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pędzle oraz przykłady. Pędzle umożliwia malowanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obiektów ze wszystkim z proste, pełne kolory do złożonych zestawów wzorców i obrazy.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Malowanie przy użyciu pędzla  
 Element <xref:System.Windows.Media.Brush> "umożliwia malowanie" obszar za pomocą jego dane wyjściowe. Pędzle różnych mają różne typy danych wyjściowych. Niektóre pędzle Maluj obszar jednolitym kolorem, osoby z gradientu, wzorzec, obrazu lub rysunku. Poniższa ilustracja przedstawia przykłady każdego z różnych <xref:System.Windows.Media.Brush> typów.  
  
 ![Pędzel, typy](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Przykłady pędzla  
  
 Większość obiektów wizualnych umożliwiają określenie, jak są rysowane. W poniższej tabeli wymieniono niektóre typowe obiektów i właściwości, za pomocą których można użyć <xref:System.Windows.Media.Brush>.  
  
|Class|Właściwości pędzla|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 W poniższych sekcjach opisano poszczególne <xref:System.Windows.Media.Brush> typów i podać przykład każdego z nich.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Malowanie jednolitym kolorem  
 A <xref:System.Windows.Media.SolidColorBrush> Malowanie obszaru za pomocą niezawodnej <xref:System.Windows.Media.Color>. Istnieją różne sposoby, aby określić <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush>: na przykład, można określić jej kanałów alfa, czerwony, niebieski i zielony lub użyj jednego z wstępnie zdefiniowany kolor, dostarczone przez <xref:System.Windows.Media.Colors> klasy.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.SolidColorBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Poniższa ilustracja przedstawia malowane prostokąta.  
  
 ![Prostokąt malowane przy użyciu SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Prostokąt malowane przy użyciu SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.SolidColorBrush> klasy, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Malowanie gradientem liniowym  
 A <xref:System.Windows.Media.LinearGradientBrush> Malowanie obszaru gradientem liniowym. Gradient liniowy miesza dwa lub więcej kolorów linii osi gradientu. Możesz użyć <xref:System.Windows.Media.GradientStop> obiektów, aby określić kolory w gradiencie i ich pozycji.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Poniższa ilustracja przedstawia malowane prostokąta.  
  
 ![Prostokąt malowane przy użyciu LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Prostokąt malowane przy użyciu LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.LinearGradientBrush> klasy, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Malowanie gradientem promieniowym  
 A <xref:System.Windows.Media.RadialGradientBrush> Malowanie obszaru gradientem promieniowym. Gradient promieniowy miesza dwa lub więcej kolorów w okręgu. Podobnie jak w przypadku <xref:System.Windows.Media.LinearGradientBrush> klasy, możesz użyć <xref:System.Windows.Media.GradientStop> obiektów, aby określić kolory w gradiencie i ich pozycji.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RadialGradientBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Poniższa ilustracja przedstawia malowane prostokąta.  
  
 ![Prostokąt malowane przy użyciu RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Prostokąt malowane przy użyciu RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.RadialGradientBrush> klasy, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Malowanie przy użyciu obrazu  
 <xref:System.Windows.Media.ImageBrush> Malowanie obszaru za pomocą <xref:System.Windows.Media.ImageSource>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Poniższa ilustracja przedstawia malowane prostokąta.  
  
 ![Prostokąt malowane przez ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Prostokąt malowane przy użyciu obrazu  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> klasy, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Malowanie za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> Malowanie obszaru za pomocą <xref:System.Windows.Media.Drawing>. Element <xref:System.Windows.Media.Drawing> może zawierać kształtów, obrazów, tekstu i media.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Poniższa ilustracja przedstawia malowane prostokąta.  
  
 ![Prostokąt malowane przy użyciu obiektu DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Prostokąt malowane przy użyciu obiektu DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush> klasy, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Malowanie przy użyciu wizualizacji  
 A <xref:System.Windows.Media.VisualBrush> Malowanie obszaru za pomocą <xref:System.Windows.Media.Visual> obiektu. Przykłady obiektów wizualnych <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, i <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> umożliwia także zawartość projektu z jednej części aplikacji do innego obszaru; jest ono bardzo przydatne do tworzenia efektów odbicia i powiększanie części ekranu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Poniższa ilustracja przedstawia malowane prostokąta.  
  
 ![Prostokąt malowane przy użyciu VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Prostokąt malowane przy użyciu VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.VisualBrush> klasy, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Malowanie przy użyciu wstępnie zdefiniowane i pędzli systemowych  
 Dla wygody Windows Presentation Foundation (WPF) zapewnia zestaw wstępnie zdefiniowanych i system pędzle, której można malować obiektów.  
  
-   Aby uzyskać listę dostępnych pędzle wstępnie zdefiniowanych, zobacz <xref:System.Windows.Media.Brushes> klasy. Przykład przedstawiający sposób użycia wstępnie zdefiniowanych pędzla, zobacz [Maluj obszar jednolitym kolorem](how-to-paint-an-area-with-a-solid-color.md).  
  
-   Aby uzyskać listę pędzle dostępnej w systemie, zobacz <xref:System.Windows.SystemColors> klasy. Aby uzyskać przykład, zobacz [Maluj obszar pędzlem systemowym](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Typowe funkcje pędzla  
 <xref:System.Windows.Media.Brush> obiekty oferują <xref:System.Windows.Media.Brush.Opacity%2A> właściwość, która może służyć do wprowadzenia pędzla, przezroczyste lub częściowo przezroczyste. <xref:System.Windows.Media.Brush.Opacity%2A> Wartość 0 powoduje, że pędzel jest całkowicie przezroczysty podczas <xref:System.Windows.Media.Brush.Opacity%2A> wartość 1 powoduje, że pędzel jest całkowicie nieprzezroczysty. W poniższym przykładzie użyto <xref:System.Windows.Media.Brush.Opacity%2A> właściwość się <xref:System.Windows.Media.SolidColorBrush> 25 procent nieprzezroczystości.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Jeśli pędzel zawiera kolorów, które są częściowo przezroczyste, wartość nieprzezroczystości koloru jest połączone za pośrednictwem mnożenia wartością przezroczystość pędzla. Na przykład jeśli pędzel ma wartość 0,5 kolor pędzla, a ponadto wartość 0,5 kolor danych wyjściowych ma wartość 0,25.  
  
> [!NOTE]
>  Jest bardziej wydajne, aby zmienić wartość nieprzezroczystości pędzla, niż można zmienić nieprzezroczystość całego elementu za pomocą jego <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> właściwości.  
  
 Może obrócić, skalowanie, pochylanie i tłumaczenie pędzla zawartości przy użyciu jego <xref:System.Windows.Media.Brush.Transform%2A> lub <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości. Aby uzyskać więcej informacji, zobacz [Przekształcanie pędzla — Przegląd](brush-transformation-overview.md).  
  
 Ponieważ są one <xref:System.Windows.Media.Animation.Animatable> obiektów <xref:System.Windows.Media.Brush> obiekty mogą być animowane. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy on z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Brush> klasa udostępnia kilka funkcji specjalnych: <xref:System.Windows.Media.Brush> obiekty mogą być deklarowane jako [zasobów](../advanced/xaml-resources.md)współużytkowane przez wiele obiektów i sklonować. Ponadto wszystkie <xref:System.Windows.Media.Brush> typów z wyjątkiem <xref:System.Windows.Media.VisualBrush> może być tylko do odczytu do zwiększenia wydajności i wprowadzone metodą o bezpiecznych wątkach.  
  
 Aby uzyskać więcej informacji na temat różnych funkcji oferowanych przez <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
 Aby uzyskać więcej informacji o tym, dlaczego <xref:System.Windows.Media.VisualBrush> obiekty nie mogą być zablokowane, zobacz <xref:System.Windows.Media.VisualBrush> typ strony.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [Przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973)
- [Przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049)
- [Tematy z instrukcjami](brushes-how-to-topics.md)
- [Inne zalecenia dotyczące wydajności](../advanced/optimizing-performance-other-recommendations.md)
