---
title: Przegląd Masek krycia
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 680d7441301b425c088d549f9e0e0d2b976cc69f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="opacity-masks-overview"></a>Przegląd Masek krycia
Nieprzezroczystość maski umożliwiają upewnij części elementu lub visual przezroczystego lub częściowo przezroczysty. Aby utworzyć maskę przezroczystości, należy zastosować <xref:System.Windows.Media.Brush> do <xref:System.Windows.UIElement.OpacityMask%2A> właściwości elementu lub <xref:System.Windows.Media.Visual>.  Pędzel jest mapowana do elementu lub visual, a wartość nieprzezroczystości każdego piksela pędzla służy do określania wynikowy nieprzezroczystość każdego piksela odpowiedniego elementu lub visual.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 To omówienie przyjęto założenie, że czytelnik zna <xref:System.Windows.Media.Brush> obiektów. Aby obejrzeć wprowadzenie do przy użyciu pędzle, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać informacje o <xref:System.Windows.Media.ImageBrush> i <xref:System.Windows.Media.DrawingBrush>, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Tworzenie efektów wizualnych za pomocą maski przezroczystości  
 Maskę przezroczystości działa przez mapowanie jego zawartość do elementu lub visual. Kanał alfa każdego pikseli pędzla następnie są używane do określania wynikowy nieprzezroczystość elementu lub jego visual odpowiedniego pikseli; rzeczywiste kolor pędzla jest ignorowana. Jeśli dany część pędzla jest niewidoczny, odpowiednich części elementu lub visual staje się przezroczysty. W przypadku nieprzezroczyste danej części pędzla nieprzezroczystość odpowiednich części elementu lub visual pozostaje niezmieniona. Nieprzezroczystość określony przez maskę przezroczystości w połączeniu z ustawienia nieprzezroczystość w elemencie lub visual. Na przykład jeśli element jest 25 procent nieprzezroczystych i zastosowanej maskę przezroczystości przejścia z całkowicie nieprzezroczyste, aby w pełni przezroczyste, wynik jest element, który przechodzi z nieprzezroczystość 25 procent w pełni przezroczyste.  
  
