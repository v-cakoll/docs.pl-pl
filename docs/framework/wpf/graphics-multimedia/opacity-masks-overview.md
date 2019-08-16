---
title: Przegląd Masek krycia
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 76ec595b1d2cc732e1c8bc2dc2ca6def904bf94c
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545343"
---
# <a name="opacity-masks-overview"></a>Przegląd Masek krycia
Maski kryjące umożliwiają udostępnianie części elementu lub wizualizacji jako przezroczyste lub częściowo przezroczyste. Aby utworzyć maskę nieprzezroczystości, należy <xref:System.Windows.Media.Brush> zastosować <xref:System.Windows.UIElement.OpacityMask%2A> do właściwości elementu lub <xref:System.Windows.Media.Visual>.  Pędzel jest mapowany do elementu lub wizualizacji, a wartość nieprzezroczystości każdego koloru pędzla jest używana do określenia nieprzezroczystości każdego odpowiadającego piksela elementu lub wizualizacji.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W <xref:System.Windows.Media.Brush> tym omówieniu założono, że znasz już obiekty. Aby zapoznać się z wprowadzeniem do używania pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać informacje <xref:System.Windows.Media.ImageBrush> o <xref:System.Windows.Media.DrawingBrush>i, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Tworzenie efektów wizualnych przy użyciu masek nieprzezroczystości  
 Maska nieprzezroczystości działa przez mapowanie jej zawartości do elementu lub wizualizacji. Kanał alfa każdego z pikseli pędzla jest następnie używany do określenia nieprawidłowej przejrzystości elementu lub odpowiednich pikseli wizualizacji; rzeczywisty kolor pędzla jest ignorowany. Jeśli dana część pędzla jest przezroczysta, odpowiednia część elementu lub wizualizacji staną się przezroczyste. Jeśli dana część pędzla jest nieprzezroczysta, przezroczystość odpowiedniej części elementu lub wizualizacji nie jest zmieniana. Nieprzezroczystość określona przez maskę nieprzezroczystości jest łączona z wszystkimi ustawieniami nieprzezroczystości obecnymi w elemencie lub wizualizacji. Na przykład, jeśli element ma wartość 25 procent nieprzezroczystości, a maska nieprzezroczystości jest stosowana, która przechodzi z całkowitego kryjącego do pełnego przezroczystości, wynikiem jest element, który przechodzi od przezroczystości 25 procent do pełnego przezroczystości.  
  
