---
title: Przegląd Moduły indeksowania układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111182"
---
# <a name="adorners-overview"></a><span data-ttu-id="cab76-102">Przegląd Moduły indeksowania układu</span><span class="sxs-lookup"><span data-stu-id="cab76-102">Adorners Overview</span></span>

<span data-ttu-id="cab76-103">Adorners są specjalnym <xref:System.Windows.FrameworkElement>typem , używane do dostarczania wizualnych wskazówek dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cab76-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="cab76-104">Wśród innych zastosowań Adorners może służyć do dodawania uchwytów funkcjonalnych do elementów lub podać informacje o stanie formantu.</span><span class="sxs-lookup"><span data-stu-id="cab76-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="cab76-105">Więcej o: Adorners</span><span class="sxs-lookup"><span data-stu-id="cab76-105">About Adorners</span></span>

<span data-ttu-id="cab76-106">Jest <xref:System.Windows.Documents.Adorner> to <xref:System.Windows.FrameworkElement> zwyczaj, który <xref:System.Windows.UIElement>jest powiązany z .</span><span class="sxs-lookup"><span data-stu-id="cab76-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="cab76-107">Adorners są renderowane <xref:System.Windows.Documents.AdornerLayer>w programie , który jest powierzchnią renderowania, która jest zawsze na szczycie element zdobione lub kolekcji elementów zdobione.</span><span class="sxs-lookup"><span data-stu-id="cab76-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="cab76-108">Renderowanie adorner jest niezależna od <xref:System.Windows.UIElement> renderowania, że adorner jest zobowiązany do.</span><span class="sxs-lookup"><span data-stu-id="cab76-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="cab76-109">Adorner jest zazwyczaj umieszczony względem elementu, do którego jest powiązany, przy użyciu standardowego początku współrzędnych 2D znajduje się w lewym górnym rogu elementu zdobione.</span><span class="sxs-lookup"><span data-stu-id="cab76-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="cab76-110">Typowe zastosowania adorners obejmują:</span><span class="sxs-lookup"><span data-stu-id="cab76-110">Common applications for adorners include:</span></span>

- <span data-ttu-id="cab76-111">Dodawanie uchwytów funkcjonalnych <xref:System.Windows.UIElement> do, które umożliwiają użytkownikowi manipulowanie elementem w jakiś sposób (zmień rozmiar, obróć, zmień położenie itp.).</span><span class="sxs-lookup"><span data-stu-id="cab76-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="cab76-112">Przekaż wizualne informacje zwrotne, aby wskazać różne stany lub w odpowiedzi na różne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cab76-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="cab76-113">Nakładaj dekoracje wizualne na . <xref:System.Windows.UIElement></span><span class="sxs-lookup"><span data-stu-id="cab76-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="cab76-114">Wizualnie maskować lub zastępować część <xref:System.Windows.UIElement>lub całość pliku .</span><span class="sxs-lookup"><span data-stu-id="cab76-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="cab76-115">zapewnia podstawową strukturę zdobiąc elementy wizualne.</span><span class="sxs-lookup"><span data-stu-id="cab76-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="cab76-116">W poniższej tabeli wymieniono typy podstawowe używane podczas ozdabiania obiektów i ich przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="cab76-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="cab76-117">Kilka przykładów użycia wykonaj następujące:</span><span class="sxs-lookup"><span data-stu-id="cab76-117">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="cab76-118">Abstrakcyjna klasa podstawowa, z której dziedziczą wszystkie implementacje adornera betonu.</span><span class="sxs-lookup"><span data-stu-id="cab76-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="cab76-119">Klasa reprezentująca warstwę renderowania dla adorner(ów) jednego lub więcej elementów ozdobionych.</span><span class="sxs-lookup"><span data-stu-id="cab76-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="cab76-120">Klasa, która umożliwia adorner warstwy do skojarzenia z kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="cab76-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="cab76-121">Implementowanie niestandardowego adornera</span><span class="sxs-lookup"><span data-stu-id="cab76-121">Implementing a Custom Adorner</span></span>

