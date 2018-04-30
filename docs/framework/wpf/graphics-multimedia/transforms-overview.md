---
title: Przegląd Przekształcenia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e63b83ea455a342d5d3fedaee0ad7d1714e90998
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="transforms-overview"></a>Przegląd Przekształcenia
W tym temacie opisano sposób użycia [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> klasy obracanie, skalowanie, Przenieś (tłumaczenie) i pochylanie <xref:System.Windows.FrameworkElement> obiektów.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co to jest transformacja?  
 A <xref:System.Windows.Media.Transform> definiuje sposób mapowania lub Przekształć punkty z jednej przestrzeni współrzędnych do innej przestrzeni współrzędnych. To mapowanie jest opisane przez transformację <xref:System.Windows.Media.Matrix>, która jest kolekcją trzy wiersze z trzy kolumny <xref:System.Double> wartości.  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) korzysta z macierzami zapisywanymi wierszami. Wektory są wyrażane jako wektory wiersza, nie wektory kolumny.  
  
 W poniższej tabeli przedstawiono struktury [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] macierzy.  
  
### <a name="a-2-d-transformation-matrix"></a>Macierzy transformacji 2-D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Domyślne: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Domyślne: 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Domyślne: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Domyślne: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Domyślne: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Domyślne: 0,0|1.0|  
  
 Przez manipulowanie wartości macierzy, można obrócić, skalowanie, pochylanie i Przenieś (tłumaczenie) obiektu. Na przykład zmień wartość w pierwszej kolumnie trzeciego wiersza ( <xref:System.Windows.Media.Matrix.OffsetX%2A> wartość) do 100, można go przenieść obiekt 100 jednostki wzdłuż osi x. Jeśli zmienisz wartość w drugiej kolumnie drugiego wiersza z 3, można użyć go do rozciągania trzy razy Bieżąca wysokość obiektu. Jeśli zmienisz obie wartości, Przenieś obiekt jednostki 100 wzdłuż osi x i rozciąganie wysokość o 3. Program Windows Presentation Foundation (WPF) obsługuje tylko affine — przekształcenia, wartości w prawej kolumnie są zawsze 0, 0, 1.  
  
 Mimo że Windows Presentation Foundation (WPF) umożliwia bezpośrednie manipulowanie wartości macierzy, dostępne są także kilka <xref:System.Windows.Media.Transform> klasy, które umożliwiają Przekształć obiekt bez uprzedniego uzyskania informacji o konfiguracji struktury macierzy. Na przykład <xref:System.Windows.Media.ScaleTransform> klasa pozwala na skalowanie obiektu przez ustawienie jej <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości, zamiast manipulowanie macierzy transformacji. Podobnie <xref:System.Windows.Media.RotateTransform> klasa umożliwia obracanie obiektu tylko ustawiając jego <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwości.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Przekształć klas  
 Windows Presentation Foundation (WPF) zawiera następujące [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> klasy dla typowych transformacji:  
  
|Class|Opis|Przykład|Ilustracja|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Obraca element przez określony <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Obracanie obiektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Ilustracja przedstawiająca obrót](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Skaluje przez określony element <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> kwoty.|[Skalowanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Skalowanie ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Pochyla przez określony element <xref:System.Windows.Media.SkewTransform.AngleX%2A> i <xref:System.Windows.Media.SkewTransform.AngleY%2A> kwoty.|[Pochylanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Pochylanie ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Przenosi (przekłada) elementu przez określony <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> kwoty.|[Przesuwanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Ilustracja przedstawiająca translację](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Do tworzenia bardziej złożone przekształcenia, Windows Presentation Foundation (WPF) zawiera następujące dwie klasy:  
  
|Class|Opis|Przykład|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Wiele grup <xref:System.Windows.Media.TransformGroup> obiektów w ramach jednej <xref:System.Windows.Media.Transform> które następnie można zastosować do właściwości transform.|[Stosowanie wielu przekształceń do obiektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Tworzy niestandardowych przekształceń, które nie są dostarczane przez innych <xref:System.Windows.Media.Transform> klasy. Jeśli używasz <xref:System.Windows.Media.MatrixTransform>, bezpośrednio manipulowania macierzy.|[Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) zawiera również [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] przekształcenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Media3D.Transform3D> klasy.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Wspólne właściwości przekształcania  
 Jednym ze sposobów transformacji obiektu jest aby zadeklarować odpowiednie <xref:System.Windows.Media.Transform> wpisz i zastosować je do właściwości transformacji obiektu. Różne typy obiektów mają różne typy właściwości transformacji. W poniższej tabeli wymieniono kilka często używanych typów Windows Presentation Foundation (WPF) oraz ich właściwości transformacji.  
  
|Typ|Właściwości przekształcania|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Przekształcenia i system współrzędnych  
 Przekształcenie obiektu można nie tylko przekształcają obiekt, Przekształć przestrzeni współrzędnych, w której znajduje się ten obiekt. Domyślnie transformacji jest wyśrodkowywana w źródle współrzędnych obiektu docelowego: (0,0). Jedynym wyjątkiem jest <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> nie ma center właściwości można ustawić, ponieważ tłumaczenia efekt jest taki sam, niezależnie od tego, gdzie jest wyśrodkowywana.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> obracania <xref:System.Windows.Shapes.Rectangle> elementu, typ <xref:System.Windows.FrameworkElement>, o 45 stopni, o jego domyślne Centrum (0, 0). Na poniższej ilustracji przedstawiono wpływu obrotu.  
  
 ![FrameworkElement obrócony o 45 stopni o &#40;0,0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Element prostokąt obrócony o 45 stopni wokół punktu (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Domyślnie element obraca się o jego lewym górnym rogu (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, I <xref:System.Windows.Media.SkewTransform> klasy dostarczenie CenterX i CenterY właściwości, które umożliwiają określenie punktu, w którym stosowana jest transformacja.  
  
 W następnym przykładzie użyto również <xref:System.Windows.Media.RotateTransform> obracania <xref:System.Windows.Shapes.Rectangle> element o 45 stopni; jednak teraz <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości są ustawione, aby <xref:System.Windows.Media.RotateTransform> ma środek (25, 25). Na poniższej ilustracji przedstawiono wpływu obrotu.  
  
 ![Obiekt Geometry obrócony o 45 stopni o &#40;25, 25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Element prostokąt obrócony o 45 stopni punktu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Przekształcanie typu FrameworkElement  
 Do stosowania przekształcenia do <xref:System.Windows.FrameworkElement>, Utwórz <xref:System.Windows.Media.Transform> i zastosować je do jednej z dwóch właściwości który <xref:System.Windows.FrameworkElement> zawiera klasy:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> — Transformację stosowaną przed przebiegu układu. Po zastosowaniu przekształcenia systemu układu przetwarza po przekształceniu rozmiar i położenie elementu.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> — Transformację modyfikuje wygląd elementu, ale są stosowane po ukończeniu przebiegu układu. Za pomocą <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości, można uzyskać zwiększenia wydajności.  
  
 Które właściwości należy użyć? Z powodu zwiększenia wydajności, które zapewnia, użyj <xref:System.Windows.UIElement.RenderTransform%2A> właściwość zawsze, gdy to możliwe, szczególnie w przypadku, gdy używasz animowany <xref:System.Windows.Media.Transform> obiektów. Użyj <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości podczas skalowania, obracania lub pochylanie i potrzebujesz nadrzędnego elementu na dostosowanie rozmiaru po przekształceniu elementu. Należy zauważyć, że gdy są one używane z <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwość <xref:System.Windows.Media.TranslateTransform> obiektów prawdopodobnie nie mają wpływu na elementy. Wynika to z systemu układu zwraca element przetłumaczone do oryginalnego położenia podczas jego przetwarzania.  
  
 Aby uzyskać dodatkowe informacje dotyczące układu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md) omówienie.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Przykład: Obracanie FrameworkElement 45 stopni  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> obracania zegara przycisk o 45 stopni. Przycisk znajduje się w <xref:System.Windows.Controls.StackPanel> która ma dwa inne przyciski.  
  
 Domyślnie <xref:System.Windows.Media.RotateTransform> obraca o punkt (0, 0). Ponieważ przykładzie nie określa wartości Centrum, przycisk obraca informacje o punkcie (0, 0), który jest jego lewym górnym rogu. <xref:System.Windows.Media.RotateTransform> Jest stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony przy użyciu właściwości RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
45 stopni od lewego górnego rogu obrót w prawo  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 W następnym przykładzie użyto również <xref:System.Windows.Media.RotateTransform> obracania przycisk 45 stopni w prawo, ale także ustawia <xref:System.Windows.UIElement.RenderTransformOrigin%2A> przycisku (0,5, 0,5). Wartość <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości jest zależny od rozmiaru przycisku. W związku z tym obrót jest stosowany do Centrum przycisku, zamiast jego lewym górnym rogu. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony o jego center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
45 stopni wokół środka obrót w prawo  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości zamiast <xref:System.Windows.UIElement.RenderTransform%2A> Obróć przycisk Właściwości.  Powoduje to przekształcenie wpływ na układ przycisku, który wyzwala pełny przebieg przez system układu. W związku z tym przycisku jest obracana i następnie położenia, ponieważ jego rozmiar został zmieniony. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony przy użyciu właściwości LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Właściwości LayoutTransform używany do obracania przycisku  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animowanie przekształcenia  
 Ponieważ dziedziczą z <xref:System.Windows.Media.Animation.Animatable> klasy <xref:System.Windows.Media.Transform> klasy można animować. Aby animować <xref:System.Windows.Media.Transform>, dotyczą animacji zgodne z typem właściwości mają być animowane.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.DoubleAnimation> z <xref:System.Windows.Media.RotateTransform> dokonanie <xref:System.Windows.Controls.Button> pokrętła w miejscu po kliknięciu.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252). Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkcje obiektu freezable  
 Ponieważ dziedziczy on z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Transform> klasy udostępnia kilka funkcje specjalne: <xref:System.Windows.Media.Transform> obiekty mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md)współużytkowanych przez wiele obiektów, aby poprawić jest tylko do odczytu wydajność, sklonowany, a wprowadzone wątkowo. Aby uzyskać więcej informacji na temat różnych funkcji, które są udostępniane przez <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Przykład 2-D transformacji](http://go.microsoft.com/fwlink/?LinkID=158252)
