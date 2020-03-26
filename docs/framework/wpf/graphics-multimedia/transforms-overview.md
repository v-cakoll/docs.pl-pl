---
title: Przegląd Przekształcenia
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2D transform
- transform classes [WPF], 2D
- 2D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: c5f29404a301eb023ff24b2890531dede6440ec4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111962"
---
# <a name="transforms-overview"></a>Przegląd Przekształcenia
W tym temacie opisano sposób <xref:System.Windows.Media.Transform> używania klas 2D do obracania, skalowania, przenoszenia (tłumaczenia) i pochylania <xref:System.Windows.FrameworkElement> obiektów.  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>Co to jest transformacja?  
 A <xref:System.Windows.Media.Transform> definiuje sposób mapowania lub przekształcania punktów z jednej przestrzeni współrzędnych do innej przestrzeni współrzędnych. To mapowanie jest opisane <xref:System.Windows.Media.Matrix>przez transformację , która jest zbiorem <xref:System.Double> trzech wierszy z trzema kolumnami wartości.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) używa macierzy głównych wierszy. Wektory są wyrażone jako wektory wierszy, a nie wektory kolumn.  
  
 W poniższej tabeli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przedstawiono strukturę macierzy.  
  
### <a name="a-2d-transformation-matrix"></a>Macierz transformacji 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Domyślnie: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Wartość domyślna: 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Wartość domyślna: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Domyślnie: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Wartość domyślna: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Wartość domyślna: 0,0|1.0|  
  
 Manipulując wartościami macierzy, można obracać, skalować, pochylać i przesuwać (tłumaczyć) obiekt. Jeśli na przykład wartość w pierwszej kolumnie trzeciego wiersza <xref:System.Windows.Media.Matrix.OffsetX%2A> (wartość) zostanie zmieniona na 100, można ją użyć do przesuń obiekt o 100 jednostek wzdłuż osi x. Jeśli zmienisz wartość w drugiej kolumnie drugiego wiersza na 3, możesz użyć jej do rozciągnięcia obiektu do trzykrotnie starszej jego bieżącej wysokości. Jeśli zmienisz obie wartości, przesuniesz obiekt o 100 jednostek wzdłuż osi x i rozciągnij jego wysokość o współczynnik 3. Ponieważ Windows Presentation Foundation (WPF) obsługuje tylko przekształca afine, wartości w prawej kolumnie są zawsze 0, 0, 1.  
  
 Mimo że Windows Presentation Foundation (WPF) umożliwia bezpośrednie manipulowanie <xref:System.Windows.Media.Transform> wartościami macierzy, udostępnia również kilka klas, które umożliwiają przekształcanie obiektu bez wiedzy o konfiguracji podstawowej struktury macierzy. Na przykład <xref:System.Windows.Media.ScaleTransform> klasa umożliwia skalowanie obiektu przez <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ustawienie jego i właściwości, zamiast manipulowania macierzy transformacji. Podobnie <xref:System.Windows.Media.RotateTransform> klasa umożliwia obracanie obiektu przez ustawienie jego <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwości.  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>Przekształcanie klas  
 Windows Presentation Foundation (WPF) udostępnia <xref:System.Windows.Media.Transform> następujące klasy 2D dla typowych operacji transformacji:  
  
