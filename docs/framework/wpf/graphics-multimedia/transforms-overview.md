---
title: Przegląd Przekształcenia
ms.date: 03/30/2017
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
ms.openlocfilehash: 4fd846502fd348222bc1da1c8746f037e9f237fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425846"
---
# <a name="transforms-overview"></a>Przegląd Przekształcenia
W tym temacie opisano sposób użycia [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> klasy, aby obrócić, skalowanie, Przenieś (tłumaczenia) i pochylanie <xref:System.Windows.FrameworkElement> obiektów.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co to jest przekształcenie?  
 A <xref:System.Windows.Media.Transform> definiuje sposób mapowania lub Przekształcanie punktów z jednej przestrzeni współrzędnych do innej przestrzeni współrzędnych. To mapowanie jest opisana przez przekształcenie <xref:System.Windows.Media.Matrix>, który jest kolekcją trzy wiersze z trzy kolumny <xref:System.Double> wartości.  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) korzysta z macierzy wierszu. Wektory są wyrażane jako wektorów wiersza, nie wektorów kolumny.  
  
 W poniższej tabeli przedstawiono strukturę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] macierzy.  
  
### <a name="a-2-d-transformation-matrix"></a>Macierzy transformacji 2-D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Domyślne: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Domyślne: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Domyślne: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Domyślne: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Domyślne: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Domyślne: 0.0|1.0|  
  
 Przez operacje wartości macierzy, może obrócić, skalowanie, pochylanie i przenieść (tłumaczenia) obiektu. Na przykład, jeśli zmienisz wartość w pierwszej kolumnie trzeciego wiersza ( <xref:System.Windows.Media.Matrix.OffsetX%2A> wartość) na 100, można go przenieść obiekt 100 jednostki wzdłuż osi x. Jeśli zmienisz wartość w drugiej kolumnie drugi wiersz 3 służy do rozciągania trzykrotnie jego wysokość bieżącego obiektu. Jeśli zmienisz obie wartości, Przenieś obiekt, 100 jednostek wzdłuż osi x i rozciągnij swoją wysokość ośmiokrotnego 3. Ponieważ Windows Presentation Foundation (WPF) obsługuje tylko affine — przekształcenia, wartości w prawej kolumnie to zawsze 0, 0, 1.  
  
 Windows Presentation Foundation (WPF) umożliwia bezpośrednie manipulowanie wartości macierzy, zawiera także kilka <xref:System.Windows.Media.Transform> klas, które umożliwiają przekształcanie obiektu, nie wiedząc o tym, jak skonfigurowano wewnętrzna struktura macierzy. Na przykład <xref:System.Windows.Media.ScaleTransform> klasy umożliwia skalowanie obiektu przez ustawienie jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości zamiast operować macierzy transformacji. Podobnie <xref:System.Windows.Media.RotateTransform> klasy umożliwia obracanie obiektu przez ustawienie tylko jego <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwości.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Klasy przekształceń  
 Windows Presentation Foundation (WPF) udostępnia następujące [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> klasy dla typowych operacji przekształcania:  
  
|Class|Opis|Przykład|Ilustracja|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Obraca element przez określony <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Obracanie obiektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Ilustracja przedstawiająca obrót](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Skaluje się przez określony element <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> kwoty.|[Skalowanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Skalowanie ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Pochyla element o określonym <xref:System.Windows.Media.SkewTransform.AngleX%2A> i <xref:System.Windows.Media.SkewTransform.AngleY%2A> kwoty.|[Pochylanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Pochylanie ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Przenosi (przekłada) element o określonym <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> kwoty.|[Przesuwanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Ilustracja przedstawiająca translację](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Do utworzenia bardziej złożonych przekształceń, Windows Presentation Foundation (WPF) zawiera następujące dwie klasy:  
  
|Class|Opis|Przykład|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Grupuje wielu <xref:System.Windows.Media.TransformGroup> obiektów w jednym <xref:System.Windows.Media.Transform> , można użyć do przekształcania właściwości.|[Stosowanie wielu przekształceń do obiektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Tworzy niestandardowe przekształcenia, które nie są udostępniane przez inne <xref:System.Windows.Media.Transform> klasy. Kiedy używasz <xref:System.Windows.Media.MatrixTransform>, bezpośrednie manipulowanie macierzy.|[Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) zapewnia również [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] przekształcenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Media3D.Transform3D> klasy.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Wspólne właściwości transformacji  
 Jednym ze sposobów, aby przekształcić obiekt jest deklarować odpowiednie <xref:System.Windows.Media.Transform> wpisz i zastosować je do właściwości przekształcenie obiektu. Różne typy obiektów mają różne typy właściwości transformacji. W poniższej tabeli wymieniono kilka często używanych typów Windows Presentation Foundation (WPF) i ich właściwości transformacji.  
  
|Typ|Właściwości transformacji|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Przekształcenia i systemów współrzędnych  
 Przekształcenie obiektu nie po prostu przekształcić obiekt, Przekształć przestrzeni współrzędnych, w której istnieje tego obiektu. Domyślnie przekształcenia skupia się na źródło współrzędnych obiekt docelowy: (0,0). Jedynym wyjątkiem jest <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> nie ma żadnych właściwości Centrum, ponieważ tłumaczenia efekt jest taki sam, niezależnie od tego, gdzie jest wyśrodkowywana.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> wymienić <xref:System.Windows.Shapes.Rectangle> elementu, typ <xref:System.Windows.FrameworkElement>, o 45 stopni, o jej środka domyślna (0, 0). Poniższa ilustracja przedstawia wpływu obrotu.  
  
 ![FrameworkElement obracać 45 stopni, o &#40;0,0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Element prostokąt obrócony o 45 stopni, o punkt (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Domyślnie element obraca się o jego lewego górnego rogu (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, I <xref:System.Windows.Media.SkewTransform> klasy zapewniają CenterX i CenterY właściwości, które umożliwiają określenie punktu, w którym zastosowano transformacji.  
  
 W następnym przykładzie użyto również <xref:System.Windows.Media.RotateTransform> wymienić <xref:System.Windows.Shapes.Rectangle> element o 45 stopni; jednak tym razem <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości są ustawione tak, aby <xref:System.Windows.Media.RotateTransform> ma środek (25, 25). Poniższa ilustracja przedstawia wpływu obrotu.  
  
 ![Geometria obracać 45 stopni, o &#40;25, 25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Element prostokąt obrócony o 45 stopni, o punkt (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Przekształcanie FrameworkElement  
 Aby zastosować przekształceń w celu <xref:System.Windows.FrameworkElement>, Utwórz <xref:System.Windows.Media.Transform> i zastosować je do jednej z dwóch właściwości, <xref:System.Windows.FrameworkElement> klasa oferuje:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Przekształcenie, który zostanie zastosowany przed przekazanie układu. Po zastosowaniu przekształcenia system układu przetwarza przekształcone rozmiar i położenie elementu.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> — Przekształcenia modyfikuje wygląd elementu, które są stosowane po zakończeniu przebiegu układu. Za pomocą <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości, można uzyskać korzyści wydajności.  
  
 Które właściwości należy użyć? Ze względu na korzyści w zakresie wydajności, które zawiera, użyj <xref:System.Windows.UIElement.RenderTransform%2A> właściwość zawsze wtedy, gdy to możliwe, szczególnie w przypadku, gdy używasz animowane <xref:System.Windows.Media.Transform> obiektów. Użyj <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości podczas skalowania, rotacji lub pochylania, jeśli jest konieczne element nadrzędny elementu, aby dopasować rozmiar po przekształceniu elementu. Należy zauważyć, że gdy są one używane z <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości <xref:System.Windows.Media.TranslateTransform> obiekty wydają się nie mają wpływu na elementy. To, ponieważ system układu zwraca element przetłumaczone do swojego pierwotnego położenia w ramach jego przetwarzania.  
  
 Aby uzyskać dodatkowe informacje na temat układu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], zobacz [układ](../../../../docs/framework/wpf/advanced/layout.md) Przegląd.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Przykład: Obracanie FrameworkElement 45 stopni  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> obracanie przycisku obrotu w prawo o 45 stopni. Przycisk znajduje się w <xref:System.Windows.Controls.StackPanel> zawierający dwa inne przyciski.  
  
 Domyślnie <xref:System.Windows.Media.RotateTransform> obraca się o punkt (0, 0). Ponieważ przykład określają wartością środkową, przycisk obraca się o punkt (0, 0), który jest jego lewego górnego rogu. <xref:System.Windows.Media.RotateTransform> Jest stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Poniższa ilustracja przedstawia wynik przekształcenia.  
  
 ![Przekształcona przy użyciu RenderTransform przycisku](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Obrót w prawo wokół 45 stopni od lewego górnego rogu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 W następnym przykładzie użyto również <xref:System.Windows.Media.RotateTransform> obracanie przycisku 45 stopni w prawo, ale także ustawia <xref:System.Windows.UIElement.RenderTransformOrigin%2A> przycisku (0,5, 0,5). Wartość <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość jest określana względem rozmiar przycisku. W rezultacie obrót zastosowano do środka przycisk, a nie jego lewego górnego rogu. Poniższa ilustracja przedstawia wynik przekształcenia.  
  
 ![Przycisk przekształcony o jej środka](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Obrót w prawo wokół 45 stopni wokół środka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości zamiast <xref:System.Windows.UIElement.RenderTransform%2A> właściwość obracanie przycisku.  Powoduje to przekształcenie wpływ na układ przycisku, który wyzwala pełny przebieg przez system układu. W rezultacie przycisku jest obracana i następnie przeniesiony, ponieważ jego rozmiar został zmieniony. Poniższa ilustracja przedstawia wynik przekształcenia.  
  
 ![Przycisk przekształcony przy użyciu właściwości LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform umożliwiają obracanie przycisku  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animowanie przekształcenia  
 Ponieważ dziedziczą z <xref:System.Windows.Media.Animation.Animatable> klasy <xref:System.Windows.Media.Transform> klasy mogą być animowane. Aby animować <xref:System.Windows.Media.Transform>, dotyczą animacji zgodne z typem właściwości mają być animowane.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.DoubleAnimation> z <xref:System.Windows.Media.RotateTransform> się <xref:System.Windows.Controls.Button> pokrętła w miejscu po kliknięciu.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252). Aby uzyskać więcej informacji na temat animacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy on z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Transform> klasy zapewniają kilka funkcji specjalnych: <xref:System.Windows.Media.Transform> obiekty mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md), udostępnione wśród wielu obiektów, aby poprawić jest tylko do odczytu wydajność, sklonować i wprowadzone metodą o bezpiecznych wątkach. Aby uzyskać więcej informacji na temat różnych funkcji, które są dostarczane przez <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Przykładowe transformacje 2-D](https://go.microsoft.com/fwlink/?LinkID=158252)
