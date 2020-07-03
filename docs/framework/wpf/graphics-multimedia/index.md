---
title: Grafika i multimedia
description: Odkryj funkcje multimedialne Windows Presentation Foundation (WPF). Dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.
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
ms.openlocfilehash: ba52e78564484f7714ab0035a5e1861766b72bbf
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853675"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="16fab-104">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="16fab-104">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="16fab-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia obsługę multimediów, grafiki wektorowej, animacji i kompozycji zawartości, dzięki czemu deweloperzy mogą łatwo tworzyć interesujące interfejsy użytkownika i zawartość.</span><span class="sxs-lookup"><span data-stu-id="16fab-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="16fab-106">Za pomocą programu Visual Studio można tworzyć grafiki wektorowe lub złożone animacje oraz integrować multimedia z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="16fab-106">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="16fab-107">W tym temacie przedstawiono funkcje grafiki, animacji i multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które umożliwiają dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16fab-107">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="16fab-108">Korzystanie z typów WPF w usłudze systemu Windows jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="16fab-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="16fab-109">Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługa może nie zadziałała zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="16fab-109">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="16fab-110">Nowości dotyczące grafiki i multimediów w WPF 4</span><span class="sxs-lookup"><span data-stu-id="16fab-110">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="16fab-111">Wprowadzono kilka zmian dotyczących grafiki i animacji.</span><span class="sxs-lookup"><span data-stu-id="16fab-111">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="16fab-112">Zaokrąglenie układu</span><span class="sxs-lookup"><span data-stu-id="16fab-112">Layout Rounding</span></span>

  <span data-ttu-id="16fab-113">Gdy brzeg obiektu znajduje się w środku urządzenia pikselowego, niezależny od DPI system grafiki może tworzyć artefakty renderowania, takie jak rozmyte lub częściowo przezroczyste krawędzie.</span><span class="sxs-lookup"><span data-stu-id="16fab-113">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="16fab-114">Poprzednie wersje WPF obejmowały przyciąganie pikseli do obsługi tego przypadku.</span><span class="sxs-lookup"><span data-stu-id="16fab-114">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="16fab-115">Program Silverlight 2 wprowadził zaokrąglenie układu, który jest innym sposobem przenoszenia elementów tak, aby krawędzie mieściły się w całej krawędzi pikseli.</span><span class="sxs-lookup"><span data-stu-id="16fab-115">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="16fab-116">WPF obsługuje teraz zaokrąglanie układu z <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> dołączoną właściwością w <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="16fab-116">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="16fab-117">Buforowana kompozycja</span><span class="sxs-lookup"><span data-stu-id="16fab-117">Cached Composition</span></span>

  <span data-ttu-id="16fab-118">Za pomocą nowych <xref:System.Windows.Media.BitmapCache> klas i <xref:System.Windows.Media.BitmapCacheBrush> można buforować złożoną część drzewa wizualnego jako mapę bitową i znacznie poprawić czas renderowania.</span><span class="sxs-lookup"><span data-stu-id="16fab-118">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="16fab-119">Mapa bitowa pozostaje niezależna od danych wejściowych użytkownika, takich jak kliknięcia myszą i można ją malować na innych elementach, podobnie jak w przypadku dowolnego pędzla.</span><span class="sxs-lookup"><span data-stu-id="16fab-119">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="16fab-120">Obsługa programów do cieniowania pikseli 3</span><span class="sxs-lookup"><span data-stu-id="16fab-120">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="16fab-121">Program WPF 4 jest oparty na <xref:System.Windows.Media.Effects.ShaderEffect> pomocy technicznej wprowadzonej w wpf 3,5 SP1 przez umożliwienie aplikacjom zapisywania efektów przy użyciu programu Pixel Shader (PS) w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="16fab-121">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="16fab-122">Model cieniowania PS 3,0 jest bardziej zaawansowany niż PS 2,0, co pozwala na jeszcze większy wpływ na obsługiwany sprzęt.</span><span class="sxs-lookup"><span data-stu-id="16fab-122">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="16fab-123">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="16fab-123">Easing Functions</span></span>

  <span data-ttu-id="16fab-124">Możesz wzbogacić animacje za pomocą funkcji, które zapewniają dodatkową kontrolę nad zachowaniem animacji.</span><span class="sxs-lookup"><span data-stu-id="16fab-124">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="16fab-125">Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby nadać animacji zachowanie sprężynowe.</span><span class="sxs-lookup"><span data-stu-id="16fab-125">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="16fab-126">Aby uzyskać więcej informacji, zobacz Typy krzywych napięcia w <xref:System.Windows.Media.Animation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="16fab-126">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="16fab-127">Grafika i renderowanie</span><span class="sxs-lookup"><span data-stu-id="16fab-127">Graphics and Rendering</span></span>

