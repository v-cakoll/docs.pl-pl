---
title: Przegląd Moduły indeksowania układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b5788b3ddb14b1acae9c6661420ab439205d000b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591253"
---
# <a name="adorners-overview"></a><span data-ttu-id="f2f7d-102">Przegląd Moduły indeksowania układu</span><span class="sxs-lookup"><span data-stu-id="f2f7d-102">Adorners Overview</span></span>
<span data-ttu-id="f2f7d-103">Moduły definiowania układu są specjalnym typem <xref:System.Windows.FrameworkElement>, który jest używany w celu zapewnienia podpowiedzi wizualne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="f2f7d-104">Wśród innych zastosowań moduły definiowania układu może służyć do dodawania funkcjonalności dojść do elementów lub podaj informacje o kontrolce stanie.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="f2f7d-105">Moduły indeksowania układu — informacje</span><span class="sxs-lookup"><span data-stu-id="f2f7d-105">About Adorners</span></span>  
 <span data-ttu-id="f2f7d-106"><xref:System.Windows.Documents.Adorner> Jest niestandardowy <xref:System.Windows.FrameworkElement> , jest powiązany z <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f2f7d-107">Moduły indeksowania układu — zostaną zrenderowane w <xref:System.Windows.Documents.AdornerLayer>, czyli powierzchnię renderowania, który jest zawsze na górze elementu element lub kolekcję elementów element.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="f2f7d-108">Renderowanie moduł definiowania układu jest niezależny od renderowanie <xref:System.Windows.UIElement> powiązaną moduł definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="f2f7d-109">Moduł definiowania układu zwykle znajduje się względem elementu, do którego jest powiązany, przy użyciu standardowego źródła współrzędnych 2-D, znajduje się w lewym górnym rogu elementu element.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="f2f7d-110">Typowe dla modułów definiowania układu zastosowań:</span><span class="sxs-lookup"><span data-stu-id="f2f7d-110">Common applications for adorners include:</span></span>  
  
