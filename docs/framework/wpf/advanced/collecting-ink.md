---
title: Zbieranie atramentu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f3effe358ba2d7accf1b0eea3493f63cfea6598
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="collecting-ink"></a><span data-ttu-id="65f09-102">Zbieranie atramentu</span><span class="sxs-lookup"><span data-stu-id="65f09-102">Collecting Ink</span></span>
<span data-ttu-id="65f09-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platformy zbiera elektroniczne pismo odręczne jako podstawowy element jej funkcji.</span><span class="sxs-lookup"><span data-stu-id="65f09-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="65f09-104">W tym temacie omówiono metody dla kolekcji odręczne w systemie Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="65f09-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="65f09-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="65f09-105">Prerequisites</span></span>  
 <span data-ttu-id="65f09-106">Aby użyć w poniższych przykładach, należy najpierw zainstalować [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] i [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65f09-106">To use the following examples, you must first install [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="65f09-107">Należy także zrozumienie sposobu pisania aplikacji dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65f09-107">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="65f09-108">Aby uzyskać więcej informacji na temat rozpoczynania pracy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="65f09-108">For more information about getting started with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="using-the-inkcanvas-element"></a><span data-ttu-id="65f09-109">Za pomocą elementu InkCanvas</span><span class="sxs-lookup"><span data-stu-id="65f09-109">Using the InkCanvas Element</span></span>  
 <span data-ttu-id="65f09-110"><xref:System.Windows.Controls.InkCanvas> Element udostępnia Najprostszym sposobem zbieranie pismo odręczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65f09-110">The <xref:System.Windows.Controls.InkCanvas> element provides the easiest way to collect ink in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="65f09-111"><xref:System.Windows.Controls.InkCanvas> Element jest podobny do [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) obiekt z [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] i starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="65f09-111">The <xref:System.Windows.Controls.InkCanvas> element is similar to the [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) object from the [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] and earlier versions.</span></span>  
  
 <span data-ttu-id="65f09-112">Użyj <xref:System.Windows.Controls.InkCanvas> element do pobierania i wyświetlania odręczne.</span><span class="sxs-lookup"><span data-stu-id="65f09-112">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="65f09-113">Często wejściowe odręczne przy użyciu pióra, współpracującej z dyskretyzatora, aby utworzyć pociągnięcia odręczne.</span><span class="sxs-lookup"><span data-stu-id="65f09-113">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="65f09-114">Ponadto można użyć myszy zamiast pióra.</span><span class="sxs-lookup"><span data-stu-id="65f09-114">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="65f09-115">Utworzona kolekcja strokes są reprezentowane jako <xref:System.Windows.Ink.Stroke> obiektów i ich może manipulować programowo i przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65f09-115">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="65f09-116"><xref:System.Windows.Controls.InkCanvas> , Użytkownicy mogą wybrać, zmodyfikować lub usunąć istniejące <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="65f09-116">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>  
  
 <span data-ttu-id="65f09-117">Przy użyciu języka XAML, możesz skonfigurować zbieranie pisma odręcznego równie łatwo, jak dodawanie `InkCanvas` elementu z drzewa.</span><span class="sxs-lookup"><span data-stu-id="65f09-117">By using XAML, you can set up ink collection as easily as adding an `InkCanvas` element to your tree.</span></span> <span data-ttu-id="65f09-118">W poniższym przykładzie dodano <xref:System.Windows.Controls.InkCanvas> do domyślnego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt utworzony w [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65f09-118">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project created in [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span></span>  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 <span data-ttu-id="65f09-119">`InkCanvas` Może również zawierać elementy podrzędne, umożliwiające dodanie funkcji adnotacji odręczne prawie każdego typu elementu XAML.</span><span class="sxs-lookup"><span data-stu-id="65f09-119">The `InkCanvas` element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="65f09-120">Na przykład, umożliwiające dodanie funkcji pisma odręcznego do elementu tekstu, po prostu była elementem podrzędnym <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="65f09-120">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 <span data-ttu-id="65f09-121">Dodawanie obsługi do oznaczania obrazu odręczne jest równie proste.</span><span class="sxs-lookup"><span data-stu-id="65f09-121">Adding support for marking up an image with ink is just as easy.</span></span>  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a><span data-ttu-id="65f09-122">Tryby InkCollection</span><span class="sxs-lookup"><span data-stu-id="65f09-122">InkCollection Modes</span></span>  
 <span data-ttu-id="65f09-123"><xref:System.Windows.Controls.InkCanvas> Zapewnia obsługę wejściowych różne metody za pomocą jego <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="65f09-123">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>  
  
### <a name="manipulating-ink"></a><span data-ttu-id="65f09-124">Manipulowanie odręcznego</span><span class="sxs-lookup"><span data-stu-id="65f09-124">Manipulating Ink</span></span>  
 <span data-ttu-id="65f09-125"><xref:System.Windows.Controls.InkCanvas> Zapewnia obsługę wielu odręczne operacje edycji.</span><span class="sxs-lookup"><span data-stu-id="65f09-125">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="65f09-126">Na przykład <xref:System.Windows.Controls.InkCanvas> wstecz pióra obsługuje wymazać z żaden dodatkowy kod, aby dodać funkcje do elementu.</span><span class="sxs-lookup"><span data-stu-id="65f09-126">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase with no additional code needed to add the functionality to the element.</span></span>  
  
#### <a name="selection"></a><span data-ttu-id="65f09-127">Wybór</span><span class="sxs-lookup"><span data-stu-id="65f09-127">Selection</span></span>  
 <span data-ttu-id="65f09-128">Ustawienie trybu wyboru jest tak proste, jak ustawienie <xref:System.Windows.Controls.InkCanvasEditingMode> właściwości **wybierz**.</span><span class="sxs-lookup"><span data-stu-id="65f09-128">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span> <span data-ttu-id="65f09-129">Poniższy kod ustawia tryb edycji, na podstawie wartości z <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="65f09-129">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a><span data-ttu-id="65f09-130">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="65f09-130">DrawingAttributes</span></span>  
 <span data-ttu-id="65f09-131">Użyj <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> właściwości, aby zmienić wygląd pociągnięcia odręczne.</span><span class="sxs-lookup"><span data-stu-id="65f09-131">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="65f09-132">Na przykład <xref:System.Windows.Ink.DrawingAttributes.Color%2A> członkiem <xref:System.Windows.Ink.DrawingAttributes> Ustawia kolor renderowanych <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="65f09-132">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="65f09-133">Poniższy przykład umożliwia zmianę wybranych pociągnięć kolor na czerwony.</span><span class="sxs-lookup"><span data-stu-id="65f09-133">The following example changes the color of the selected strokes to red.</span></span>  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a><span data-ttu-id="65f09-134">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="65f09-134">DefaultDrawingAttributes</span></span>  
 <span data-ttu-id="65f09-135"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Właściwości zapewnia dostęp do właściwości, takie jak wysokość, szerokość i kolor pociągnięć mogą być tworzone w <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="65f09-135">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="65f09-136">Po zmianie <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, wszystkie przyszłe pociągnięć wprowadzany do <xref:System.Windows.Controls.InkCanvas> są renderowane przy użyciu nowych wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="65f09-136">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>  
  
 <span data-ttu-id="65f09-137">Oprócz modyfikowania <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> w pliku związanym z kodem za pomocą składni języka XAML służący do określania <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="65f09-137">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span> <span data-ttu-id="65f09-138">Poniższy kod XAML przedstawia sposób ustawiania <xref:System.Windows.Ink.DrawingAttributes.Color%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="65f09-138">The following XAML code demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="65f09-139">Aby użyć tego kodu, Utwórz nową [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projektu o nazwie "HelloInkCanvas" w programie Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="65f09-139">To use this code, create a new [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project called "HelloInkCanvas" in Visual Studio 2005.</span></span> <span data-ttu-id="65f09-140">Zastąp kod w pliku Window1.xaml następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="65f09-140">Replace the code in the Window1.xaml file with the following code.</span></span>  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="65f09-141">Następnie dodaj poniższe obsługi zdarzeń przycisku do kodzie pliku wewnątrz klasy Window1.</span><span class="sxs-lookup"><span data-stu-id="65f09-141">Next, add the following button event handlers to the code behind file, inside the Window1 class.</span></span>  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 <span data-ttu-id="65f09-142">Po skopiowaniu tego kodu, naciśnij klawisz **F5** programu Microsoft Visual Studio 2005 do uruchomienia programu w debugerze.</span><span class="sxs-lookup"><span data-stu-id="65f09-142">After copying this code, press **F5** in Microsoft Visual Studio 2005 to run the program in the debugger.</span></span>  
  
 <span data-ttu-id="65f09-143">Powiadomienie jak <xref:System.Windows.Controls.StackPanel> umieszcza przycisków nad <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="65f09-143">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="65f09-144">Jeśli spróbujesz pismo odręczne na początku przyciski, <xref:System.Windows.Controls.InkCanvas> zbiera i renderuje pismo odręczne za pomocą przycisków.</span><span class="sxs-lookup"><span data-stu-id="65f09-144">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="65f09-145">Wynika to z faktu przyciski są elementy równorzędne <xref:System.Windows.Controls.InkCanvas> w przeciwieństwie do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="65f09-145">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="65f09-146">Przyciski są także wyżej w kolejności, więc pismo odręczne jest renderowany za ich.</span><span class="sxs-lookup"><span data-stu-id="65f09-146">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f09-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65f09-147">See Also</span></span>  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