> [!NOTE]
>  Chociaż przykłady w tym omówieniu pokazują użycie masek kryjących elementów obrazu, maska kryjąca może być stosowana do dowolnego elementu lub <xref:System.Windows.Media.Visual>, w tym paneli i kontrolki.  
  
 Maski nieprzezroczystości są używane do tworzenia interesujących efektów wizualnych, takich jak tworzenie obrazów lub przycisków, które stopniowo rozjaśniają się z widoku, dodawanie tekstury do elementów lub łączenie gradientów w celu tworzenia powierzchni przypominających. Na poniższej ilustracji przedstawiono użycie maski kryjącej. Tło z modułem sprawdzonym służy do pokazywania przezroczystych części maski.  
  
 ![Obiekt z maską nieprzezroczystości LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Przykład maski kryjącej  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Tworzenie maski kryjącej  
 Aby utworzyć maskę nieprzezroczystości, należy <xref:System.Windows.Media.Brush> ją utworzyć i zastosować <xref:System.Windows.UIElement.OpacityMask%2A> do właściwości elementu lub wizualizacji. Można użyć dowolnego typu <xref:System.Windows.Media.Brush> jako maski kryjącej.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Służy do stopniowego zanikania elementu lub wizualizacji.  
  
     Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.LinearGradientBrush> użycie maski kryjącej.  
  
     ![Obiekt z maską nieprzezroczystości LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Przykład maski nieprzezroczystości LinearGradientBrush  
  
- <xref:System.Windows.Media.ImageBrush>: Służy do tworzenia tekstury i niewygładzonych lub podartych efektów krawędzi.  
  
     Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.ImageBrush> użycie maski kryjącej.  
  
     ![Obiekt, który ma maskę nieprzezroczystość ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Przykład maski nieprzezroczystości LinearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Służy do tworzenia złożonych masek kryjących ze wzorów kształtów, obrazów i gradientów.  
  
     Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.DrawingBrush> użycie maski kryjącej.  
  
     ![Obiekt z maską nieprzezroczystości DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Przykład maski nieprzezroczystości DrawingBrush  
  
 Pędzle gradientowe<xref:System.Windows.Media.LinearGradientBrush> ( <xref:System.Windows.Media.RadialGradientBrush>i) są szczególnie odpowiednie do użycia jako maska nieprzezroczystości. Ponieważ wypełnia obszar jednolitym kolorem, sprawia, że stają się słabymi maskami kryjącymi; <xref:System.Windows.Media.SolidColorBrush> użycie jest równoważne z ustawieniem <xref:System.Windows.UIElement.OpacityMask%2A> właściwości elementu lub wizualizacji. <xref:System.Windows.Media.SolidColorBrush>  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Używanie gradientu jako maski kryjącej  
 Aby utworzyć wypełnienie gradientu, należy określić dwa lub więcej zatrzymań gradientu. Każde zatrzymanie gradientu zawiera opis koloru i położenia (zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md) , aby uzyskać więcej informacji na temat tworzenia i używania gradientów). Ten proces jest taki sam, gdy jest używany gradient jako maska nieprzezroczystości, z tą różnicą, że zamiast mieszania kolorów, Gradient maski kryjącej miesza wartości kanału alfa. Dlatego rzeczywisty kolor zawartości gradientu nie ma znaczenia; tylko kanał alfa lub nieprzezroczystość dla każdego koloru. Oto przykład.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Określanie zatrzymań gradientu dla maski nieprzezroczystości  
 W poprzednim przykładzie kolor <xref:System.Windows.Media.Colors.Black%2A> zdefiniowany przez system jest używany jako kolor początkowy gradientu. Ponieważ wszystkie kolory w <xref:System.Windows.Media.Colors> klasie, z wyjątkiem <xref:System.Windows.Media.Colors.Transparent%2A>, są całkowicie nieprzezroczyste, mogą służyć do zwykłego definiowania koloru początkowego dla maski nieprzezroczystości gradientu.  
  
 Aby uzyskać dodatkową kontrolę nad wartościami alfa przy definiowaniu maski kryjącej, można określić kanał alfa kolorów przy użyciu notacji szesnastkowej ARGB w znaczniku <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> lub przy użyciu metody.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Określanie nieprzezroczystości koloru w "XAML"  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programie używasz notacji szesnastkowej ARGB, aby określić nieprzezroczystość poszczególnych kolorów. Notacja szesnastkowa ARGB używa następującej składni:  
  
 `#`**AA** *RRGGBB*  
  
 *AA* w poprzednim wierszu reprezentuje dwucyfrową wartość szesnastkową służącą do określenia nieprzezroczystości koloru. Wartości *RR*, *gg*i *BB* reprezentują dwie cyfry szesnastkowe, używane do określania ilości czerwonego, zielonego i niebieskiego w kolorze. Każda cyfra szesnastkowa może mieć wartość z prze0-9 lub A-F. 0 jest najmniejszą wartością, a F jest największa. Wartość alfa 00 określa kolor, który jest całkowicie przezroczysty, podczas gdy wartość alfa FF tworzy kolor, który jest całkowicie nieprzezroczysty.  W poniższym przykładzie szesnastkowa notacja ARGB jest używana do określenia dwóch kolorów. Pierwszy jest całkowicie nieprzezroczysty, a drugi jest całkowicie przezroczysty.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Używanie obrazu jako maski kryjącej  
 Obrazy mogą również służyć jako maska nieprzezroczystość. Na poniższej ilustracji przedstawiono przykład. Tło z modułem sprawdzonym służy do pokazywania przezroczystych części maski.  
  
 ![Obiekt z maską nieprzezroczystości ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Przykład maski kryjącej  
  
 Aby użyć obrazu jako maski kryjącej, należy użyć <xref:System.Windows.Media.ImageBrush> , aby zawierać obraz. Podczas tworzenia obrazu, który ma być używany jako maska nieprzezroczystości, Zapisz obraz w formacie obsługującym wiele poziomów przezroczystości, takich jak Portable Network Graphics (PNG). Poniższy przykład pokazuje kod używany do tworzenia poprzedniej ilustracji.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Używanie obrazu sąsiadującego jako maski kryjącej  
 W poniższym przykładzie ten sam obraz jest używany z innym <xref:System.Windows.Media.ImageBrush>, ale funkcje dzielenia pędzla są używane do tworzenia kafelków kwadratu obrazu 50 pikseli.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Tworzenie maski kryjącej na podstawie rysunku  
 Na rysunkach można używać maski nieprzezroczystości. Kształty zawarte na rysunku mogą być wypełniane gradientem, pełnymi kolorami, obrazami, a nawet innymi rysunkami. Na poniższej ilustracji przedstawiono przykładowy rysunek używany jako maska nieprzezroczystość. Tło z modułem sprawdzonym służy do pokazywania przezroczystych części maski.  
  
 ![Obiekt z maską nieprzezroczystości DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Przykład maski nieprzezroczystości DrawingBrush  
  
 Aby użyć rysowania jako maski kryjącej, należy użyć <xref:System.Windows.Media.DrawingBrush> , aby zawierać rysunek. Poniższy przykład pokazuje kod używany do tworzenia poprzedniej ilustracji:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Korzystanie z sąsiadującego rysunku jako maski kryjącej  
 Podobnie jak <xref:System.Windows.Media.ImageBrush>w <xref:System.Windows.Media.DrawingBrush> , można narysować kafelki. W poniższym przykładzie pędzel rysowania służy do tworzenia wbudowanej maski nieprzezroczystości.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
