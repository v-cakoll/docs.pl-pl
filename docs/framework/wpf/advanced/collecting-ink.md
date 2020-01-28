---
title: Zbieranie cyfrowego atramentu
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747030"
---
# <a name="collect-ink"></a><span data-ttu-id="788c3-102">Zbierz atrament</span><span class="sxs-lookup"><span data-stu-id="788c3-102">Collect Ink</span></span>

<span data-ttu-id="788c3-103">Platforma [Windows Presentation Foundation](../index.md) zbiera cyfrowy atrament jako rdzeń części swojej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="788c3-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="788c3-104">W tym temacie omówiono metody zbierania pisma odręcznego w Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="788c3-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="788c3-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="788c3-105">Prerequisites</span></span>

<span data-ttu-id="788c3-106">Aby skorzystać z poniższych przykładów, należy najpierw zainstalować program Visual Studio i Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="788c3-106">To use the following examples, you must first install Visual Studio and the Windows SDK.</span></span> <span data-ttu-id="788c3-107">Należy również zrozumieć, jak pisać aplikacje dla WPF.</span><span class="sxs-lookup"><span data-stu-id="788c3-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="788c3-108">Aby uzyskać więcej informacji na temat rozpoczynania pracy z programem WPF, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="788c3-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="788c3-109">Użyj elementu InkCanvas</span><span class="sxs-lookup"><span data-stu-id="788c3-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="788c3-110">Element <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> zapewnia najprostszy sposób zbierania pisma odręcznego w WPF.</span><span class="sxs-lookup"><span data-stu-id="788c3-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="788c3-111">Użyj elementu <xref:System.Windows.Controls.InkCanvas>, aby odbierać i wyświetlać dane wejściowe odręczne.</span><span class="sxs-lookup"><span data-stu-id="788c3-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="788c3-112">Często wprowadzasz atrament za pomocą pióra, który współdziała z dyskretyzatoram do tworzenia pociągnięć odręcznych.</span><span class="sxs-lookup"><span data-stu-id="788c3-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="788c3-113">Ponadto mysz może być używana zamiast pióra.</span><span class="sxs-lookup"><span data-stu-id="788c3-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="788c3-114">Utworzone pociągnięcia są reprezentowane jako obiekty <xref:System.Windows.Ink.Stroke> i mogą być przetwarzane programowo i przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="788c3-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="788c3-115"><xref:System.Windows.Controls.InkCanvas> umożliwia użytkownikom wybranie, zmodyfikowanie lub usunięcie istniejących <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="788c3-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="788c3-116">Używając języka XAML, można tak szybko skonfigurować kolekcje farb, jak dodanie elementu **InkCanvas** do drzewa.</span><span class="sxs-lookup"><span data-stu-id="788c3-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="788c3-117">Poniższy przykład dodaje <xref:System.Windows.Controls.InkCanvas> do domyślnego projektu WPF utworzonego w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="788c3-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="788c3-118">Element **InkCanvas** może także zawierać elementy podrzędne, dzięki czemu można dodać możliwości adnotacji odręcznej do niemal dowolnego typu elementu XAML.</span><span class="sxs-lookup"><span data-stu-id="788c3-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="788c3-119">Na przykład, aby dodać możliwości pisma odręcznego do elementu tekstowego, wystarczy, że jest on elementem podrzędnym <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="788c3-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="788c3-120">Dodawanie obsługi oznaczania obrazu za pomocą pisma odręcznego jest równie proste:</span><span class="sxs-lookup"><span data-stu-id="788c3-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="788c3-121">Tryby InkCollection</span><span class="sxs-lookup"><span data-stu-id="788c3-121">InkCollection Modes</span></span>

<span data-ttu-id="788c3-122"><xref:System.Windows.Controls.InkCanvas> zapewnia obsługę różnych trybów wprowadzania za pomocą właściwości <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="788c3-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="788c3-123">Manipulowanie atramentem</span><span class="sxs-lookup"><span data-stu-id="788c3-123">Manipulate Ink</span></span>

