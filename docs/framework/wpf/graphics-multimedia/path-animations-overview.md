---
title: "Przegląd Animacja ścieżki"
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
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10f2e27a2f68dd784c6fce66ae63873436923d63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="path-animations-overview"></a>Przegląd Animacja ścieżki
<a name="introduction"></a>W tym temacie przedstawiono animacje ścieżki, które umożliwiają korzystanie geometrycznych ścieżki do generowania wartości danych wyjściowych. Ścieżka animacje są przydatne w przypadku przenoszenia i obracanie obiektów wzdłuż ścieżki złożone.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje animacji. Aby obejrzeć wprowadzenie do funkcji animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Ponieważ używasz <xref:System.Windows.Media.PathGeometry> obiekt do definiowania animacji ścieżki, należy także zapoznać się z <xref:System.Windows.Media.PathGeometry> i różne typy <xref:System.Windows.Media.PathSegment> obiektów. Aby uzyskać więcej informacji, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>Co to jest animacji ścieżki?  
 Animacja ścieżki jest typem <xref:System.Windows.Media.Animation.AnimationTimeline> używającą <xref:System.Windows.Media.PathGeometry> jako dane wejściowe. Zamiast do ustawiania From, lub przez właściwość (podobnie jak w przypadku From lub do/przez animacji) lub przy użyciu klucza ramki (należy użyć animacji klucza ramki), definiują ścieżkę geometryczne i użyj jej do ustawienia `PathGeometry` właściwości animacji ścieżki. W trakcie animacji ścieżki odczytuje x, y oraz informacje o kąt ze ścieżki i używa tych informacji do generowania danych wyjściowych.  
  
 Ścieżka animacje są bardzo przydatne w przypadku obiektu wzdłuż ścieżki złożonych animacji. Aby przenieść obiekt na ścieżce jest użycie <xref:System.Windows.Media.MatrixTransform> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Aby przekształcić obiektu na ścieżce złożonych. W poniższym przykładzie pokazano tej metody za pomocą <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu do animowania <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Jest stosowana do przycisku i powoduje, że aby przesunąć wzdłuż ścieżki. Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest ustawiona na `true`, prostokąt obraca wzdłuż tangens ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Aby uzyskać więcej informacji o składni ścieżki, który jest używany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) omówienie. Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Animacja ścieżki można zastosować do właściwości, za pomocą <xref:System.Windows.Media.Animation.Storyboard> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kodu lub przy użyciu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Umożliwia także animacji ścieżki do utworzenia <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do co najmniej jednej właściwości. Aby uzyskać więcej informacji na temat różnych metod do zastosowania animacji, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Typy animacji ścieżki  
 Ponieważ animacje Generowanie wartości właściwości, istnieją typy innej animacji dla różnych typach właściwości. Do animowania właściwości, która przyjmuje <xref:System.Double> (takich jak <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform>), użyj animacji tworzącego <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji tworzącego <xref:System.Windows.Point> wartości i tak dalej.  
  
 Ścieżka animacji klasy należą do <xref:System.Windows.Media.Animation> przestrzeni nazw i korzystać z następującą konwencją nazewnictwa:  
  
 *\<Typ >*`AnimationUsingPath`  
  
 Gdzie  *\<typu >* jest typ wartości, które animuje klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia następujące ścieżki klasy animacji.  
  
|Typ właściwości|Odpowiadającą klasę animacji ścieżki|Przykład|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja double)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja Matrix)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animowanie obiektu na ścieżce (animacja punktu)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> generuje <xref:System.Windows.Media.Matrix> wartości z jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. W przypadku użycia z <xref:System.Windows.Media.MatrixTransform>, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> można przenieść obiekt na ścieżce. Jeśli ustawisz <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do `true`, również obraca obiekt wzdłuż krzywych ścieżki.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> generuje <xref:System.Windows.Point> wartości z x-y współrzędne i jego <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Za pomocą <xref:System.Windows.Media.Animation.PointAnimationUsingPath> do animowania właściwości, która przyjmuje <xref:System.Windows.Point> wartości, można przenieść obiekt na ścieżce. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nie można obrócić obiektów.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> generuje <xref:System.Double> wartości z jego <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Przez ustawienie <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> właściwości, można określić czy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> używa współrzędną x, współrzędną y lub kąta ścieżki jako dane wyjściowe. Można użyć <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> Obracanie obiektu lub przenieś go wzdłuż osi x i y.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Ścieżka animacji w danych wejściowych  
 Każda klasa animacji ścieżka zawiera <xref:System.Windows.Media.PathGeometry> właściwości do określenia jej danych wejściowych. Używa animacji ścieżki <xref:System.Windows.Media.PathGeometry> do generowania wartości jego dane wyjściowe. <xref:System.Windows.Media.PathGeometry> Klasa umożliwia opisują wiele złożonych dane, które składają się z łuki, krzywych i linii.  
  
 Istotą <xref:System.Windows.Media.PathGeometry> jest kolekcją <xref:System.Windows.Media.PathFigure> obiektów; te obiekty są więc o nazwie, ponieważ każdy rysunek opisuje dyskretne kształtu w <xref:System.Windows.Media.PathGeometry>. Każdy <xref:System.Windows.Media.PathFigure> składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiektów, z których każdy zawiera opis segment rysunku.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy łuku między dwoma punktami.|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy sześcienny krzywej Beziera między dwoma punktami.|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię sześcienny krzywych Beziera.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię kwadratową krzywych Beziera.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy kwadratową krzywą Beziera.|  
  
 Segmenty w <xref:System.Windows.Media.PathFigure> są łączone w pojedynczego kształtu geometryczne, która wykorzystuje punkt końcowy segmentu jako punkt początkowy następnego segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Właściwość <xref:System.Windows.Media.PathFigure> określa punkt, z którego ma zostać narysowana pierwszy segment. Każdy z segmentów kolejnych zostanie uruchomiony w punkcie końcowym poprzedniego segmentu. Na przykład linią pionową z `10,50` do `10,150` można zdefiniować ustawiając <xref:System.Windows.Media.PathFigure.StartPoint%2A> właściwości `10,50` i tworzenie <xref:System.Windows.Media.LineSegment> z <xref:System.Windows.Media.LineSegment.Point%2A> ustawienie właściwości `10,150`.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> obiekty, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], umożliwia także specjalnej składni skróconej można ustawić <xref:System.Windows.Media.PathGeometry.Figures%2A> właściwość <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) omówienie.  
  
 Aby uzyskać więcej informacji o składni ścieżki, który jest używany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) omówienie.  
  
## <a name="see-also"></a>Zobacz też  
 [Ścieżka animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Składnia znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
