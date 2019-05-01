---
title: Przegląd Masek krycia
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 84525e58487ce9b0bc26f77ff8dbced734bc90a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008476"
---
# <a name="opacity-masks-overview"></a>Przegląd Masek krycia
Maski krycia umożliwiać wykonywanie części elementu lub visual przezroczyste lub częściowo przezroczyste. Aby utworzyć maski krycia, należy zastosować <xref:System.Windows.Media.Brush> do <xref:System.Windows.UIElement.OpacityMask%2A> właściwość elementu lub <xref:System.Windows.Media.Visual>.  Pędzel jest mapowany na element "lub" visual, a wartość nieprzezroczystości każdego piksela pędzla służy do określania wynikowy nieprzezroczystość każdego piksela odpowiedniego elementu lub visual.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym omówieniu przyjęto założenie, że czytelnik zna <xref:System.Windows.Media.Brush> obiektów. Wprowadzenie do korzystania z pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać informacje o <xref:System.Windows.Media.ImageBrush> i <xref:System.Windows.Media.DrawingBrush>, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Tworzenie efektów wizualnych za pomocą maski krycia  
 Maski krycia działa przez mapowanie jego zawartość do elementu lub visual. Kanał alfa poszczególnych pikseli pędzla są następnie używane do określenia wynikowy nieprzezroczystość elementu lub pikselach odpowiedniego elementu wizualnego; rzeczywiste kolor pędzla jest ignorowany. Jeśli dany fragment pędzla, który jest niewidoczny, odpowiednie części elementu lub wizualizacji staje się przezroczyste. W przypadku nieprzezroczyste danej części pędzel nieprzezroczystość odpowiednią część elementu lub wizualizacji ulega zmianie. Nieprzezroczystość określony przez maski nieprzezroczystości w połączeniu z ustawienia nieprzezroczystość obecna w elemencie lub visual. Na przykład jeśli element jest 25 procent nieprzezroczystych i stosowane maski krycia przechodzi z całkowicie nieprzezroczyste, aby w pełni przezroczyste, wynik jest element, który przechodzi w z 25 procent krycia w pełni przezroczyste.  
  