- <span data-ttu-id="f2f7d-111">Dodawanie funkcjonalności dojścia do <xref:System.Windows.UIElement> , dzięki którym użytkownika do manipulowania elementem w jakiś sposób (zmiana rozmiaru, obracanie, zmiana położenia itp.).</span><span class="sxs-lookup"><span data-stu-id="f2f7d-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
- <span data-ttu-id="f2f7d-112">Przekazać wizualną opinię, aby wskazać różne stany, lub w odpowiedzi na różne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
- <span data-ttu-id="f2f7d-113">Nakładki visual dekoracje na <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="f2f7d-114">Wizualnie maska lub zastąpić część lub całość <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="f2f7d-115">zapewnia podstawowe struktury adorning elementów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="f2f7d-116">W poniższej tabeli wymieniono podstawowe typy używane podczas adorning obiektów i ich przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="f2f7d-117">Wykonaj kilka przykładów użycia.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="f2f7d-118">Abstrakcyjna klasa bazowa, z którego dziedziczą wszystkie implementacji konkretnego modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="f2f7d-119">Klasa reprezentująca warstwy renderowania dla adorner(s) elementów co najmniej jeden element.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="f2f7d-120">Klasa, która umożliwia warstwy moduł definiowania układu kodu ma zostać skojarzony z kolekcją elementów.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="f2f7d-121">Implementowanie niestandardowego modułu definiowania układu kodu</span><span class="sxs-lookup"><span data-stu-id="f2f7d-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="f2f7d-122">Dostarczone przez platformę moduły definiowania układu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest przeznaczony głównie do obsługi tworzenia niestandardowych modułów definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="f2f7d-123">Niestandardowy moduł definiowania układu, w której jest tworzona poprzez implementację klasy, która dziedziczy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f7d-124">Element nadrzędny <xref:System.Windows.Documents.Adorner> jest <xref:System.Windows.Documents.AdornerLayer> która renderuje <xref:System.Windows.Documents.Adorner>, nie jest powiązany element.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="f2f7d-125">Poniższy przykład przedstawia klasę, która implementuje prosty moduł definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="f2f7d-126">Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> przy użyciu kółka.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="f2f7d-127">Na poniższej ilustracji przedstawiono SimpleCircleAdorner dotyczą <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 ![Zrzut ekranu pokazujący pole tekstowe element.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="f2f7d-129">Zachowanie renderowania dla modułów definiowania układu</span><span class="sxs-lookup"><span data-stu-id="f2f7d-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="f2f7d-130">Ważne jest, aby należy pamiętać, moduły definiowania układu nie ma żadnych zachowań nieprzerwaną pracę renderowania; zapewnienie, że moduł definiowania układu renderuje spoczywa implementujący moduł definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="f2f7d-131">Często stosowaną metodą wdrażania zachowanie renderowania jest zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody i używać co najmniej jednej <xref:System.Windows.Media.DrawingContext> obiekty do renderowania moduł definiowania układu wizualizacji, zgodnie z potrzebami (jak pokazano w powyższym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="f2f7d-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f7d-132">Cokolwiek umieszczone w warstwie moduł definiowania układu kodu jest renderowany na podstawie pozostałą część wszystkie style, które zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="f2f7d-133">Innymi słowy moduły definiowania układu są zawsze wizualnie u góry i nie można zastąpić przy użyciu porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="f2f7d-134">Zdarzenia i testowania trafień</span><span class="sxs-lookup"><span data-stu-id="f2f7d-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="f2f7d-135">Moduły definiowania układu odbierania zdarzeń wejściowych, podobnie jak każdy inny <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="f2f7d-136">Ponieważ moduł definiowania układu ma zawsze wyższy porządku niż element go adorns, moduł definiowania układu odbiera zdarzenia wejściowe (takie jak <xref:System.Windows.UIElement.Drop> lub <xref:System.Windows.UIElement.MouseMove>) mogą być przeznaczone dla podstawowych powiązany element.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="f2f7d-137">Moduł definiowania układu można wykrywać niektórych zdarzeń wejściowych i przekazać je do podstawowego elementu ze zdefiniowanym przez ponownego zgłaszania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="f2f7d-138">Aby włączyć, przekazywanego testowania trafień elementów w ramach modułu definiowania układu, należy ustawić testu trafienia <xref:System.Windows.UIElement.IsHitTestVisible%2A> właściwości **false** na moduł definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="f2f7d-139">Aby uzyskać więcej informacji na temat testowania trafień zobacz</span><span class="sxs-lookup"><span data-stu-id="f2f7d-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="f2f7d-140">[Test trafienia w warstwie Visual](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="f2f7d-140">[Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="f2f7d-141">Adorning pojedynczy element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f2f7d-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="f2f7d-142">Aby powiązać moduł definiowania układu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f2f7d-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="f2f7d-143">Wywołanie metody statycznej <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można pobrać <xref:System.Windows.Documents.AdornerLayer> dla obiektu <xref:System.Windows.UIElement> do być powiązany.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="f2f7d-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> przeprowadza górę drzewa wizualnego, rozpoczynając od określonego <xref:System.Windows.UIElement>i zwraca pierwszą warstwą moduł definiowania układu kodu znajdzie.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="f2f7d-145">(Jeśli nie warstwy moduł definiowania układu kodu nie zostaną znalezione, metoda zwraca wartość null.)</span><span class="sxs-lookup"><span data-stu-id="f2f7d-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="f2f7d-146">Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z obiektem docelowym <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="f2f7d-147">Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="f2f7d-148">Za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać moduł definiowania układu z innego elementu nie jest obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="f2f7d-149">Adorning elementy podrzędne panelu</span><span class="sxs-lookup"><span data-stu-id="f2f7d-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="f2f7d-150">Aby powiązać moduł definiowania układu z elementami podrzędnymi <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f2f7d-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="f2f7d-151">Wywołaj `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można odnaleźć warstwy moduł definiowania układu dla elementu, którego elementy podrzędne, które mają być powiązany.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="f2f7d-152">Wyliczyć elementy podrzędne elementu nadrzędnego, a wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="f2f7d-153">Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), z elementami podrzędnymi <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="f2f7d-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2f7d-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="f2f7d-155">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="f2f7d-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="f2f7d-156">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="f2f7d-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="f2f7d-157">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="f2f7d-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="f2f7d-158">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f2f7d-158">How-to Topics</span></span>](adorners-how-to-topics.md)
