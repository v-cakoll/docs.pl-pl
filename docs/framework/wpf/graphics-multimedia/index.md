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
ms.openlocfilehash: ecc54ad9453343f6306b0133fa180abd0db46f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596425"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="3786e-102">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="3786e-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="3786e-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia obsługę multimediów, grafiki wektorowej, animacji i kompozycji zawartości, dzięki czemu deweloperzy mogą łatwo tworzyć interesujące interfejsy użytkownika i zawartość.</span><span class="sxs-lookup"><span data-stu-id="3786e-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="3786e-104">Za pomocą programu Visual Studio można tworzyć grafiki wektorowe lub złożone animacje oraz integrować multimedia z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="3786e-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="3786e-105">W tym temacie przedstawiono funkcje grafiki, animacji i multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które umożliwiają dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3786e-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="3786e-106">Korzystanie z typów WPF w usłudze systemu Windows jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="3786e-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="3786e-107">Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługa może nie zadziałała zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="3786e-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="3786e-108">Nowości dotyczące grafiki i multimediów w WPF 4</span><span class="sxs-lookup"><span data-stu-id="3786e-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="3786e-109">Wprowadzono kilka zmian dotyczących grafiki i animacji.</span><span class="sxs-lookup"><span data-stu-id="3786e-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="3786e-110">Zaokrąglenie układu</span><span class="sxs-lookup"><span data-stu-id="3786e-110">Layout Rounding</span></span>

  <span data-ttu-id="3786e-111">Gdy brzeg obiektu znajduje się w środku urządzenia pikselowego, niezależny od DPI system grafiki może tworzyć artefakty renderowania, takie jak rozmyte lub częściowo przezroczyste krawędzie.</span><span class="sxs-lookup"><span data-stu-id="3786e-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="3786e-112">Poprzednie wersje WPF obejmowały przyciąganie pikseli do obsługi tego przypadku.</span><span class="sxs-lookup"><span data-stu-id="3786e-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="3786e-113">Program Silverlight 2 wprowadził zaokrąglenie układu, który jest innym sposobem przenoszenia elementów tak, aby krawędzie mieściły się w całej krawędzi pikseli.</span><span class="sxs-lookup"><span data-stu-id="3786e-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="3786e-114">WPF obsługuje teraz zaokrąglanie układu z <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> dołączoną właściwością w <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="3786e-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="3786e-115">Buforowana kompozycja</span><span class="sxs-lookup"><span data-stu-id="3786e-115">Cached Composition</span></span>

  <span data-ttu-id="3786e-116">Za pomocą nowych <xref:System.Windows.Media.BitmapCache> klas i <xref:System.Windows.Media.BitmapCacheBrush> można buforować złożoną część drzewa wizualnego jako mapę bitową i znacznie poprawić czas renderowania.</span><span class="sxs-lookup"><span data-stu-id="3786e-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="3786e-117">Mapa bitowa pozostaje niezależna od danych wejściowych użytkownika, takich jak kliknięcia myszą i można ją malować na innych elementach, podobnie jak w przypadku dowolnego pędzla.</span><span class="sxs-lookup"><span data-stu-id="3786e-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="3786e-118">Obsługa programów do cieniowania pikseli 3</span><span class="sxs-lookup"><span data-stu-id="3786e-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="3786e-119">Program WPF 4 jest oparty na <xref:System.Windows.Media.Effects.ShaderEffect> pomocy technicznej wprowadzonej w wpf 3,5 SP1 przez umożliwienie aplikacjom zapisywania efektów przy użyciu programu Pixel Shader (PS) w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="3786e-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="3786e-120">Model cieniowania PS 3,0 jest bardziej zaawansowany niż PS 2,0, co pozwala na jeszcze większy wpływ na obsługiwany sprzęt.</span><span class="sxs-lookup"><span data-stu-id="3786e-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="3786e-121">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="3786e-121">Easing Functions</span></span>

  <span data-ttu-id="3786e-122">Możesz wzbogacić animacje za pomocą funkcji, które zapewniają dodatkową kontrolę nad zachowaniem animacji.</span><span class="sxs-lookup"><span data-stu-id="3786e-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="3786e-123">Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby nadać animacji zachowanie sprężynowe.</span><span class="sxs-lookup"><span data-stu-id="3786e-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="3786e-124">Aby uzyskać więcej informacji, zobacz Typy krzywych napięcia w <xref:System.Windows.Media.Animation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3786e-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="3786e-125">Grafika i renderowanie</span><span class="sxs-lookup"><span data-stu-id="3786e-125">Graphics and Rendering</span></span>