> [!NOTE]
>  Mimo że przykłady w tym omówieniu przedstawiają sposób używania masek nieprzezroczystości dla elementów obrazu, maskę przezroczystości mogą być stosowane do dowolnego elementu lub <xref:System.Windows.Media.Visual>, w tym paneli i kontrolek.  
  
 Nieprzezroczystość maski służą do utworzyć interesujące efekty wizualne, takie jak obrazy lub stopniowe przycisków z widoku, aby dodać tekstury elementów lub połączyć gradientów do produkcji szkła przypominającej powierzchni. Poniższa ilustracja przedstawia użycie maskę przezroczystości. Tle specjalną służy do wyświetlenia przezroczyste obiekty maski.  
  
 ![Obiekt z maską nieprzezroczystości LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Przykład maskowania nieprzezroczystość.  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Tworzenie maskę przezroczystości  
 Aby utworzyć maskę przezroczystości, należy utworzyć <xref:System.Windows.Media.Brush> i zastosować je do <xref:System.Windows.UIElement.OpacityMask%2A> właściwości elementu lub visual. Można użyć dowolnego typu <xref:System.Windows.Media.Brush> jak maskę przezroczystości.  
  
-   <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Umożliwia pokazanie element lub visual zanikania z widoku.  
  
     Poniższy obraz przedstawia <xref:System.Windows.Media.LinearGradientBrush> używany jak maskę przezroczystości.  
  
     ![Obiekt o nieprzezroczystości LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Przykład maskowania nieprzezroczystości LinearGradientBrush  
  
-   <xref:System.Windows.Media.ImageBrush>: Używany do tworzenia tekstury i nietrwałego lub przerwana efekty krawędzi.  
  
     Poniższy obraz przedstawia <xref:System.Windows.Media.ImageBrush> używany jak maskę przezroczystości.  
  
     ![Obiekt, który ma nieprzezroczystości ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Przykład maskowania nieprzezroczystości LinearGradientBrush  
  
-   <xref:System.Windows.Media.DrawingBrush>: Używany do tworzenia złożonych nieprzezroczystość maski z wzorców kształtów, obrazy i gradienty.  
  
     Poniższy obraz przedstawia <xref:System.Windows.Media.DrawingBrush> używany jak maskę przezroczystości.  
  
     ![Obiekt z maską przezroczystość pędzla](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Przykład maskowania przezroczystość pędzla  
  
 Pędzle gradientów (<xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>) są szczególnie odpowiednie do użycia jako maskę przezroczystości. Ponieważ <xref:System.Windows.Media.SolidColorBrush> wypełnienia jako obszar kolorem jednolite, należy niską nieprzezroczystość maski; przy użyciu <xref:System.Windows.Media.SolidColorBrush> jest równoznaczne z ustawieniem elementu lub jego visual <xref:System.Windows.UIElement.OpacityMask%2A> właściwości.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Przy użyciu gradientu jak maskę przezroczystości  
 Aby utworzyć wypełnienia gradientowego, należy określić co najmniej dwa gradientu. Zawiera każdego gradientu opisano kolorów i pozycji (zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Aby uzyskać więcej informacji na temat tworzenia i używania gradienty). Proces jest taki sam, używając gradientu jak maskę przezroczystości z tą różnicą, że zamiast mieszania kolorów, gradientu maskę przezroczystości miesza wartości kanału alfa. Tak rzeczywiste kolor gradientu treści nie ma znaczenia; ma znaczenie tylko kanału alfa lub przezroczystość poszczególnych kolorów. Poniżej przedstawiono przykład.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Określanie gradientu maskę przezroczystości  
 W poprzednim przykładzie, kolor zdefiniowany przez system <xref:System.Windows.Media.Colors.Black%2A> jest używany jako kolor początkowy gradientu. Ponieważ wszystkie kolory w <xref:System.Windows.Media.Colors> klasy, z wyjątkiem <xref:System.Windows.Media.Colors.Transparent%2A>, są całkowicie nieprzezroczyste, może służyć do definiowania po prostu początkowy kolor gradientu nieprzezroczystość maski.  
  
 Dodatkową kontrolę nad wartości alfa podczas definiowania maskę przezroczystości, można określić dla kanału alfa kolorów przy użyciu [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] szesnastkowym znaczników lub przy użyciu <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metody.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Określanie Przezroczystość koloru w "XAML"  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], możesz użyć [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] szesnastkowym, aby określić przezroczystość poszczególnych kolorów. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] szesnastkowym używa następującej składni:  
  
 `#` **AA** *rrggbb*  
  
 *Aa* w poprzednim wierszu reprezentuje wartość szesnastkowa dwucyfrowe używany do określenia Przezroczystość koloru. *Rr*, *gg*, i *bb* każdy reprezentuje wartość szesnastkowa dwóch cyfr używana do określania ilości czerwony, zielony i niebieski w kolor. Każdy szesnastkową wartością cyfrową może mieć wartość z zakresu od 0 – 9 lub A-F. najmniejsza wartość to 0, a F jest większa. Wartości alfa 00 Określa kolor, który jest całkowicie niewidoczne, gdy wartość alfa FF tworzy kolor jest całkowicie nieprzezroczyste.  W poniższym przykładzie szesnastkową [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji służy do określania dwóch kolorów. Pierwsza to całkowicie nieprzezroczyste, podczas gdy druga jest całkowicie niewidoczne.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Przy użyciu obrazu jak maskę przezroczystości  
 Obrazy można również jak maskę przezroczystości. Na poniższej ilustracji przedstawiono przykład. Tle specjalną służy do wyświetlenia przezroczyste obiekty maski.  
  
 ![Obiekt z maską nieprzezroczystości ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Przykład maskowania nieprzezroczystość.  
  
 Aby użyć obrazu jak maskę przezroczystości, użyj <xref:System.Windows.Media.ImageBrush> zawiera obraz. Podczas tworzenia obrazu do użycia jak maskę przezroczystości, zapisania obrazu w formacie, który obsługuje wiele poziomów przezroczystości, takich jak [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. Poniższy przykład przedstawia kod używany do utworzenia na poprzedniej ilustracji.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Przy użyciu obrazu sąsiadującym jak maskę przezroczystości  
 W poniższym przykładzie ten sam obraz jest używana z inną <xref:System.Windows.Media.ImageBrush>, ale pędzla kafelków funkcje są używane do tworzenia Kafelki kwadratu obrazu 50 pikseli.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Tworzenie z rysunku maskę przezroczystości  
 Rysunki mogą być używane maskę przezroczystości. Kształty znajdujących się na rysunku się można podać gradientów, pełne kolory, obrazy lub nawet inne rysunki. Na poniższej ilustracji przedstawiono przykład rysunku używany jak maskę przezroczystości. Tle specjalną służy do wyświetlenia przezroczyste obiekty maski.  
  
 ![Obiekt z maską przezroczystość pędzla](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Przykład maskowania przezroczystość pędzla  
  
 Aby użyć rysunku jak maskę przezroczystości, użyj <xref:System.Windows.Media.DrawingBrush> zawiera rysunku. W poniższym przykładzie pokazano kod, który został użyty do utworzenia na poprzedniej ilustracji:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Za pomocą rysowania sąsiadującym jak maskę przezroczystości  
 Podobnie jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> można wprowadzić na kafelku jej rysowania. W poniższym przykładzie pędzla do rysowania służy do tworzenia maskę przezroczystości sąsiadującym.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