<span data-ttu-id="cab76-122">Adorners framework dostarczone [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przez ma na celu przede wszystkim do obsługi tworzenia niestandardowych adorners.</span><span class="sxs-lookup"><span data-stu-id="cab76-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="cab76-123">Niestandardowy adorner jest tworzony przez implementowanie klasy, <xref:System.Windows.Documents.Adorner> która dziedziczy z klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="cab76-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="cab76-124">Element nadrzędny <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> jest, który <xref:System.Windows.Documents.Adorner>renderuje , nie element jest zdobione.</span><span class="sxs-lookup"><span data-stu-id="cab76-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="cab76-125">W poniższym przykładzie pokazano klasy, która implementuje prosty adorner.</span><span class="sxs-lookup"><span data-stu-id="cab76-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="cab76-126">Przykład adorner po prostu zdobi rogi <xref:System.Windows.UIElement> z okręgów.</span><span class="sxs-lookup"><span data-stu-id="cab76-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="cab76-127">Na poniższej ilustracji przedstawiono simplecircleAdorner zastosowane do <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="cab76-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Zrzut ekranu przedstawiający pole tekstowe z ozdobami.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="cab76-129">Zachowanie renderowania dla Adorners</span><span class="sxs-lookup"><span data-stu-id="cab76-129">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="cab76-130">Należy pamiętać, że adorners nie zawierają żadnych nieodłączne zachowanie renderowania; zapewnienie, że adorner renderuje jest odpowiedzialny za implementator adorner.</span><span class="sxs-lookup"><span data-stu-id="cab76-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="cab76-131">Typowym sposobem implementowania zachowania renderowania jest <xref:System.Windows.UIElement.OnRender%2A> zastąpienie metody i <xref:System.Windows.Media.DrawingContext> użycie jednego lub więcej obiektów do renderowania wizualizacji adorner w razie potrzeby (jak pokazano w powyższym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="cab76-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="cab76-132">Wszystko, co znajduje się w warstwie adorner, jest renderowane na pozostałych ustawionych stylach.</span><span class="sxs-lookup"><span data-stu-id="cab76-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="cab76-133">Innymi słowy adorners są zawsze wizualnie na górze i nie można zastąpić za pomocą z-order.</span><span class="sxs-lookup"><span data-stu-id="cab76-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="cab76-134">Testy zdarzeń i trafień</span><span class="sxs-lookup"><span data-stu-id="cab76-134">Events and Hit Testing</span></span>

<span data-ttu-id="cab76-135">Adorners odbierać zdarzenia wejściowe, podobnie jak każdy inny <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="cab76-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="cab76-136">Ponieważ adorner zawsze ma wyższy porządek z niż element, który zdobi, adorner <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove>odbiera zdarzenia wejściowe (takie jak lub ), które mogą być przeznaczone dla podstawowego elementu zdobionego.</span><span class="sxs-lookup"><span data-stu-id="cab76-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="cab76-137">Adorner można nasłuchiwać niektórych zdarzeń wejściowych i przekazać je do podstawowego element zdobione przez ponowne podnoszenie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cab76-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="cab76-138">Aby włączyć pass-through testowania trafień elementów w <xref:System.Windows.UIElement.IsHitTestVisible%2A> adorner, ustaw właściwość testu trafienia **false** na adorner.</span><span class="sxs-lookup"><span data-stu-id="cab76-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="cab76-139">Aby uzyskać więcej informacji na temat testowania trafień, zobacz [Testowanie trafień w warstwie wizualnej](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="cab76-139">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="cab76-140">Ozdabianie pojedynczego interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cab76-140">Adorning a Single UIElement</span></span>

<span data-ttu-id="cab76-141">Aby powiązać adorner <xref:System.Windows.UIElement>z określonym , wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cab76-141">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="cab76-142">Wywołanie metody <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> statycznej, <xref:System.Windows.Documents.AdornerLayer> aby <xref:System.Windows.UIElement> uzyskać obiekt do zdobienia.</span><span class="sxs-lookup"><span data-stu-id="cab76-142">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="cab76-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>przechodzi w górę drzewa wizualnego, zaczynając od określonego <xref:System.Windows.UIElement>programu i zwraca pierwszą warstwę adorner, która zostanie wynajęta.</span><span class="sxs-lookup"><span data-stu-id="cab76-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="cab76-144">(Jeśli nie zostaną znalezione żadne warstwy adorner, metoda zwraca wartość null.)</span><span class="sxs-lookup"><span data-stu-id="cab76-144">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="cab76-145">Wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody, aby powiązać adorner do obiektu docelowego <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="cab76-145">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="cab76-146">Poniższy przykład wiąże SimpleCircleAdorner (pokazano powyżej) o <xref:System.Windows.Controls.TextBox> nazwie *myTextBox:*</span><span class="sxs-lookup"><span data-stu-id="cab76-146">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="cab76-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind adorner to another element is currently not supported Using to bind an adorner to another element is currently not supported.</span><span class="sxs-lookup"><span data-stu-id="cab76-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="cab76-148">Ozdabianie dzieci panelu</span><span class="sxs-lookup"><span data-stu-id="cab76-148">Adorning the Children of a Panel</span></span>

<span data-ttu-id="cab76-149">Aby powiązać adorner z <xref:System.Windows.Controls.Panel>elementami podrzędnymi , wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cab76-149">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="cab76-150">Wywołanie `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody, aby znaleźć warstwę adorner dla elementu, którego elementy podrzędne mają być zdobione.</span><span class="sxs-lookup"><span data-stu-id="cab76-150">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="cab76-151">Wyliczyć za pośrednictwem elementów podrzędnych <xref:System.Windows.Documents.AdornerLayer.Add%2A> elementu nadrzędnego i wywołać metodę powiązania adorner do każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="cab76-151">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="cab76-152">Poniższy przykład wiąże SimpleCircleAdorner (pokazano powyżej) do <xref:System.Windows.Controls.StackPanel> elementów podrzędnych o nazwie *myStackPanel:*</span><span class="sxs-lookup"><span data-stu-id="cab76-152">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="cab76-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cab76-153">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="cab76-154">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="cab76-154">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="cab76-155">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="cab76-155">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="cab76-156">Przegląd Rysowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="cab76-156">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="cab76-157">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="cab76-157">How-to Topics</span></span>](adorners-how-to-topics.md)
