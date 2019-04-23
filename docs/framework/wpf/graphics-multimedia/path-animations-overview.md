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
ms.openlocfilehash: 195af217ddf3a78a0ef1bb54957a65b6ce62deae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182471"
---
# <a name="path-animations-overview"></a>Przegląd Animacja ścieżki
<a name="introduction"></a> W tym temacie przedstawiono animacje ścieżki, które pozwalają na potrzeby generowania danych wyjściowych wartości ścieżki geometrycznej. Animacje ścieżki są przydatne w przypadku przenoszenia i obracanie obiekty wzdłuż ścieżek złożonych.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje animacji. Aby zapoznać się z wprowadzeniem do funkcji animacji, zobacz [Przegląd animacja](animation-overview.md).  
  
 Ponieważ używasz <xref:System.Windows.Media.PathGeometry> obiekt do definiowania Animacja ścieżki, należy także zapoznać się z <xref:System.Windows.Media.PathGeometry> i różnego rodzaju <xref:System.Windows.Media.PathSegment> obiektów. Aby uzyskać więcej informacji, zobacz [Przegląd Geometria](geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>Co to jest animacja ścieżki?  
 Animacja ścieżki jest typem <xref:System.Windows.Media.Animation.AnimationTimeline> , który używa <xref:System.Windows.Media.PathGeometry> jako dane wejściowe. Zamiast ustawień od pozycji lub przez właściwość (podobnie jak w przypadku od/do/przez animację) lub przy użyciu klatek kluczowych (jak używać protokołu animacji kluczowych klatek), definiowanie ścieżki geometrycznej i użyj go, aby ustawić `PathGeometry` właściwość Animacja ścieżki. W miarę postępów Animacja ścieżki odczytuje x, y i kąta informacji ze ścieżki i wykorzystuje te informacje do generowania danych wyjściowych.  
  
 Animacje ścieżki są bardzo przydatne w przypadku animowanie obiektu na ścieżce złożone. Jednym ze sposobów, aby przenieść obiekt na ścieżce jest użycie <xref:System.Windows.Media.MatrixTransform> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Aby przekształcić obiekt na ścieżce złożone. W poniższym przykładzie pokazano tej techniki, za pomocą <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Jest stosowany do przycisku i powoduje, że przesunąć wzdłuż ścieżki. Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest ustawiona na `true`, prostokąt obraca się wzdłuż tangens ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Aby uzyskać więcej informacji na temat składni ścieżki, który jest używany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) Przegląd. Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Animacja ścieżki można zastosować do właściwości, używając <xref:System.Windows.Media.Animation.Storyboard> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod lub przy użyciu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Animacja ścieżki również służy do tworzenia <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do co najmniej jednej właściwości. Aby uzyskać więcej informacji na temat różnych metod do zastosowania animacji, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Typy Animacja ścieżki  
 Animacje generować wartości właściwości, dlatego są typy inną animację dla różnych typach właściwości. Aby animować właściwości, która przyjmuje <xref:System.Double> (takie jak <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform>), użyj animacji, która tworzy <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji, która tworzy <xref:System.Windows.Point> wartości i tak dalej.  
  
 Klasy animacji ścieżki należą do <xref:System.Windows.Media.Animation> przestrzeni nazw i następująca Konwencja nazewnictwa:  
  
 *\<Typ >* `AnimationUsingPath`  
  
 Gdzie  *\<typ >* ma typ wartości, które animuje klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące ścieżki klasy animacji.  
  
|Typ właściwości|Odpowiednią klasę Animacja ścieżki|Przykład|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja double)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja Matrix)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja punktu)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> generuje <xref:System.Windows.Media.Matrix> wartości z jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. Gdy jest używane z <xref:System.Windows.Media.MatrixTransform>, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> można przenieść obiekt na ścieżce. Jeśli ustawisz <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do `true`, obraca się także obiekt wzdłuż krzywych ścieżki.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> generuje <xref:System.Windows.Point> wartości od - współrzędnych x i y-z jego <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Za pomocą <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animować właściwości, która przyjmuje <xref:System.Windows.Point> wartości, można przenieść obiekt na ścieżce. Element <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nie można obrócić obiektów.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> generuje <xref:System.Double> wartości z jego <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Ustawiając <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> właściwości, można określić czy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> używa współrzędne x, współrzędna y lub kąta ścieżki jako dane wyjściowe. Możesz użyć <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> Obracanie obiektu lub przenieś go wzdłuż osi x lub osi y.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Animacja ścieżki w danych wejściowych  
 Każda klasa Animacja ścieżki zawiera <xref:System.Windows.Media.PathGeometry> właściwości do określania danych wejściowych. Animacja ścieżki używa <xref:System.Windows.Media.PathGeometry> do generowania wartości jego danych wyjściowych. <xref:System.Windows.Media.PathGeometry> Klasa umożliwia opisują wiele rysunki złożone, które składają się z łuki, krzywych i linii.  
  
 Istotą <xref:System.Windows.Media.PathGeometry> to zbiór <xref:System.Windows.Media.PathFigure> obiekty; obiekty te są nazywane tak, ponieważ każdy rysunek opisuje dyskretnych kształtu w <xref:System.Windows.Media.PathGeometry>. Każdy <xref:System.Windows.Media.PathFigure> składa się z co najmniej jeden <xref:System.Windows.Media.PathSegment> obiektów, z których każdy zawiera opis segment rysunku.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy łuk eliptyczny między dwoma punktami.|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy krzywą Beziera trzeciego stopnia między dwoma punktami.|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię krzywe Beziera trzeciego stopnia.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię krzywe Beziera drugiego stopnia.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy krzywą Beziera drugiego stopnia.|  
  
 Segmenty w <xref:System.Windows.Media.PathFigure> są łączone do pojedynczego kształtu geometrycznego, którego używa punkt końcowy segmentu jako punkt początkowy następnego segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Właściwość <xref:System.Windows.Media.PathFigure> określa punkt, z którego jest rysowana pierwszy segment. Każdy z kolejnych segmentów rozpoczyna się w punkcie końcowym poprzedniego segmentu. Na przykład, pionowa linia z `10,50` do `10,150` można zdefiniować, ustawiając <xref:System.Windows.Media.PathFigure.StartPoint%2A> właściwości `10,50` i tworzenie <xref:System.Windows.Media.LineSegment> z <xref:System.Windows.Media.LineSegment.Point%2A> ustawienie właściwości `10,150`.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> obiekty, zobacz [Przegląd Geometria](geometry-overview.md).  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można również użyć specjalnej składni skróconej można ustawić <xref:System.Windows.Media.PathGeometry.Figures%2A> właściwość <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) Przegląd.  
  
 Aby uzyskać więcej informacji na temat składni ścieżki, który jest używany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) Przegląd.  
  
## <a name="see-also"></a>Zobacz także

- [Przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Składnia znacznikowania ścieżki](path-markup-syntax.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
- [Animacja — przegląd](animation-overview.md)
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
