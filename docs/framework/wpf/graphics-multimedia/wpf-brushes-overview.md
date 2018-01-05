---
title: "Przegląd Pędzle WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec7e566e6f56c215bbaeafdfb5c5e97cc0add0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-brushes-overview"></a>Przegląd Pędzle WPF
Wszystko, co jest widoczne na ekranie jest widoczna, ponieważ został on rysowane przez pędzla. Na przykład służy pędzel opisujący tło przycisku, pierwszego planu tekstu i wypełnienia kształtu. W tym temacie przedstawiono koncepcję malowanie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pędzle oraz przykłady. Pędzle umożliwiają malowanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obiekty o nic proste, pełne kolory do złożonych zestawów wzorców i obrazów.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Malowanie pędzla  
 A <xref:System.Windows.Media.Brush> "umożliwia malowanie" obszar o jego dane wyjściowe. Pędzle różnych mają różne typy danych wyjściowych. Niektóre pędzle malowanie obszar jednolitym kolorem, osoby z gradientu, wzorzec, obrazu lub rysunku. Na poniższej ilustracji przedstawiono przykłady każdego z różnych <xref:System.Windows.Media.Brush> typów.  
  
 ![Pędzel typy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Przykłady pędzla  
  
 Większość obiektów visual pozwalają określić, jak są rysowane. W poniższej tabeli przedstawiono niektóre typowe obiekty i właściwości, których można użyć <xref:System.Windows.Media.Brush>.  
  
|Class|Właściwości pędzla|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 W poniższych sekcjach opisano różne <xref:System.Windows.Media.Brush> typów i podać przykład każdego z nich.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Paint jednolitym kolorem  
 A <xref:System.Windows.Media.SolidColorBrush> rysują obszar o niezawodnej <xref:System.Windows.Media.Color>. Istnieje wiele sposobów, aby określić <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush>: na przykład można określić jego kanałów alfa, czerwony, niebieski i zielony lub użyj jednej z kolor wstępnie zdefiniowanego podał <xref:System.Windows.Media.Colors> klasy.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.SolidColorBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowane prostokąta.  
  
 ![Prostokąt rysowane przy użyciu obiektu SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Prostokąt rysowane przy użyciu obiektu SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.SolidColorBrush> , zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Paint z gradientu liniowego  
 A <xref:System.Windows.Media.LinearGradientBrush> rysują obszar o gradientu liniowego. Gradient liniowy miesza dwa lub więcej kolory na linii osi gradientu. Możesz użyć <xref:System.Windows.Media.GradientStop> obiektów, aby określić kolory gradientu i ich pozycji.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowane prostokąta.  
  
 ![Prostokąt rysowane przy użyciu LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Prostokąt rysowane przy użyciu LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.LinearGradientBrush> , zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Paint z gradientu promieniowego  
 A <xref:System.Windows.Media.RadialGradientBrush> rysują obszar o gradientu promieniowego. Gradient promieniowy miesza dwa lub więcej kolorów między okręgu. Jak <xref:System.Windows.Media.LinearGradientBrush> klasy, należy użyć <xref:System.Windows.Media.GradientStop> obiektów, aby określić kolory gradientu i ich pozycji.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RadialGradientBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowane prostokąta.  
  
 ![Prostokąt rysowane przy użyciu obiektu RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Prostokąt rysowane przy użyciu obiektu RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.RadialGradientBrush> , zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Paint z obrazem  
 <xref:System.Windows.Media.ImageBrush> Rysują obszar o <xref:System.Windows.Media.ImageSource>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowane prostokąta.  
  
 ![Prostokąt rysowane przy użyciu obiektu ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Prostokąt rysowane przy użyciu obrazu  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> , zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Paint z rysunkiem  
 A <xref:System.Windows.Media.DrawingBrush> rysują obszar o <xref:System.Windows.Media.Drawing>. A <xref:System.Windows.Media.Drawing> może zawierać kształtów, obrazy, tekst i nośnika.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowane prostokąta.  
  
 ![Prostokąt rysowane przy użyciu obiektu DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Prostokąt rysowane przy użyciu obiektu DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.DrawingBrush> , zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Rysuj za pomocą Visual  
 A <xref:System.Windows.Media.VisualBrush> rysują obszar o <xref:System.Windows.Media.Visual> obiektu. Przykłady Visual obiektów <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, i <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> umożliwia także zawartości projektu z jednej części aplikacji do innego obszaru; jest ono bardzo przydatne do tworzenia odbicia efekty i powiększanie części ekranu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> namalować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>. Na poniższej ilustracji przedstawiono malowane prostokąta.  
  
 ![Prostokąt rysowane przy użyciu VisualBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Prostokąt rysowane przy użyciu VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.VisualBrush> , zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Paint przy użyciu wstępnie zdefiniowane i pędzle systemu  
 Dla wygody [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] udostępnia zestaw wstępnie zdefiniowanych i system pędzle, której można malować obiektów.  
  
-   Lista dostępnych pędzle wstępnie zdefiniowane, zobacz <xref:System.Windows.Media.Brushes> klasy. Na przykład przedstawiający sposób użycia wstępnie zdefiniowanych pędzla zobacz [malowanie obszar jednolitym kolorem](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md).  
  
-   Aby uzyskać listę pędzle dostępnej w systemie, zobacz <xref:System.Windows.SystemColors> klasy. Na przykład zobacz [malowanie obszar o pędzla systemu](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Wspólne funkcje pędzla  
 <xref:System.Windows.Media.Brush>Podaj obiekty <xref:System.Windows.Media.Brush.Opacity%2A> właściwość, która może służyć do upewnij pędzla przezroczystego lub częściowo przezroczysty. <xref:System.Windows.Media.Brush.Opacity%2A> Wartość 0 powoduje, że pędzel jest całkowicie przezroczysty podczas <xref:System.Windows.Media.Brush.Opacity%2A> wartość 1 powoduje, że pędzel jest całkowicie przezroczystości. W poniższym przykładzie użyto <xref:System.Windows.Media.Brush.Opacity%2A> właściwości, aby <xref:System.Windows.Media.SolidColorBrush> 25 procent przezroczystości.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Jeśli pędzla zawiera kolorów, które są częściowo przezroczysty, wartość Przezroczystość koloru są łączone za pomocą mnożenia wartości przezroczystość pędzla. Na przykład jeśli pędzel ma wartość 0,5 kolor pędzla, a ponadto wartość 0,5 kolor wyjściowy ma wartość 0,25.  
  
> [!NOTE]
>  Jest bardziej wydajne, aby zmienić wartość przezroczystość pędzla niż zmienić nieprzezroczystość cały element przy użyciu jego <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> właściwości.  
  
 Można obrócić, skalowanie, pochylanie i przetłumaczenie pędzla zawartości przy użyciu jego <xref:System.Windows.Media.Brush.Transform%2A> lub <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości. Aby uzyskać więcej informacji, zobacz [omówienie przekształcania pędzla](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Ponieważ są one <xref:System.Windows.Media.Animation.Animatable> obiektów, <xref:System.Windows.Media.Brush> obiektów można animować. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Funkcje obiektu freezable  
 Ponieważ dziedziczy on z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Brush> klasa udostępnia kilka funkcje specjalne: <xref:System.Windows.Media.Brush> obiekty mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md)współużytkowane przez wiele obiektów i sklonować. Ponadto wszystkie <xref:System.Windows.Media.Brush> typów, z wyjątkiem <xref:System.Windows.Media.VisualBrush> może być tylko do odczytu do zwiększenia wydajności i wprowadzone wątkowo.  
  
 Aby uzyskać więcej informacji o różnych funkcjach dostarczonych przez <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Aby uzyskać więcej informacji o tym, dlaczego <xref:System.Windows.Media.VisualBrush> obiekty nie mogą być zablokowane, zobacz <xref:System.Windows.Media.VisualBrush> typu strony.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Pędzle próbki](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [Przykładowe ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Przykładowe VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