<span data-ttu-id="3786e-126">WPF obejmuje obsługę grafiki 2D o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="3786e-126">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="3786e-127">Funkcje obejmują pędzle, geometrie, obrazy, kształty i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="3786e-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="3786e-128">Aby uzyskać więcej informacji, zobacz [grafika](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="3786e-129">Renderowanie elementów graficznych jest oparte na <xref:System.Windows.Media.Visual> klasie.</span><span class="sxs-lookup"><span data-stu-id="3786e-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="3786e-130">Struktura obiektów wizualizacji na ekranie jest opisana przez drzewo wizualne.</span><span class="sxs-lookup"><span data-stu-id="3786e-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="3786e-131">Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="3786e-132">Kształty 2D</span><span class="sxs-lookup"><span data-stu-id="3786e-132">2D Shapes</span></span>

<span data-ttu-id="3786e-133">WPF udostępnia bibliotekę często używanych, rysowanych w wektorach kształtów 2D, takich jak prostokąty i wielokropek, które przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="3786e-133">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram przedstawiający wielokropek i prostokąty.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="3786e-135">Te Wewnętrzne kształty WPF nie są tylko kształtami: są to elementy programowalne, które implementują wiele funkcji oczekiwanych od najbardziej typowych kontrolek, takich jak klawiatura i mysz.</span><span class="sxs-lookup"><span data-stu-id="3786e-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="3786e-136">Poniższy przykład pokazuje, jak obsłużyć <xref:System.Windows.UIElement.MouseUp> zdarzenie wywoływane przez kliknięcie <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="3786e-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="3786e-137">Na poniższej ilustracji przedstawiono dane wyjściowe dla poprzedzającego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika i kodu.</span><span class="sxs-lookup"><span data-stu-id="3786e-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno komunikatu z informacją "kliknięto elipsę!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="3786e-139">Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="3786e-140">Aby zapoznać się z przykładem wstępnym, zobacz [element Shape Samples](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="3786e-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="3786e-141">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="3786e-141">2D Geometries</span></span>

<span data-ttu-id="3786e-142">Gdy kształty 2D udostępniane przez program WPF nie są wystarczające, można użyć obsługi platformy WPF dla geometrie i ścieżek, aby utworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="3786e-142">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="3786e-143">Na poniższej ilustracji przedstawiono, jak można użyć geometrie do tworzenia kształtów, jako pędzla rysowania i obcinania innych elementów WPF.</span><span class="sxs-lookup"><span data-stu-id="3786e-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Zrzut ekranu przedstawiający sposób tworzenia kształtów za pomocą geometrie.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="3786e-145">Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="3786e-146">Aby zapoznać się z przykładem wstępnym, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="3786e-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="3786e-147">Efekty 2D</span><span class="sxs-lookup"><span data-stu-id="3786e-147">2D Effects</span></span>

<span data-ttu-id="3786e-148">WPF udostępnia bibliotekę klas 2D, których można użyć do tworzenia rozmaitych efektów.</span><span class="sxs-lookup"><span data-stu-id="3786e-148">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="3786e-149">Funkcja renderowania 2D platformy WPF umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów, które mają gradienty, mapy bitowe, rysunki i wideo, a także manipulowanie nimi przy użyciu rotacji, skalowania i skośności.</span><span class="sxs-lookup"><span data-stu-id="3786e-149">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="3786e-150">Na poniższej ilustracji przedstawiono przykład wielu efektów, które można osiągnąć przy użyciu pędzli WPF.</span><span class="sxs-lookup"><span data-stu-id="3786e-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Ilustracja przedstawiająca różne pędzle WPF i elementy programu Paint.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="3786e-152">Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="3786e-153">Aby zapoznać się z przykładem wstępnym, zobacz [przykłady pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="3786e-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="3786e-154">Renderowanie 3W</span><span class="sxs-lookup"><span data-stu-id="3786e-154">3D Rendering</span></span>

<span data-ttu-id="3786e-155">WPF oferuje zestaw funkcji renderowania 3W, które integrują się z obsługą grafiki 2D w programie WPF w celu tworzenia bardziej atrakcyjnego układu, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i wizualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="3786e-155">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="3786e-156">Na jednym końcu spektrum WPF umożliwia renderowanie obrazów 2D na powierzchni kształtów 3W, które przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="3786e-156">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Zrzut ekranu przedstawiający przykład pokazujący kształty 3W z różnymi teksturami.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="3786e-158">Aby uzyskać więcej informacji, zobacz [grafika 3D — Omówienie](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-158">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="3786e-159">Aby uzyskać próbę wstępną, zobacz [przykład pełnych 3W](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="3786e-159">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="3786e-160">Animacja</span><span class="sxs-lookup"><span data-stu-id="3786e-160">Animation</span></span>

<span data-ttu-id="3786e-161">Używaj animacji, aby tworzyć, wstrząsać, obracać i przerastać elementy. i aby tworzyć interesujące przejścia stron i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="3786e-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="3786e-162">Ponieważ WPF pozwala animować większość właściwości, nie tylko można animować większość obiektów WPF, można również użyć WPF do animowania tworzonych obiektów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3786e-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Zrzut ekranu animowanego modułu.](./media/index/animate-custom-objects.png)

<span data-ttu-id="3786e-164">Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="3786e-165">Aby zapoznać się z przykładem wstępnym, zobacz [Galeria przykładów animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="3786e-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="3786e-166">Multimedia</span><span class="sxs-lookup"><span data-stu-id="3786e-166">Media</span></span>

<span data-ttu-id="3786e-167">Obrazy, wideo i audio to bogate w multimedia sposoby przekazywania informacji i środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3786e-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="3786e-168">Obrazy</span><span class="sxs-lookup"><span data-stu-id="3786e-168">Images</span></span>

<span data-ttu-id="3786e-169">Obrazy, takie jak ikony, tła i nawet części animacji, są podstawową częścią większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3786e-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="3786e-170">Ze względu na to, że często trzeba używać obrazów, WPF udostępnia możliwość pracy z nimi na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="3786e-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="3786e-171">Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.</span><span class="sxs-lookup"><span data-stu-id="3786e-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="3786e-172">![Przykładowy zrzut ekranu z stylem](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="3786e-172">![Styling sample screenshot](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="3786e-173">Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="3786e-174">Wideo i audio</span><span class="sxs-lookup"><span data-stu-id="3786e-174">Video and Audio</span></span>

<span data-ttu-id="3786e-175">Podstawową funkcją funkcji graficznych platformy WPF jest zapewnienie natywnej obsługi pracy z multimediami, w tym wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="3786e-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="3786e-176">Poniższy przykład pokazuje, jak wstawić odtwarzacz multimedialny do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3786e-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="3786e-177"><xref:System.Windows.Controls.MediaElement>jest w stanie odtwarzać wideo i dźwięk, i jest wystarczająco rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3786e-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="3786e-178">Aby uzyskać więcej informacji, zobacz [Omówienie multimediów](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3786e-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3786e-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3786e-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="3786e-180">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="3786e-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="3786e-181">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="3786e-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="3786e-182">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="3786e-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="3786e-183">Malowanie obrazami, rysowaniem i Visual</span><span class="sxs-lookup"><span data-stu-id="3786e-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="3786e-184">Animacja i chronometraż Tematy porad</span><span class="sxs-lookup"><span data-stu-id="3786e-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="3786e-185">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="3786e-185">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="3786e-186">Przegląd Multimedia</span><span class="sxs-lookup"><span data-stu-id="3786e-186">Multimedia Overview</span></span>](multimedia-overview.md)
