---
title: "Przegląd Moduły indeksowania układu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47b43b1b9848f91e77448d41609d8be5d60ecda5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adorners-overview"></a><span data-ttu-id="fd1d8-102">Przegląd Moduły indeksowania układu</span><span class="sxs-lookup"><span data-stu-id="fd1d8-102">Adorners Overview</span></span>
<span data-ttu-id="fd1d8-103">Modułu definiowania układu kodu jest specjalnym rodzajem <xref:System.Windows.FrameworkElement>używane do zapewnienia wizualnych do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="fd1d8-104">Oprócz innych zastosowań modułu definiowania układu kodu może służyć do dodawania funkcjonalności dojść do elementów lub podaj informacje o formancie.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="fd1d8-105">Temat definiowania układu</span><span class="sxs-lookup"><span data-stu-id="fd1d8-105">About Adorners</span></span>  
 <span data-ttu-id="fd1d8-106"><xref:System.Windows.Documents.Adorner> Jest niestandardowy <xref:System.Windows.FrameworkElement> który jest powiązany <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="fd1d8-107">Modułu definiowania układu kodu są renderowane w <xref:System.Windows.Documents.AdornerLayer>, czyli powierzchnię renderowania, który jest zawsze element element lub zbiór elementów ze zdefiniowanym.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="fd1d8-108">Renderowanie moduł definiowania układu jest niezależna od renderowanie <xref:System.Windows.UIElement> powiązaną moduł definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="fd1d8-109">Moduł definiowania układu zazwyczaj znajduje się względem elementu, do którego jest powiązany, przy użyciu standardowych 2-D zerowy znajduje się w lewym górnym ze zdefiniowanym elementu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="fd1d8-110">Typowe zastosowania do definiowania układu obejmują:</span><span class="sxs-lookup"><span data-stu-id="fd1d8-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="fd1d8-111">Dodawanie funkcjonalności dojścia do <xref:System.Windows.UIElement> umożliwiających użytkownika do manipulowania elementem w jakiś sposób (zmiana rozmiaru, obracanie, zmiana położenia itp.).</span><span class="sxs-lookup"><span data-stu-id="fd1d8-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="fd1d8-112">Wizualne, aby wskazać różne stany, lub w odpowiedzi na różne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="fd1d8-113">Nakładki visual dekoracje na <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="fd1d8-114">Wizualne zamaskować lub zastąpienie części lub całości <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="fd1d8-115">zapewnia podstawową strukturę adorning elementów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-115"> provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="fd1d8-116">W poniższej tabeli wymieniono podstawowych typów używany, gdy adorning obiektów i ich przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="fd1d8-117">Należy wykonać kilka przykładów użycia.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="fd1d8-118">Abstrakcyjna klasa podstawowa, z której dziedziczy wszystkie implementacje konkretnego modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="fd1d8-119">Klasa reprezentująca warstwy renderowania dla adorner(s) elementów co najmniej jeden element.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="fd1d8-120">Klasa, która umożliwia warstwy modułu definiowania układu kodu ma zostać skojarzony z kolekcją elementów.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="fd1d8-121">Implementowanie niestandardowego modułu definiowania układu kodu</span><span class="sxs-lookup"><span data-stu-id="fd1d8-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="fd1d8-122">Dostarczone przez platformę modułu definiowania układu kodu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest przeznaczony głównie do obsługi tworzenia niestandardowych modułów definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="fd1d8-123">Niestandardowy moduł definiowania układu kodu jest tworzony przez implementującej klasy, która dziedziczy z klasy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd1d8-124">Element nadrzędny <xref:System.Windows.Documents.Adorner> jest <xref:System.Windows.Documents.AdornerLayer> która renderuje <xref:System.Windows.Documents.Adorner>, nie jest adorned element.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="fd1d8-125">Poniższy przykład przedstawia klasę zawierającą implementację prostego moduł definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="fd1d8-126">Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> z okręgi.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="fd1d8-127">Na poniższej ilustracji przedstawiono SimpleCircleAdorner stosowane do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="fd1d8-128">![Przykład definiowania układu: Pole tekstowe ze zdefiniowanym](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="fd1d8-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="fd1d8-129">Sposób renderowania modułu definiowania układu kodu</span><span class="sxs-lookup"><span data-stu-id="fd1d8-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="fd1d8-130">Należy pamiętać, że modułu definiowania układu kodu nie zawierają żadnych zachowania związanego z używaniem renderowania; zapewnienie, że moduł definiowania układu renderuje jest odpowiedzialny za implementujący modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="fd1d8-131">Jest to często stosowana metoda wdrażania sposób renderowania do przesłonięcia <xref:System.Windows.UIElement.OnRender%2A> — metoda i użyj co najmniej jeden <xref:System.Windows.Media.DrawingContext> obiekty do renderowania elementów wizualnych moduł definiowania układu, zgodnie z potrzebami (jak pokazano w powyższym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="fd1d8-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd1d8-132">Niczego umieszczone w warstwie modułu definiowania układu kodu jest renderowany na górze reszty wszystkie style, które zostało ustawione.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="fd1d8-133">Innymi słowy modułu definiowania układu kodu są zawsze wizualnie u góry i nie można zastąpić przy użyciu porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="fd1d8-134">Zdarzenia i testowania trafień</span><span class="sxs-lookup"><span data-stu-id="fd1d8-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="fd1d8-135">Definiowania układu odbierania zdarzeń wejściowych, podobnie jak każdy inny <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="fd1d8-136">Moduł definiowania układu ma zawsze wyższe porządek od elementu go adorns, moduł definiowania układu odbiera zdarzenia wejściowe (takie jak <xref:System.Windows.UIElement.Drop> lub <xref:System.Windows.UIElement.MouseMove>) mogą być przeznaczone dla podstawowych adorned elementu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="fd1d8-137">Moduł definiowania układu można nasłuchiwać określone zdarzenia wejściowe i przekazać je do odpowiedniego elementu ze zdefiniowanym przez ponownego podniesienie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="fd1d8-138">Przekazujący testowania trafień elementów w obszarze moduł definiowania układu, ustaw testu trafienia <xref:System.Windows.UIElement.IsHitTestVisible%2A> właściwości **false** na moduł definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="fd1d8-139">Aby uzyskać więcej informacji na temat testowania trafień zobacz</span><span class="sxs-lookup"><span data-stu-id="fd1d8-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="fd1d8-140">[Testowanie w warstwie Visual trafień](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="fd1d8-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="fd1d8-141">Adorning pojedynczy element UIElement</span><span class="sxs-lookup"><span data-stu-id="fd1d8-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="fd1d8-142">Aby powiązać modułu definiowania układu kodu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="fd1d8-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fd1d8-143">Wywołanie metody statycznej <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> uzyskanie <xref:System.Windows.Documents.AdornerLayer> obiekt do <xref:System.Windows.UIElement> do można adorned.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="fd1d8-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>przedstawiono w górę drzewa wizualnego, rozpoczynając od określonego <xref:System.Windows.UIElement>i zwraca znajdzie pierwszą warstwę modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="fd1d8-145">(Jeśli nie zostaną znalezione nie warstwy modułu definiowania układu kodu, metoda zwraca wartość null.)</span><span class="sxs-lookup"><span data-stu-id="fd1d8-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="fd1d8-146">Wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu w miejscu docelowym <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="fd1d8-147">Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="fd1d8-148">Przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać modułu definiowania układu kodu do innego elementu nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="fd1d8-149">Adorning elementy podrzędne panelu</span><span class="sxs-lookup"><span data-stu-id="fd1d8-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="fd1d8-150">Aby powiązać modułu definiowania układu kodu do elementów podrzędnych <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="fd1d8-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fd1d8-151">Wywołanie `static` metody <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można znaleźć warstwy modułu definiowania układu kodu dla elementu, którego elementy podrzędne mają być adorned.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="fd1d8-152">Wyliczenia elementów podrzędnych elementu nadrzędnego i wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu do każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="fd1d8-153">Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej) do elementów podrzędnych <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="fd1d8-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd1d8-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="fd1d8-155">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="fd1d8-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="fd1d8-156">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="fd1d8-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="fd1d8-157">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="fd1d8-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="fd1d8-158">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="fd1d8-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