<span data-ttu-id="788c3-124"><xref:System.Windows.Controls.InkCanvas> zapewnia obsługę wielu operacji edycji farb.</span><span class="sxs-lookup"><span data-stu-id="788c3-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="788c3-125">Na przykład <xref:System.Windows.Controls.InkCanvas> obsługuje wymazywanie z tyłu pióra i nie jest wymagany żaden dodatkowy kod, aby dodać funkcje do elementu.</span><span class="sxs-lookup"><span data-stu-id="788c3-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="788c3-126">Wybór</span><span class="sxs-lookup"><span data-stu-id="788c3-126">Selection</span></span>

<span data-ttu-id="788c3-127">Ustawienie tryb wyboru jest proste, ponieważ ustawia właściwość <xref:System.Windows.Controls.InkCanvasEditingMode> do **wybrania**.</span><span class="sxs-lookup"><span data-stu-id="788c3-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="788c3-128">Poniższy kod ustawia tryb edycji na podstawie wartości <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="788c3-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="788c3-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="788c3-129">DrawingAttributes</span></span>

<span data-ttu-id="788c3-130">Użyj właściwości <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>, aby zmienić wygląd pociągnięć odręcznych.</span><span class="sxs-lookup"><span data-stu-id="788c3-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="788c3-131">Na przykład <xref:System.Windows.Ink.DrawingAttributes.Color%2A> element członkowski <xref:System.Windows.Ink.DrawingAttributes> ustawia kolor renderowanego <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="788c3-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="788c3-132">Poniższy przykład zmienia kolor wybranych pociągnięć na czerwony:</span><span class="sxs-lookup"><span data-stu-id="788c3-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="788c3-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="788c3-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="788c3-134">Właściwość <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> zapewnia dostęp do właściwości, takich jak wysokość, Szerokość i kolor pociągnięć, które mają zostać utworzone w <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="788c3-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="788c3-135">Po zmianie <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>wszystkie przyszłe pociągnięcia wprowadzane do <xref:System.Windows.Controls.InkCanvas> są renderowane z nowymi wartościami właściwości.</span><span class="sxs-lookup"><span data-stu-id="788c3-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="788c3-136">Oprócz modyfikacji <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> w pliku związanym z kodem, można użyć składni języka XAML do określania właściwości <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="788c3-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="788c3-137">W następnym przykładzie pokazano, jak ustawić właściwość <xref:System.Windows.Ink.DrawingAttributes.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="788c3-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="788c3-138">Aby użyć tego kodu, Utwórz nowy projekt WPF o nazwie "HelloInkCanvas" w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="788c3-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="788c3-139">Zastąp kod w pliku *MainWindow. XAML* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="788c3-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="788c3-140">Następnie Dodaj następujące programy obsługi zdarzeń przycisku do kodu związanego z kodem, wewnątrz klasy MainWindow:</span><span class="sxs-lookup"><span data-stu-id="788c3-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="788c3-141">Po skopiowaniu tego kodu naciśnij klawisz **F5** w programie Visual Studio, aby uruchomić program w debugerze.</span><span class="sxs-lookup"><span data-stu-id="788c3-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="788c3-142">Zauważ, jak <xref:System.Windows.Controls.StackPanel> umieszcza przyciski na górze <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="788c3-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="788c3-143">Jeśli spróbujesz użyć atramentu w górnej części przycisków, <xref:System.Windows.Controls.InkCanvas> zbiera i renderuje pismo odręczne za przyciskami.</span><span class="sxs-lookup"><span data-stu-id="788c3-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="788c3-144">Dzieje się tak, ponieważ przyciski są elementami równorzędnymi <xref:System.Windows.Controls.InkCanvas>, a nie elementami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="788c3-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="788c3-145">Ponadto przyciski są wyższe w kolejności z, dlatego atrament jest renderowany w tle.</span><span class="sxs-lookup"><span data-stu-id="788c3-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="788c3-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="788c3-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
