---
title: Grafika i multimedia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: be8dcfce44347e8099e8cfa693bcee341514de2b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291439"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="8aca4-102">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="8aca4-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
 <span data-ttu-id="8aca4-103">@ no__t-2 zapewnia obsługę multimediów, grafiki wektorowej, animacji i kompozycji zawartości, dzięki czemu deweloperzy mogą łatwo tworzyć interesujące interfejsy użytkownika i zawartość.</span><span class="sxs-lookup"><span data-stu-id="8aca4-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="8aca4-104">Za pomocą [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] można tworzyć grafiki wektorowe lub złożone animacje oraz integrować multimedia z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="8aca4-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="8aca4-105">W tym temacie przedstawiono funkcje grafiki, animacji i multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które umożliwiają dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8aca4-106">Korzystanie z typów WPF w usłudze systemu Windows jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="8aca4-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="8aca4-107">Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługa może nie zadziałała zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="8aca4-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="8aca4-108">Nowości dotyczące grafiki i multimediów w WPF 4</span><span class="sxs-lookup"><span data-stu-id="8aca4-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="8aca4-109">Wprowadzono kilka zmian dotyczących grafiki i animacji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="8aca4-110">Zaokrąglenie układu</span><span class="sxs-lookup"><span data-stu-id="8aca4-110">Layout Rounding</span></span>

  <span data-ttu-id="8aca4-111">Gdy brzeg obiektu znajduje się w środku urządzenia pikselowego, niezależny od DPI system grafiki może tworzyć artefakty renderowania, takie jak rozmyte lub częściowo przezroczyste krawędzie.</span><span class="sxs-lookup"><span data-stu-id="8aca4-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="8aca4-112">Poprzednie wersje WPF obejmowały przyciąganie pikseli do obsługi tego przypadku.</span><span class="sxs-lookup"><span data-stu-id="8aca4-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="8aca4-113">Program Silverlight 2 wprowadził zaokrąglenie układu, który jest innym sposobem przenoszenia elementów tak, aby krawędzie mieściły się w całej krawędzi pikseli.</span><span class="sxs-lookup"><span data-stu-id="8aca4-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="8aca4-114">WPF obsługuje teraz zaokrąglanie układu z właściwością dołączoną <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> w <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="8aca4-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="8aca4-115">Buforowana kompozycja</span><span class="sxs-lookup"><span data-stu-id="8aca4-115">Cached Composition</span></span>

  <span data-ttu-id="8aca4-116">Przy użyciu nowych klas <xref:System.Windows.Media.BitmapCache> i <xref:System.Windows.Media.BitmapCacheBrush> można buforować złożoną część drzewa wizualnego jako mapę bitową i znacznie poprawić czas renderowania.</span><span class="sxs-lookup"><span data-stu-id="8aca4-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="8aca4-117">Mapa bitowa pozostaje niezależna od danych wejściowych użytkownika, takich jak kliknięcia myszą i można ją malować na innych elementach, podobnie jak w przypadku dowolnego pędzla.</span><span class="sxs-lookup"><span data-stu-id="8aca4-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="8aca4-118">Obsługa programów do cieniowania pikseli 3</span><span class="sxs-lookup"><span data-stu-id="8aca4-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="8aca4-119">Program WPF 4 jest oparty na obsłudze <xref:System.Windows.Media.Effects.ShaderEffect> programu WPF 3,5 SP1, umożliwiając aplikacjom pisanie efektów przy użyciu programu Pixel Shader (PS) w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="8aca4-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="8aca4-120">Model cieniowania PS 3,0 jest bardziej zaawansowany niż PS 2,0, co pozwala na jeszcze większy wpływ na obsługiwany sprzęt.</span><span class="sxs-lookup"><span data-stu-id="8aca4-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="8aca4-121">Funkcje krzywej napięcia</span><span class="sxs-lookup"><span data-stu-id="8aca4-121">Easing Functions</span></span>

  <span data-ttu-id="8aca4-122">Możesz wzbogacić animacje za pomocą funkcji, które zapewniają dodatkową kontrolę nad zachowaniem animacji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="8aca4-123">Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby nadać animacji zachowanie sprężynowe.</span><span class="sxs-lookup"><span data-stu-id="8aca4-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="8aca4-124">Aby uzyskać więcej informacji, zobacz Typy krzywych napięcia w przestrzeni nazw <xref:System.Windows.Media.Animation>.</span><span class="sxs-lookup"><span data-stu-id="8aca4-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="8aca4-125">Grafika i renderowanie</span><span class="sxs-lookup"><span data-stu-id="8aca4-125">Graphics and Rendering</span></span>

