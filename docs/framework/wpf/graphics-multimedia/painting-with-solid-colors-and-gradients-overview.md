---
title: Przegląd Malowanie jednolitymi kolorami i gradientami
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: fb6b7da4be46f361b263c573339b1a6b73ef24bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855888"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Przegląd Malowanie jednolitymi kolorami i gradientami

W tym temacie opisano, jak <xref:System.Windows.Media.SolidColorBrush>używać <xref:System.Windows.Media.LinearGradientBrush>obiektów, <xref:System.Windows.Media.RadialGradientBrush> i do malowania przy użyciu pełnych kolorów, gradientów liniowych i gradientów promieniowych.

<a name="solidcolor"></a>

## <a name="painting-an-area-with-a-solid-color"></a>Malowanie obszaru za pomocą pełnego koloru

Jedną z najczęstszych operacji na dowolnej platformie jest malowanie obszaru za pomocą pełnego <xref:System.Windows.Media.Color>. Aby wykonać to zadanie, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.SolidColorBrush> udostępnia klasę. W poniższych sekcjach opisano różne sposoby malowania przy użyciu <xref:System.Windows.Media.SolidColorBrush>programu.

<a name="solidcolorinxaml"></a>

### <a name="using-a-solidcolorbrush-in-xaml"></a>Używanie elementu SolidColorBrush w języku "XAML"

Aby malować obszar z pełnymi kolorami w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie, użyj jednej z następujących opcji.

- Wybierz wstępnie zdefiniowany pędzel pełnego koloru według nazwy.  Na przykład można ustawić przycisk <xref:System.Windows.Controls.Control.Background%2A> na "czerwony" lub "MediumBlue".  Aby zapoznać się z listą innych wstępnie zdefiniowanych pędzli pełnych kolorów, zobacz <xref:System.Windows.Media.Brushes> właściwości statyczne klasy. Oto przykład.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]

- Wybierz kolor z palety kolorów 32-bitowej, określając ilość czerwony, zielony i niebieski, aby połączyć się w jeden pełny kolor.  Format służący do określania koloru z palety 32-bitowej jest " *#rrggbb*", gdzie *RR* jest cyfrą szesnastkową, określającą względną ilość czerwieni, *gg* określa ilość zieloną, a *BB* określa ilość niebieską.  Dodatkowo kolor można określić jako "#*aarrggbb*", gdzie *AA* określa wartość *alfa* (lub przezroczystość koloru). Takie podejście umożliwia tworzenie kolorów, które są częściowo przezroczyste.  W poniższym przykładzie, <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.Controls.Button> jest ustawione na całkowicie nieprzezroczyste czerwono przy użyciu notacji szesnastkowej.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]

- Użyj składni tagów właściwości, aby opisać <xref:System.Windows.Media.SolidColorBrush>a. Ta składnia jest bardziej pełna, ale umożliwia określenie dodatkowych ustawień, takich jak nieprzezroczystość pędzla. W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> właściwości dwóch <xref:System.Windows.Controls.Button> elementów są ustawione na wartość w pełni nieprzezroczystą czerwoną. Kolor pierwszego pędzla został opisany przy użyciu wstępnie zdefiniowanej nazwy koloru. Kolor drugiego pędzla został opisany przy użyciu notacji szesnastkowej.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]

<a name="solidcolorsincode"></a>

### <a name="painting-with-a-solidcolorbrush-in-code"></a>Malowanie przy użyciu SolidColorBrush w kodzie

Aby malować obszar z pełnymi kolorami w kodzie, użyj jednej z następujących opcji.

- Użyj jednego ze wstępnie zdefiniowanych pędzli dostarczonych przez <xref:System.Windows.Media.Brushes> klasę. W poniższym przykładzie, <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.Controls.Button> jest ustawione na <xref:System.Windows.Media.Brushes.Red%2A>.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]

- Utwórz i ustaw jej <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość przy użyciu <xref:System.Windows.Media.Color> struktury. <xref:System.Windows.Media.SolidColorBrush> Możesz użyć wstępnie zdefiniowanego koloru z <xref:System.Windows.Media.Colors> klasy lub można <xref:System.Windows.Media.Color> utworzyć za pomocą metody statycznej <xref:System.Windows.Media.Color.FromArgb%2A> .

  Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Media.SolidColorBrush.Color%2A> Właściwość <xref:System.Windows.Media.SolidColorBrush> przy użyciu wstępnie zdefiniowanego koloru.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]

