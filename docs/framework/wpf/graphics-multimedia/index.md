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
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112040"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="fe3be-102">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="fe3be-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="fe3be-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia obsługę multimediów, grafiki wektorowej, animacji i kompozycji zawartości, ułatwiając programistom tworzenie interesujących interfejsów użytkownika i treści.</span><span class="sxs-lookup"><span data-stu-id="fe3be-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="fe3be-104">Za pomocą programu Visual Studio można tworzyć grafiki wektorowe lub złożone animacje i integrować multimedia z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="fe3be-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="fe3be-105">W tym temacie przedstawiono funkcje grafiki, animacji i multimediów, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]które umożliwiają dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe3be-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="fe3be-106">Za pomocą WPF typów w usłudze systemu Windows jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="fe3be-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="fe3be-107">Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługa może nie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="fe3be-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="fe3be-108">Co nowego w grafice i multimediach w WPF 4</span><span class="sxs-lookup"><span data-stu-id="fe3be-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="fe3be-109">Wprowadzono kilka zmian związanych z grafiką i animacjami.</span><span class="sxs-lookup"><span data-stu-id="fe3be-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="fe3be-110">Zaokrąglanie układu</span><span class="sxs-lookup"><span data-stu-id="fe3be-110">Layout Rounding</span></span>

  <span data-ttu-id="fe3be-111">Gdy krawędź obiektu spadnie na środku urządzenia pikselowego, niezależny od DPI system graficzny może tworzyć artefakty renderowania, takie jak rozmyte lub półprzezroczyste krawędzie.</span><span class="sxs-lookup"><span data-stu-id="fe3be-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="fe3be-112">Poprzednie wersje WPF zawiera przyciąganie pikseli, aby pomóc w obsłudze tej sprawy.</span><span class="sxs-lookup"><span data-stu-id="fe3be-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="fe3be-113">Program Silverlight 2 wprowadził zaokrąglanie układu, które jest kolejnym sposobem przenoszenia elementów, tak aby krawędzie spadały na granice całych pikseli.</span><span class="sxs-lookup"><span data-stu-id="fe3be-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="fe3be-114">WPF WPF obsługuje teraz <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> zaokrąglanie układu z dołączoną właściwością na <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="fe3be-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="fe3be-115">Kompozycja buforowana</span><span class="sxs-lookup"><span data-stu-id="fe3be-115">Cached Composition</span></span>

  <span data-ttu-id="fe3be-116">Za pomocą <xref:System.Windows.Media.BitmapCache> nowych <xref:System.Windows.Media.BitmapCacheBrush> i klas, można buforować złożoną część drzewa wizualnego jako mapy bitowej i znacznie poprawić czas renderowania.</span><span class="sxs-lookup"><span data-stu-id="fe3be-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="fe3be-117">Mapa bitowa pozostaje wrażliwa na dane wejściowe użytkownika, takie jak kliknięcia myszą, i można ją malować na inne elementy, tak jak każdy pędzel.</span><span class="sxs-lookup"><span data-stu-id="fe3be-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="fe3be-118">Obsługa modułu cieniującego pikseli 3</span><span class="sxs-lookup"><span data-stu-id="fe3be-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="fe3be-119">WPF 4 opiera się <xref:System.Windows.Media.Effects.ShaderEffect> na podstawie pomocy technicznej wprowadzonej w WPF 3.5 SP1, umożliwiając aplikacjom do zapisu efektów przy użyciu Pixel Shader (PS) w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="fe3be-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="fe3be-120">Model modułu cieniującego PS 3.0 jest bardziej zaawansowany niż PS 2.0, co pozwala na jeszcze większy wpływ na obsługiwany sprzęt.</span><span class="sxs-lookup"><span data-stu-id="fe3be-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="fe3be-121">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="fe3be-121">Easing Functions</span></span>

  <span data-ttu-id="fe3be-122">Animacje można ulepszać za pomocą funkcji dynamiki, które zapewniają dodatkową kontrolę nad zachowaniem animacji.</span><span class="sxs-lookup"><span data-stu-id="fe3be-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="fe3be-123">Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby nadać animacji sprężyste zachowanie.</span><span class="sxs-lookup"><span data-stu-id="fe3be-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="fe3be-124">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Animation> typy dynamiki w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="fe3be-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="fe3be-125">Grafika i renderowanie</span><span class="sxs-lookup"><span data-stu-id="fe3be-125">Graphics and Rendering</span></span>