<span data-ttu-id="8aca4-126">WPF obejmuje obsługę grafiki 2-D o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="8aca4-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="8aca4-127">Funkcje obejmują pędzle, geometrie, obrazy, kształty i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="8aca4-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="8aca4-128">Aby uzyskać więcej informacji, zobacz [grafika](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="8aca4-129">Renderowanie elementów graficznych zależy od klasy <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="8aca4-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="8aca4-130">Struktura obiektów wizualizacji na ekranie jest opisana przez drzewo wizualne.</span><span class="sxs-lookup"><span data-stu-id="8aca4-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="8aca4-131">Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="8aca4-132">Kształty 2-D</span><span class="sxs-lookup"><span data-stu-id="8aca4-132">2-D Shapes</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="8aca4-133">udostępnia bibliotekę często używanych, rysowanych w wektorach kształtów 2-D, takich jak prostokąty i wielokropek, które przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-133">provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram przedstawiający wielokropek i prostokąty.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="8aca4-135">Te kształty wewnętrzne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nie są tylko kształtami: są elementami programowalnymi, które implementują wiele funkcji, których oczekujesz od najbardziej typowych kontrolek, takich jak klawiatura i mysz.</span><span class="sxs-lookup"><span data-stu-id="8aca4-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="8aca4-136">Poniższy przykład pokazuje, jak obsłużyć zdarzenie <xref:System.Windows.UIElement.MouseUp> wywoływane przez kliknięcie elementu <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="8aca4-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

<span data-ttu-id="8aca4-137">Na poniższej ilustracji przedstawiono dane wyjściowe dla poprzedniego znacznika [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kodu.</span><span class="sxs-lookup"><span data-stu-id="8aca4-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno komunikatu z informacją "kliknięto elipsę!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="8aca4-139">Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="8aca4-140">Aby zapoznać się z przykładem wstępnym, zobacz [element Shape Samples](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="8aca4-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="8aca4-141">Geometrie 2-D</span><span class="sxs-lookup"><span data-stu-id="8aca4-141">2-D Geometries</span></span>

<span data-ttu-id="8aca4-142">Gdy kształty 2-D zawierające [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] są niewystarczające, można użyć obsługi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dla geometrie i ścieżek, aby utworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="8aca4-142">When the 2-D shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="8aca4-143">Na poniższej ilustracji przedstawiono, jak można użyć geometrie do tworzenia kształtów, jako pędzla rysowania i obcinania innych elementów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8aca4-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>

![Zrzut ekranu przedstawiający sposób tworzenia kształtów za pomocą geometrie.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="8aca4-145">Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="8aca4-146">Aby zapoznać się z przykładem wstępnym, zobacz [przykład geometrie](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="8aca4-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="8aca4-147">Efekty 2-D</span><span class="sxs-lookup"><span data-stu-id="8aca4-147">2-D Effects</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="8aca4-148">udostępnia bibliotekę klas 2-D, których można użyć do tworzenia rozmaitych efektów.</span><span class="sxs-lookup"><span data-stu-id="8aca4-148">provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="8aca4-149">Funkcja renderowania 2-D [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia malowanie elementów [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które mają gradienty, mapy bitowe, rysunki i wideo. i do manipulowania nimi przy użyciu rotacji, skalowania i skośności.</span><span class="sxs-lookup"><span data-stu-id="8aca4-149">The 2-D rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="8aca4-150">Na poniższej ilustracji przedstawiono przykład wielu efektów, które można osiągnąć przy użyciu pędzli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8aca4-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>

![Ilustracja przedstawiająca różne pędzle WPF i elementy programu Paint.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="8aca4-152">Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="8aca4-153">Aby zapoznać się z przykładem wstępnym, zobacz [przykłady pędzli](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="8aca4-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="8aca4-154">Renderowanie 3-D</span><span class="sxs-lookup"><span data-stu-id="8aca4-154">3-D Rendering</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="8aca4-155">udostępnia zestaw funkcji renderowania trójwymiarowego, które integrują się z obsługą grafiki 2-D w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], aby można było tworzyć bardziej atrakcyjne funkcje układu, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i wizualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="8aca4-155">provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="8aca4-156">Na jednym końcu spektrum [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia renderowanie obrazów 2-D na powierzchni trójwymiarowych kształtów, które przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![Zrzut ekranu przedstawiający przykład pokazujący kształty trójwymiarowe z różnymi teksturami.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="8aca4-158">Aby uzyskać więcej informacji, zobacz temat [Omówienie grafiki trójwymiarowej](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="8aca4-159">Aby zapoznać się z przykładem wstępnym, zobacz [3-D pełne próbki](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="8aca4-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="8aca4-160">Odtwarzania</span><span class="sxs-lookup"><span data-stu-id="8aca4-160">Animation</span></span>

<span data-ttu-id="8aca4-161">Używaj animacji, aby tworzyć, wstrząsać, obracać i przerastać elementy. i aby tworzyć interesujące przejścia stron i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="8aca4-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="8aca4-162">Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pozwala animować większość właściwości, nie tylko można animować większość obiektów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można także użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do animowania tworzonych obiektów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="8aca4-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>

![Zrzut ekranu animowanego modułu.](./media/index/animate-custom-objects.png)

<span data-ttu-id="8aca4-164">Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="8aca4-165">Aby zapoznać się z przykładem wstępnym, zobacz [Galeria przykładów animacji](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="8aca4-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="8aca4-166">Multimedia</span><span class="sxs-lookup"><span data-stu-id="8aca4-166">Media</span></span>

<span data-ttu-id="8aca4-167">Obrazy, wideo i audio to bogate w multimedia sposoby przekazywania informacji i środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8aca4-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="8aca4-168">Obrazy</span><span class="sxs-lookup"><span data-stu-id="8aca4-168">Images</span></span>

<span data-ttu-id="8aca4-169">Obrazy, takie jak ikony, tła i nawet części animacji, są podstawową częścią większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="8aca4-170">Ze względu na to, że często trzeba używać obrazów, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uwidacznia możliwość pracy z nimi na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="8aca4-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="8aca4-171">Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.</span><span class="sxs-lookup"><span data-stu-id="8aca4-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="8aca4-172">![Przykładowy StylingIntro_EventTriggers zrzutu ekranu](../controls/./media/stylingintro-eventtriggers.png "")</span><span class="sxs-lookup"><span data-stu-id="8aca4-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="8aca4-173">Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="8aca4-174">Wideo i audio</span><span class="sxs-lookup"><span data-stu-id="8aca4-174">Video and Audio</span></span>

<span data-ttu-id="8aca4-175">Podstawową funkcją możliwości grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest zapewnienie natywnej obsługi pracy z multimediami, w tym wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="8aca4-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="8aca4-176">Poniższy przykład pokazuje, jak wstawić odtwarzacz multimedialny do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8aca4-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="8aca4-177"><xref:System.Windows.Controls.MediaElement> jest w stanie odtwarzać wideo i audio, i jest wystarczająco rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8aca4-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="8aca4-178">Aby uzyskać więcej informacji, zobacz [Omówienie multimediów](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8aca4-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8aca4-179">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aca4-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="8aca4-180">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="8aca4-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="8aca4-181">Kształty i podstawowe Rysowanie w WPF — Omówienie</span><span class="sxs-lookup"><span data-stu-id="8aca4-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="8aca4-182">Malowanie przy użyciu pełnych kolorów i gradientów — Omówienie</span><span class="sxs-lookup"><span data-stu-id="8aca4-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="8aca4-183">Malowanie przy użyciu obrazów, rysunków i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="8aca4-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="8aca4-184">Animacja i chronometraż — Tematy porad</span><span class="sxs-lookup"><span data-stu-id="8aca4-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="8aca4-185">Grafika trójwymiarowa — Omówienie</span><span class="sxs-lookup"><span data-stu-id="8aca4-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="8aca4-186">Omówienie multimediów</span><span class="sxs-lookup"><span data-stu-id="8aca4-186">Multimedia Overview</span></span>](multimedia-overview.md)
