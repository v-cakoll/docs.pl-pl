---
title: Przegląd Masek krycia
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 0c859659c35e2a5806b8585214c87c18fbcb62d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187687"
---
# <a name="opacity-masks-overview"></a>Przegląd Masek krycia
Maski krycia umożliwiają tworzenie części elementu lub wizualizacji przezroczystych lub częściowo przezroczystych. Aby utworzyć maskę krycia, <xref:System.Windows.Media.Brush> należy <xref:System.Windows.UIElement.OpacityMask%2A> zastosować a do <xref:System.Windows.Media.Visual>właściwości elementu lub .  Pędzel jest mapowany na element lub wizualizację, a wartość krycia każdego piksela pędzla jest używana do określenia wynikowego krycia każdego odpowiedniego piksela elementu lub wizualizacji.  
  
<a name="prereqs"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przeglądzie przyjęto <xref:System.Windows.Media.Brush> założenie, że użytkownik jest zaznajomiony z obiektami. Aby zapoznać się z wprowadzeniem do używania pędzli, zobacz [Omówienie malowania za pomocą jednolitych kolorów i gradientów](painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>informacje na temat i , zobacz [Malowanie za pomocą obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>
## <a name="creating-visual-effects-with-opacity-masks"></a>Tworzenie efektów wizualnych za pomocą masek krycia  
 Maska krycia działa poprzez mapowanie jego zawartości do elementu lub wizualizacji. Kanał alfa każdego z pikseli pędzla są następnie używane do określenia wynikowej krycia elementu lub wizualnych odpowiednich pikseli; rzeczywisty kolor pędzla jest ignorowany. Jeśli dana część pędzla jest przezroczysta, odpowiednia część elementu lub wizualizacji staje się przezroczysta. Jeśli dana część pędzla jest nieprzezroczysta, nieprzezroczystość odpowiedniej części elementu lub wizualizacji pozostaje niezmieniona. Krycie określone przez maskę krycia jest łączone z dowolnymi ustawieniami krycia obecnymi w elemencie lub wizualizacji. Na przykład jeśli element jest 25 procent nieprzezroczyste i maska krycia jest stosowana, że przejścia z całkowicie nieprzezroczyste do w pełni przezroczyste, wynik jest elementem, który przechodzi z 25 procent krycia do w pełni przezroczyste.  
  
> [!NOTE]
> Chociaż przykłady w tym przeglądzie pokazują użycie masek krycia na elementach obrazu, maska <xref:System.Windows.Media.Visual>krycia może być stosowana do dowolnego elementu lub , w tym paneli i formantów.  
  
 Maski krycia służą do tworzenia interesujących efektów wizualnych, takich jak tworzenie obrazów lub przycisków, które zanikają z widoku, dodawanie tekstur do elementów lub łączenie gradientów w celu wytworzenia powierzchni przypominających szkło. Na poniższej ilustracji przedstawiono użycie maski krycia. Tło w szachowane służy do pokazywalenia przezroczystych części maski.  
  
 ![Obiekt z maską krycia lineargradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Przykład maskowania krycia  
  
<a name="creatingopacitymasks"></a>
## <a name="creating-an-opacity-mask"></a>Tworzenie maski krycia  
 Aby utworzyć maskę krycia, <xref:System.Windows.Media.Brush> należy utworzyć ją <xref:System.Windows.UIElement.OpacityMask%2A> i zastosować do właściwości elementu lub wizualizacji. Można użyć dowolnego <xref:System.Windows.Media.Brush> typu jako maski krycia.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Służy do tworzenia elementu lub wizualnego zanikania z widoku.  
  
     Na poniższej <xref:System.Windows.Media.LinearGradientBrush> ilustracji przedstawiono maskę krycia używanego jako maskę krycia.  
  
     ![Obiekt z maską krycia lineargradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Przykład maskowania krycia liniowego pędzla  
  
- <xref:System.Windows.Media.ImageBrush>: Służy do tworzenia tekstur i miękkich lub rozdartych efektów krawędzi.  
  
     Na poniższej <xref:System.Windows.Media.ImageBrush> ilustracji przedstawiono maskę krycia używanego jako maskę krycia.  
  
     ![Obiekt z maską krycia ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Przykład maskowania krycia linearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Służy do tworzenia złożonych masek krycia z wzorów kształtów, obrazów i gradientów.  
  
     Na poniższej <xref:System.Windows.Media.DrawingBrush> ilustracji przedstawiono maskę krycia używanego jako maskę krycia.  
  
     ![Obiekt z maską pędzla drawingbrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Przykład maskowania krycia pędzla drawingBrush  
  
 Szczotki gradientowe<xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>( i ) są szczególnie dobrze nadaje się do stosowania jako maska krycia. Ponieważ <xref:System.Windows.Media.SolidColorBrush> obszar wypełnia jednolitym kolorem, robią słabe maski krycia; przy <xref:System.Windows.Media.SolidColorBrush> użyciu a jest odpowiednikiem ustawienia elementu <xref:System.Windows.UIElement.OpacityMask%2A> lub właściwości wizualnej.  
  
<a name="creatingopacitymaskswithgradients"></a>
## <a name="using-a-gradient-as-an-opacity-mask"></a>Używanie gradientu jako maski krycia  
 Aby utworzyć wypełnienie gradientowe, należy określić co najmniej dwa przystanki gradientu. Każdy przystanek gradientu zawiera opisuje kolor i położenie (zobacz [Malowanie za pomocą jednolitych kolorów i gradientów Omówienie, aby](painting-with-solid-colors-and-gradients-overview.md) uzyskać więcej informacji na temat tworzenia i używania gradientów). Proces jest taki sam, gdy używa się gradientu jako maski krycia, z tą różnicą, że zamiast mieszania kolorów gradient maski krycia miesza wartości kanałów alfa. Tak więc rzeczywisty kolor zawartości gradientu nie ma znaczenia; tylko kanał alfa lub krycie każdego koloru ma znaczenie. Poniżej przedstawiono przykład.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Określanie przystanków gradientu dla maski krycia  
 W poprzednim przykładzie kolor <xref:System.Windows.Media.Colors.Black%2A> zdefiniowany przez system jest używany jako kolor początkowy gradientu. Ponieważ wszystkie kolory w <xref:System.Windows.Media.Colors> klasie, <xref:System.Windows.Media.Colors.Transparent%2A>z wyjątkiem , są całkowicie nieprzezroczyste, mogą być używane po prostu zdefiniować kolor początkowy dla maski krycia gradientu.  
  
 Aby uzyskać dodatkową kontrolę nad wartościami alfa podczas definiowania maski krycia, można określić kanał alfa kolorów za <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> pomocą notacji szesnastkowej ARGB w znacznikach lub przy użyciu metody.  
  
<a name="argbsyntax"></a>
### <a name="specifying-color-opacity-in-xaml"></a>Określanie krycia kolorów w "XAML"  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]obszarze , należy użyć notacji szesnastkowej ARGB, aby określić krycie poszczególnych kolorów. Notacja szesnastkowa ARGB używa następującej składni:  
  
 `#`**aa** *rrggbb*  
  
 *Aa* w poprzednim wierszu reprezentuje dwucyfrową wartość szesnastową używaną do określenia krycia koloru. *Rr*, *gg*i *bb* reprezentują dwucyfrową wartość szesnastkową używaną do określenia ilości koloru czerwonego, zielonego i niebieskiego. Każda cyfra szesnastkowa może mieć wartość od 0-9 lub A-F. 0 jest najmniejszą wartością, a F jest największa. Wartość alfa 00 określa kolor, który jest całkowicie przezroczysty, podczas gdy wartość alfa FF tworzy kolor, który jest całkowicie nieprzezroczysty.  W poniższym przykładzie szesnastkowy notacja ARGB jest używana do określenia dwóch kolorów. Pierwszy jest całkowicie nieprzezroczysty, a drugi jest całkowicie przezroczysty.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>
## <a name="using-an-image-as-an-opacity-mask"></a>Używanie obrazu jako maski krycia  
 Obrazy mogą być również używane jako maska krycia. Na poniższej ilustracji przedstawiono przykładowy raport. Tło w szachowane służy do pokazywalenia przezroczystych części maski.  
  
 ![Obiekt z maską krycia ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Przykład maskowania krycia  
  
 Aby użyć obrazu jako maski krycia, użyj obrazu, <xref:System.Windows.Media.ImageBrush> aby go zawierać. Podczas tworzenia obrazu, który ma być używany jako maska krycia, zapisz obraz w formacie obsługującym wiele poziomów przezroczystości, takich jak przenośna grafika sieciowa (PNG). W poniższym przykładzie przedstawiono kod używany do tworzenia poprzedniej ilustracji.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Używanie obrazu sąsiadującego jako maski krycia  
 W poniższym przykładzie ten sam <xref:System.Windows.Media.ImageBrush>obraz jest używany z innym , ale funkcje kafli pędzla są używane do tworzenia kafelków obrazu 50 pikseli kwadratowych.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Tworzenie maski krycia z rysunku  
 Rysunki mogą być używane maską krycia. Kształty zawarte w rysunku mogą być wypełnione gradientami, jednolitymi kolorami, obrazami, a nawet innymi rysunkami. Na poniższej ilustracji przedstawiono przykład rysunku używanego jako maska krycia. Tło w szachowane służy do pokazywalenia przezroczystych części maski.  
  
 ![Obiekt z maską krycia DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Przykład maskowania krycia pędzla drawingBrush  
  
 Aby użyć rysunku jako maski krycia, użyj a, <xref:System.Windows.Media.DrawingBrush> aby zawierać rysunek. Poniższy przykład przedstawia kod używany do tworzenia poprzedniej ilustracji:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Używanie rysunku sąsiadującego jako maski krycia  
 Podobnie <xref:System.Windows.Media.ImageBrush>jak <xref:System.Windows.Media.DrawingBrush> , można zrobić, aby płytki jego rysunek. W poniższym przykładzie pędzel rysunku jest używany do tworzenia kafelkowej maski krycia.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Zobacz też

- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
