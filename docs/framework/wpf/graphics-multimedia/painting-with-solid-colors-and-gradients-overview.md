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
ms.openlocfilehash: cea4b2dbd17178a6943b0f4a84182e65232330fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566785"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Przegląd Malowanie jednolitymi kolorami i gradientami
W tym temacie opisano sposób użycia <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, i <xref:System.Windows.Media.RadialGradientBrush> obiektów namalować z kolorami, gradienty liniowe i gradientu promieniowego.  
  

  
<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Malowanie obszaru jednolitym kolorem  
 Jednym z najbardziej typowych operacji na dowolnej platformie jest namalować obszar o niezawodnej <xref:System.Windows.Media.Color>. Aby wykonać to zadanie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia <xref:System.Windows.Media.SolidColorBrush> klasy. W poniższych sekcjach opisano różne sposoby malować <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>Przy użyciu obiektu SolidColorBrush w "XAML"  
 Namalować obszar jednolitym kolorem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj jednej z następujących opcji.  
  
-   Wybierz pędzla pełnego koloru wstępnie zdefiniowanych według nazwy.  Na przykład można ustawić element button <xref:System.Windows.Controls.Control.Background%2A> "Red" lub "MediumBlue".  Dla innych listy wstępnie zdefiniowanych pędzle pełnego koloru, zobacz statycznej właściwości <xref:System.Windows.Media.Brushes> klasy. Poniżej przedstawiono przykład.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
-   Wybierz kolor z palety kolorów 32-bitowy, określając ilości czerwony, zielony i niebieski można łączyć w jednej pełnego koloru.  Format służący do określania koloru z palety 32-bitowych jest "*#rrggbb*", gdzie *rr* jest dwóch szesnastkową wartością cyfrową określania względnych ilość czerwony, *gg* Określa kolor zielony, i *bb* określa ilość niebieski.  Ponadto można określić kolor jako "#*aarrggbb*" gdzie *aa* Określa *alfa* wartość lub Przezroczystość koloru. Ta metoda umożliwia utworzenie kolorów, które są częściowo przezroczysty.  W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> jest ustawiona na czerwony pełni nieprzezroczyste przy użyciu notacji szesnastkowej.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
-   Użyj składni tagów właściwości do opisywania <xref:System.Windows.Media.SolidColorBrush>. Ta składnia jest na pełniejsze, ale można określić dodatkowe ustawienia, takie jak przezroczystość pędzla. W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> właściwości dwóch <xref:System.Windows.Controls.Button> elementy są ustawione na czerwono pełni nieprzezroczyste. Kolor pędzla pierwszy opisano przy użyciu nazwy kolor wstępnie zdefiniowane. Kolor pędzla drugi opisano przy użyciu notacji szesnastkowej.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Malowanie SolidColorBrush w kodzie  
 Do malowania obszar jednolitym kolorem w kodzie, użyj jednej z następujących opcji.  
  
