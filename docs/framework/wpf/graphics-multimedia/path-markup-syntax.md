---
title: "Składni znacznikowania ścieżki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd8f9b14f114060ebec8e336c1212d61fa19c83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki
Ścieżki zostały omówione w [kształtów i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) i [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), jednak w tym temacie opisano szczegółowo wydajny i złożone mini języka można określić ścieżkę wykorzystuje więcej compactly mają geometrię [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z podstawowymi funkcjami programu <xref:System.Windows.Media.Geometry> obiektów. Aby uzyskać więcej informacji, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry i PathFigureCollection Mini języków  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje dwie klasy zapewniające mini języków dla opisu geometrycznych ścieżki: <xref:System.Windows.Media.StreamGeometry> i <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Możesz użyć <xref:System.Windows.Media.StreamGeometry> mini języka podczas ustawiania właściwości typu <xref:System.Windows.Media.Geometry>, takich jak <xref:System.Windows.UIElement.Clip%2A> właściwość <xref:System.Windows.UIElement> lub <xref:System.Windows.Shapes.Path.Data%2A> właściwość <xref:System.Windows.Shapes.Path> elementu. W poniższym przykładzie użyto Składnia atrybutu, aby utworzyć <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Możesz użyć <xref:System.Windows.Media.PathFigureCollection> mini języka podczas ustawiania <xref:System.Windows.Media.PathGeometry.Figures%2A> właściwość <xref:System.Windows.Media.PathGeometry>. W poniższym przykładzie użyto Składnia atrybutu, aby utworzyć <xref:System.Windows.Media.PathFigureCollection> dla <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak widać w poprzednich przykładach, dwóch języków mini są bardzo podobne. Zawsze jest możliwe użycie <xref:System.Windows.Media.PathGeometry> w każdej sytuacji, w których można użyć <xref:System.Windows.Media.StreamGeometry>; tak które z nich należy używać? Użyj <xref:System.Windows.Media.StreamGeometry> nie można zmodyfikować po utworzeniu; ścieżka użyj <xref:System.Windows.Media.PathGeometry> Jeśli trzeba zmodyfikować tę ścieżkę.  
  
 Aby uzyskać więcej informacji o różnicach między <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> obiekty, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Uwagi dotyczące biały znak  
 Jednak jednego miejsca jest wyświetlany w kolejnych sekcjach składni, ale wiele spacje są również dopuszczalne wszędzie tam, gdzie jest wyświetlany jednego miejsca.  
  
 Dwóch liczb faktycznie nie muszą być oddzielone przecinkiem lub odstępem, ale to tylko możliwe, gdy wynikowy ciąg jest jednoznaczne. Na przykład `2..3` jest rzeczywiście dwóch liczb: "2". I ". 3". Podobnie `2-3` "2" i "-3". Spacje nie są wymagane przed lub po poleceniach, albo.  
  
### <a name="syntax"></a>Składnia  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Składni użycia dla atrybutu <xref:System.Windows.Media.StreamGeometry> składa się z opcjonalną <xref:System.Windows.Media.FillRule> wartość i przynajmniej jedna rysunek opisy.  
  
|Użycie atrybutu StreamGeometry XAML|  
|-----------------------------------------|  
|`<`*obiektu* *właściwości* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] *`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Składni użycia dla atrybutu <xref:System.Windows.Media.PathFigureCollection> składa się z co najmniej jeden opisy rysunku.  
  
|Użycie atrybutu PathFigureCollection XAML|  
|-----------------------------------------------|  
|`<`*obiektu* *właściwości* `="` `figureDescription`[ `figureDescription`] *`" ... />`|  
  
|Termin|Opis|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Określa, czy <xref:System.Windows.Media.StreamGeometry> używa <xref:System.Windows.Media.FillRule.EvenOdd> lub <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0`Określa <xref:System.Windows.Media.FillRule.EvenOdd> reguły wypełniania.<br />-   `F1`Określa <xref:System.Windows.Media.FillRule.Nonzero> reguły wypełniania.<br /><br /> W przypadku pominięcia tego polecenia, podrzędną stosowanie domyślnego zachowania, czyli <xref:System.Windows.Media.FillRule.EvenOdd>. Jeśli określisz tego polecenia, należy go najpierw umieścić.|  
|*figureDescription*|Ilustracja składa się z polecenia move, Rysuj poleceń i opcjonalnie polecenie Zamknij.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Polecenie move, która określa punkt początkowy liczby. Zobacz [polecenie Przenieś](#themovecommand) sekcji.|  
|*drawCommands*|Co najmniej jednego polecenia rysowania opisujące zawartość rysunku. Zobacz [rysowania polecenia](#drawcommands) sekcji.|  
|*closeCommand*|Opcjonalne Zamknij polecenie zamyka rysunku. Zobacz [polecenie Zamknij](#closecommand) sekcji.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Polecenie MOVE  
 Określa punkt początkowy nowej wartości.  
  
|Składnia|  
|------------|  
|`M`*startPoint*<br /><br /> - lub -<br /><br /> `m`*startPoint*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt początkowy nowej wartości.|  
  
 Wielkie litery `M` oznacza to, że `startPoint` jest wartość bezwzględna; jedną małą literę `m` oznacza to, że `startPoint` jest przesunięcie do poprzedniego punktu lub (0,0), jeśli żaden nie istnieje. Jeśli wiele punktów jest wyświetlany po polecenia move, rysowana linia punktów chociaż określonego wiersza polecenia.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Polecenia rysowania  
 Polecenie rysowania może składać się z kilku poleceń kształtu. Dostępne są następujące polecenia kształtu: wiersza, linia pozioma linii pionowej, sześcienny krzywej Beziera, kwadratową krzywej Beziera, smooth sześcienny krzywej Beziera, smooth kwadratową krzywej Beziera i łuku.  
  
 Wprowadź każde polecenie za pomocą wielką lub małą literą: wielkie litery oznaczenia wartości bezwzględne i małe litery oznaczają względne wartości: punktów kontrolnych dla tego segmentu są względem punktu końcowego w poprzednim przykładzie. Wprowadzając sekwencyjnie więcej niż jednego polecenia tego samego typu, można pominąć zduplikowane polecenie wpisu; na przykład `L 100,200 300,400` jest odpowiednikiem `L 100,200 L 300,400`. W poniższej tabeli opisano **Przenieś** i **rysowania** poleceń.  
  
### <a name="line-command"></a>Wiersz polecenia  
 Tworzy prostą pomiędzy bieżącym punktem a określonym punktu końcowego. `l 20 30`i `L 20,30` przedstawiono przykładowe prawidłowe **wiersza** poleceń.  
  
|Składnia|  
|------------|  
|`L`*punktu końcowego*<br /><br /> - lub -<br /><br /> `l`*punktu końcowego*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*punkt końcowy*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt końcowy linii.|  

Wielkie litery `L` oznacza to, że `endPoint` jest wartość bezwzględna; jedną małą literę `l` oznacza to, że `endPoint` jest przesunięcie do poprzedniego punktu lub (0,0), jeśli żaden nie istnieje.

### <a name="horizontal-line-command"></a>Polecenie Linia pozioma  
 Tworzy linia pozioma pomiędzy bieżącym punktem a określonym współrzędną x. `H 90`jest to przykład polecenia prawidłowy linii poziomej.

  
|Składnia|  
|------------|  
|`H`  *x*<br /><br /> - lub -<br /><br /> `h`  *x*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu końcowego linii.|  
  
Wielkie litery `H` oznacza to, że `x` jest wartość bezwzględna; jedną małą literę `h` oznacza to, że `x` jest przesunięcie do poprzedniego punktu lub (0,0), jeśli żaden nie istnieje.
  
### <a name="vertical-line-command"></a>Pionowym wierszem polecenia  
 Tworzy linią pionową pomiędzy bieżącym punktem a określonym współrzędną y. `v 90`jest to przykład prawidłowy pionowym wierszem polecenia.

  
|Składnia|  
|------------|  
|`V`  *y*<br /><br /> - lub -<br /><br /> `v`  *y*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu końcowego linii.|  

Wielkie litery `V` oznacza to, że `y` jest wartość bezwzględna; jedną małą literę `v` oznacza to, że `y` jest przesunięcie do poprzedniego punktu lub (0,0), jeśli żaden nie istnieje.  
    
### <a name="cubic-bezier-curve-command"></a>Polecenie sześcienny krzywej Beziera  
 Tworzy sześcienny krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego za pomocą dwóch punktów kontrolnych określonych (`controlPoint`1 i `controlPoint`2). `C 100,200 200,400 300,200`jest to przykład polecenia krzywej prawidłowe.  
  
|Składnia|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - lub -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Pierwszy punkt kontrolny krzywej, która określa początkowy tangens krzywej.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Drugi punkt kontrolny krzywej, która określa końcowy tangens krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt jest narysowanie krzywej.|  
  
### <a name="quadratic-bezier-curve-command"></a>Polecenie kwadratową krzywej Beziera  
 Tworzy kwadratową krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego za pomocą punkt kontrolny określony (`controlPoint`). `q 100,200 300,200`jest to przykład prawidłowe polecenie kwadratową krzywej Beziera.  
  
|Składnia|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - lub -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, która określa początkową i końcową stycznych krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt jest narysowanie krzywej.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Smooth sześcienny krzywej Beziera polecenia  
 Tworzy sześcienny krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego. Pierwszy punkt kontrolny zakłada się, że odbicia drugiego punktu kontrolnego poprzedniego polecenia względem bieżącego punktu. Jeśli nie ma żadnego poprzedniego polecenia lub poprzednie polecenie nie sześcienny polecenia krzywej Beziera lub smooth polecenia sześcienny krzywej Beziera, przyjęto założenie, że pierwszy punkt kontrolny jest zbieżna z bieżącego punktu. Drugiego punktu, punkt kontrolny na koniec krzywej, jest określona przez `controlPoint`2. Na przykład `S 100,200 200,300` jest prawidłowe smooth sześcienny Beziera krzywej polecenie.  
  
|Składnia|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - lub -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa końcowy tangens krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt jest narysowanie krzywej.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Smooth kwadratową krzywej Beziera polecenia  
 Tworzy kwadratową krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego. Punkt kontrolny zakłada się, że odbicie punkt kontrolny poprzedniego polecenia względem bieżącego punktu. Jeśli nie ma żadnego poprzedniego polecenia lub poprzednie polecenie nie kwadratową polecenia krzywej Beziera lub smooth polecenia kwadratową krzywej Beziera, punkt kontrolny jest zbieżna z bieżącego punktu.  
  
|Składnia|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - lub -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, która określa początkowy i stycznej krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt jest narysowanie krzywej.|  
  
### <a name="elliptical-arc-command"></a>Polecenie łuku  
 Tworzy łuku pomiędzy bieżącym punktem a określonym punktu końcowego.  
  
|Składnia|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - lub -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> X - i y promień łuku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Obrót elipsy w stopniach.|  
|`isLargeArcFlag`|Ustaw wartość 1, jeśli kąt łuk powinny być 180 stopni lub większym; w przeciwnym razie wartość równa 0.|  
|`sweepDirectionFlag`|Ustaw wartość 1, jeśli łuku w kierunku dodatnie kąta; w przeciwnym razie wartość równa 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt jest narysowanie łuk.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Polecenie Zamknij  
 Kończy bieżący rysunek i tworzy linię, które umożliwia połączenie punktu bieżący punkt początkowy liczby. To polecenie tworzy sprzężeniu wiersza (róg) między ostatni segment i pierwszy segment rysunku.  
  
|Składnia|  
|------------|  
|`Z`<br /><br /> - lub -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Składnia punktu  
 W tym artykule opisano współrzędne x i y punktu gdzie (0,0) jest w lewym górnym rogu.
  
|Składnia|  
|------------|  
|`x` `,` `y`<br /><br /> - lub -<br /><br /> `x``y`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Specjalne wartości  
 Zamiast standardowego wartość liczbową umożliwia także następujące wartości specjalnych. Te wartości jest rozróżniana wielkość liter.  
  
 Infinity  
 Reprezentuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 — Infinity  
 Reprezentuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Reprezentuje <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Można także użyć notacji naukowej. Na przykład `+1.e17` jest prawidłową wartością.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