<span data-ttu-id="16fab-128">WPF obejmuje obsługę grafiki 2D o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="16fab-128">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="16fab-129">Funkcje obejmują pędzle, geometrie, obrazy, kształty i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="16fab-129">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="16fab-130">Aby uzyskać więcej informacji, zobacz [grafika](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-130">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="16fab-131">Renderowanie elementów graficznych jest oparte na <xref:System.Windows.Media.Visual> klasie.</span><span class="sxs-lookup"><span data-stu-id="16fab-131">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="16fab-132">Struktura obiektów wizualizacji na ekranie jest opisana przez drzewo wizualne.</span><span class="sxs-lookup"><span data-stu-id="16fab-132">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="16fab-133">Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-133">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="16fab-134">Kształty 2D</span><span class="sxs-lookup"><span data-stu-id="16fab-134">2D Shapes</span></span>

<span data-ttu-id="16fab-135">WPF udostępnia bibliotekę często używanych, rysowanych w wektorach kształtów 2D, takich jak prostokąty i wielokropek, które przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="16fab-135">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram przedstawiający wielokropek i prostokąty.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="16fab-137">Te Wewnętrzne kształty WPF nie są tylko kształtami: są to elementy programowalne, które implementują wiele funkcji oczekiwanych od najbardziej typowych kontrolek, takich jak klawiatura i mysz.</span><span class="sxs-lookup"><span data-stu-id="16fab-137">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="16fab-138">Poniższy przykład pokazuje, jak obsłużyć <xref:System.Windows.UIElement.MouseUp> zdarzenie wywoływane przez kliknięcie <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="16fab-138">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="16fab-139">Na poniższej ilustracji przedstawiono dane wyjściowe dla poprzedzającego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika i kodu.</span><span class="sxs-lookup"><span data-stu-id="16fab-139">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno komunikatu z informacją "kliknięto elipsę!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="16fab-141">Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-141">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="16fab-142">Aby zapoznać się z przykładem wstępnym, zobacz [element Shape Samples](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="16fab-142">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="16fab-143">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="16fab-143">2D Geometries</span></span>

<span data-ttu-id="16fab-144">Gdy kształty 2D udostępniane przez program WPF nie są wystarczające, można użyć obsługi platformy WPF dla geometrie i ścieżek, aby utworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="16fab-144">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="16fab-145">Na poniższej ilustracji przedstawiono, jak można użyć geometrie do tworzenia kształtów, jako pędzla rysowania i obcinania innych elementów WPF.</span><span class="sxs-lookup"><span data-stu-id="16fab-145">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Zrzut ekranu przedstawiający sposób tworzenia kształtów za pomocą geometrie.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="16fab-147">Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-147">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="16fab-148">Aby zapoznać się z przykładem wstępnym, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="16fab-148">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="16fab-149">Efekty 2D</span><span class="sxs-lookup"><span data-stu-id="16fab-149">2D Effects</span></span>

<span data-ttu-id="16fab-150">WPF udostępnia bibliotekę klas 2D, których można użyć do tworzenia rozmaitych efektów.</span><span class="sxs-lookup"><span data-stu-id="16fab-150">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="16fab-151">Funkcja renderowania 2D platformy WPF umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów, które mają gradienty, mapy bitowe, rysunki i wideo, a także manipulowanie nimi przy użyciu rotacji, skalowania i skośności.</span><span class="sxs-lookup"><span data-stu-id="16fab-151">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="16fab-152">Na poniższej ilustracji przedstawiono przykład wielu efektów, które można osiągnąć przy użyciu pędzli WPF.</span><span class="sxs-lookup"><span data-stu-id="16fab-152">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Ilustracja przedstawiająca różne pędzle WPF i elementy programu Paint.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="16fab-154">Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-154">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="16fab-155">Aby zapoznać się z przykładem wstępnym, zobacz [przykłady pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="16fab-155">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="16fab-156">Renderowanie 3W</span><span class="sxs-lookup"><span data-stu-id="16fab-156">3D Rendering</span></span>

<span data-ttu-id="16fab-157">WPF oferuje zestaw funkcji renderowania 3W, które integrują się z obsługą grafiki 2D w programie WPF w celu tworzenia bardziej atrakcyjnego układu, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i wizualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="16fab-157">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="16fab-158">Na jednym końcu spektrum WPF umożliwia renderowanie obrazów 2D na powierzchni kształtów 3W, które przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="16fab-158">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Zrzut ekranu przedstawiający przykład pokazujący kształty 3W z różnymi teksturami.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="16fab-160">Aby uzyskać więcej informacji, zobacz [grafika 3D — Omówienie](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-160">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="16fab-161">Aby uzyskać próbę wstępną, zobacz [przykład pełnych 3W](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="16fab-161">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="16fab-162">Animacja</span><span class="sxs-lookup"><span data-stu-id="16fab-162">Animation</span></span>

<span data-ttu-id="16fab-163">Używaj animacji, aby tworzyć, wstrząsać, obracać i przerastać elementy. i aby tworzyć interesujące przejścia stron i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="16fab-163">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="16fab-164">Ponieważ WPF pozwala animować większość właściwości, nie tylko można animować większość obiektów WPF, można również użyć WPF do animowania tworzonych obiektów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="16fab-164">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Zrzut ekranu animowanego modułu.](./media/index/animate-custom-objects.png)

<span data-ttu-id="16fab-166">Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-166">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="16fab-167">Aby zapoznać się z przykładem wstępnym, zobacz [Galeria przykładów animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="16fab-167">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="16fab-168">Multimedia</span><span class="sxs-lookup"><span data-stu-id="16fab-168">Media</span></span>

<span data-ttu-id="16fab-169">Obrazy, wideo i audio to bogate w multimedia sposoby przekazywania informacji i środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="16fab-169">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="16fab-170">Obrazy</span><span class="sxs-lookup"><span data-stu-id="16fab-170">Images</span></span>

<span data-ttu-id="16fab-171">Obrazy, takie jak ikony, tła i nawet części animacji, są podstawową częścią większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16fab-171">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="16fab-172">Ze względu na to, że często trzeba używać obrazów, WPF udostępnia możliwość pracy z nimi na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="16fab-172">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="16fab-173">Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.</span><span class="sxs-lookup"><span data-stu-id="16fab-173">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="16fab-174">![Przykładowy zrzut ekranu z stylem](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="16fab-174">![Styling sample screenshot](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="16fab-175">Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-175">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="16fab-176">Wideo i audio</span><span class="sxs-lookup"><span data-stu-id="16fab-176">Video and Audio</span></span>

<span data-ttu-id="16fab-177">Podstawową funkcją funkcji graficznych platformy WPF jest zapewnienie natywnej obsługi pracy z multimediami, w tym wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="16fab-177">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="16fab-178">Poniższy przykład pokazuje, jak wstawić odtwarzacz multimedialny do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16fab-178">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="16fab-179"><xref:System.Windows.Controls.MediaElement>jest w stanie odtwarzać wideo i dźwięk, i jest wystarczająco rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="16fab-179"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="16fab-180">Aby uzyskać więcej informacji, zobacz [Omówienie multimediów](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-180">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16fab-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16fab-181">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="16fab-182">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="16fab-182">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="16fab-183">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="16fab-183">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="16fab-184">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="16fab-184">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="16fab-185">Malowanie obrazami, rysowaniem i Visual</span><span class="sxs-lookup"><span data-stu-id="16fab-185">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="16fab-186">Animacja i chronometraż Tematy porad</span><span class="sxs-lookup"><span data-stu-id="16fab-186">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="16fab-187">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="16fab-187">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="16fab-188">Przegląd Multimedia</span><span class="sxs-lookup"><span data-stu-id="16fab-188">Multimedia Overview</span></span>](multimedia-overview.md)
