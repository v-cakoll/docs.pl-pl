---
title: Grafika i multimedia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 013ae46e2d90a9eda42d33e95e590812489fa04b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="a2243-102">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="a2243-102">Graphics and Multimedia</span></span>
<a name="introduction"></a>
<span data-ttu-id="a2243-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia obsługę multimediów, grafiki wektorowej, animacji i zawartości kompozycji, dzięki czemu deweloperzy mogą tworzyć interesujące interfejsów użytkownika i zawartości.</span><span class="sxs-lookup"><span data-stu-id="a2243-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="a2243-104">Przy użyciu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], można utworzyć grafiki wektorowej lub złożonych animacji i integracji nośnika w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>  
  
 <span data-ttu-id="a2243-105">W tym temacie przedstawiono funkcje grafiki, animacji i multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które umożliwiają dodanie grafiki, efekty przejścia dźwięku i wideo do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2243-106">Używanie typów WPF w usłudze systemu Windows jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="a2243-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="a2243-107">Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługi mogą nie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="a2243-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="a2243-108">Nowości dotyczące grafiki i multimediów na platformie WPF 4</span><span class="sxs-lookup"><span data-stu-id="a2243-108">What's New with Graphics and Multimedia in WPF 4</span></span>  
 <span data-ttu-id="a2243-109">Kilka wprowadzono zmiany dotyczące grafiki i animacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-109">Several changes have been made related to graphics and animations.</span></span>  
  
-   <span data-ttu-id="a2243-110">Zaokrąglanie układu</span><span class="sxs-lookup"><span data-stu-id="a2243-110">Layout Rounding</span></span>  
  
     <span data-ttu-id="a2243-111">Podczas krawędzi obiektu znajduje się w środku urządzenia pikseli, system grafiki niezależny od DPI można utworzyć renderowania artefaktów, takich jak rozmyte lub półprzezroczysty krawędzi.</span><span class="sxs-lookup"><span data-stu-id="a2243-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="a2243-112">Poprzednie wersje WPF włączone przyciąganie pikseli, które dodatkowo ułatwią obsługę tego przypadku.</span><span class="sxs-lookup"><span data-stu-id="a2243-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="a2243-113">Silverlight 2 wprowadzono zaokrąglania układu, sposób można przenosić elementy, dzięki czemu znajdują się na cały pikseli.</span><span class="sxs-lookup"><span data-stu-id="a2243-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="a2243-114">WPF obsługuje teraz układu zaokrąglania z <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> dołączona właściwość <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="a2243-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>  
  
-   <span data-ttu-id="a2243-115">Kompozycja pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="a2243-115">Cached Composition</span></span>  
  
     <span data-ttu-id="a2243-116">Przy użyciu nowej <xref:System.Windows.Media.BitmapCache> i <xref:System.Windows.Media.BitmapCacheBrush> klasy, można buforować złożonych częścią drzewa wizualnego jako mapę bitową i znacznie zwiększyć czas renderowania.</span><span class="sxs-lookup"><span data-stu-id="a2243-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="a2243-117">Mapa bitowa reaguje na dane wejściowe użytkownika, takie jak kliknięcie myszą i malować na inne elementy, podobnie jak wszelkie pędzla.</span><span class="sxs-lookup"><span data-stu-id="a2243-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>  
  
-   <span data-ttu-id="a2243-118">Obsługa 3 cieniowania pikseli</span><span class="sxs-lookup"><span data-stu-id="a2243-118">Pixel Shader 3 Support</span></span>  
  
     <span data-ttu-id="a2243-119">WPF 4 kompilacje nad <xref:System.Windows.Media.Effects.ShaderEffect> Obsługa wprowadzone w WPF 3.5 z dodatkiem SP1, umożliwiając aplikacjom zapisać efekty przy użyciu programu do cieniowania pikseli (PS) w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="a2243-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="a2243-120">Model programu do cieniowania PS 3.0 jest bardziej złożone niż PS 2.0, dzięki czemu jeszcze bardziej skutków dla obsługiwanego sprzętu.</span><span class="sxs-lookup"><span data-stu-id="a2243-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>  
  
