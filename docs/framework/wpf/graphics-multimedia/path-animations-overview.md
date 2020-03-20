---
title: Przegląd Animacja ścieżki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181866"
---
# <a name="path-animations-overview"></a>Przegląd Animacja ścieżki
<a name="introduction"></a>W tym temacie przedstawiono animacje ścieżek, które umożliwiają użycie ścieżki geometrycznej do generowania wartości wyjściowych. Animacje ścieżek są przydatne do przenoszenia i obracania obiektów wzdłuż złożonych ścieżek.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapoznać się z funkcjami animacji. Aby zapoznać się z wprowadzeniem do funkcji animacji, zobacz [Omówienie animacji](animation-overview.md).  
  
 Ponieważ <xref:System.Windows.Media.PathGeometry> obiekt służy do definiowania animacji ścieżki, <xref:System.Windows.Media.PathGeometry> należy również znać <xref:System.Windows.Media.PathSegment> i różne typy obiektów. Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>Co to jest animacja ścieżki?  
 Animacja ścieżki jest <xref:System.Windows.Media.Animation.AnimationTimeline> typem, <xref:System.Windows.Media.PathGeometry> który używa jako jego danych wejściowych. Zamiast ustawiać właściwość Od, Do lub Według (tak jak w przypadku animacji Od/Do/Przez) lub używając klatek kluczowych (używanych do animacji `PathGeometry` klatki kluczowej), definiujesz ścieżkę geometryczną i używasz jej do ustawienia właściwości animacji ścieżki. W miarę postępu animacji ścieżki odczytuje informacje o x, y i kątem ze ścieżki i używa tych informacji do wygenerowania danych wyjściowych.  
  
 Animacje ścieżek są bardzo przydatne do animowania obiektu wzdłuż złożonej ścieżki. Jednym ze sposobów przesuwania obiektu wzdłuż <xref:System.Windows.Media.MatrixTransform> ścieżki <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> jest użycie a i a do przekształcenia obiektu wzdłuż złożonej ścieżki. W poniższym przykładzie przedstawiono <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> tę technikę <xref:System.Windows.Media.MatrixTransform.Matrix%2A> przy <xref:System.Windows.Media.MatrixTransform>użyciu obiektu do animowania właściwości . . Jest <xref:System.Windows.Media.MatrixTransform> stosowany do przycisku i powoduje, że porusza się po zakrzywionej ścieżce. Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest `true`ustawiona na , prostokąt obraca się wzdłuż stycznej ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Aby uzyskać więcej informacji na temat składni [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ścieżki, która jest używana w przykładzie, zobacz [omówienie składni znaczników ścieżki.](path-markup-syntax.md) Aby uzyskać pełną próbkę, zobacz [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Animację ścieżki można zastosować do właściwości <xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu in i <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodu lub przy użyciu metody w kodzie. Można również użyć animacji ścieżki, aby utworzyć <xref:System.Windows.Media.Animation.AnimationClock> i zastosować ją do jednej lub więcej właściwości. Aby uzyskać więcej informacji na temat różnych metod stosowania animacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>Typy animacji ścieżki  
 Ponieważ animacje generują wartości właściwości, istnieją różne typy animacji dla różnych typów właściwości. Aby animować właściwość, <xref:System.Double> która <xref:System.Windows.Media.TranslateTransform.X%2A> ma (na przykład właściwość <xref:System.Windows.Media.TranslateTransform>a <xref:System.Double> ), należy użyć animacji, która tworzy wartości. Aby animować właściwość, która przyjmuje <xref:System.Windows.Point>program <xref:System.Windows.Point> , należy użyć animacji, która tworzy wartości i tak dalej.  
  
 Klasy animacji ścieżki <xref:System.Windows.Media.Animation> należą do obszaru nazw i używają następującej konwencji nazewnictwa:  
  
 * \<>typu*`AnimationUsingPath`  
  
 Gdzie * \<Type>* jest typem wartości, który animuje klasę.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera następujące klasy animacji ścieżki.  
  
|Typ właściwości|Odpowiednia klasa animacji ścieżki|Przykład|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja double)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja Matrix)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja punktu)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> generuje <xref:System.Windows.Media.Matrix> wartości <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>z jego . W przypadku <xref:System.Windows.Media.MatrixTransform>użycia <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> z programem , a można przenieść obiekt wzdłuż ścieżki. Jeśli ustawisz <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do `true`, obraca również obiekt wzdłuż krzywych ścieżki.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> generuje <xref:System.Windows.Point> wartości z współrzędnych x- <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>i y jego . Za pomocą <xref:System.Windows.Media.Animation.PointAnimationUsingPath> a do animowania <xref:System.Windows.Point> właściwości, która przyjmuje wartości, można przenieść obiekt wzdłuż ścieżki. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nie może obracać obiektów.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> generuje <xref:System.Double> wartości <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>z jego . Ustawiając <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> właściwość, można określić, czy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> używa współrzędnej x, współrzędnej y lub kąta ścieżki jako jej danych wyjściowych. Za pomocą <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> a można obrócić obiekt lub przesunąć go wzdłuż osi x lub osi y.  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>Wprowadzanie animacji ścieżki  
 Każda klasa animacji <xref:System.Windows.Media.PathGeometry> ścieżki zawiera właściwość do określania jego danych wejściowych. Animacja ścieżki używa <xref:System.Windows.Media.PathGeometry> do generowania wartości wyjściowych. Klasa <xref:System.Windows.Media.PathGeometry> umożliwia opisanie wielu złożonych liczb, które składają się z łuków, krzywych i linii.  
  
 W sercu <xref:System.Windows.Media.PathGeometry> jest zbiór <xref:System.Windows.Media.PathFigure> przedmiotów; obiekty te są tak nazwane, ponieważ każda <xref:System.Windows.Media.PathGeometry>figura opisuje dyskretny kształt w pliku . Każdy <xref:System.Windows.Media.PathFigure> składa się <xref:System.Windows.Media.PathSegment> z jednego lub więcej obiektów, z których każdy opisuje segment rysunku.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy łuk eliptyczny między dwoma punktami.|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy krzywą beziera sześciennego między dwoma punktami.|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię sześciennych krzywych Beziera.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię kwadratowych krzywych Beziera.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy kwadratową krzywą Beziera.|  
  
 Segmenty w <xref:System.Windows.Media.PathFigure> a są łączone w jeden kształt geometryczny, który wykorzystuje punkt końcowy segmentu jako punkt początkowy następnego segmentu. Właściwość <xref:System.Windows.Media.PathFigure.StartPoint%2A> a <xref:System.Windows.Media.PathFigure> określa punkt, z którego jest rysowany pierwszy segment. Każdy kolejny segment rozpoczyna się w punkcie końcowym poprzedniego segmentu. Na przykład pionową `10,50` linię `10,150` od do można <xref:System.Windows.Media.PathFigure.StartPoint%2A> zdefiniować, `10,50` ustawiając <xref:System.Windows.Media.LineSegment.Point%2A> właściwość i tworząc z ustawieniem `10,150` <xref:System.Windows.Media.LineSegment> właściwości .  
  
 Aby uzyskać <xref:System.Windows.Media.PathGeometry> więcej informacji o obiektach, zobacz [Omówienie geometrii](geometry-overview.md).  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programze można również użyć specjalnej skróconej składni, aby ustawić <xref:System.Windows.Media.PathGeometry.Figures%2A> właściwość programu <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [omówienie składni znaczników ścieżki.](path-markup-syntax.md)  
  
 Aby uzyskać więcej informacji na temat składni [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ścieżki, która jest używana w przykładzie, zobacz [omówienie składni znaczników ścieżki.](path-markup-syntax.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Składni znacznikowania ścieżki](path-markup-syntax.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
- [Przegląd Animacja](animation-overview.md)
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