-   Użyj jednej z wstępnie zdefiniowanych pędzle pochodzącymi <xref:System.Windows.Media.Brushes> klasy. W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> ma ustawioną wartość <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
-   Utwórz <xref:System.Windows.Media.SolidColorBrush> i ustawić jej <xref:System.Windows.Media.SolidColorBrush.Color%2A> za pomocą właściwości <xref:System.Windows.Media.Color> struktury. Można użyć wstępnie zdefiniowanych koloru z <xref:System.Windows.Media.Colors> klasy albo można utworzyć <xref:System.Windows.Media.Color> przy użyciu statycznych <xref:System.Windows.Media.Color.FromArgb%2A> metody.  
  
     Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush> przy użyciu wstępnie zdefiniowanych koloru.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Statycznych <xref:System.Windows.Media.Color.FromArgb%2A> umożliwia określenie wartości alfa, kolor czerwony, zielonemu i niebieskiemu. Typowy zakres dla każdej z tych wartości to 0 – 255. Na przykład alfa wartość 0 wskazuje, czy kolor jest całkowicie niewidoczne, gdy wartość 255 oznacza, że kolor jest całkowicie nieprzezroczysta. Podobnie red wartość 0 oznacza, że koloru ma nie czerwony, o podczas wartość 255 oznacza, że koloru ma maksymalną ilość czerwony możliwe.  W poniższym przykładzie opisano kolor pędzla, określając wartości alfa, czerwony, zielony i niebieski.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Dodatkowe sposoby określić kolor, zobacz <xref:System.Windows.Media.Color> temat referencyjny.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Malowanie obszaru gradientem  
 Pędzla gradientów do malowania obszar o wiele kolorów, które przejście do siebie, wzdłuż osi. Ich umożliwia utworzenie odcisków jasnym i w tle, podając formantów trójwymiarowy działania. Można także używać ich do symulowania awaryjne, chrome limitu górnego i innych smooth powierzchni.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Istnieją dwa rodzaje pędzle gradientów: <xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Gradienty liniowe  
 A <xref:System.Windows.Media.LinearGradientBrush> rysują obszaru gradientem definiowane wiersza, *oś*.  Określ kolorami gradientu i ich lokalizacji wzdłuż osi gradientu, przy użyciu <xref:System.Windows.Media.GradientStop> obiektów.  Może także modyfikować gradientu osi, która umożliwia tworzenie gradientów poziome i pionowe oraz aby odwrócić kierunek gradientu. Oś jest opisany w następnej sekcji. Domyślnie jest tworzony przekątnej gradientu.  
  
 Poniższy przykład przedstawia kod, który tworzy cztery kolorami gradientu liniowego.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Ten kod tworzy następujące gradientu:  
  
 ![Przekątnej gradientu liniowego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Uwaga:** gradientu przykłady w tym temacie Korzystanie z systemu współrzędnych domyślne ustawienie punkty początkowy i końcowy. System współrzędnych domyślna jest określana względem obwiedni: 0 oznacza 0 procent obwiedni i 1 oznacza 100 procent obwiedni. Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute>. Bezwzględny układ współrzędnych nie jest określana względem obwiedni. Wartości są interpretowane bezpośrednio w lokalnej przestrzeni.  
  
 <xref:System.Windows.Media.GradientStop> Jest podstawowym blokiem konstrukcyjnym pędzla gradientu.  Określa gradientu <xref:System.Windows.Media.GradientStop.Color%2A> na <xref:System.Windows.Media.GradientStop.Offset%2A> osi gradientu.  
  
-   Ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Color%2A> właściwość określa kolor gradientu. Kolor może ustawić przy użyciu wstępnie zdefiniowanych kolorów (dostarczonych przez <xref:System.Windows.Media.Colors> klasy) albo określając ScRGB lub ARGB wartości. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można także użyć szesnastkowym opisujący kolor. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Color> struktury.  
  
-   Ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> właściwość określa położenie kolor gradientu na osi gradientu. Przesunięcie jest <xref:System.Double> który zakresu od 0 do 1. Bliższe ograniczniku gradientu przesunięcia ma wartość 0, bliżej jest kolor początkowy gradientu. Bliższe gradientu przesunięcia ma wartość 1, bliżej jest kolor końcowy gradientu.  
  
 Kolor każdego punktu między gradientu jest liniowo interpolowane jako połączenie kolorów określonego przez dwie ograniczenia gradientu. Poniższa ilustracja wyróżnia gradientu w poprzednim przykładzie. Kółka Oznacz pozycja gradientu i linia przerywana, co przedstawiono gradientu osi.  
  
 ![Gradientu liniowego gradientu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 Pierwszy gradientu kolor żółty przy przesunięciu z `0.0`.  Drugi gradientu Określa kolor czerwony przy przesunięciu z `0.25`.  Punkty między tych dwóch zatrzymuje stopniowo zmienić z żółtym czerwony podczas przenoszenia od lewej do prawej osi gradientu.  Trzeci gradientu kolor niebieski przy przesunięciu z `0.75`.  Punkty między drugiego i trzeciego gradientu stopniowo zmienić kolor czerwony, niebieski. Czwarty gradientu określa wapna kolor zielony przy przesunięciu z `1.0`. Punkty między trzecim i czwartym gradientu stopniowo zmienić niebieski do Limonowy zielony.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>Oś gradientu  
 Jak wcześniej wspomniano pędzla gradientu liniowego gradientu są pozycjonowane wzdłuż linii osi gradientu. Możesz zmienić Orientacja i rozmiar wiersza przy użyciu pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> właściwości. Przez manipulowanie pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, można utworzyć poziome i pionowe gradienty odwrócić kierunek gradientu, zmniejszanie gradientu rozpowszechniania i inne.  
  
 Domyślnie pędzla gradientu liniowego w <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> są względem obszaru są rysowane. Punkt (0,0) reprezentuje lewego górnego rogu obszaru jest malowane i (1,1) reprezentuje prawym dolnym rogu obszaru są rysowane. Wartość domyślna <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> jest (0,0) i jego domyślne <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> jest (1,1), co powoduje przekątnej gradientu, zaczynając od lewego górnego rogu oraz w celu rozszerzenia w prawym dolnym rogu obszaru są rysowane. Na poniższej ilustracji przedstawiono osi gradientu liniowego pędzla gradientu z domyślnymi <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Oś przekątnej gradientu liniowego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 W poniższym przykładzie przedstawiono sposób tworzenia poziomym gradientu, określając pędzla <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Zwróć uwagę, że gradientu są takie same jak w poprzednich przykładach; po prostu zmieniając <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, na poziomie została zmieniona z przekątnej gradientu.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradientu, który jest tworzony. Oś jest oznaczonej jako linia przerywana, a gradientu są oznaczone ikoną koła.  
  
 ![Oś pozioma gradientu liniowego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 Kolejnym przykładzie pokazano, jak utworzyć pionowego.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradientu, który jest tworzony. Oś jest oznaczonej jako linia przerywana, a gradientu są oznaczone ikoną koła.  
  
 ![Oś gradientu pionowego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Gradientu promieniowego  
 Podobnie jak <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> rysują obszar o kolorów, które razem blend wzdłuż osi. W poprzednich przykładach pokazano, jak osi pędzla gradientu liniowego jest prostą. Oś pędzla gradientu promieniowego jest definiowana za pomocą koło; jego kolorów "wysyłać" na zewnątrz ze swoją witryną źródłową.  
  
 W poniższym przykładzie pędzla gradientu promieniowego umożliwia malowanie wnętrza prostokąta.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu. Ma zostały wyróżnione pędzla gradientu. Należy zauważyć, że mimo że wyniki są różne, gradientu w tym przykładzie są identyczne z gradientu w poprzednich przykładach pędzla gradientu liniowego.  
  
 ![Gradientu promieniowego gradientu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Określa punkt początkowy gradientu osi pędzla gradientu promieniowego. Oś wychodzącą z punktu początkowego gradientu do okręgu gradientu. Pędzel okręgu gradientu jest definiowana za pomocą jego <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, i <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> właściwości.  
  
 Na poniższej ilustracji przedstawiono kilka gradientu promieniowego z różnymi <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, i <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> ustawienia.  
  
 ![Ustawienia obiektu RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
RadialGradientBrushes z różnymi ustawieniami GradientOrigin, Centrum RadiusX i RadiusY.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Określanie przezroczystego lub częściowo przezroczyste gradientu  
 Ponieważ gradientu nie udostępniają właściwości nieprzezroczystość, należy określić kanału alfa kolorów przy użyciu [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] szesnastkowym znaczników lub użyj <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metodę w celu utworzenia gradientu przezroczysty lub częściowo przezroczysty. W poniższych sekcjach opisano sposób tworzenia częściowo przezroczyste gradientu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Określanie Przezroczystość koloru w "XAML"  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] szesnastkowym, aby określić przezroczystość poszczególnych kolorów. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] szesnastkowym używa następującej składni:  
  
 `#` **AA** *rrggbb*  
  
 *Aa* w poprzednim wierszu reprezentuje wartość szesnastkowa dwucyfrowe używany do określenia Przezroczystość koloru. *Rr*, *gg*, i *bb* każdy reprezentuje wartość szesnastkowa dwóch cyfr używana do określania ilości czerwony, zielony i niebieski w kolor. Każdy szesnastkową wartością cyfrową może mieć wartość z zakresu od 0 – 9 lub A-F. najmniejsza wartość to 0, a F jest większa. Wartości alfa 00 Określa kolor, który jest całkowicie niewidoczne, gdy wartość alfa FF tworzy kolor jest całkowicie nieprzezroczyste.  W poniższym przykładzie szesnastkową [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji służy do określania dwóch kolorów. Pierwsza to częściowo przezroczyste (ma wartość alfa x20), podczas gdy druga jest całkowicie nieprzezroczysta.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Określanie Przezroczystość koloru w kodzie  
 Jeśli przy użyciu kodu, statycznych <xref:System.Windows.Media.Color.FromArgb%2A> metody umożliwia określenie wartości alfa podczas tworzenia koloru. Metoda przyjmuje cztery parametry typu <xref:System.Byte>. Pierwszy parametr określa kanału alfa koloru; trzy parametry Określ czerwony, zielonemu i niebieskiemu wartości koloru. Każdej wartości powinna należeć do zakresu od 0 do 255 włącznie. Wartości alfa 0 określa, czy kolor jest całkowicie niewidoczne, gdy wartość alfa 255 Określa, czy kolor jest całkowicie nieprzezroczysta. W poniższym przykładzie <xref:System.Windows.Media.Color.FromArgb%2A> metoda jest używana do tworzenia dwóch kolorów. Pierwszy kolor jest częściowo przezroczysty (ma wartość alfa 32), a drugą jest całkowicie nieprzezroczyste.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Alternatywnie można użyć <xref:System.Windows.Media.Color.FromScRgb%2A> metodę, która pozwala na użycie wartości ScRGB, aby utworzyć kolor.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Malowanie obrazów, rysunki elementów wizualnych i wzorce  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> klasy umożliwiają malowanie obszar o obrazy, rysunki lub elementów wizualnych. Informacje o malowanie obrazów, rysunki i wzorce, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Przekształcanie pędzla — przegląd](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Warstwy renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)