-   <span data-ttu-id="a2243-121">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="a2243-121">Easing Functions</span></span>  
  
     <span data-ttu-id="a2243-122">Można zwiększyć animacje z funkcji sterowania tempem zmian, które zapewniają dodatkową kontrolę nad zachowanie animacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="a2243-123">Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby zapewnić zachowanie o zmiennym rozmiarze animacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="a2243-124">Aby uzyskać więcej informacji, zobacz Typy sterowania tempem zmian w <xref:System.Windows.Media.Animation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a2243-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a><span data-ttu-id="a2243-125">Grafika i renderowania</span><span class="sxs-lookup"><span data-stu-id="a2243-125">Graphics and Rendering</span></span>  
 <span data-ttu-id="a2243-126">WPF obsługuje grafiki 2-D wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="a2243-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="a2243-127">Funkcje obejmują pędzle, mają geometrię, obrazy, kształty i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="a2243-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="a2243-128">Aby uzyskać więcej informacji, zobacz [grafiki](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-128">For more information, see [Graphics](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span></span> <span data-ttu-id="a2243-129">Renderowanie elementów graficznego opiera się na <xref:System.Windows.Media.Visual> klasy.</span><span class="sxs-lookup"><span data-stu-id="a2243-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="a2243-130">Struktura obiektów visual na ekranie została opisana w drzewie wizualnym.</span><span class="sxs-lookup"><span data-stu-id="a2243-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="a2243-131">Aby uzyskać więcej informacji, zobacz [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-131">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
### <a name="2-d-shapes"></a><span data-ttu-id="a2243-132">Kształty 2-D</span><span class="sxs-lookup"><span data-stu-id="a2243-132">2-D Shapes</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="a2243-133">zawiera bibliotekę często używane, rysowane wektor [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] kształtów, takich jak prostokąty i wielokropek, które na poniższej ilustracji przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="a2243-133"> provides a library of commonly used, vector-drawn [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>  
  
 <span data-ttu-id="a2243-134">![Wielokropki i prostokąty](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span><span class="sxs-lookup"><span data-stu-id="a2243-134">![Ellipses and rectangles](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span></span>  
  
 <span data-ttu-id="a2243-135">Te wewnętrzne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kształtów nie są po prostu kształtów: są programowalny elementy, które implementuje wiele funkcji, których można oczekiwać od najbardziej typowych formantów, które obejmują klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="a2243-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="a2243-136">Poniższy przykład przedstawia sposób obsługi <xref:System.Windows.UIElement.MouseUp> Zdarzenie wywoływane po kliknięciu <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="a2243-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>  
  
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
  
 <span data-ttu-id="a2243-137">Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i związane z kodem.</span><span class="sxs-lookup"><span data-stu-id="a2243-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>  
  
 <span data-ttu-id="a2243-138">![Okno z tekstem "kliknięto przycisk wielokropka &33;" ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span><span class="sxs-lookup"><span data-stu-id="a2243-138">![A window with the text "you clicked the ellipse&#33;"](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span></span>  
  
 <span data-ttu-id="a2243-139">Aby uzyskać więcej informacji, zobacz [kształtów i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-139">For more information, see [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="a2243-140">Dla przykładu wprowadzające, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="a2243-140">For an introductory sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
### <a name="2-d-geometries"></a><span data-ttu-id="a2243-141">2-D mają geometrię</span><span class="sxs-lookup"><span data-stu-id="a2243-141">2-D Geometries</span></span>  
 <span data-ttu-id="a2243-142">Gdy [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, który [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia nie są wystarczające, można użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługę mają geometrię i ścieżki do tworzenia własnych.</span><span class="sxs-lookup"><span data-stu-id="a2243-142">When the [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="a2243-143">Na poniższej ilustracji pokazano, jak używać mają geometrię Utwórz kształtów, jako pędzla do rysowania i obcina innych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów.</span><span class="sxs-lookup"><span data-stu-id="a2243-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>  
  
 <span data-ttu-id="a2243-144">![Różnych zastosowań ścieżki](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span><span class="sxs-lookup"><span data-stu-id="a2243-144">![Various uses of a Path](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span></span>  
  
 <span data-ttu-id="a2243-145">Aby uzyskać więcej informacji, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-145">For more information, see [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span> <span data-ttu-id="a2243-146">Dla przykładu wprowadzające, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="a2243-146">For an introductory sample, see [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
### <a name="2-d-effects"></a><span data-ttu-id="a2243-147">Efekty 2-D</span><span class="sxs-lookup"><span data-stu-id="a2243-147">2-D Effects</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="a2243-148">zawiera bibliotekę [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] klasy, które umożliwia tworzenie wielu efektów.</span><span class="sxs-lookup"><span data-stu-id="a2243-148"> provides a library of [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="a2243-149">[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Możliwości renderowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów, które mają gradientów, mapy bitowe, rysunki i wideo; i manipulowania nimi przy użyciu obracanie, skalowanie i pochylanie.</span><span class="sxs-lookup"><span data-stu-id="a2243-149">The [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="a2243-150">Na poniższej ilustracji przedstawiono przykładowy wiele efektów można osiągnąć za pomocą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Pędzle.</span><span class="sxs-lookup"><span data-stu-id="a2243-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>  
  
 <span data-ttu-id="a2243-151">![Ilustracja różnych pędzli](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span><span class="sxs-lookup"><span data-stu-id="a2243-151">![Illustration of different brushes](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span></span>  
  
 <span data-ttu-id="a2243-152">Aby uzyskać więcej informacji, zobacz [omówienie pędzle WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-152">For more information, see [WPF Brushes Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span></span> <span data-ttu-id="a2243-153">Dla przykładu wprowadzające, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="a2243-153">For an introductory sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a><span data-ttu-id="a2243-154">Renderowanie 3-D</span><span class="sxs-lookup"><span data-stu-id="a2243-154">3-D Rendering</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="a2243-155">zawiera zestaw [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] możliwości renderowania, które integrują się z [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obsługuje grafiki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w kolejności do tworzenia układu ciekawsze [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]i wizualizacja danych.</span><span class="sxs-lookup"><span data-stu-id="a2243-155"> provides a set of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering capabilities that integrate with [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="a2243-156">Na jednym końcu widma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia renderowanie [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazów na powierzchni [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] kształtów, co pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="a2243-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] images onto the surfaces of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] shapes, which the following illustration demonstrates.</span></span>  
  
 <span data-ttu-id="a2243-157">![Zrzut ekranu przedstawiający przykładowy Visual3D](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span><span class="sxs-lookup"><span data-stu-id="a2243-157">![Visual3D sample screen shot](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span></span>  
  
 <span data-ttu-id="a2243-158">Aby uzyskać więcej informacji, zobacz [3-Przegląd grafiki](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-158">For more information, see [3-D Graphics Overview](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span></span> <span data-ttu-id="a2243-159">Dla przykładu wprowadzające, zobacz [3-próbki stałych](http://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="a2243-159">For an introductory sample, see [3-D Solids Sample](http://go.microsoft.com/fwlink/?LinkID=159964).</span></span>  
  
<a name="animation"></a>   
## <a name="animation"></a><span data-ttu-id="a2243-160">Animacja</span><span class="sxs-lookup"><span data-stu-id="a2243-160">Animation</span></span>  
 <span data-ttu-id="a2243-161">Użyj animacji, aby wprowadzić formanty i elementy powiększania, potrząsanie pokrętła i stopniowe; i utwórz interesujące przejścia stron i inne.</span><span class="sxs-lookup"><span data-stu-id="a2243-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="a2243-162">Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia do animowania właściwości większości, tylko nie można animować większość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obiekty, można również użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do animowania tworzonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a2243-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>  
  
 <span data-ttu-id="a2243-163">![Obrazy modułu animowany](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span><span class="sxs-lookup"><span data-stu-id="a2243-163">![Images of an animated cube](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span></span>  
  
 <span data-ttu-id="a2243-164">Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-164">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="a2243-165">Dla przykładu wprowadzające, zobacz [galerii przykład animacji](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="a2243-165">For an introductory sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
<a name="media"></a>   
## <a name="media"></a><span data-ttu-id="a2243-166">Nośnik</span><span class="sxs-lookup"><span data-stu-id="a2243-166">Media</span></span>  
 <span data-ttu-id="a2243-167">Obrazy, wideo i audio metodami bogatych przekazywania informacji i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a2243-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>  
  
### <a name="images"></a><span data-ttu-id="a2243-168">Obrazy</span><span class="sxs-lookup"><span data-stu-id="a2243-168">Images</span></span>  
 <span data-ttu-id="a2243-169">Obrazów, które obejmują ikony, tła i nawet części animacji, są częścią podstawowych większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="a2243-170">Ponieważ często muszą używać obrazów, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia pracować z nimi w różny sposób.</span><span class="sxs-lookup"><span data-stu-id="a2243-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="a2243-171">Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.</span><span class="sxs-lookup"><span data-stu-id="a2243-171">The following illustration shows just one of those ways.</span></span>  
  
 <span data-ttu-id="a2243-172">![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="a2243-172">![Styling sample screen shot](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>  
  
 <span data-ttu-id="a2243-173">Aby uzyskać więcej informacji, zobacz [Imaging omówienie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-173">For more information, see [Imaging Overview](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span></span>  
  
### <a name="video-and-audio"></a><span data-ttu-id="a2243-174">Audio i wideo</span><span class="sxs-lookup"><span data-stu-id="a2243-174">Video and Audio</span></span>  
 <span data-ttu-id="a2243-175">Funkcja podstawowe możliwości grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest zapewnienie macierzystą obsługę do pracy z multimediów, w tym audio i wideo.</span><span class="sxs-lookup"><span data-stu-id="a2243-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="a2243-176">Poniższy przykład pokazuje, jak można umieścić Windows media player w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2243-176">The following example shows how to insert a media player into an application.</span></span>  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <span data-ttu-id="a2243-177"><xref:System.Windows.Controls.MediaElement>ma możliwość odtwarzania audio i wideo i jest rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2243-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="a2243-178">Aby uzyskać więcej informacji, zobacz [omówienie Multimedia](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2243-178">For more information, see the [Multimedia Overview](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2243-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2243-179">See Also</span></span>  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [<span data-ttu-id="a2243-180">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="a2243-180">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="a2243-181">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="a2243-181">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="a2243-182">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="a2243-182">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="a2243-183">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="a2243-183">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="a2243-184">Synchronizację</span><span class="sxs-lookup"><span data-stu-id="a2243-184">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="a2243-185">3-grafiki</span><span class="sxs-lookup"><span data-stu-id="a2243-185">3-D Graphics</span></span>](http://msdn.microsoft.com/library/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [<span data-ttu-id="a2243-186">Multimedia</span><span class="sxs-lookup"><span data-stu-id="a2243-186">Multimedia</span></span>](http://msdn.microsoft.com/library/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
