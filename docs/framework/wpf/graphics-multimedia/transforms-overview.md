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
ms.openlocfilehash: 89b781d3e5b88a66598a301a1d08cf7dfedd57a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962898"
---
# <a name="transforms-overview"></a>Przegląd Przekształcenia
W tym temacie opisano, jak używać klas 2- <xref:System.Windows.Media.Transform> D do obracania, skalowania, przenoszenia (tłumaczenia) i <xref:System.Windows.FrameworkElement> pochylania obiektów.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co to jest transformacja?  
 <xref:System.Windows.Media.Transform> Definiuje sposób mapowania lub przekształcania punktów z jednego współrzędu do innej przestrzeni współrzędnych. To mapowanie jest opisane przez transformację <xref:System.Windows.Media.Matrix>, która jest kolekcją trzech wierszy z trzema <xref:System.Double> kolumnami wartości.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) używa macierzy najważniejszych wierszy. Wektory są wyrażane jako wektory wiersza, a nie wektory kolumn.  
  
 W poniższej tabeli przedstawiono strukturę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] macierzy.  
  
### <a name="a-2-d-transformation-matrix"></a>Macierz transformacji 2-D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Wartooć 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Wartooć 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Wartooć 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Wartooć 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Wartooć 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Wartooć 0.0|1.0|  
  
 Manipulowanie wartościami macierzy pozwala na obracanie, skalowanie, pochylanie i przenoszenie (przetłumaczenie) obiektu. Na przykład jeśli zmienisz wartość w pierwszej kolumnie trzeciego wiersza ( <xref:System.Windows.Media.Matrix.OffsetX%2A> wartość) na 100, możesz użyć jej do przenoszenia jednostek 100 jednostki wzdłuż osi x. Jeśli zmienisz wartość z drugiej kolumny drugiego wiersza na 3, możesz użyć jej do rozciągnięcia obiektu do trzykrotnie jego bieżącej wysokości. Jeśli zmienisz obie wartości, przenosisz obiekt 100 jednostek wzdłuż osi x i rozciągasz jej wysokość o współczynnik 3. Ponieważ Windows Presentation Foundation (WPF) obsługuje tylko przekształcenia afinicznym, wartości w prawej kolumnie mają zawsze wartość 0, 0, 1.  
  
 Mimo że Windows Presentation Foundation (WPF) umożliwia bezpośrednie manipulowanie wartościami macierzy, zawiera również kilka <xref:System.Windows.Media.Transform> klas, które umożliwiają przekształcanie obiektu bez znajomości sposobu konfiguracji źródłowej struktury macierzy. Na przykład <xref:System.Windows.Media.ScaleTransform> Klasa umożliwia skalowanie obiektu przez ustawienie jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> zamiast manipulowania macierzą transformacji. Podobnie Klasa umożliwia obrócenie obiektu przez ustawienie jego <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwości. <xref:System.Windows.Media.RotateTransform>  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Klasy transformacji  
 Windows Presentation Foundation (WPF) udostępnia następujące klasy 2-D <xref:System.Windows.Media.Transform> dla typowych operacji transformacji:  
  