Statyczny <xref:System.Windows.Media.Color.FromArgb%2A> umożliwia określenie wartości alfa, czerwonego, zielonego i niebieskiego koloru. Typowy zakres dla każdej z tych wartości to 0-255. Na przykład wartość alfa 0 wskazuje, że kolor jest całkowicie przezroczysty, a wartość 255 wskazuje, że kolor jest całkowicie nieprzezroczysty. Analogicznie, czerwona wartość 0 oznacza, że kolor nie ma koloru czerwonego, a wartość 255 wskazuje, że kolor ma maksymalną możliwą wartość czerwoną.  W poniższym przykładzie kolor pędzla został opisany przez określenie wartości alfa, czerwony, zielony i niebieski.

[!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]

Dodatkowe sposoby określania koloru można znaleźć <xref:System.Windows.Media.Color> w temacie Reference.

<a name="gradient"></a>

## <a name="painting-an-area-with-a-gradient"></a>Malowanie obszaru za pomocą gradientu

Pędzel gradientu maluje obszar z wieloma kolorami, które mieszają się w siebie wzdłuż osi. Można ich używać do tworzenia wyglądu jasnego i cieniowania, co daje kontrolki trójwymiarowe. Można ich również użyć do symulowania szkła, Chrome, wody i innych gładkich powierzchni.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje dwa typy pędzli gradientu <xref:System.Windows.Media.LinearGradientBrush> : <xref:System.Windows.Media.RadialGradientBrush>i.

<a name="lineargradientbrush"></a>

## <a name="linear-gradients"></a>Gradienty liniowe

Maluje obszar z gradientem zdefiniowanym wzdłuż linii, *osi gradientu.* <xref:System.Windows.Media.LinearGradientBrush>  Możesz określić kolory gradientu i ich położenie wzdłuż osi gradientu przy użyciu <xref:System.Windows.Media.GradientStop> obiektów.  Możesz również zmodyfikować oś gradientu, która umożliwia tworzenie gradientów poziomych i pionowych oraz odwracanie kierunku gradientu. Oś gradientu jest opisana w następnej sekcji. Domyślnie gradient ukośny jest tworzony.

Poniższy przykład pokazuje kod, który tworzy gradient liniowy z czterema kolorami.

[!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]

Ten kod generuje następujący gradient:

![Ukośny gradient liniowy](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")

> [!NOTE]
> Przykłady gradientu w tym temacie używają domyślnego układu współrzędnych do ustawiania punktów początkowych i punktów końcowych. Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: 0 wskazuje 0 procent pola ograniczenia i 1 wskazuje 100 procent pola ograniczenia. Można zmienić ten system współrzędnych przez ustawienie <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość. <xref:System.Windows.Media.BrushMappingMode.Absolute> Bezwzględny układ współrzędnych nie należy do obwiedni. Wartości są interpretowane bezpośrednio w miejscu lokalnym.

<xref:System.Windows.Media.GradientStop> Jest podstawowym blokiem konstrukcyjnym pędzla gradientu.  Zatrzymanie gradientu określa <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.GradientStop.Offset%2A> wzdłuż osi gradientu.

- <xref:System.Windows.Media.GradientStop.Color%2A> Właściwość Stop gradientu określa kolor zatrzymania gradientu. Kolor można ustawić przy użyciu wstępnie zdefiniowanego koloru (dostarczonego przez <xref:System.Windows.Media.Colors> klasę) lub określając wartości ScRGB lub ARGB. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie można również opisać kolor przy użyciu notacji szesnastkowej. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Color> strukturę.

- <xref:System.Windows.Media.GradientStop.Offset%2A> Właściwość Stop gradientu określa pozycję koloru zatrzymania gradientu na osi gradientu. Przesunięcie to <xref:System.Double> zakres od 0 do 1. Bliżej wartości przesunięcia stopnia gradientu jest równa 0, bliżej koloru jest początek gradientu. Im bliżej wartości przesunięcia gradientu jest 1, tym bliżej koloru jest koniec gradientu.

Kolor każdego punktu między zatrzymania gradientu jest liniowo interpolowany jako kombinacja koloru określonego przez dwa powiązane gradienty. Poniższa ilustracja przedstawia zatrzymywanie gradientu w poprzednim przykładzie. Okręgi oznaczają położenie zatrzymań gradientu, a linia kreskowana pokazuje oś gradientu.

![Gradienty zatrzymane w gradiencie liniowym](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")

Pierwszy stopień gradientu określa kolor żółty przy przesunięciu `0.0`.  Drugi stopień gradientu określa kolor czerwony przy przesunięciu `0.25`.  Punkty między tymi dwoma stanami są stopniowo zmieniane z żółtego na czerwony podczas przesuwania od lewej do prawej wzdłuż osi gradientu.  Trzeci Stop gradientu określa kolor niebieski przy przesunięciu `0.75`.  Punkty między drugim i trzecim gradientem zatrzymają stopniowo zmianę z czerwony na niebieski. Czwarty stopień gradientu określa kolor wapna zielony przy przesunięciu `1.0`. Punkty między trzecim i czwartym gradientem zatrzymają stopniowo zmiany z niebieskiego na wapno zielonego.

<a name="gradientaxis"></a>

### <a name="the-gradient-axis"></a>Oś gradientu

Jak wspomniano wcześniej, stopka gradientowego pędzla gradientu jest umieszczana wzdłuż linii, osi gradientu. Można zmienić orientację i rozmiar linii przy użyciu pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> właściwości. Poprzez manipulowanie pędzlem <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, można tworzyć gradienty w poziomie i w pionie, odwrócić kierunek gradientu, zaskraplać nadlewkę gradientu i inne.

Domyślnie pędzel <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> gradientu liniowego i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> odnoszą się do obszaru rysowanego. Punkt (0, 0) reprezentuje lewy górny róg obszaru, a (1, 1) reprezentuje prawy dolny róg obszaru, w którym jest namalowane. Wartością domyślną <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> jest (0, 0), a jej wartością domyślną <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> jest (1, 1), która tworzy gradient ukośny zaczynający się w lewym górnym rogu i rozszerza do prawego dolnego rogu rysowanego obszaru. Na poniższej ilustracji przedstawiono oś gradientu pędzla gradientowego z wartościami <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> domyślnymi <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>i.

![Oś gradientu ukośnego gradientu liniowego](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")

Poniższy przykład pokazuje, jak utworzyć gradient poziomy przy użyciu pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i. <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> Zwróć uwagę, że gradient jest zatrzymywany tak samo jak w poprzednich przykładach; po prostu zmiana <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, Gradient został zmieniony z przekątnej na poziomą.

[!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]

Na poniższej ilustracji przedstawiono gradient, który został utworzony. Oś gradientu jest oznaczona linią kreskowaną, a gradienty są oznaczane kółkami.

![Oś gradientu dla poziomego gradientu liniowego](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")

W następnym przykładzie pokazano, jak utworzyć gradient pionowy.

[!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]

Na poniższej ilustracji przedstawiono gradient, który został utworzony. Oś gradientu jest oznaczona linią kreskowaną, a gradienty są oznaczane kółkami.

![Oś gradientu gradientu pionowego](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")

<a name="radialgradients"></a>

## <a name="radial-gradients"></a>Gradienty promieniowe

Podobnie jak w przypadku <xref:System.Windows.Media.RadialGradientBrush> ,malujeobszarzkolorami,któremieszająsięzesobąwzdłużosi.<xref:System.Windows.Media.LinearGradientBrush> Poprzednie przykłady pokazują, jak oś pędzla gradientu liniowego jest linią prostą. Oś pędzla gradientu promieniowego jest definiowana przez okrąg; kolory "promieniujące" na zewnątrz od jego pochodzenia.

W poniższym przykładzie pędzel gradientu promieniowego jest używany do malowania wnętrza prostokąta.

[!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]

Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie. Wyświetlona zostanie Stopka gradientu pędzla. Zwróć uwagę, że mimo że wyniki są inne, Gradient zostanie zatrzymany w tym przykładzie, tak samo jak w przypadku gradientu zatrzyma się w poprzednim przykładzie pędzla gradientu.

![Gradienty zatrzymane w gradiencie promieniowym](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")

<xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Określa punkt początkowy osi gradientu pędzla gradientu promieniowego. Oś gradientu jest wychodząca z punktu początkowego gradientu do okręgu gradientu. Okrąg gradientu pędzla jest definiowany przy użyciu <xref:System.Windows.Media.RadialGradientBrush.Center%2A>właściwości <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, i <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> .

Na poniższej ilustracji przedstawiono kilka gradientów promieniowych z <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>różnymi <xref:System.Windows.Media.RadialGradientBrush.Center%2A>ustawieniami <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>,, <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> i.

![Ustawienia RadialGradientBrush](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii") RadialGradientBrushes z różnymi ustawieniami GradientOrigin, Center, RadiusX i RADIUS.

<a name="specifyinggradientcolors"></a>

## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Określanie przezroczystego lub częściowo przezroczystego gradientu

Ponieważ zatrzymanie gradientu nie zapewnia właściwości nieprzezroczystości, należy określić kanał alfa kolorów przy użyciu notacji szesnastkowej ARGB w znaczniku lub <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> użyć metody w celu utworzenia zatrzymań gradientów, które są przezroczyste lub częściowo przezroczyste. W poniższych sekcjach wyjaśniono, jak utworzyć gradient częściowo przezroczysty w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodzie i.

<a name="argbsyntax"></a>

### <a name="specifying-color-opacity-in-xaml"></a>Określanie nieprzezroczystości koloru w "XAML"

W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie używasz notacji szesnastkowej ARGB, aby określić nieprzezroczystość poszczególnych kolorów. Notacja szesnastkowa ARGB używa następującej składni:

`#`**AA** *RRGGBB*

*AA* w poprzednim wierszu reprezentuje dwucyfrową wartość szesnastkową służącą do określenia nieprzezroczystości koloru. Wartości *RR*, *gg*i *BB* reprezentują dwie cyfry szesnastkowe, używane do określania ilości czerwonego, zielonego i niebieskiego w kolorze. Każda cyfra szesnastkowa może mieć wartość z prze0-9 lub A-F. 0 jest najmniejszą wartością, a F jest największa. Wartość alfa 00 określa kolor, który jest całkowicie przezroczysty, podczas gdy wartość alfa FF tworzy kolor, który jest całkowicie nieprzezroczysty.  W poniższym przykładzie szesnastkowa notacja ARGB jest używana do określenia dwóch kolorów. Pierwszy jest częściowo przezroczysty (ma wartość alfa x20), podczas gdy drugi jest całkowicie nieprzezroczysty.

[!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]

<a name="fromscrgbsyntax"></a>

### <a name="specifying-color-opacity-in-code"></a>Określanie nieprzezroczystości koloru w kodzie

W przypadku korzystania z kodu Metoda <xref:System.Windows.Media.Color.FromArgb%2A> statyczna umożliwia określenie wartości alfa podczas tworzenia koloru. Metoda przyjmuje cztery parametry typu <xref:System.Byte>. Pierwszy parametr określa kanał alfa koloru. Pozostałe trzy parametry określają wartości czerwony, zielony i niebieski koloru. Każda wartość powinna mieścić się w przedziale od 0 do 255 włącznie. Wartość alfa 0 Określa, że kolor jest całkowicie przezroczysty, a wartość alfa 255 określa, że kolor jest całkowicie nieprzezroczysty. W poniższym przykładzie <xref:System.Windows.Media.Color.FromArgb%2A> Metoda jest używana do tworzenia dwóch kolorów. Pierwszy kolor jest częściowo przezroczysty (ma wartość alfa 32), podczas gdy drugi jest całkowicie nieprzezroczysty.

[!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]

Alternatywnie możesz użyć <xref:System.Windows.Media.Color.FromScRgb%2A> metody, która umożliwia tworzenie koloru przy użyciu wartości ScRGB.

<a name="otherbrushes"></a>

## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Malowanie przy użyciu obrazów, rysunków, wizualizacji i wzorców

<xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> klasy umożliwiają malowanie obszaru za pomocą obrazów, rysunków lub wizualizacji. Aby uzyskać informacje na temat rysowania z obrazami, rysunkami i wzorcami, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przekształcanie pędzla — przegląd](brush-transformation-overview.md)
- [Warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md)