<span data-ttu-id="fe3be-126">WPF WPF obejmuje obsługę wysokiej jakości grafiki 2D.</span><span class="sxs-lookup"><span data-stu-id="fe3be-126">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="fe3be-127">Funkcja obejmuje pędzle, geometrie, obrazy, kształty i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="fe3be-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="fe3be-128">Aby uzyskać więcej informacji, zobacz [Grafika](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="fe3be-129">Renderowanie elementów graficznych opiera <xref:System.Windows.Media.Visual> się na klasie.</span><span class="sxs-lookup"><span data-stu-id="fe3be-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="fe3be-130">Struktura obiektów wizualnych na ekranie jest opisana przez drzewo wizualne.</span><span class="sxs-lookup"><span data-stu-id="fe3be-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="fe3be-131">Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="fe3be-132">Kształty 2D</span><span class="sxs-lookup"><span data-stu-id="fe3be-132">2D Shapes</span></span>

<span data-ttu-id="fe3be-133">WPF WPF udostępnia bibliotekę powszechnie używanych, wektorowych kształtów 2D, takich jak prostokąty i elipsy, które pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="fe3be-133">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram przedstawiający elipsy i prostokąty.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="fe3be-135">Te wewnętrzne kształty WPF są nie tylko kształty: są one programowalne elementy, które implementują wiele funkcji, których oczekujesz od większości typowych formantów, które obejmują klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="fe3be-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="fe3be-136">W poniższym przykładzie <xref:System.Windows.UIElement.MouseUp> pokazano, jak obsługiwać zdarzenie wywoływane przez kliknięcie <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="fe3be-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="fe3be-137">Na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dane wyjściowe dla poprzedniego znaczników i związanych z kodem.</span><span class="sxs-lookup"><span data-stu-id="fe3be-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno komunikatu z napisem "Kliknąłeś elipsę!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="fe3be-139">Aby uzyskać więcej informacji, zobacz [Kształty i rysunek podstawowy w przeglądzie WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="fe3be-140">Aby zapoznać się z przykładem wprowadzającym, zobacz [Przykład elementów kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="fe3be-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="fe3be-141">Geometrie 2D</span><span class="sxs-lookup"><span data-stu-id="fe3be-141">2D Geometries</span></span>

<span data-ttu-id="fe3be-142">Gdy kształty 2D, które zapewnia WPF nie są wystarczające, można użyć WPF obsługi geometrii i ścieżek do tworzenia własnych.</span><span class="sxs-lookup"><span data-stu-id="fe3be-142">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="fe3be-143">Na poniższej ilustracji pokazano, jak można używać geometrii do tworzenia kształtów jako pędzla rysunku i do przycinania innych elementów WPF.</span><span class="sxs-lookup"><span data-stu-id="fe3be-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Zrzut ekranu przedstawiający sposób tworzenia kształtów za pomocą geometrii.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="fe3be-145">Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="fe3be-146">Aby zapoznać się z próbką wprowadzającą, zobacz [Przykład geometrii](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="fe3be-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="fe3be-147">Efekty 2D</span><span class="sxs-lookup"><span data-stu-id="fe3be-147">2D Effects</span></span>

<span data-ttu-id="fe3be-148">WPF WPF udostępnia bibliotekę klas 2D, których można użyć do tworzenia różnych efektów.</span><span class="sxs-lookup"><span data-stu-id="fe3be-148">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="fe3be-149">Funkcja renderowania 2D WPF WPF umożliwia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] malowanie elementów, które mają gradienty, mapy bitowe, rysunki i klipy wideo; i manipulować nimi za pomocą obrotu, skalowania i pochylania.</span><span class="sxs-lookup"><span data-stu-id="fe3be-149">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="fe3be-150">Poniższa ilustracja podaje przykład wielu efektów, które można osiągnąć przy użyciu pędzli WPF.</span><span class="sxs-lookup"><span data-stu-id="fe3be-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Ilustracja przedstawiająca różne pędzle WPF i elementy malowania.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="fe3be-152">Aby uzyskać więcej informacji, zobacz [WPF Brushes Overview](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="fe3be-153">Aby zapoznać się z przykładem wprowadzającym, zobacz [Przykład pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="fe3be-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="fe3be-154">Renderowanie 3D</span><span class="sxs-lookup"><span data-stu-id="fe3be-154">3D Rendering</span></span>

<span data-ttu-id="fe3be-155">WPF WPF zapewnia zestaw możliwości renderowania 3D, które integrują się z obsługą grafiki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]2D w WPF w celu utworzenia bardziej ekscytującego układu i wizualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="fe3be-155">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="fe3be-156">Na jednym końcu spektrum WPF WPF umożliwia renderowanie obrazów 2D na powierzchniach kształtów 3D, co pokazuje poniższa ilustracja.</span><span class="sxs-lookup"><span data-stu-id="fe3be-156">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Zrzut ekranu przedstawiający przykład przedstawiający kształty 3D o różnych teksturach.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="fe3be-158">Aby uzyskać więcej informacji, zobacz [Omówienie grafiki 3D](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-158">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="fe3be-159">Aby zapoznać się z przykładem wprowadzającym, zobacz [Przykład bryły 3D](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="fe3be-159">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="fe3be-160">Animacja</span><span class="sxs-lookup"><span data-stu-id="fe3be-160">Animation</span></span>

<span data-ttu-id="fe3be-161">Użyj animacji, aby formanty i elementy rosły, wstrząsały, obracały się i zanikały; i tworzyć ciekawe przejścia stron i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="fe3be-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="fe3be-162">Ponieważ WPF umożliwia animowanie większości właściwości, nie tylko można animować większość obiektów WPF, można również użyć WPF do animowania obiektów niestandardowych, które tworzysz.</span><span class="sxs-lookup"><span data-stu-id="fe3be-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Zrzut ekranu animowanego sześcianu.](./media/index/animate-custom-objects.png)