|Class|Opis|Przykład|Ilustracji|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Obraca element o określony <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Obracanie obiektu](how-to-rotate-an-object.md)|![Obróć ilustrację](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Skaluje element o określonych <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartościach i. <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>|[Skalowanie elementu](how-to-scale-an-element.md)|![Ilustracja przedstawiająca skalę](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Pochyla element o określone <xref:System.Windows.Media.SkewTransform.AngleX%2A> wartości i. <xref:System.Windows.Media.SkewTransform.AngleY%2A>|[Pochylanie elementu](how-to-skew-an-element.md)|![Ilustracja przedstawiająca pochylenie](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Przenosi (tłumaczy) element o określone <xref:System.Windows.Media.TranslateTransform.X%2A> wartości i. <xref:System.Windows.Media.TranslateTransform.Y%2A>|[Przesuwanie elementu](how-to-translate-an-element.md)|![Tłumaczenie ilustracji](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Aby utworzyć bardziej złożone przekształcenia, Windows Presentation Foundation (WPF) udostępnia następujące dwie klasy:  
  
|Class|Opis|Przykład|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Grupuje <xref:System.Windows.Media.TransformGroup> wiele obiektów w jednym <xref:System.Windows.Media.Transform> , który można następnie zastosować do właściwości transformacji.|[Stosowanie wielu przekształceń do obiektu](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Tworzy niestandardowe przekształcenia, które nie są dostarczane przez inne <xref:System.Windows.Media.Transform> klasy. W przypadku korzystania z <xref:System.Windows.Media.MatrixTransform>programu można bezpośrednio manipulować macierzą.|[Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) oferuje również przekształcenia trójwymiarowe. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Media3D.Transform3D> Klasa.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Typowe właściwości transformacji  
 Jednym ze sposobów przekształcenia obiektu jest zadeklarowanie odpowiedniego <xref:System.Windows.Media.Transform> typu i zastosowanie go do właściwości przekształcenia obiektu. Różne typy obiektów mają różne typy właściwości transformacji. W poniższej tabeli wymieniono kilka często używanych typów Windows Presentation Foundation (WPF) i ich właściwości transformacji.  
  
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
## <a name="transformations-and-coordinate-systems"></a>Przekształcenia i systemy współrzędnych  
 Gdy przekształcasz obiekt, nie tylko przekształcasz obiekt, przekształćsz przestrzeń współrzędnych, w której ten obiekt istnieje. Domyślnie transformacja jest wyśrodkowana na początku układu współrzędnych obiektu docelowego: (0, 0). Jedyny wyjątek <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform> : nie ma właściwości centralnych do ustawienia, ponieważ efekt tłumaczenia jest taki sam, niezależnie od tego, gdzie jest wyśrodkowane.  
  
 Poniższy przykład używa <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Shapes.Rectangle> obracania elementu, typu o <xref:System.Windows.FrameworkElement>45 stopni o jego domyślnym centrum (0, 0). Na poniższej ilustracji przedstawiono efekt obrotu.  
  
 ![Element FrameworkElement został obrócony o 45 &#40;stopni około 0&#41; , 0](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Element prostokąta został obrócony o 45 stopni wokół punktu (0, 0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Domyślnie element obraca się w lewym górnym rogu, (0, 0). Klasy <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform> i<xref:System.Windows.Media.SkewTransform> udostępniają właściwości CenterX i Center, które umożliwiają określenie punktu, w którym ma zostać zastosowana transformacja.  
  
 <xref:System.Windows.Media.RotateTransform> W następnym przykładzie używa się do <xref:System.Windows.Shapes.Rectangle> obracania elementu o 45 stopni, <xref:System.Windows.Media.RotateTransform.CenterX%2A> jednak ten czas i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości są ustawiane tak <xref:System.Windows.Media.RotateTransform> , aby miało środek (25, 25). Na poniższej ilustracji przedstawiono efekt obrotu.  
  
 ![Geometria obrócona 45 stopni o &#40;25, 25&#41; ](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Element prostokąta został obrócony o 45 stopni wokół punktu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Przekształcanie elementu FrameworkElement  
 Aby zastosować przekształcenia do <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Media.Transform> Utwórz i zastosuj je do jednej z dwóch właściwości dostarczanych przez <xref:System.Windows.FrameworkElement> klasę:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>— Transformacja stosowana przed przekazaniem układu. Po zastosowaniu przekształcenia system układu przetwarza przekształcony rozmiar i położenie elementu.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>— Przekształcanie modyfikujące wygląd elementu, ale jest stosowane po zakończeniu przebiegu układu. Korzystając z <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości, można uzyskać korzyści z wydajności.  
  
 Której właściwości należy używać? Ze względu na wydajność oferowanych przez nią korzyści należy używać <xref:System.Windows.UIElement.RenderTransform%2A> właściwości wszędzie tam, gdzie jest to możliwe, <xref:System.Windows.Media.Transform> szczególnie w przypadku używania animowanych obiektów. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Użyj właściwości podczas skalowania, obracania lub pochylania i potrzebujesz elementu nadrzędnego elementu, aby dopasować go do przekształconego rozmiaru elementu. Należy pamiętać, że gdy są one używane z <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwością <xref:System.Windows.Media.TranslateTransform> , obiekty wyglądają, aby nie miały wpływu na elementy. Wynika to z faktu, że system układu zwraca przetłumaczony element do jego oryginalnej pozycji w ramach przetwarzania.  
  
 Aby uzyskać dodatkowe informacje na temat [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]układu w, zobacz Omówienie [układu](../advanced/layout.md) .  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Przykład: Obróć element FrameworkElement 45 stopni  
 Poniższy przykład używa, <xref:System.Windows.Media.RotateTransform> aby obrócić przycisk w prawo o 45 stopni. Przycisk jest zawarty w <xref:System.Windows.Controls.StackPanel> , który ma dwa inne przyciski.  
  
 Domyślnie <xref:System.Windows.Media.RotateTransform> obraca się o punkt (0, 0). Ponieważ w przykładzie nie określono wartości środkowej, przycisk jest obracany o punkt (0, 0), który jest w lewym górnym rogu. Zastosowano<xref:System.Windows.UIElement.RenderTransform%2A>dowłaściwości. <xref:System.Windows.Media.RotateTransform> Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony przy użyciu Właściwość RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Obrót w prawo o 45 stopni od lewego górnego rogu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 W następnym przykładzie używa się również <xref:System.Windows.Media.RotateTransform> , aby obrócić przycisk o 45 stopni w prawo, ale <xref:System.Windows.UIElement.RenderTransformOrigin%2A> ustawia również przycisk na (0,5, 0,5). Wartość <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości jest określana względem rozmiaru przycisku. W związku z tym obrót jest stosowany do środka przycisku, a nie w lewym górnym rogu. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony na jego centrum](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Obrót w prawo o 45 stopni wokół środka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Poniższy przykład używa <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości zamiast <xref:System.Windows.UIElement.RenderTransform%2A> właściwości, aby obrócić przycisk.  Powoduje to, że transformacja ma wpływ na układ przycisku, który wyzwala pełny przebieg przez system układu. W związku z tym przycisk jest obrócony, a następnie ponownie pozycjonowany, ponieważ jego rozmiar zmienił się. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony przy użyciu LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform używany do obracania przycisku  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animowanie transformacji  
 Ponieważ dziedziczą z <xref:System.Windows.Media.Animation.Animatable> klasy <xref:System.Windows.Media.Transform> , klasy mogą być animowane. Aby animować a <xref:System.Windows.Media.Transform>, Zastosuj animację zgodnego typu do właściwości, którą chcesz animować.  
  
 W poniższym przykładzie w momencie <xref:System.Windows.Media.Animation.Storyboard> kliknięcia jest <xref:System.Windows.Media.Animation.DoubleAnimation> stosowane a <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Controls.Button> z i i.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [przykład przekształcenia 2-D](https://go.microsoft.com/fwlink/?LinkID=158252). Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Transform> , Klasa oferuje kilka specjalnych funkcji: <xref:System.Windows.Media.Transform> obiekty mogą być deklarowane jako [zasoby](../advanced/xaml-resources.md), współużytkowane przez wiele obiektów, wykonywane tylko do odczytu w celu poprawy wydajności, klonowania i bezpieczny wątkowo. Aby uzyskać więcej informacji o różnych funkcjach dostarczanych przez <xref:System.Windows.Freezable> obiekty, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Tematy z instrukcjami](transformations-how-to-topics.md)
- [Przykład transformacji 2-D](https://go.microsoft.com/fwlink/?LinkID=158252)