|Klasa|Opis|Przykład|Ilustracji|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Obraca element o określony <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Obracanie obiektu](how-to-rotate-an-object.md)|![Obróć ilustrację](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Skaluje element o <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> określone <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> i kwoty.|[Skalowanie elementu](how-to-scale-an-element.md)|![Ilustracja skali](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Pochyla element o określone <xref:System.Windows.Media.SkewTransform.AngleX%2A> <xref:System.Windows.Media.SkewTransform.AngleY%2A> i kwoty.|[Pochyl element](how-to-skew-an-element.md)|![Pochyl ilustrację](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Przenosi (tłumaczy) element o <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform.Y%2A> określone i kwoty.|[Przesuwanie elementu](how-to-translate-an-element.md)|![Tłumaczenie ilustracji](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Do tworzenia bardziej złożonych przekształceń, Windows Presentation Foundation (WPF) udostępnia następujące dwie klasy:  
  
|Klasa|Opis|Przykład|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Grupuje <xref:System.Windows.Media.TransformGroup> wiele obiektów <xref:System.Windows.Media.Transform> w jeden, który można następnie zastosować do właściwości przekształcania.|[Stosowanie wielu przekształceń do obiektu](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Tworzy niestandardowe przekształcenia, które <xref:System.Windows.Media.Transform> nie są dostarczane przez inne klasy. Podczas korzystania <xref:System.Windows.Media.MatrixTransform>z programu , można manipulować Macierzy bezpośrednio.|[Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) zapewnia również przekształcenia 3D. Aby uzyskać więcej <xref:System.Windows.Media.Media3D.Transform3D> informacji, zobacz klasę.  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>Typowe właściwości transformacji  
 Jednym ze sposobów przekształcenia obiektu <xref:System.Windows.Media.Transform> jest zadeklarowanie odpowiedniego typu i zastosowanie go do właściwości transformacji obiektu. Różne typy obiektów mają różne typy właściwości transformacji. W poniższej tabeli wymieniono kilka powszechnie używanych typów programu Windows Presentation Foundation (WPF) i ich właściwości transformacji.  
  
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
## <a name="transformations-and-coordinate-systems"></a>Przekształcenia i układy współrzędnych  
 Podczas przekształcania obiektu nie można tylko przekształcać obiekt, przekształcać przestrzeń współrzędnych, w której ten obiekt istnieje. Domyślnie transformacja jest wyśrodkowyna na początku układu współrzędnych obiektu docelowego: (0,0). Jedynym wyjątkiem <xref:System.Windows.Media.TranslateTransform>jest ; a <xref:System.Windows.Media.TranslateTransform> nie ma właściwości środka do ustawionego, ponieważ efekt tłumaczenia jest taki sam, niezależnie od tego, gdzie jest wyśrodkowany.  
  
 W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> użyto <xref:System.Windows.Shapes.Rectangle> a do <xref:System.Windows.FrameworkElement>obracania elementu, typu , o 45 stopni o jego domyślny środek (0, 0). Na poniższej ilustracji przedstawiono efekt obrotu.  
  
 ![FrameworkElement obrócony o 45 stopni o &#40;0,0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Element prostokąta obrócony o 45 stopni w punkcie (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Domyślnie element obraca się w lewym górnym rogu (0, 0). Klasy <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ScaleTransform>, <xref:System.Windows.Media.SkewTransform> i klasy zapewniają właściwości CenterX i CenterY, które umożliwiają określenie punktu, w którym transformacja jest stosowana.  
  
 W następnym przykładzie <xref:System.Windows.Media.RotateTransform> użyto również <xref:System.Windows.Shapes.Rectangle> a do obracania elementu o 45 stopni; jednak tym razem <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości i są ustawione <xref:System.Windows.Media.RotateTransform> tak, że ma środek (25, 25). Na poniższej ilustracji przedstawiono efekt obrotu.  
  
 ![Geometria obracała się o 45 stopni około &#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Element prostokąta obrócony o 45 stopni w punkcie (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>Przekształcanie frameworkelement  
 Aby zastosować przekształcenia do , <xref:System.Windows.FrameworkElement>utworzyć <xref:System.Windows.Media.Transform> i zastosować go do <xref:System.Windows.FrameworkElement> jednej z dwóch właściwości, które zapewnia klasa:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Transformacja, która jest stosowana przed przebiegiem układu. Po zastosowaniu transformacji system układu przetwarza przekształcony rozmiar i położenie elementu.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– Transformacja, która modyfikuje wygląd elementu, ale jest stosowana po zakończeniu przebiegu układu. Korzystając z <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości, można uzyskać korzyści wydajności.  
  
 Której właściwości należy używać? Ze względu na korzyści wydajności, <xref:System.Windows.UIElement.RenderTransform%2A> które zapewnia, należy użyć właściwości, gdy jest to możliwe, zwłaszcza w przypadku korzystania z obiektów animowanych. <xref:System.Windows.Media.Transform> Użyj <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości podczas skalowania, obracania lub pochylania i potrzebujesz elementu nadrzędnego elementu, aby dostosować się do przekształconego rozmiaru elementu. Należy zauważyć, że gdy <xref:System.Windows.FrameworkElement.LayoutTransform%2A> są <xref:System.Windows.Media.TranslateTransform> one używane z właściwości, obiekty wydają się nie mieć wpływu na elementy. Dzieje się tak, ponieważ system układu zwraca przetłumaczony element do jego oryginalnej pozycji jako część jego przetwarzania.  
  
 Aby uzyskać dodatkowe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]informacje na temat układu w obszarze , zobacz [Omówienie układu.](../advanced/layout.md)  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Przykład: Obróć o 45 stopni w ramach frameworkelement  
 W poniższym przykładzie użyto przycisku <xref:System.Windows.Media.RotateTransform> do ruchu wskazówek zegara o 45 stopni. Przycisk jest zawarty w <xref:System.Windows.Controls.StackPanel> a, który ma dwa inne przyciski.  
  
 Domyślnie obraca <xref:System.Windows.Media.RotateTransform> się o punkt (0, 0). Ponieważ w przykładzie nie określono wartości środka, przycisk obraca się wokół punktu (0, 0), który jest jego lewym górnym rogu. Jest <xref:System.Windows.Media.RotateTransform> stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony za pomocą rendertransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Obrót zgodnie z ruchem wskazówek zegara o 45 stopni od lewego górnego rogu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 W następnym przykładzie <xref:System.Windows.Media.RotateTransform> użyto również a do obracania przycisku o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 45 stopni zgodnie z ruchem wskazówek zegara, ale ustawia również przycisk (0,5, 0,5). Wartość <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości jest w stosunku do rozmiaru przycisku. W rezultacie obrót jest stosowany do środka przycisku, a nie do lewego górnego rogu. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony o jego centrum](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Obrót zgodnie z ruchem wskazówek zegara o 45 stopni wokół środka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 W poniższym przykładzie <xref:System.Windows.FrameworkElement.LayoutTransform%2A> użyto <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zamiast właściwości, aby obrócić przycisk.  Powoduje to, że transformacja wpływa na układ przycisku, który wyzwala pełne przejście przez system układu. W rezultacie przycisk jest obracany, a następnie zmieniany, ponieważ jego rozmiar uległ zmianie. Na poniższej ilustracji przedstawiono wynik transformacji.  
  
 ![Przycisk przekształcony za pomocą layouttransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
UkładTransform używany do obracania przycisku  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>Animowanie przekształceń  
 Ponieważ dziedziczą <xref:System.Windows.Media.Animation.Animatable> z klasy, <xref:System.Windows.Media.Transform> klasy mogą być animowane. Aby animować animację, <xref:System.Windows.Media.Transform>zastosuj animację zgodnego typu do właściwości, którą chcesz animować.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> a i a <xref:System.Windows.Media.Animation.DoubleAnimation> z a, <xref:System.Windows.Media.RotateTransform> aby <xref:System.Windows.Controls.Button> spin w miejscu po kliknięciu.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms). Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable Funkcje  
 Ponieważ dziedziczy z <xref:System.Windows.Freezable> klasy, <xref:System.Windows.Media.Transform> klasa zapewnia kilka <xref:System.Windows.Media.Transform> funkcji specjalnych: obiekty mogą być zadeklarowane jako [zasoby,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)współużytkowane przez wiele obiektów, wykonane tylko do odczytu w celu zwiększenia wydajności, sklonowane i wykonane wątku bezpieczne. Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> różnych funkcji udostępnianych przez obiekty, zobacz [Omówienie obiektów freezable](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Tematy in jakże](transformations-how-to-topics.md)
- [Przykład transformacji 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