> [!NOTE]
>  Mimo że na potrzeby przykładów w tym omówieniu pokazują użycie maski krycia dla elementów obrazu, maski krycia mogą być stosowane do dowolnego elementu lub <xref:System.Windows.Media.Visual>, w tym paneli i formanty.  
  
 Maski krycia są używane do tworzenia efektów wizualnych interesujące, takich jak tworzenie obrazów lub przyciski zanikanie w widoku, można dodać tekstury do elementów lub połączyć gradientów do produkcji szkła przypominającej powierzchnie. Poniższa ilustracja przedstawia użycie maski nieprzezroczystości. Tle specjalną służy do pokazywania przezroczyste obiekty maski.  
  
 ![Obiekt przy użyciu nieprzezroczystości LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Przykład maskowania krycia  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Tworzenie maski krycia  
 Aby utworzyć maski krycia, należy utworzyć <xref:System.Windows.Media.Brush> i zastosować je do <xref:System.Windows.UIElement.OpacityMask%2A> właściwość elementu lub wizualizacji. Można użyć dowolnego typu <xref:System.Windows.Media.Brush> jako maski nieprzezroczystości.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Umożliwia elementu lub visual fade z widoku.  
  
     Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.LinearGradientBrush> używany jako maski nieprzezroczystości.  
  
     ![Obiekt o nieprzezroczystości LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Przykład maskowania nieprzezroczystości LinearGradientBrush  
  
- <xref:System.Windows.Media.ImageBrush>: Pozwala utworzyć tekstury i efekty krawędzi nietrwałego lub przerwana.  
  
     Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.ImageBrush> używany jako maski nieprzezroczystości.  
  
     ![Obiekt, który ma maski krycia ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Przykład maskowania nieprzezroczystości LinearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Używane do tworzenia złożonych maski krycia z wzorców kształtów, obrazy i gradientów.  
  
     Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.DrawingBrush> używany jako maski nieprzezroczystości.  
  
     ![Obiekt, za pomocą maski krycia DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Przykład maskowania przezroczystość pędzla  
  
 Pędzle gradientów (<xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>) są szczególnie dobrze nadaje się do użytku jako maski nieprzezroczystości. Ponieważ <xref:System.Windows.Media.SolidColorBrush> wypełnienia wiadomość obszar za pomocą jednolitego koloru, wprowadzić niskiej nieprzezroczystości maskuje; przy użyciu <xref:System.Windows.Media.SolidColorBrush> jest równoznaczne z ustawieniem elementu lub elementu wizualnego <xref:System.Windows.UIElement.OpacityMask%2A> właściwości.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Przy użyciu gradientu maski krycia  
 Aby utworzyć wypełniacza gradientu, należy określić co najmniej dwa ograniczniki gradientu. Zawiera każdy gradientu opisuje kolor i położenie (zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md) Aby uzyskać więcej informacji na temat tworzenia i używania gradientów). Proces jest taka sama, korzystając z gradientu jako maski krycia, z tą różnicą, że zamiast mieszania kolorów, maski krycia gradientu miesza wartości kanał alfa. Dlatego rzeczywiste kolor gradientu zawartość nie mają znaczenia; ma znaczenie tylko kanał alfa lub nieprzezroczystości każdy kolor. Oto przykład.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Określanie ograniczniki gradientu maski krycia  
 W poprzednim przykładzie kolor zdefiniowaną przez system <xref:System.Windows.Media.Colors.Black%2A> jest używany jako kolor początkowy gradientu. Ponieważ wszystkie kolory w <xref:System.Windows.Media.Colors> klasy, z wyjątkiem <xref:System.Windows.Media.Colors.Transparent%2A>, są całkowicie nieprzezroczyste, może służyć do definiowania po prostu kolor początkowy maski krycia gradientu.  
  
 Dla dodatkowej kontroli nad wartości alfa podczas definiowania maski krycia, należy określić kanał alfa kolorów przy użyciu [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] notacji szesnastkowej w znaczników lub przy użyciu <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metody.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Określanie Przezroczystość koloru w "XAML"  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], możesz użyć [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji szesnastkowej określić krycie poszczególnych kolorów. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji szesnastkowej używa następującej składni:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* w poprzednim wierszu reprezentuje wartość szesnastkową dwucyfrowy używany do określenia Przezroczystość koloru. *Rr*, *gg*, i *bb* każdy reprezentuje dwucyfrowa wartość szesnastkową, można określić ilość czerwony, zielony i niebieski w kolorze. Każdy cyfra szesnastkowa może mieć wartość z zakresu od 0 – 9 lub A – F. Usługa 0 jest najmniejsza wartość, a F jest większa. Wartości alfa 00 Określa, że kolor, który jest całkowicie przezroczysty, a wartość alfa FF tworzy kolor, który jest całkowicie nieprzezroczyste.  W poniższym przykładzie szesnastkowe [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] notacji służy do określania dwóch kolorów. Pierwszy jest całkowicie nieprzezroczyste, podczas gdy druga jest całkowicie przezroczysty.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Przy użyciu obrazu jako maski krycia  
 Obrazy może również służyć jako maski nieprzezroczystości. Na poniższej ilustracji przedstawiono przykład. Tle specjalną służy do pokazywania przezroczyste obiekty maski.  
  
 ![Obiekt, za pomocą maski krycia ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Przykład maskowania krycia  
  
 Aby użyć obrazu jako maski krycia, należy użyć <xref:System.Windows.Media.ImageBrush> zawiera obraz. Po utworzeniu obrazu ma być używany jako maski krycia zapisania obrazu w formacie, który obsługuje wiele poziomów przejrzystości, takie jak [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. Poniższy przykład pokazuje kod używany do utworzenia na poprzedniej ilustracji.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Przy użyciu fragmentacji obrazu jako maski krycia  
 W poniższym przykładzie ten sam obraz jest używana z inną <xref:System.Windows.Media.ImageBrush>, ale pędzla fragmentacji funkcje są używane do tworzenia Kafelki kwadratu obraz 50 pikseli.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Tworzenie maski nieprzezroczystości z rysunku  
 Rysunki mogą być używane maski nieprzezroczystości. Kształty znajdujących się na rysunku może się zostać wypełniony przy użyciu gradientów, jednolitymi kolorami, obrazów lub nawet inne rysunki. Na poniższej ilustracji przedstawiono przykład używany jako maski krycia rysowania. Tle specjalną służy do pokazywania przezroczyste obiekty maski.  
  
 ![Obiekt, za pomocą maski krycia DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Przykład maskowania przezroczystość pędzla  
  
 Aby użyć rysowania jako maski krycia, należy użyć <xref:System.Windows.Media.DrawingBrush> zawierać rysunku. Poniższy przykład przedstawia kod używany do utworzenia na poprzedniej ilustracji:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Przy użyciu fragmentacji rysowania jako maski krycia  
 Podobnie jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> można wprowadzić do kafelka jej rysowania. W poniższym przykładzie pędzla umożliwia tworzenie maski nieprzezroczystości fragmentacji.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
