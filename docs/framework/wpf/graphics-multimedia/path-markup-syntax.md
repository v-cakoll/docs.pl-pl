---
title: Składni znacznikowania ścieżki
description: Dowiedz się więcej na temat zaawansowanego i złożonego języka mini, którego możesz użyć do określenia ścieżki kompaktowej geometrie w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 6d2778522b622f0b0dcb59673e793a6d772a4b4f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853657"
---
# <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki
Ścieżki są omówione w obszarze [kształty i podstawowe rysunki w WPF Omówienie](shapes-and-basic-drawing-in-wpf-overview.md) i [Omówienie geometrii](geometry-overview.md), jednak w tym temacie szczegółowo opisano zaawansowane i skomplikowane, kompleksowe środowisko, którego można użyć do określenia ścieżki geometrie bardziej kompaktowo przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z podstawowymi funkcjami <xref:System.Windows.Media.Geometry> obiektów. Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry i PathFigureCollection mini-Languages  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Program udostępnia dwie klasy, które zapewniają następujące języki do opisywania ścieżek geometrycznych: <xref:System.Windows.Media.StreamGeometry> i <xref:System.Windows.Media.PathFigureCollection> .  
  
- <xref:System.Windows.Media.StreamGeometry>Język mini jest używany podczas ustawiania właściwości typu <xref:System.Windows.Media.Geometry> , takich jak <xref:System.Windows.UIElement.Clip%2A> Właściwość <xref:System.Windows.UIElement> lub <xref:System.Windows.Shapes.Path.Data%2A> właściwości <xref:System.Windows.Shapes.Path> elementu. W poniższym przykładzie użyto składni atrybutu do utworzenia <xref:System.Windows.Media.StreamGeometry> .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- Używasz <xref:System.Windows.Media.PathFigureCollection> języka mini podczas ustawiania <xref:System.Windows.Media.PathGeometry.Figures%2A> właściwości <xref:System.Windows.Media.PathGeometry> . W poniższym przykładzie użyto składni atrybutu w celu utworzenia elementu <xref:System.Windows.Media.PathFigureCollection> dla <xref:System.Windows.Media.PathGeometry> .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak widać w powyższych przykładach, dwa języki są bardzo podobne. <xref:System.Windows.Media.PathGeometry>W każdej sytuacji, w której można użyć elementu, jest zawsze możliwe użycie <xref:System.Windows.Media.StreamGeometry> . Użyj, <xref:System.Windows.Media.StreamGeometry> gdy nie musisz modyfikować ścieżki po jej utworzeniu; Użyj, <xref:System.Windows.Media.PathGeometry> Jeśli musisz zmodyfikować ścieżkę.  
  
 Aby uzyskać więcej informacji o różnicach między <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> obiektami, zobacz [Omówienie geometrii](geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Notatka o białym miejscu  
 W przypadku zwięzłości, w poniższych sekcjach składni są wyświetlane pojedyncze miejsce, ale wiele spacji jest również akceptowalne wszędzie tam, gdzie jest pokazywana pojedyncza spacja.  
  
 Dwie liczby nie muszą być oddzielone przecinkiem ani białym znakiem, ale można to zrobić tylko wtedy, gdy ciąg otrzymany jest niejednoznaczny. Na przykład `2..3` ma wartość dwie liczby: "2". I ". 3". Podobnie, `2-3` ma wartość "2" i "-3". Spacje nie są wymagane przed poleceniami ani po nim.  
  
### <a name="syntax"></a>Składnia  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Składnia użycia atrybutu dla elementu <xref:System.Windows.Media.StreamGeometry> składa się z wartości opcjonalnej <xref:System.Windows.Media.FillRule> i co najmniej jednego opisu rysunku.  
  
|StreamGeometry użycie atrybutu XAML|  
|-----------------------------------------|  
|`<`*object* *Właściwość* obiektu `="` [ `fillRule` ] `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Składnia użycia atrybutu dla programu <xref:System.Windows.Media.PathFigureCollection> składa się z co najmniej jednego opisu rysunku.  
  
|PathFigureCollection użycie atrybutu XAML|  
|-----------------------------------------------|  
|`<`*object* *Właściwość* obiektu `="` `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
|Termin|Opis|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Określa, czy program <xref:System.Windows.Media.StreamGeometry> używa <xref:System.Windows.Media.FillRule.EvenOdd> lub <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A> .<br /><br /> -   `F0`Określa <xref:System.Windows.Media.FillRule.EvenOdd> regułę wypełniania.<br />-   `F1`Określa <xref:System.Windows.Media.FillRule.Nonzero> regułę wypełniania.<br /><br /> W przypadku pominięcia tego polecenia Ścieżka podrzędna będzie używać zachowania domyślnego, czyli <xref:System.Windows.Media.FillRule.EvenOdd> . W przypadku określenia tego polecenia należy je najpierw umieścić.|  
|*figureDescription*|Rysunek składający się z polecenia Move, rysowania poleceń i opcjonalnego polecenia Close.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Polecenie przenoszenia, które określa punkt początkowy rysunku. Zobacz sekcję [Przenieś polecenie](#themovecommand) .|  
|*drawCommands*|Co najmniej jedno polecenie rysowania opisujące zawartość rysunku. Zobacz sekcję [rysowanie poleceń](#drawcommands) .|  
|*closeCommand*|Opcjonalne polecenie Close zamykające rysunek. Zapoznaj się z sekcją [Zamknij polecenie](#closecommand) .|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>Move — polecenie  
 Określa punkt początkowy nowego rysunku.  
  
|Składnia|  
|------------|  
|`M`*startPoint*<br /><br /> — lub —<br /><br /> `m`*startPoint*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt początkowy nowego rysunku.|  
  
 Wielkie litery `M` wskazuje, że `startPoint` jest wartością bezwzględną; małe litery `m` wskazuje, że `startPoint` jest przesunięciem do poprzedniego punktu lub (0, 0), jeśli nie istnieje. Jeśli lista zawiera wiele punktów po przeniesieniu polecenia, wiersz jest rysowany do tych punktów, mimo że określono polecenie line.  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>Polecenia rysowania  
 Polecenie rysowania może składać się z kilku poleceń kształtu. Dostępne są następujące polecenia kształtu: wiersz, linia pozioma, linia pionowa, Krzywa Beziera sześcienna, Krzywa Beziera kwadratowa, gładkia krzywa Beziera, gładka krzywa Beziera i Łuk eliptyczny.  
  
 Każde polecenie można wprowadzić przy użyciu wielkich liter lub małej litery: wielkie litery oznacza wartości bezwzględne i małe litery — wartości względne: punkty kontrolne dla tego segmentu są względne do punktu końcowego poprzedniego przykładu. Po sekwencyjnym wprowadzeniu więcej niż jednego polecenia tego samego typu można pominąć Zduplikowany wpis polecenia; na przykład `L 100,200 300,400` jest równoważne `L 100,200 L 300,400` . W poniższej tabeli opisano polecenia **Move** i **Draw** .  
  
### <a name="line-command"></a>Line — polecenie  
 Tworzy prostą linię między bieżącym punktem a określonym punktem końcowym. `l 20 30`i `L 20,30` to przykłady prawidłowych poleceń **wiersza** .  
  
|Składnia|  
|------------|  
|`L`*punkt końcowy*<br /><br /> — lub —<br /><br /> `l`*punkt końcowy*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*Punktu końcowego*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt końcowy wiersza.|  

Wielkie litery `L` wskazuje, że `endPoint` jest wartością bezwzględną; małe litery `l` wskazuje, że `endPoint` jest przesunięciem do poprzedniego punktu lub (0, 0), jeśli nie istnieje.

### <a name="horizontal-line-command"></a>Linia pozioma — polecenie  
 Tworzy linię poziomą między bieżącym punktem a określoną współrzędną x. `H 90`to przykład prawidłowej linii poziomej.

|Składnia|  
|------------|  
|`H`  *y*<br /><br /> — lub —<br /><br /> `h`  *y*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu końcowego wiersza.|  
  
Wielkie litery `H` wskazuje, że `x` jest wartością bezwzględną; małe litery `h` wskazuje, że `x` jest przesunięciem do poprzedniego punktu lub (0, 0), jeśli nie istnieje.
  
### <a name="vertical-line-command"></a>Wiersz pionowy — polecenie  
 Tworzy linię pionową między bieżącym punktem a określoną współrzędną y. `v 90`jest przykładem prawidłowej linii pionowej.

|Składnia|  
|------------|  
|`V`  *t*<br /><br /> — lub —<br /><br /> `v`  *t*|  
  
|Termin|Opis|  
|----------|-----------------|  
|*t*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu końcowego wiersza.|  

Wielkie litery `V` wskazuje, że `y` jest wartością bezwzględną; małe litery `v` wskazuje, że `y` jest przesunięciem do poprzedniego punktu lub (0, 0), jeśli nie istnieje.  

### <a name="cubic-bezier-curve-command"></a>Sześcienna krzywa Beziera — polecenie  
 Tworzy zaokrągloną krzywą Beziera między bieżącym punktem a określonym punktem końcowym przy użyciu dwóch określonych punktów kontrolnych ( `controlPoint` 1 i `controlPoint` 2). `C 100,200 200,400 300,200`jest przykładem prawidłowej krzywej.  
  
|Składnia|  
|------------|  
|`C``controlPoint`1 `controlPoint` 2`endPoint`<br /><br /> — lub —<br /><br /> `c``controlPoint`1 `controlPoint` 2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`jedno|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Pierwszy punkt kontrolny krzywej, który określa początkową styczną krzywej.|  
|`controlPoint`dwóch|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Drugi punkt kontrolny krzywej, który określa końcowy tangens krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego jest rysowana krzywa.|  
  
### <a name="quadratic-bezier-curve-command"></a>Kwadratowa krzywa Beziera  
 Tworzy krzywą Beziera kwadratu między bieżącym punktem a określonym punktem końcowym przy użyciu określonego punktu kontrolnego ( `controlPoint` ). `q 100,200 300,200`to przykład prawidłowej krzywej Beziera.  
  
|Składnia|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> — lub —<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa początkową i końcową styczną krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego jest rysowana krzywa.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Gładkie próbkowanie krzywej Beziera  
 Tworzy wartość krzywej Beziera sześciennego między bieżącym punktem a określonym punktem końcowym. Pierwszy punkt kontrolny przyjmuje się jako odbicie drugiego punktu kontrolnego poprzedniego polecenia względem bieżącego punktu. Jeśli nie istnieje poprzednie polecenie lub jeśli poprzednie polecenie nie było w sześcienny krzywej Beziera lub gładkiej krzywej Beziera, założono, że pierwszy punkt kontrolny pokrywa się z bieżącym punktem. Drugi punkt kontrolny, punkt kontroli dla końca krzywej, jest określony przez `controlPoint` 2. Na przykład `S 100,200 200,300` jest prawidłowym, gładkim krzywą Beziera.  
  
|Składnia|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> — lub —<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`dwóch|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa końcowy tangens krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego jest rysowana krzywa.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Gładkie krzywe Beziera  
 Tworzy krzywą Beziera kwadratu między bieżącym punktem a określonym punktem końcowym. Przyjęto, że punkt kontrolny jest odbiciem punktu sterującego poprzedniego polecenia względem bieżącego punktu. Jeśli nie istnieje poprzednie polecenie lub jeśli poprzednie polecenie nie było poleceniem krzywej Beziera kwadratu lub gładkiej krzywej Beziera, punkt kontrolny pokrywa się z bieżącym punktem.  
  
|Składnia|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> — lub —<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt kontrolny krzywej, który określa początek i styczność krzywej.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego jest rysowana krzywa.|  
  
### <a name="elliptical-arc-command"></a>Łuk eliptyczny — polecenie  
 Tworzy Łuk eliptyczny między bieżącym punktem a określonym punktem końcowym.  
  
|Składnia|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> — lub —<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Wartości x i y promienia łuku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Obrót elipsy (w stopniach).|  
|`isLargeArcFlag`|Ustaw wartość 1, jeśli kąt łuku ma wynosić 180 stopni lub więcej; w przeciwnym razie ustaw wartość 0.|  
|`sweepDirectionFlag`|Ustaw wartość 1, jeśli łuk jest rysowany w kierunku dodatnim; w przeciwnym razie ustaw wartość 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Punkt, do którego jest rysowany łuk.|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>Close — polecenie  
 Zatrzymuje bieżącą figurę i tworzy linię, która łączy bieżący punkt z punktem początkowym na rysunku. To polecenie tworzy sprzężenie liniowe (narożne) między ostatnim segmentem a pierwszym segmentem rysunku.  
  
|Składnia|  
|------------|  
|`Z`<br /><br /> — lub —<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>Składnia punktu  
 Opisuje współrzędne x i y punktu, gdzie (0, 0) jest lewym górnym rogu.
  
|Składnia|  
|------------|  
|`x` `,` `y`<br /><br /> — lub —<br /><br /> `x` `y`|  
  
|Termin|Opis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna x punktu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Współrzędna y punktu.|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>Wartości specjalne  
 Zamiast standardowej wartości liczbowej, można również użyć następujących specjalnych wartości. W tych wartościach jest rozróżniana wielkość liter.  
  
 Nieskończoność  
 Reprezentuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .  
  
 -Nieskończoność  
 Reprezentuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> .  
  
 NaN  
 Reprezentuje <xref:System.Double.NaN?displayProperty=nameWithType> .  
  
 Możesz również użyć notacji wykładniczej. Na przykład `+1.e17` jest prawidłową wartością.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Geometria](geometry-overview.md)
- [— Tematy porad](geometries-how-to-topics.md)
