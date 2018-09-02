---
title: Zbieranie pisma odręcznego w aplikacjach WPF
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
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394932"
---
# <a name="collect-ink"></a><span data-ttu-id="f8a1a-102">Zbieranie pisma odręcznego</span><span class="sxs-lookup"><span data-stu-id="f8a1a-102">Collect Ink</span></span>

<span data-ttu-id="f8a1a-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platformy zbiera cyfrowy atrament w ramach podstawowych jego funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="f8a1a-104">W tym temacie omówiono metody do kolekcji pisma odręcznego w Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f8a1a-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8a1a-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f8a1a-105">Prerequisites</span></span>

<span data-ttu-id="f8a1a-106">Aby użyć poniższych przykładów, należy najpierw zainstalować program Visual Studio i [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8a1a-106">To use the following examples, you must first install Visual Studio and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="f8a1a-107">Należy również zrozumieć sposób pisania aplikacji dla WPF.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="f8a1a-108">Aby uzyskać więcej informacji na temat rozpoczynania pracy przy użyciu platformy WPF, zobacz [Instruktaż: Mój pierwszy aplikacji klasycznej WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="f8a1a-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="f8a1a-109">Użyj elementu InkCanvas</span><span class="sxs-lookup"><span data-stu-id="f8a1a-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="f8a1a-110"><xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> Element udostępnia najprostszy sposób zbieranie pisma odręcznego na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="f8a1a-111">Użyj <xref:System.Windows.Controls.InkCanvas> element do odbierania i wyświetlania danych wejściowych pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="f8a1a-112">Często danych wejściowych pisma odręcznego za pomocą pióra, która współdziała z dyskretyzatora, aby wygenerować pociągnięcia odręczne.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="f8a1a-113">Ponadto można użyć myszy zamiast pióra.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="f8a1a-114">Utworzono pociągnięć są reprezentowane jako <xref:System.Windows.Ink.Stroke> obiektów i ich można modyfikować programowo i przez użytkownika dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="f8a1a-115"><xref:System.Windows.Controls.InkCanvas> Pozwala użytkownikom wybrać, zmodyfikować lub usunąć istniejące <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="f8a1a-116">Przy użyciu XAML, możesz skonfigurować zbieranie pisma odręcznego równie łatwo, jak dodawanie **InkCanvas** elementu z drzewa.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="f8a1a-117">W poniższym przykładzie dodano <xref:System.Windows.Controls.InkCanvas> do domyślnego projektu WPF w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="f8a1a-118">**InkCanvas** elementu może również zawierać elementy podrzędne, dzięki czemu można dodać możliwości adnotacji pisma odręcznego prawie żadnego typu elementu XAML.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="f8a1a-119">Na przykład, umożliwiające dodanie funkcji pisma odręcznego do elementów tekstowych, po prostu Uczyń elementem podrzędnym elementu <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="f8a1a-120">Dodano obsługę Oznaczanie obrazu z pisma odręcznego jest równie proste:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="f8a1a-121">Tryby InkCollection</span><span class="sxs-lookup"><span data-stu-id="f8a1a-121">InkCollection Modes</span></span>

<span data-ttu-id="f8a1a-122"><xref:System.Windows.Controls.InkCanvas> Obsługuje różne dane wejściowe metody za pomocą jego <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="f8a1a-123">Manipulowanie pisma odręcznego</span><span class="sxs-lookup"><span data-stu-id="f8a1a-123">Manipulate Ink</span></span>

<span data-ttu-id="f8a1a-124"><xref:System.Windows.Controls.InkCanvas> Obsługuje wiele pisma odręcznego operacje edycji.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="f8a1a-125">Na przykład <xref:System.Windows.Controls.InkCanvas> wstecz pióra obsługuje wymazanie, a żaden dodatkowy kod nie jest potrzebna do dodawania funkcjonalności do elementu.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="f8a1a-126">Wybór</span><span class="sxs-lookup"><span data-stu-id="f8a1a-126">Selection</span></span>

<span data-ttu-id="f8a1a-127">Ustawienie trybu wyboru jest tak proste, jak ustawienie <xref:System.Windows.Controls.InkCanvasEditingMode> właściwości **wybierz**.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="f8a1a-128">Poniższy kod ustawia tryb edycji, w oparciu o wartość <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="f8a1a-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="f8a1a-129">DrawingAttributes</span></span>

<span data-ttu-id="f8a1a-130">Użyj <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> właściwości, aby zmienić wygląd pociągnięcia odręczne.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="f8a1a-131">Na przykład <xref:System.Windows.Ink.DrawingAttributes.Color%2A> członkiem <xref:System.Windows.Ink.DrawingAttributes> Ustawia kolor renderowanych <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="f8a1a-132">Poniższy przykład umożliwia zmianę koloru wybranych pociągnięć czerwony:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="f8a1a-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="f8a1a-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="f8a1a-134"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Właściwości zapewnia dostęp do właściwości, takie jak wysokość, szerokość i kolor pociągnięć, które zostały utworzone w <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="f8a1a-135">Po zmianie <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, wszystkie przyszłe pociągnięć zawierana <xref:System.Windows.Controls.InkCanvas> są renderowane przy użyciu nowej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="f8a1a-136">Oprócz modyfikowania <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> w pliku związanym z kodem, składnia XAML można użyć do określenia <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="f8a1a-137">Następny przykład pokazuje, jak ustawić <xref:System.Windows.Ink.DrawingAttributes.Color%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="f8a1a-138">Aby użyć tego kodu, Utwórz nowy projekt WPF w programie Visual Studio o nazwie "HelloInkCanvas".</span><span class="sxs-lookup"><span data-stu-id="f8a1a-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="f8a1a-139">Zastąp kod w *MainWindow.xaml* pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="f8a1a-140">Następnie dodaj poniższe procedury obsługi zdarzeń przycisku do kodzie pliku wewnątrz klasy MainWindow:</span><span class="sxs-lookup"><span data-stu-id="f8a1a-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="f8a1a-141">Po skopiowaniu tego kodu, naciśnij klawisz **F5** w programie Visual Studio, aby uruchomić program w debugerze.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="f8a1a-142">Zwróć uwagę sposób, w jaki <xref:System.Windows.Controls.StackPanel> umieszcza przycisków w górnej części <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="f8a1a-143">Jeśli zostanie podjęta próba pisma odręcznego w górnej części przyciski, <xref:System.Windows.Controls.InkCanvas> zbiera i renderowanie pisma odręcznego za pomocą przycisków.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="f8a1a-144">Jest to spowodowane przyciski są elementy równorzędne <xref:System.Windows.Controls.InkCanvas> w przeciwieństwie do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="f8a1a-145">Przyciski są także wyżej w porządku, więc pisma odręcznego jest renderowany za ich.</span><span class="sxs-lookup"><span data-stu-id="f8a1a-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a1a-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8a1a-146">See Also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>