<span data-ttu-id="fe3be-164">Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="fe3be-165">Aby zapoznać się z przykładem wprowadzającym, zobacz [Galeria przykładów animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="fe3be-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="fe3be-166">Multimedia</span><span class="sxs-lookup"><span data-stu-id="fe3be-166">Media</span></span>

<span data-ttu-id="fe3be-167">Obrazy, wideo i audio to bogate w multimedia sposoby przekazywania informacji i doświadczeń użytkowników.</span><span class="sxs-lookup"><span data-stu-id="fe3be-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="fe3be-168">Obrazy</span><span class="sxs-lookup"><span data-stu-id="fe3be-168">Images</span></span>

<span data-ttu-id="fe3be-169">Obrazy, które zawierają ikony, tła, a nawet części animacji, są podstawową częścią większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe3be-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="fe3be-170">Ponieważ często trzeba używać obrazów, WPF udostępnia możliwość pracy z nimi na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="fe3be-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="fe3be-171">Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.</span><span class="sxs-lookup"><span data-stu-id="fe3be-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="fe3be-172">![Przykładowy zrzut ekranu przedstawiający styl](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="fe3be-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="fe3be-173">Aby uzyskać więcej informacji, zobacz [Omówienie obrazowania](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="fe3be-174">Wideo i audio</span><span class="sxs-lookup"><span data-stu-id="fe3be-174">Video and Audio</span></span>

<span data-ttu-id="fe3be-175">Podstawową cechą możliwości grafiki WPF jest zapewnienie natywnej obsługi pracy z multimediami, która obejmuje wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="fe3be-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="fe3be-176">W poniższym przykładzie pokazano, jak wstawić odtwarzacz multimedialny do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe3be-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="fe3be-177"><xref:System.Windows.Controls.MediaElement>jest w stanie odtwarzać zarówno wideo, jak i audio i jest wystarczająco rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fe3be-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="fe3be-178">Aby uzyskać więcej informacji, zobacz [Przegląd multimediów](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe3be-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe3be-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe3be-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="fe3be-180">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="fe3be-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="fe3be-181">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="fe3be-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="fe3be-182">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="fe3be-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="fe3be-183">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="fe3be-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="fe3be-184">Animacja i chronometraż Tematy porad</span><span class="sxs-lookup"><span data-stu-id="fe3be-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="fe3be-185">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="fe3be-185">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="fe3be-186">Multimedia — przegląd</span><span class="sxs-lookup"><span data-stu-id="fe3be-186">Multimedia Overview</span></span>](multimedia-overview.md)
