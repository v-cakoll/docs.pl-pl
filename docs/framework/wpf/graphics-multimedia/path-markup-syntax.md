---
title: Składni znacznikowania ścieżki
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: adcedcea6c8d6d988021cbbccf87bd25a042fd16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181859"
---
# <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki
Ścieżki są omawiane w [shapes and Basic Drawing w przeglądzie WPF](shapes-and-basic-drawing-in-wpf-overview.md) i [Przegląd geometrii,](geometry-overview.md)jednak w tym temacie opisano szczegółowo potężny [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]i złożony mini-język, którego można użyć do bardziej kompaktowego określania geometrii ścieżek za pomocą .  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać <xref:System.Windows.Media.Geometry> się z podstawowymi cechami obiektów. Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>Minija languagezy streamgeometry i pathfigurecollection  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera dwie klasy, które zapewniają mini-języki do <xref:System.Windows.Media.StreamGeometry> opisywania ścieżek geometrycznych: i <xref:System.Windows.Media.PathFigureCollection>.  
  
- Mini-język <xref:System.Windows.Media.StreamGeometry> jest używany podczas ustawiania <xref:System.Windows.Media.Geometry>właściwości typu <xref:System.Windows.UIElement.Clip%2A> , <xref:System.Windows.UIElement> takich <xref:System.Windows.Shapes.Path.Data%2A> jak właściwość lub właściwość <xref:System.Windows.Shapes.Path> elementu. W poniższym przykładzie użyto składni <xref:System.Windows.Media.StreamGeometry>atrybutu do utworzenia pliku .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- Minijękniasu <xref:System.Windows.Media.PathFigureCollection> należy <xref:System.Windows.Media.PathGeometry.Figures%2A> używać <xref:System.Windows.Media.PathGeometry>podczas ustawiania właściwości pliku . W poniższym przykładzie użyto składni <xref:System.Windows.Media.PathFigureCollection> atrybutu <xref:System.Windows.Media.PathGeometry>do utworzenia fora .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak widać z poprzednich przykładów, dwa mini-języki są bardzo podobne. Zawsze można użyć <xref:System.Windows.Media.PathGeometry> w każdej sytuacji, w której <xref:System.Windows.Media.StreamGeometry>można użyć ; więc który z nich należy użyć? Użyj, <xref:System.Windows.Media.StreamGeometry> gdy nie trzeba modyfikować ścieżkę po jej utworzeniu; użyj, <xref:System.Windows.Media.PathGeometry> jeśli trzeba zmodyfikować ścieżkę.  
  
 Aby uzyskać więcej informacji <xref:System.Windows.Media.PathGeometry> na <xref:System.Windows.Media.StreamGeometry> temat różnic między obiektami i obiektami, zobacz [Omówienie geometrii](geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Uwaga dotycząca białej przestrzeni  
 W przypadku zwięzłości pojedyncza przestrzeń jest wyświetlana w kolejnych sekcjach składni, ale wiele spacji jest również dopuszczalnych wszędzie tam, gdzie wyświetlana jest pojedyncza przestrzeń.  
  
 Dwie liczby w rzeczywistości nie muszą być oddzielone przecinkiem lub białymi znakami, ale można to zrobić tylko wtedy, gdy wynikowy ciąg jest jednoznaczny. Na przykład, `2..3` jest w rzeczywistości dwie liczby: "2". I ".3". Podobnie `2-3` jest "2" i "-3". Spacje nie są wymagane przed lub po poleceniach, albo.  
  
### <a name="syntax"></a>Składnia  
 Składnia [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] użycia atrybutu dla <xref:System.Windows.Media.StreamGeometry> a składa <xref:System.Windows.Media.FillRule> się z wartości opcjonalnej i co najmniej jednego opisu rysunku.  
  
|Użycie atrybutu XAML StreamGeometry|  
|-----------------------------------------|  
|`<`*object* *właściwość* `="` `fillRule`obiektu `figureDescription` `figureDescription`[ ] [ ]*`" ... />`|  
  
 Składnia [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] użycia atrybutu dla <xref:System.Windows.Media.PathFigureCollection> a składa się z jednego lub więcej opisów rysunku.  
  
|Użycie atrybutu PathFigureCollection XAML|  
|-----------------------------------------------|  
|`<`*właściwość* `="` *object* `figureDescription` `figureDescription`obiektu [ ]*`" ... />`|  
  
|Termin|Opis|  
|----------|-----------------|  
|*fillRule (reguła)*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Określa, <xref:System.Windows.Media.StreamGeometry> czy używa <xref:System.Windows.Media.FillRule.EvenOdd> lub <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0`określa regułę <xref:System.Windows.Media.FillRule.EvenOdd> wypełnienia.<br />-   `F1`określa regułę <xref:System.Windows.Media.FillRule.Nonzero> wypełnienia.<br /><br /> Jeśli to polecenie zostanie pominięte, ścieżka podrzędna użyje domyślnego zachowania, którym jest <xref:System.Windows.Media.FillRule.EvenOdd>. Jeśli to polecenie zostanie określone, należy je najpierw umieścić.|  
|*rysunekOskrypt*|Postać składająca się z polecenia move, polecenia rysowania i opcjonalnego polecenia zamknięcia.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand ( moveCommand )*|Polecenie move określające punkt początkowy rysunku. Zobacz sekcję [Przenieś polecenie.](#themovecommand)|  
|*drawCommands (remisCommands)*|Co najmniej jedno polecenie rysowania opisujące zawartość rysunku. Zobacz sekcję [Rysowanie poleceń.](#drawcommands)|  
|*zamknijCommand*|Opcjonalne polecenie zamknij, które zamyka rysunek. Zobacz sekcję [Zamknij polecenie.](#closecommand)|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>Polecenie Przenieś  
 Określa punkt początkowy nowej figury.  
  
|Składnia|  
|------------|  
|`M`*startPoint*<br /><br /> — lub —<br /><br /> `m`*startPoint*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*Startpoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt początkowy nowej figury.|  
  
 Wielkie litery `M` wskazują, `startPoint` że jest to wartość bezwzględna; małe litery `m` wskazują, `startPoint` że jest to przesunięcie do poprzedniego punktu lub (0,0), jeśli nie istnieje. Jeśli po poleceniu move zostanie wyświetlone wiele punktów, linia zostanie narysowana do tych punktów, po poleceniu wiersza.  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>Polecenia rysowania  
 Polecenie rysowanie może składać się z kilku poleceń kształtu. Dostępne są następujące polecenia kształtu: linia, linia pozioma, linia pionowa, sześcienna krzywa Beziera, kwadratowa krzywa Beziera, gładka sześcienna krzywa Beziera, gładka kwadratowa krzywa Beziera i łuk eliptyczny.  
  
 Każde polecenie należy wprowadzić za pomocą wielkich lub małych liter: wielkie litery oznaczają wartości bezwzględne, a małe litery oznaczają wartości względne: punkty kontrolne dla tego segmentu są względem punktu końcowego poprzedniego przykładu. Podczas sekwencyjnego wprowadzania więcej niż jednego polecenia tego samego typu można pominąć zduplikowany wpis polecenia; na przykład `L 100,200 300,400` jest `L 100,200 L 300,400`odpowiednikiem . W poniższej tabeli opisano polecenia **przenoszenia** i **rysowania.**  
  
### <a name="line-command"></a>Polecenie wiersz  
 Tworzy linię prostą między bieżącym punktem a określonym punktem końcowym. `l 20 30`i `L 20,30` są przykładami prawidłowych poleceń **wiersza.**  
  
|Składnia|  
|------------|  
|`L`*punkt końcowy*<br /><br /> — lub —<br /><br /> `l`*punkt końcowy*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*Punktu końcowego*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt końcowy wiersza.|  

Wielkie litery `L` wskazują, `endPoint` że jest to wartość bezwzględna; małe litery `l` wskazują, `endPoint` że jest to przesunięcie do poprzedniego punktu lub (0,0), jeśli nie istnieje.

### <a name="horizontal-line-command"></a>Polecenie Linia pozioma  
 Tworzy linię poziomą między bieżącym punktem a określoną współrzędną x. `H 90`jest przykładem prawidłowego polecenia linii poziomej.

|Składnia|  
|------------|  
|`H`  *X*<br /><br /> — lub —<br /><br /> `h`  *X*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*X*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu końcowego linii.|  
  
Wielkie litery `H` wskazują, `x` że jest to wartość bezwzględna; małe litery `h` wskazują, `x` że jest to przesunięcie do poprzedniego punktu lub (0,0), jeśli nie istnieje.
  
### <a name="vertical-line-command"></a>Polecenie Pionowa linia  
 Tworzy pionową linię między bieżącym punktem a określoną współrzędną y. `v 90`jest przykładem prawidłowego polecenia linii pionowej.

|Składnia|  
|------------|  
|`V`  *Y*<br /><br /> — lub —<br /><br /> `v`  *Y*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu końcowego linii.|  

Wielkie litery `V` wskazują, `y` że jest to wartość bezwzględna; małe litery `v` wskazują, `y` że jest to przesunięcie do poprzedniego punktu lub (0,0), jeśli nie istnieje.  

### <a name="cubic-bezier-curve-command"></a>Polecenie Krzywa beziera sześcienna  
 Tworzy sześcienną krzywą Beziera między bieżącym punktem a`controlPoint`określonym `controlPoint`punktem końcowym przy użyciu dwóch określonych punktów kontrolnych ( 1 i 2). `C 100,200 200,400 300,200`jest przykładem prawidłowego polecenia krzywej.  
  
|Składnia|  
|------------|  
|`C``controlPoint`1`controlPoint`2`endPoint`<br /><br /> — lub —<br /><br /> `c``controlPoint`1`controlPoint`2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Pierwszy punkt kontrolny krzywej, który określa początkową styczną krzywej.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Drugi punkt kontrolny krzywej, który określa końcową styczną krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego rysowana jest krzywa.|  
  
### <a name="quadratic-bezier-curve-command"></a>Kwadratowe polecenie krzywej beziera  
 Tworzy kwadratową krzywą Beziera między bieżącym punktem a określonym punktem końcowym przy użyciu określonego punktu kontrolnego (`controlPoint`). `q 100,200 300,200`jest przykładem prawidłowego polecenia krzywej kwadratowej Beziera.  
  
|Składnia|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> — lub —<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa styczne początkowe i końcowe krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego rysowana jest krzywa.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Gładka sześcienna krzywa Beziera Polecenie  
 Tworzy sześcienną krzywą Beziera między bieżącym punktem a określonym punktem końcowym. Przyjmuje się, że pierwszy punkt kontrolny jest odbiciem drugiego punktu kontrolnego poprzedniego polecenia względem bieżącego punktu. Jeśli nie ma poprzedniego polecenia lub poprzednie polecenie nie było poleceniem krzywej beziera sześciennego ani poleceniem gładkiej krzywej beziera, przy założeniu, że pierwszy punkt kontrolny jest zbieżny z bieżącym punktem. Drugi punkt kontrolny, punkt kontrolny dla końca krzywej, `controlPoint`jest określony przez 2. Na przykład `S 100,200 200,300` jest prawidłowym poleceniem gładkiej krzywej beziera.  
  
|Składnia|  
|------------|  
|`S``controlPoint`2.`endPoint`<br /><br /> — lub —<br /><br /> `s``controlPoint`2.`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa końcową styczną krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego rysowana jest krzywa.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Gładka kwadratowa krzywa Beziera Polecenie  
 Tworzy krzywą kwadratową Beziera między bieżącym punktem a określonym punktem końcowym. Przyjmuje się, że punkt kontrolny jest odbiciem punktu kontrolnego poprzedniego polecenia względem bieżącego punktu. Jeśli nie ma poprzedniego polecenia lub poprzednie polecenie nie było kwadratowym poleceniem krzywej Beziera lub gładkim kwadratowym poleceniem krzywej Beziera, punkt kontrolny jest zbieżny z bieżącym punktem.  
  
|Składnia|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> — lub —<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa początek i styczne krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego rysowana jest krzywa.|  
  
### <a name="elliptical-arc-command"></a>Polecenie łuku eliptycznego  
 Tworzy łuk eliptyczny między bieżącym punktem a określonym punktem końcowym.  
  
|Składnia|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> — lub —<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Promienia x i y łuku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Obrót elipsy w stopniach.|  
|`isLargeArcFlag`|Ustawić na 1, jeśli kąt łuku powinien wynosić 180 stopni lub więcej; w przeciwnym razie ustawiono na 0.|  
|`sweepDirectionFlag`|Ustawić na 1, jeśli łuk jest rysowany w kierunku dodatnim; w przeciwnym razie ustawiono na 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego jest rysowany łuk.|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>Polecenie Zamknij  
 Kończy bieżącą figurę i tworzy linię łączącą bieżący punkt z punktem początkowym rysunku. To polecenie tworzy sprzężenie wiersza (narożnik) między ostatnim segmentem a pierwszym segmentem rysunku.  
  
|Składnia|  
|------------|  
|`Z`<br /><br /> — lub —<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>Składnia punktów  
 Opisuje współrzędne x- i y punktu, w którym (0,0) jest lewym górnym rogu.
  
|Składnia|  
|------------|  
|`x` `,` `y`<br /><br /> — lub —<br /><br /> `x` `y`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu.|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>Wartości specjalne  
 Zamiast standardowej wartości liczbowej można również użyć następujących wartości specjalnych. W tych wartościach rozróżniana jest wielkość liter.  
  
 Nieskończoność  
 Reprezentuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Nieskończoność  
 Reprezentuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Reprezentuje <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Można również użyć notacji naukowej. Na przykład `+1.e17` jest prawidłową wartością.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Geometria](geometry-overview.md)
- [Tematy in jakże](geometries-how-to-topics.md)
