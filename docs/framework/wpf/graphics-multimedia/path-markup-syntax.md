---
title: Składni znacznikowania ścieżki
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: d681cd15fa3daa3698edc5e0ad3d3c2669c1dfdf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207528"
---
# <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki
Ścieżki są omówione w [kształty i podstawowe Rysowanie w WPF — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) i [Przegląd Geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), jednak w tym temacie opisano szczegółowo zaawansowanych i złożonych mini języka można użyć do określenia ścieżki Więcej bardziej kompaktowy przy użyciu geometrii [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z podstawowymi funkcjami programu <xref:System.Windows.Media.Geometry> obiektów. Aby uzyskać więcej informacji, zobacz [Przegląd Geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>Streamgeometry — i PathFigureCollection Mini języków  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera dwie klasy, które zapewniają mini języków do opisywania względem ścieżek geometrycznych: <xref:System.Windows.Media.StreamGeometry> i <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Możesz użyć <xref:System.Windows.Media.StreamGeometry> mini języka podczas ustawiania właściwości typu <xref:System.Windows.Media.Geometry>, takich jak <xref:System.Windows.UIElement.Clip%2A> właściwość <xref:System.Windows.UIElement> lub <xref:System.Windows.Shapes.Path.Data%2A> właściwość <xref:System.Windows.Shapes.Path> elementu. W poniższym przykładzie użyto składni atrybutów, aby utworzyć <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Możesz użyć <xref:System.Windows.Media.PathFigureCollection> mini języka podczas ustawiania <xref:System.Windows.Media.PathGeometry.Figures%2A> właściwość <xref:System.Windows.Media.PathGeometry>. W poniższym przykładzie użyto składni atrybutów, aby utworzyć <xref:System.Windows.Media.PathFigureCollection> dla <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak widać w poprzednich przykładach, te dwa języki mini są bardzo podobne. Zawsze jest możliwe użycie <xref:System.Windows.Media.PathGeometry> w każdej sytuacji, w których można użyć <xref:System.Windows.Media.StreamGeometry>; dlatego który z nich należy używać? Użyj <xref:System.Windows.Media.StreamGeometry> nie konieczność zmodyfikowania tej ścieżki po utworzeniu; użyj <xref:System.Windows.Media.PathGeometry> Jeśli trzeba zmodyfikować tę ścieżkę.  
  
 Aby uzyskać więcej informacji na temat różnic między <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> obiekty, zobacz [Przegląd Geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Uwaga dotycząca biały znak  
 Celu skrócenia programu pojedyncza spacja jest wyświetlany w kolejnych sekcjach składni, ale wiele spacji także są dopuszczalne, wszędzie tam, gdzie jest wyświetlana pojedyncza spacja.  
  
 Dwie liczby faktycznie nie muszą być rozdzielone przecinkami lub spacjami, ale to tylko możliwe, gdy wynikowy ciąg jest jednoznaczna. Na przykład `2..3` jest faktycznie dwóch liczb: "2". A ". 3". Podobnie `2-3` "2" i "-3". Miejsca do magazynowania nie jest wymagane przed lub po poleceniach, albo.  
  
### <a name="syntax"></a>Składnia  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Składni dla atrybutu <xref:System.Windows.Media.StreamGeometry> składa się z opcjonalną <xref:System.Windows.Media.FillRule> wartość i co najmniej jednym rysunek opisy.  
  
|Użycie atrybutu XAML StreamGeometry|  
|-----------------------------------------|  
|`<` *obiekt* *właściwość* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] * `" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Składni dla atrybutu <xref:System.Windows.Media.PathFigureCollection> składa się z co najmniej jeden opisy rysunku.  
  
|Użycie atrybutu PathFigureCollection XAML|  
|-----------------------------------------------|  
|`<` *obiekt* *właściwość* `="` `figureDescription`[ `figureDescription`] * `" ... />`|  
  
|Termin|Opis|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Określa, czy <xref:System.Windows.Media.StreamGeometry> używa <xref:System.Windows.Media.FillRule.EvenOdd> lub <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0` Określa <xref:System.Windows.Media.FillRule.EvenOdd> reguły wypełniania.<br />-   `F1` Określa <xref:System.Windows.Media.FillRule.Nonzero> reguły wypełniania.<br /><br /> Jeżeli pominięto tego polecenia, ścieżka podrzędna używa zachowanie domyślne, czyli <xref:System.Windows.Media.FillRule.EvenOdd>. Jeśli określisz tego polecenia, należy go najpierw umieścić.|  
|*figureDescription*|Rysunek, składające się z poleceniem przenoszenia narysuj poleceń i opcjonalnie polecenie Zamknij.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Polecenie przenoszenia, która określa punkt początkowy liczby. Zobacz [polecenie Przenieś](#themovecommand) sekcji.|  
|*drawCommands*|Co najmniej jeden polecenia rysowania, które opisują rysunek zawartość. Zobacz [polecenia rysowania](#drawcommands) sekcji.|  
|*closeCommand*|Zamknij polecenie opcjonalne który zamyka rysunku. Zobacz [polecenia Zamknij](#closecommand) sekcji.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Polecenia MOVE  
 Określa punkt początkowy nowe wartości.  
  
|Składnia|  
|------------|  
|`M` *startPoint*<br /><br /> - lub -<br /><br /> `m` *startPoint*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt początkowy nowe wartości.|  
  
 Wielkie litery `M` wskazuje, że `startPoint` jest wartością bezwzględną; małymi literami `m` wskazuje, że `startPoint` to przesunięcie do wcześniejszego punktu lub (0,0), jeśli żaden nie istnieje. Po wyświetleniu listy wiele punktów po poleceniu przenoszenia, linia jest rysowana do tych punktów, chociaż określony wiersz polecenia.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Polecenia rysowania  
 Polecenie rysowania może obejmować kilka poleceń kształtu. Dostępne są następujące polecenia kształtu: wiersza, linii poziomej, linii pionowej, krzywą Beziera trzeciego stopnia, krzywą Beziera drugiego stopnia, smooth krzywą Beziera trzeciego stopnia, smooth krzywą Beziera drugiego stopnia i łuk eliptyczny.  
  
 Wprowadź każde polecenie przy użyciu wielką lub małą literą: wielkie litery oznaczają wartości bezwzględne i małe litery oznaczają względne wartości: punkty kontrolne dla tego segmentu są względne wobec punktu końcowego w poprzednim przykładzie. Wprowadzając sekwencyjnie więcej niż jednego polecenia tego samego typu, można pominąć zduplikowane polecenie zgłoszenia; na przykład `L 100,200 300,400` jest odpowiednikiem `L 100,200 L 300,400`. W poniższej tabeli opisano **przenieść** i **Rysowanie** poleceń.  
  
### <a name="line-command"></a>Wiersz polecenia  
 Tworzy prostą pomiędzy bieżącym punktem a określonym punktem końcowym. `l 20 30` i `L 20,30` są prawidłowe przykłady **wiersza** poleceń.  
  
|Składnia|  
|------------|  
|`L` *punkt końcowy*<br /><br /> - lub -<br /><br /> `l` *punkt końcowy*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt końcowy linii.|  

Wielkie litery `L` wskazuje, że `endPoint` jest wartością bezwzględną; małymi literami `l` wskazuje, że `endPoint` to przesunięcie do wcześniejszego punktu lub (0,0), jeśli żaden nie istnieje.

### <a name="horizontal-line-command"></a>Polecenie Linia pozioma  
 Tworzy linii poziomej pomiędzy bieżącym punktem a określonym współrzędną x. `H 90` znajduje się przykład polecenia prawidłowy linii poziomej.

  
|Składnia|  
|------------|  
|`H`  *x*<br /><br /> - lub -<br /><br /> `h`  *x*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu końcowego linii.|  
  
Wielkie litery `H` wskazuje, że `x` jest wartością bezwzględną; małymi literami `h` wskazuje, że `x` to przesunięcie do wcześniejszego punktu lub (0,0), jeśli żaden nie istnieje.
  
### <a name="vertical-line-command"></a>Polecenie linii pionowej  
 Tworzy linię pionowy pomiędzy bieżącym punktem a określonym współrzędną y. `v 90` znajduje się przykład polecenia prawidłowy pionowym wierszem.

  
|Składnia|  
|------------|  
|`V`  *y*<br /><br /> - lub -<br /><br /> `v`  *y*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu końcowego linii.|  

Wielkie litery `V` wskazuje, że `y` jest wartością bezwzględną; małymi literami `v` wskazuje, że `y` to przesunięcie do wcześniejszego punktu lub (0,0), jeśli żaden nie istnieje.  
    
### <a name="cubic-bezier-curve-command"></a>Polecenie krzywą Beziera trzeciego stopnia  
 Tworzy krzywą Beziera trzeciego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym przy użyciu dwóch punktów określoną kontrolkę (`controlPoint`1 i `controlPoint`2). `C 100,200 200,400 300,200` znajduje się przykład polecenia prawidłowy krzywej.  
  
|Składnia|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - lub -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Pierwszy punkt kontrolny krzywej, która określa początkowy tangens krzywej.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Drugi punkt kontrolny krzywej, która określa końcowy tangens krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt na jest rysowana krzywej.|  
  
### <a name="quadratic-bezier-curve-command"></a>Polecenie krzywą Beziera drugiego stopnia  
 Tworzy krzywą Beziera drugiego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym przy użyciu punktu określonego formantu (`controlPoint`). `q 100,200 300,200` znajduje się przykład prawidłowe polecenie krzywej Beziera drugiego stopnia.  
  
|Składnia|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - lub -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa początkowy i końcowy styczne krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt na jest rysowana krzywej.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Zestaw Smooth krzywą Beziera trzeciego stopnia polecenia  
 Tworzy krzywą Beziera trzeciego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym. Pierwszy punkt kontrolny zakłada się, że odbicie drugi punkt kontrolny poprzedniego polecenia względem bieżącego punktu. Jeśli nie ma żadnego poprzedniego polecenia lub poprzednie polecenie nie jest poleceniem krzywej Beziera trzeciego stopnia lub smooth polecenia krzywej Beziera trzeciego stopnia, zakłada się, że pierwszy punkt kontrolny jest zbieżna z bieżącym punkcie. Drugi formant punktu, punkt kontrolny dla elementu end krzywej, jest określony przez `controlPoint`2. Na przykład `S 100,200 200,300` jest prawidłowym smooth trzeciego stopnia Beziera krzywej poleceniem.  
  
|Składnia|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - lub -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, określający końcowy tangens krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt na jest rysowana krzywej.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Zestaw Smooth krzywą Beziera drugiego stopnia polecenia  
 Tworzy krzywą Beziera drugiego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym. Punkt kontrolny zakłada się, że odbicie punkt kontrolny poprzedniego polecenia względem bieżącego punktu. Jeśli nie ma żadnego poprzedniego polecenia lub poprzednie polecenie nie jest poleceniem krzywej Beziera drugiego stopnia lub smooth polecenia krzywej Beziera drugiego stopnia, punkt kontrolny jest zbieżna z bieżącym punkcie.  
  
|Składnia|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - lub -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa początkowy i stycznej krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt na jest rysowana krzywej.|  
  
### <a name="elliptical-arc-command"></a>Polecenie łuk eliptyczny  
 Tworzy łuk eliptyczny pomiędzy bieżącym punktem a określonym punktem końcowym.  
  
|Składnia|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - lub -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> X - i -promień y łuku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Obrót elipsy, w stopniach.|  
|`isLargeArcFlag`|Ustawiona na 1, jeśli kąt łuk powinien być 180 stopni lub większym; w przeciwnym wypadku ustaw na wartość 0.|  
|`sweepDirectionFlag`|Ustawiona na 1, jeśli łuku w kierunku Kąt dodatni; w przeciwnym wypadku ustaw na wartość 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego łuku.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Polecenie Zamknij  
 Kończy bieżący rysunek i tworzy linię łączący bieżący punkt początkowy punkt rysunku. To polecenie umożliwia utworzenie wiersza — sprzężenie (róg) ostatni segment i pierwszy segment rysunku.  
  
|Składnia|  
|------------|  
|`Z`<br /><br /> - lub -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Składnia punktu  
 W tym artykule opisano współrzędnych x i y punktu gdzie (0,0) jest w lewym górnym rogu.
  
|Składnia|  
|------------|  
|`x` `,` `y`<br /><br /> - lub -<br /><br /> `x``y`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Specjalnych wartości  
 Zamiast wartość liczbową standardowa umożliwia także następujące specjalnych wartości. Te wartości jest rozróżniana wielkość liter.  
  
 infinity  
 Reprezentuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Nieskończoność.  
 Reprezentuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Reprezentuje <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Można także użyć notacji wykładniczej. Na przykład `+1.e17` jest prawidłową wartością.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
