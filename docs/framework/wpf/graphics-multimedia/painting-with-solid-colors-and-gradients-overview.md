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
ms.openlocfilehash: 4e004b624c331375501c5f48d2566a664b734d3b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649983"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Przegląd Malowanie jednolitymi kolorami i gradientami
W tym temacie opisano sposób użycia <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, i <xref:System.Windows.Media.RadialGradientBrush> obiektów malowanie jednolitymi kolorami, użyciu gradientów liniowych i użyciu gradientów promieniowych.  

<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Malowanie obszaru jednolitym kolorem  
 Jednym z najbardziej typowych operacji, na dowolnej platformie jest Maluj obszar za pomocą niezawodnej <xref:System.Windows.Media.Color>. Aby wykonać to zadanie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia <xref:System.Windows.Media.SolidColorBrush> klasy. W poniższych sekcjach opisano różne sposoby malować <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>Za pomocą SolidColorBrush w "XAML"  
 Można malować obszar jednolitym kolorem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj jednej z następujących opcji.  
  
- Wybierz wstępnie zdefiniowany jednolitego koloru pędzla według nazwy.  Na przykład można ustawić przycisku <xref:System.Windows.Controls.Control.Background%2A> "Red" lub "MediumBlue".  Aby uzyskać listę innych wstępnie zdefiniowanych pędzle pełnego koloru, zobacz statycznej właściwości <xref:System.Windows.Media.Brushes> klasy. Oto przykład.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
- Wybierz kolor z palety kolorów 32-bitowych, określając ilości czerwony, zielony i niebieski, aby połączyć w jednym jednolitego koloru.  Określanie kolor z palety 32-bitowy format jest "*#rrggbb*", gdzie *rr* jest dwucyfrową liczbą szesnastkową, określając względna ilość czerwony, *gg* Określa kolor zielony, a *bb* określa ilość niebieski.  Ponadto można określić kolor jako "#*aarrggbb*" gdzie *aa* Określa *alfa* wartość lub Przezroczystość koloru. Takie podejście umożliwia tworzenie kolorów, które są częściowo przezroczyste.  W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> jest ustawiony na czerwony całkowicie nieprzezroczysty, przy użyciu notacji szesnastkowej.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
- Składnia znacznika właściwości można użyć do opisania <xref:System.Windows.Media.SolidColorBrush>. Ta składnia jest bardziej szczegółowy, ale można określić dodatkowe ustawienia, takie jak przezroczystość pędzla. W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> właściwości dwóch <xref:System.Windows.Controls.Button> elementy są ustawione na całkowicie nieprzezroczysty czerwony. Kolor pędzla pierwszy opisano przy użyciu nazwy wstępnie zdefiniowany kolor. Kolor pędzla drugi opisano przy użyciu notacji szesnastkowej.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Malowanie przy użyciu SolidColorBrush w kodzie  
 Aby Maluj obszar jednolitym kolorem w kodzie, użyj jednego z następujących opcji.  
  
- Użyj jednej z wstępnie zdefiniowanych pędzle, dostarczone przez <xref:System.Windows.Media.Brushes> klasy. W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> ustawiono <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
- Tworzenie <xref:System.Windows.Media.SolidColorBrush> i ustaw jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość za pomocą <xref:System.Windows.Media.Color> struktury. Możesz użyć wstępnie zdefiniowany kolor na podstawie <xref:System.Windows.Media.Colors> klasy albo możesz utworzyć <xref:System.Windows.Media.Color> przy użyciu statycznych <xref:System.Windows.Media.Color.FromArgb%2A> metody.  
  
     Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush> przy użyciu wstępnie zdefiniowany kolor.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Statyczne <xref:System.Windows.Media.Color.FromArgb%2A> umożliwia określenie wartości alfa, koloru czerwonego, zielonego i niebieskiego. Typowy zakres dla każdej z tych wartości to 0-255. Na przykład alfa wartość 0 oznacza kolor, który jest całkowicie przezroczysty, gdy wartość 255 wskazuje, że kolor jest całkowicie nieprzezroczysty. Podobnie czerwony wartość 0 wskazuje, że kolor, który ma nie czerwony, o podczas wartość 255 oznacza, że kolor, który ma maksymalną ilość red możliwe.  W poniższym przykładzie opisano kolor pędzla, określając wartości alfa, czerwony, zielony i niebieski.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Aby poznać dodatkowe sposoby określić kolor, zobacz <xref:System.Windows.Media.Color> temat referencyjny.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Malowanie obszaru gradientem  
 Pędzel gradientów Malowanie obszaru za pomocą wielu kolorów, które mieszają do siebie, wzdłuż osi. Ich umożliwia tworzenie odcisków jasny i w tle, zapewniając kontrolkom trójwymiarowej działania. Umożliwia także je do symulacji szkła, chrome, wody i innych smooth powierzchni.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia dwa typy pędzle gradientów: <xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Gradienty liniowe  
 A <xref:System.Windows.Media.LinearGradientBrush> Malowanie obszaru gradientem zdefiniowane wzdłuż linii, *oś*.  Należy określić gradient kolorów i ich lokalizacji, wzdłuż osi gradientu, za pomocą <xref:System.Windows.Media.GradientStop> obiektów.  Może także modyfikować gradientu osi, która umożliwia tworzenie gradientów poziome i pionowe oraz Odwróć kierunek gradientu. Gradient osi jest opisane w następnej sekcji. Domyślnie jest tworzony po przekątnej gradientu.  
  
 Poniższy przykład pokazuje kod, który tworzy cztery kolory gradientu liniowego.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Ten kod tworzy następujące gradientu:  
  
 ![Po przekątnej gradientu liniowego](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Uwaga:** Gradientu przykładach w niniejszym temacie na użytek w układzie współrzędnych domyślne ustawienie punktach i punktów końcowych. System współrzędnych domyślne są określane względem obwiedni: 0 wskazuje, że wartość 0 procent obwiedni i 1 wskazuje obwiedni 100 procent. Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute>. Bezwzględnych współrzędnych jest względem obwiedni. Wartości są interpretowane bezpośrednio w przestrzeni lokalnej.  
  
 <xref:System.Windows.Media.GradientStop> Jest podstawowym budulcem pędzla gradientu.  Określa gradientu <xref:System.Windows.Media.GradientStop.Color%2A> na <xref:System.Windows.Media.GradientStop.Offset%2A> wzdłuż osi gradientu.  
  
- Zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> właściwość określa kolor zatrzymania gradientu. Kolor może ustawić przy użyciu wstępnie zdefiniowany kolor (dostarczonych przez <xref:System.Windows.Media.Colors> klasy) albo określając ScRGB lub ARGB wartości. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz skorzystać z notacji szesnastkowej opisujący kolor. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Color> struktury.  
  
- Zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> właściwość określa położenie koloru zatrzymania gradientu na osi gradientu. Przesunięcie jest <xref:System.Double> , zakresu od 0 do 1. Im bliżej zatrzymania gradientu wartość przesunięcia jest 0, im bliżej kolor na początek gradientu. Im bliżej gradientu wartość przesunięcia jest 1, im bliżej jest kolor końcowy gradientu.  
  
 Kolor każdego punktu między ograniczniki gradientu jest liniowo interpolowane pod postacią połączenia kolor określony przy użyciu dwóch blokujących ograniczniki gradientu. Następująca ilustracja wyróżnia ograniczniki gradientu w poprzednim przykładzie. Okręgów oznaczyć położenie ograniczniki gradientu i linię przerywaną, co pokazuje gradientu osi.  
  
 ![Ograniczniki gradientu w gradientu liniowego](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 Pierwszy gradientu kolor żółty na przesunięcie `0.0`.  Drugi gradientu Określa kolor czerwony na przesunięcie `0.25`.  Punkty między tymi dwoma zatrzymuje stopniowo zmienia się z żółtym na czerwony po przeniesieniu od lewej do prawej osi gradientu.  Trzeci gradientu kolor niebieski na przesunięcie `0.75`.  Punkty między ograniczniki gradientu drugi i trzeci stopniowo zmienić kolor czerwony, niebieski. Czwarty gradientu określa zielono kolor na przesunięcie `1.0`. Punkty między ograniczniki gradientu trzecia i czwarta stopniowo zmienić niebieski do Limonowozielony.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>Oś gradientu  
 Jak wspomniano wcześniej ograniczniki gradientu liniowego pędzla gradientów firmy są pozycjonowane wzdłuż linii osi gradientu. Mogą ulec zmianie, orientacji i rozmiaru wiersza przy użyciu pędzli <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> właściwości. Przez operacje pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, można utworzyć poziome i pionowe gradientów Odwróć kierunek gradientu, zagęszczanie gradientu rozprzestrzeniania się i nie tylko.  
  
 Domyślnie pędzel gradientów liniowych firmy <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> są względne wobec obszaru są rysowane. Punkt (0,0) reprezentuje lewego górnego rogu obszaru jest malowane i (1,1) reprezentuje prawym dolnym rogu obszaru są rysowane. Wartość domyślna <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> jest (0,0) i jego domyślne <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> jest (1,1) tworzy ukośne gradientu, zaczynając od lewego górnego rogu, a rozszerzenie do prawego dolnego rogu obszaru są rysowane. Poniższa ilustracja przedstawia oś gradientu pędzel gradientów liniowych z domyślną <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Oś ukośne gradientu liniowego](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 Poniższy przykład pokazuje, jak utworzyć poziomej gradientu, określając pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Należy zauważyć, że ograniczniki gradientu są takie same jak w poprzednich przykładach; po prostu zmieniając <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, zmieniono gradientu pozycję z przekątnej na poziomie.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Poniższa ilustracja przedstawia gradientu, który zostanie utworzony. Gradient osi jest oznaczona za pomocą linię przerywaną, co i ograniczniki gradientu są oznaczone za pomocą kółka.  
  
 ![Oś pozioma gradientu liniowego](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 Następny przykład pokazuje, jak utworzyć gradient pionowy.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Poniższa ilustracja przedstawia gradientu, który zostanie utworzony. Gradient osi jest oznaczona za pomocą linię przerywaną, co i ograniczniki gradientu są oznaczone za pomocą kółka.  
  
 ![Oś pionowa gradientu](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Gradienty promieniowe  
 Podobnie jak <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> Malowanie obszaru za pomocą kolorów, które mieszają się wzdłuż osi. W poprzednich przykładach pokazano, jak osi pędzla gradientu liniowego jest prostą. Klasa RadialGradientBrush firmy osi jest definiowany przez circle; jego kolorów "fale" na zewnątrz od ich pochodzenia.  
  
 W poniższym przykładzie klasa RadialGradientBrush służy do wnętrza prostokąta.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie. Podkreślono pędzla gradientu. Zwróć uwagę, że mimo że wyniki są różne, ograniczniki gradientu w tym przykładzie są identyczne z ograniczniki gradientu w poprzednich przykładach pędzel gradientów liniowych.  
  
 ![Ograniczniki gradientu w gradient promieniowy](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Określa punkt początkowy gradientu osi pędzla gradientu promieniowego. Oś wychodzącą z punktu początkowego gradientu do okręgu gradientu. Pędzel gradientu okrąg jest definiowany przez jego <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, i <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> właściwości.  
  
 Na poniższej ilustracji przedstawiono kilka użyciu gradientów promieniowych z różnymi <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, i <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> ustawienia.  
  
 ![RadialGradientBrush settings](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
RadialGradientBrushes z różnymi ustawieniami GradientOrigin, Centrum, RadiusX i RadiusY.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Określanie obszarów przezroczystych lub częściowo przejrzyste ograniczniki gradientu  
 Ponieważ ograniczniki gradientu nie zostanie określona przez właściwość nieprzezroczystości, należy określić kanał alfa kolorów za pomocą [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] notacji szesnastkowej znaczników lub użyj <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metodę w celu utworzenia ograniczniki gradientu, znajdujących się na kilka obszarów przezroczystych lub częściowo przezroczyste. W poniższych sekcjach opisano sposób tworzenia częściowo przejrzyste ograniczniki gradientu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Określanie Przezroczystość koloru w "XAML"  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji szesnastkowej określić krycie poszczególnych kolorów. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji szesnastkowej używa następującej składni:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* w poprzednim wierszu reprezentuje wartość szesnastkową dwucyfrowy używany do określenia Przezroczystość koloru. *Rr*, *gg*, i *bb* każdy reprezentuje dwucyfrowa wartość szesnastkową, można określić ilość czerwony, zielony i niebieski w kolorze. Każdy cyfra szesnastkowa może mieć wartość z zakresu od 0 – 9 lub A – F. Usługa 0 jest najmniejsza wartość, a F jest większa. Wartości alfa 00 Określa, że kolor, który jest całkowicie przezroczysty, a wartość alfa FF tworzy kolor, który jest całkowicie nieprzezroczyste.  W poniższym przykładzie szesnastkowe [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji służy do określania dwóch kolorów. Pierwszy jest częściowo przezroczyste (ma wartość alfa x20), podczas gdy druga jest całkowicie nieprzezroczysty.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Określanie Przezroczystość koloru w kodzie  
 Korzystając z kodu, statycznej <xref:System.Windows.Media.Color.FromArgb%2A> metody umożliwia określenie wartości alfa, po utworzeniu kolor. Ta metoda przyjmuje cztery parametry typu <xref:System.Byte>. Pierwszy parametr określa kanał alfa koloru; trzy parametry Określ czerwonego, zielonego i niebieskiego wartości koloru. Każda wartość powinna wynosić od 0 do 255. Alfa wartość 0 oznacza, że kolor jest całkowicie przezroczysty podczas, gdy wartość alfa 255 Określa, że kolor jest całkowicie nieprzezroczysty. W poniższym przykładzie <xref:System.Windows.Media.Color.FromArgb%2A> metoda jest używana do tworzenia dwóch kolorów. Pierwszy kolor jest częściowo przezroczyste (ma wartość alfa 32), podczas gdy druga jest całkowicie nieprzezroczyste.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Alternatywnie można użyć <xref:System.Windows.Media.Color.FromScRgb%2A> metody, która pozwala na użycie ScRGB wartości, aby utworzyć kolor.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Malowanie przy użyciu obrazów, rysunki, wizualizacji i wzorce  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> klasy umożliwiają Maluj obszar za pomocą obrazów, rysunki lub wizualizacji. Aby uzyskać informacji na temat malowanie obrazami, rysunki i wzorców, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przekształcanie pędzla — przegląd](brush-transformation-overview.md)
- [Warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md)
